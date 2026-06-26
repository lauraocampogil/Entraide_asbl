<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';
	import Button from '$lib/components/ui/Button.svelte';

	let {
		title,
		ctaLabel,
		ctaHref,
		cards
	}: {
		title: string;
		ctaLabel: string;
		ctaHref: string;
		cards: { id: number; title: string; description: string }[];
	} = $props();

	const icons: Record<number, string> = {
		1: `<svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
			<path d="M8 12h14M8 18h8M22 8v16M30 8l6 16M30 8l-6 16M28 14h8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
			<path d="M20 32l8 8M28 32l-8 8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
		</svg>`,
		2: `<svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
			<rect x="10" y="8" width="28" height="34" rx="3" stroke="currentColor" stroke-width="1.5"/>
			<line x1="16" y1="20" x2="32" y2="20" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
			<line x1="16" y1="26" x2="26" y2="26" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
		</svg>`,
		3: `<svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
			<circle cx="24" cy="22" r="14" stroke="currentColor" stroke-width="1.5"/>
			<path d="M24 8c-4 4-6 9-6 14s2 10 6 14" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
			<path d="M24 8c4 4 6 9 6 14s-2 10-6 14" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
			<line x1="10" y1="22" x2="38" y2="22" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
			<path d="M32 32l4 4M36 32l2 2" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
		</svg>`,
		4: `<svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
			<path d="M10 36V14a2 2 0 0 1 2-2h10c2 4 6 6 10 0h4a2 2 0 0 1 2 2v22" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
			<path d="M10 36c4-4 24-4 28 0" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
		</svg>`
	};
</script>

<section class="bg-background px-5 py-12 xl:px-20 xl:py-20">
	<!-- Header : tagline + titre -->
	<div class="flex flex-col items-center gap-3 mb-6 xl:mb-4 text-center">
		<Tagline label="Nos programmes" />
		<h2
			class="font-fustat font-medium text-mobile-title-xl xl:text-title-2xl text-dark leading-snug max-w-2xl"
		>
			{title}
		</h2>
	</div>

	<!-- Bouton aligné à droite -->
	<div class="flex justify-end mb-8 xl:mb-10">
		<Button href={ctaHref} label={ctaLabel} variant="inline" />
	</div>

	<!-- Cards -->
	<div class="flex flex-col gap-4 xl:grid xl:grid-cols-4 xl:gap-5">
		{#each cards as card}
			<div
				class="bg-white rounded-2xl px-6 py-8 flex flex-col items-center gap-4 text-center shadow-sm"
			>
				<!-- Icône -->
				<div class="text-dark">
					{@html icons[card.id] ?? icons[1]}
				</div>
				<!-- Titre -->
				<p class="font-fustat font-bold text-title-sm text-dark">
					{card.title}
				</p>
				<!-- Description -->
				<p class="font-fustat text-description text-dark-accent leading-relaxed">
					{card.description}
				</p>
			</div>
		{/each}
	</div>
</section>
