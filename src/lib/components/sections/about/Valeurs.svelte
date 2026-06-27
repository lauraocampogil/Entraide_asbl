<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';

	let {
		title,
		valeurs
	}: {
		title: string;
		valeurs: { id: number; svg: string; item: string }[];
	} = $props();
</script>

<section class="bg-primary-dark px-5 py-12 xl:px-20 xl:py-16">
	<!-- Tagline + titre -->
	<div class="flex flex-col items-center gap-4 mb-10 xl:mb-14 text-center">
		<Tagline label="Nos valeurs" />
		<h2
			class="font-fustat font-medium text-mobile-title-xl xl:text-title-2xl text-white leading-snug"
		>
			{title}
		</h2>
	</div>

	<!-- Grille : 3 col mobile, 6 col desktop -->
	<div class="grid grid-cols-3 xl:grid-cols-6 gap-6 xl:gap-8 max-w-4xl mx-auto">
		{#each valeurs as valeur}
			<div class="flex flex-col items-center gap-3">
				<!-- Icône dans card blanche -->
				<div
					class="w-20 h-20 xl:w-24 xl:h-24 bg-white rounded-2xl xl:rounded-3xl flex items-center justify-center shadow-sm"
				>
					<img
						src={valeur.svg}
						alt={valeur.item}
						class="w-10 h-10 xl:w-12 xl:h-12 object-contain"
					/>
				</div>
				<!-- Label -->
				<span class="font-fustat text-description xl:text-body text-white text-center">
					{valeur.item}
				</span>
			</div>
		{/each}
	</div>
</section>
