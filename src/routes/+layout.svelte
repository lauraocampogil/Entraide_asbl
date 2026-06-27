<script lang="ts">
	import './layout.css';
	import Header from '$lib/components/layout/Header.svelte';
	import Footer from '$lib/components/layout/Footer.svelte';

	let { children } = $props();

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
			phone: '+32 486 89 90 58',
			email: 'anasta5853@gmail.com',
			adresse: 'Rue Moorslede 54, 1020 Bruxelles – Laeken'
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
			{ label: 'Politique de confidentialité', href: '/politique-de-confidentialite' }
		]
	};
</script>

<Header logo="/assets/svg/Logo-Entraide.svg" navigation={nav} />
{@render children()}
<Footer {...footer} />
