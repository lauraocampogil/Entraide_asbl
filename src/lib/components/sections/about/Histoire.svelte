<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';
	import Tagline from '$lib/components/ui/Tagline.svelte';

	let {
		title,
		text
	}: {
		title: string;
		text: string;
	} = $props();

	let sectionEl = $state<HTMLElement | null>(null);

	// Desktop
	let taglineEl = $state<HTMLElement | null>(null);
	let titleEl = $state<HTMLElement | null>(null);
	let textEl = $state<HTMLElement | null>(null);

	// Mobile
	let taglineMobileEl = $state<HTMLElement | null>(null);
	let titleMobileEl = $state<HTMLElement | null>(null);
	let textMobileEl = $state<HTMLElement | null>(null);

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		const tl = gsap.timeline({
			defaults: { ease: 'none' },
			scrollTrigger: {
				trigger: sectionEl,
				start: 'top 95%',
				end: 'top 25%',
				scrub: 1
			}
		});

		tl.fromTo(
			[taglineEl, taglineMobileEl],
			{ y: 30, opacity: 0 },
			{ y: 0, opacity: 1, duration: 1 }
		)
			.fromTo(
				[titleEl, titleMobileEl],
				{ y: 40, opacity: 0 },
				{ y: 0, opacity: 1, duration: 1 },
				'+=0.2'
			)
			.fromTo(
				[textEl, textMobileEl],
				{ y: 50, opacity: 0 },
				{ y: 0, opacity: 1, duration: 1 },
				'+=0.2'
			);

		return () => {
			ScrollTrigger.getAll().forEach((t) => t.kill());
		};
	});
</script>

<section bind:this={sectionEl} class="bg-background px-5 py-12 grid-section xl:py-20 xl:gap-y-8">
	<!-- ══ MOBILE : empilé ══ -->
	<div class="xl:hidden flex flex-col gap-3">
		<div bind:this={taglineMobileEl} style="opacity:0">
			<Tagline label="Notre histoire" />
		</div>
		<h2 bind:this={titleMobileEl} class="text-mobile-title-xl text-dark" style="opacity:0">
			{title}
		</h2>
		<div bind:this={textMobileEl} class="text-body text-dark [&>p+p]:mt-4" style="opacity:0">
			{@html text}
		</div>
	</div>

	<!-- ══ DESKTOP : grid 8 cols × 2 rows ══ -->
	<!-- Row 1 : tagline + titre, col 1-3 -->
	<div class="hidden xl:flex col-span-3 row-start-1 flex-col gap-2">
		<div bind:this={taglineEl} style="opacity:0">
			<Tagline label="Notre histoire" />
		</div>
		<h2 bind:this={titleEl} class="text-title-xl text-dark leading-snug" style="opacity:0">
			{title}
		</h2>
	</div>

	<!-- Row 2 : texte col 4-8, sous le titre -->
	<div
		bind:this={textEl}
		class="hidden xl:block col-span-5 col-start-4 row-start-2 text-body text-dark leading-relaxed [&>p+p]:mt-5"
		style="opacity:0"
	>
		{@html text}
	</div>
</section>
