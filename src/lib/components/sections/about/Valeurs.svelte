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

<section class="bg-primary-dark px-5 py-12 grid-section xl:py-16">
	<!-- Tagline + titre -->
	<div class="flex flex-col items-center gap-2 mb-10 xl:mb-14 text-center col-span-8">
		<Tagline label="Nos valeurs" />
		<h2 class="text-mobile-title-xl xl:text-title-xl text-white leading-snug">
			{title}
		</h2>
	</div>

	<!-- Grille : 3 col mobile, 6 col desktop -->
	<div class="col-span-8 grid grid-cols-3 xl:grid-cols-6 gap-6 xl:gap-20 max-w-4xl mx-auto">
		{#each valeurs as valeur}
			<div class="flex flex-col items-center gap-3">
				<!-- Icône dans card blanche -->
				<div
					class="w-20 h-20 xl:w-21 xl:h-21 bg-white rounded-[20px] xl:rounded-[30px] flex items-center justify-center"
				>
					<img
						src={valeur.svg}
						alt={valeur.item}
						class="w-10 h-10 xl:w-12 xl:h-12 object-contain"
					/>
				</div>
				<!-- Label -->
				<span class="text-body xl:text-tab text-white text-center">
					{valeur.item}
				</span>
			</div>
		{/each}
	</div>
</section>
