<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';

	let {
		title,
		personnel,
		formateurs,
		benevoles,
		stagiaires
	}: {
		title: string;
		personnel: { id: number; title: string; description: string }[];
		formateurs: { title: string; text1: string; text2: string; text3: string }[];
		benevoles: { title: string; description: string }[];
		stagiaires: { title: string; description: string }[];
	} = $props();
</script>

<section class="bg-primary-dark px-5 py-12 xl:px-20 xl:py-16">
	<!-- Tagline + titre -->
	<div class="flex flex-col gap-3 mb-8 xl:mb-10">
		<Tagline label="Notre équipe" />
		<h2
			class="font-fustat font-medium text-mobile-title-2xl xl:text-title-2xl text-white leading-snug"
		>
			{title}
		</h2>
	</div>

	<!-- Cards personnel : 1 col mobile / 2 col desktop -->
	<div class="grid grid-cols-1 xl:grid-cols-2 gap-4 mb-12 xl:mb-14">
		{#each personnel as person}
			<div class="bg-white rounded-2xl px-6 py-5">
				<p class="font-fustat font-medium text-title-sm text-dark">{person.title}</p>
				<p class="font-fustat text-description text-dark-accent mt-1">{person.description}</p>
			</div>
		{/each}
	</div>

	<!-- Groupes : 1 col mobile / 3 col desktop -->
	<div class="flex flex-col gap-8 xl:grid xl:grid-cols-3 xl:gap-10">
		<!-- Formateurs -->
		{#each formateurs as f}
			<div class="flex flex-col gap-4">
				<div class="border-t border-white/40 pt-4">
					<p class="font-fustat font-medium text-mobile-title-lg xl:text-title-md text-white mb-3">
						{f.title}
					</p>
					<ul class="flex flex-col gap-2">
						<li class="font-fustat text-description xl:text-body text-white/80">{f.text1}</li>
						<li class="font-fustat text-description xl:text-body text-white/80">{f.text2}</li>
						<li class="font-fustat text-description xl:text-body text-white/80">{f.text3}</li>
					</ul>
				</div>
			</div>
		{/each}

		<!-- Bénévoles -->
		{#each benevoles as b}
			<div class="flex flex-col gap-4">
				<div class="border-t border-white/40 pt-4">
					<p class="font-fustat font-medium text-mobile-title-lg xl:text-title-md text-white mb-3">
						{b.title}
					</p>
					<p class="font-fustat text-description xl:text-body text-white/80 leading-relaxed">
						{b.description}
					</p>
				</div>
			</div>
		{/each}

		<!-- Stagiaires -->
		{#each stagiaires as s}
			<div class="flex flex-col gap-4">
				<div class="border-t border-white/40 pt-4">
					<p class="font-fustat font-medium text-mobile-title-lg xl:text-title-md text-white mb-3">
						{s.title}
					</p>
					<p class="font-fustat text-description xl:text-body text-white/80 leading-relaxed">
						{s.description}
					</p>
				</div>
			</div>
		{/each}
	</div>
</section>
