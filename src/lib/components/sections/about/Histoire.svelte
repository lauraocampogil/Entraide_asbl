<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';

	let {
		title,
		text
	}: {
		title: string;
		text: string;
	} = $props();
</script>

<section class="bg-background px-5 py-12 grid-section xl:py-20">
	<!-- ══ MOBILE : empilé ══ -->
	<div class="xl:hidden flex flex-col gap-6">
		<Tagline label="Notre histoire" />
		<h2 class="font-fustat font-medium text-mobile-title-xl text-dark leading-snug">
			{title}
		</h2>
		<div class="text-body text-dark leading-relaxed [&>p+p]:mt-4">
			{@html text}
		</div>
	</div>

	<!-- ══ DESKTOP : grid 8 cols × 2 rows ══ -->
	<!-- Row 1 : tagline + titre, col 1-3 -->
	<div class="hidden xl:flex col-span-3 row-start-1 flex-col gap-2">
		<Tagline label="Notre histoire" />
		<h2 class="text-title-xl text-dark leading-snug">
			{title}
		</h2>
	</div>

	<!-- Row 2 : texte col 4-8, sous le titre -->
	<div
		class="hidden xl:block col-span-5 col-start-4 row-start-2 text-body text-dark leading-relaxed [&>p+p]:mt-5"
	>
		{@html text}
	</div>
</section>
