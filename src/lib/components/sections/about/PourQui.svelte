<script lang="ts">
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
</script>

<section class="bg-background px-5 py-12 xl:py-20 grid-section">
	<!-- ══ MOBILE : titre + cards empilés ══ -->
	<div class="xl:hidden col-span-8 flex flex-col gap-10">
		<h2 class="text-mobile-title-xl text-dark">{title}</h2>
		{#each cards as card, i}
			<div class="relative">
				<div class="absolute -top-8 right-2 w-16 h-16 z-10" aria-hidden="true">
					<img src={shapes[i % shapes.length].src} alt="" class="w-full h-full object-contain" />
				</div>
				<div class="relative z-0 bg-white rounded-[30px] px-6 py-8">
					<h3 class="text-mobile-title-lg text-dark mb-2">{card.title}</h3>
					<p class="text-body text-dark">{card.description}</p>
				</div>
			</div>
		{/each}
	</div>

	<!-- ══ DESKTOP : titre + cards dans la grid ══ -->
	<h2 class="hidden xl:block col-span-8 text-title-xl text-dark mb-4">{title}</h2>

	{#each cards as card, i}
		<div class="hidden xl:block col-span-4 relative pt-12">
			<div class="absolute -top-5 right-1 w-30 h-30 z-10" aria-hidden="true">
				<img src={shapes[i % shapes.length].src} alt="" class="w-full h-full object-contain" />
			</div>
			<div class="relative z-0 bg-white rounded-[30px] px-8 py-10 h-full">
				<h3 class="text-title-lg text-dark mb-3">{card.title}</h3>
				<p class="text-body text-dark">{card.description}</p>
			</div>
		</div>
	{/each}
</section>
