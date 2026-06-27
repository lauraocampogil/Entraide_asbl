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

<section class="bg-background px-5 py-12 xl:px-20 xl:py-20">
	<!-- ══ MOBILE : empilé ══ -->
	<div class="xl:hidden flex flex-col gap-6">
		<Tagline label="Notre histoire" />
		<h2 class="font-fustat font-medium text-mobile-title-2xl text-dark leading-snug">
			{title}
		</h2>
		<div class="font-fustat text-description text-dark leading-relaxed flex flex-col gap-4">
			{@html text}
		</div>
	</div>

	<!-- ══ DESKTOP : 2 colonnes ══ -->
	<div class="hidden xl:grid xl:grid-cols-8 xl:gap-x-5">
		<!-- Col gauche : tagline + titre -->
		<div class="col-span-3 flex flex-col gap-5 pr-8">
			<Tagline label="Notre histoire" />
			<h2 class="font-fustat font-medium text-title-2xl text-dark leading-snug">
				{title}
			</h2>
		</div>

		<!-- Col droite : texte -->
		<div
			class="col-span-5 col-start-4 font-fustat text-body text-dark leading-relaxed flex flex-col gap-5 pt-1"
		>
			{@html text}
		</div>
	</div>
</section>
