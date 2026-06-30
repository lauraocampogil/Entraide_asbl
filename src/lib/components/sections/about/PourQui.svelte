<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	let {
		title,
		cards
	}: {
		title: string;
		cards: { id: number; title: string; description: string }[];
	} = $props();

	const shapes = [
		{ src: '/assets/svg/Bol.svg', alt: '' },
		{ src: '/assets/svg/Star.svg', alt: '' }
	];

	let sectionEl = $state<HTMLElement | null>(null);
	let titleEl = $state<HTMLElement | null>(null);
	let titleMobileEl = $state<HTMLElement | null>(null);
	let shapesActive = $state(false);

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		const mm = gsap.matchMedia();

		mm.add(
			{
				isMobile: '(max-width: 1279px)',
				isDesktop: '(min-width: 1280px)'
			},
			(context) => {
				const { isMobile } = context.conditions as { isMobile: boolean };

				const tl = gsap.timeline({
					defaults: { ease: 'none' },
					scrollTrigger: {
						trigger: sectionEl,
						start: 'top 95%',
						end: isMobile ? 'top 5%' : 'top 25%',
						scrub: 1
					}
				});

				tl.fromTo(
					[titleEl, titleMobileEl],
					{ y: 40, opacity: 0 },
					{ y: 0, opacity: 1, duration: 1 }
				);

				const shapeTrigger = ScrollTrigger.create({
					trigger: sectionEl,
					start: 'top 80%',
					once: true,
					onEnter: () => (shapesActive = true)
				});

				shapesActive = shapeTrigger.isActive;
			}
		);

		const handleLoad = () => ScrollTrigger.refresh();
		window.addEventListener('load', handleLoad);

		return () => {
			window.removeEventListener('load', handleLoad);
			mm.revert();
		};
	});
</script>

<section
	bind:this={sectionEl}
	class="grid-section sm-grid-section bg-background px-5 sm:px-8 md:px-10 lg:px-12 py-12 xl:py-20 3xl:container 3xl:mx-auto"
>
	<!-- ══ MOBILE/TABLETTE jusqu'à xl ══ -->
	<div class="xl:hidden col-span-8 sm:col-span-8 flex flex-col gap-10">
		<h2 bind:this={titleMobileEl} class="text-mobile-title-xl text-dark" style="opacity:0">
			{title}
		</h2>
		<div class="flex flex-col md:grid md:grid-cols-2 gap-10 md:gap-6">
			{#each cards as card, i}
				<div class="relative">
					<div
						class="absolute -top-8 right-2 w-16 h-16 z-10 {shapesActive ? 'animate-spin-slow' : ''}"
						aria-hidden="true"
					>
						<img src={shapes[i % shapes.length].src} alt="" class="w-full h-full object-contain" />
					</div>
					<div class="relative z-0 bg-white rounded-[30px] px-6 py-8 h-full">
						<h3 class="text-mobile-title-lg text-dark mb-2">{card.title}</h3>
						<p class="text-body text-dark">{card.description}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>

	<!-- ══ DESKTOP : titre + cards dans la grid ══ -->
	<h2
		bind:this={titleEl}
		class="hidden xl:block col-span-8 text-title-xl text-dark mb-4"
		style="opacity:0"
	>
		{title}
	</h2>

	{#each cards as card, i}
		<div class="hidden xl:block col-span-4 relative pt-12">
			<div
				class="absolute -top-5 right-1 w-30 h-30 z-10 {shapesActive ? 'animate-spin-slow' : ''}"
				aria-hidden="true"
			>
				<img src={shapes[i % shapes.length].src} alt="" class="w-full h-full object-contain" />
			</div>
			<div class="relative z-0 bg-white rounded-[30px] px-8 py-10 h-full">
				<h3 class="text-title-lg text-dark mb-3">{card.title}</h3>
				<p class="text-body text-dark">{card.description}</p>
			</div>
		</div>
	{/each}
</section>

<style>
	@keyframes spin-slow {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}
	.animate-spin-slow {
		animation: spin-slow 15s linear infinite;
	}
</style>
