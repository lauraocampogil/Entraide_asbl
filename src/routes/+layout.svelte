<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';
	import Lenis from 'lenis';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';
	import { page } from '$app/state';
	import { afterNavigate } from '$app/navigation';
	import Loader from '$lib/components/layout/Loader.svelte';
	import Header from '$lib/components/layout/Header.svelte';
	import Footer from '$lib/components/layout/Footer.svelte';
	import CookieBanner from '$lib/components/ui/CookieBanner.svelte';
	import { loaderDone } from '$lib/stores/loader';

	let { children } = $props();

	const legalPages = ['/mentions-legales', '/politique-de-confidentialite', '/cookies'];
	const isLegalPage = $derived(legalPages.includes(page.url.pathname) || page.error !== null);

	const canonicalUrl = $derived(`https://entraide-bruxelles.be${page.url.pathname}`);

	const nav = {
		links: [
			{ label: 'Qui sommes-nous?', href: '/qui-sommes-nous' },
			{ label: 'Nos activités', href: '/nos-activites' },
			{ label: 'Info pratique', href: '/info-pratique' }
		]
	};

	const footer = {
		logo: '/assets/svg/Logo_Entraide_horizontal.svg',
		tagline: "Apprendre, s'intégrer\net bien vivre à Bruxelles",
		instagram: { href: 'https://instagram.com' },
		facebook: { href: 'https://facebook.com' },
		contact: {
			email: 'anasta5853@gmail.com',
			adresse: 'Rue Moorslede 54,\n1020 Bruxelles, Laeken'
		},
		liens: {
			links: [
				{ label: 'Accueil', href: '/' },
				{ label: 'Qui sommes-nous', href: '/qui-sommes-nous' },
				{ label: 'Nos activités', href: '/nos-activites' },
				{ label: 'Info pratique', href: '/info-pratique' }
			]
		},
		legal: [
			{ label: 'Mentions Légales', href: '/mentions-legales' },
			{ label: 'Politique de confidentialité', href: '/politique-de-confidentialite' },
			{ label: 'Cookies', href: '/cookies' }
		]
	};

	let lenisInstance: Lenis | null = null;

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		const lenis = new Lenis({
			duration: 1.2,
			easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
			smoothWheel: true
		});
		lenisInstance = lenis;

		lenis.on('scroll', ScrollTrigger.update);

		gsap.ticker.add((time) => {
			lenis.raf(time * 1000);
		});
		gsap.ticker.lagSmoothing(0);

		return () => {
			lenis.destroy();
			gsap.ticker.remove((time) => lenis.raf(time * 1000));
		};
	});

	// Remonte en haut à chaque navigation
	afterNavigate(() => {
		if (lenisInstance) {
			lenisInstance.scrollTo(0, { immediate: true });
		} else {
			window.scrollTo(0, 0);
		}
	});
</script>

<svelte:head>
	<link rel="canonical" href={canonicalUrl} />
</svelte:head>

<Loader />

{#if !isLegalPage}
	<Header logo="/assets/svg/Logo-Entraide.svg" navigation={nav} />
{/if}

{@render children()}

{#if !isLegalPage}
	<Footer {...footer} />
{/if}

{#if $loaderDone}
	<CookieBanner />
{/if}
