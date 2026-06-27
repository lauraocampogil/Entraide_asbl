<script lang="ts">
	let {
		title,
		cards
	}: {
		title: string;
		cards: { id: number; title: string; description: string }[];
	} = $props();
</script>

<section class="bg-background px-5 py-12 xl:px-20 xl:py-20">
	<!-- Titre -->
	<h2
		class="font-fustat font-medium text-mobile-title-2xl xl:text-title-2xl text-dark mb-8 xl:mb-10"
	>
		{title}
	</h2>

	<!-- ══ MOBILE : empilé ══ -->
	<div class="xl:hidden flex flex-col gap-10">
		{#each cards as card, i}
			<div class="relative">
				<!-- Blob au-dessus de la card -->
				<div
					class="absolute -top-6 right-4 w-14 h-14 z-0 {i === 0
						? 'text-tertiary'
						: 'text-secondary'}"
					aria-hidden="true"
				>
					<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
						<path
							d="M38.9,-64.1C50.2,-55.5,59.2,-44.3,65.1,-31.5C71,-18.7,73.7,-4.4,71.7,9.4C69.7,23.3,63,36.6,53.1,47.2C43.2,57.9,30.1,65.9,15.7,70.3C1.4,74.7,-14.2,75.4,-27.8,70.2C-41.4,65,-52.9,54,-60.2,40.9C-67.5,27.8,-70.5,12.6,-69.3,-2.1C-68.1,-16.8,-62.6,-31,-53.4,-42C-44.2,-53,-31.3,-60.8,-17.8,-65.8C-4.3,-70.8,9.8,-72.9,22.8,-71.3C35.8,-69.6,27.6,-72.7,38.9,-64.1Z"
							transform="translate(100 100) scale(0.88)"
						/>
					</svg>
				</div>
				<!-- Card -->
				<div class="relative z-10 bg-white rounded-2xl px-6 py-8 shadow-sm">
					<h3 class="font-fustat font-medium text-mobile-title-xl text-dark mb-4">
						{card.title}
					</h3>
					<p class="font-fustat text-description text-dark-accent leading-relaxed">
						{card.description}
					</p>
				</div>
			</div>
		{/each}
	</div>

	<!-- ══ DESKTOP : 2 colonnes ══ -->
	<div class="hidden xl:grid xl:grid-cols-2 xl:gap-6">
		{#each cards as card, i}
			<div class="relative pt-10">
				<!-- Blob au-dessus -->
				<div
					class="absolute top-0 right-6 w-16 h-16 z-0 {i === 0
						? 'text-tertiary'
						: 'text-secondary'}"
					aria-hidden="true"
				>
					<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
						<path
							d="M38.9,-64.1C50.2,-55.5,59.2,-44.3,65.1,-31.5C71,-18.7,73.7,-4.4,71.7,9.4C69.7,23.3,63,36.6,53.1,47.2C43.2,57.9,30.1,65.9,15.7,70.3C1.4,74.7,-14.2,75.4,-27.8,70.2C-41.4,65,-52.9,54,-60.2,40.9C-67.5,27.8,-70.5,12.6,-69.3,-2.1C-68.1,-16.8,-62.6,-31,-53.4,-42C-44.2,-53,-31.3,-60.8,-17.8,-65.8C-4.3,-70.8,9.8,-72.9,22.8,-71.3C35.8,-69.6,27.6,-72.7,38.9,-64.1Z"
							transform="translate(100 100) scale(0.88)"
						/>
					</svg>
				</div>
				<!-- Card -->
				<div class="relative z-10 bg-white rounded-2xl px-8 py-10 shadow-sm h-full">
					<h3 class="font-fustat font-medium text-title-lg text-dark mb-4">
						{card.title}
					</h3>
					<p class="font-fustat text-body text-dark-accent leading-relaxed">
						{card.description}
					</p>
				</div>
			</div>
		{/each}
	</div>
</section>
