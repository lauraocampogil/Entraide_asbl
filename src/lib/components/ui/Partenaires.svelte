<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';

	let {
		description,
		images
	}: {
		description: string;
		images: { id: number; src: string; alt: string }[];
	} = $props();

	// Duplique les logos pour le scroll infini
	const doubled = $derived([...images, ...images]);
</script>

<section class="bg-primary-dark py-10 xl:py-14 overflow-hidden">
	<!-- Tagline + description -->
	<div class="px-5 xl:px-20 flex flex-col items-center gap-4 mb-10 xl:mb-12 text-center">
		<Tagline label="Nos partenaires" />
		<p
			class="font-fustat text-mobile-title-xl xl:text-title-lg font-medium text-white leading-snug max-w-3xl"
		>
			{description}
		</p>
	</div>

	<!-- Slider infini -->
	<div class="relative w-full">
		<div class="flex gap-4 animate-scroll w-max">
			{#each doubled as img}
				<div
					class="shrink-0 h-14 xl:h-16 bg-white rounded-lg px-4 flex items-center justify-center shadow-sm"
				>
					<img
						src={img.src}
						alt={img.alt}
						class="h-10 xl:h-12 w-auto object-contain"
						loading="lazy"
					/>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	@keyframes scroll {
		0% {
			transform: translateX(0);
		}
		100% {
			transform: translateX(-50%);
		}
	}

	.animate-scroll {
		animation: scroll 30s linear infinite;
	}

	.animate-scroll:hover {
		animation-play-state: paused;
	}
</style>
