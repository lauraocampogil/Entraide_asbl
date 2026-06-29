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

<section class="bg-primary-dark px-5 py-12 grid-section xl:py-16">
	<!-- Tagline + titre -->
	<div class="col-span-8 flex flex-col gap-3 mb-8 xl:mb-10">
		<Tagline label="Notre équipe" />
		<h2 class="text-mobile-title-xl xl:text-title-xl text-white">
			{title}
		</h2>
	</div>

	<!-- Cards personnel : 1 col mobile / 2 col desktop -->
	<div class="col-span-8 grid grid-cols-1 xl:grid-cols-2 gap-4 mb-12 xl:mb-14">
		{#each personnel as person}
			<div class="bg-white rounded-[20px] xl:rounded-[30px] px-6 py-5 xl:py-8 xl:px-8">
				<p class="xl:text-title-sm text-mobile-title-sm text-dark">{person.title}</p>
				<p class="text-body text-dark-accent mt-1">{person.description}</p>
			</div>
		{/each}
	</div>

	<!-- Groupes : 1 col mobile / 3 col desktop -->
	<div class="col-span-8 flex flex-col gap-8 xl:grid xl:grid-cols-3 xl:gap-10">
		<!-- Formateurs -->
		{#each formateurs as f}
			<div class="flex flex-col">
				<p class="text-mobile-title-md xl:text-title-md text-dark mb-3">{f.title}</p>
				<div class="border-t border-dark pt-4">
					<ul class="flex flex-col gap-2">
						<li class="text-body text-dark">{f.text1}</li>
						<li class="text-body text-dark">{f.text2}</li>
						<li class="text-body text-dark">{f.text3}</li>
					</ul>
				</div>
			</div>
		{/each}

		<!-- Bénévoles -->
		{#each benevoles as b}
			<div class="flex flex-col">
				<p class="text-mobile-title-md xl:text-title-md text-dark mb-3">
					{b.title}
				</p>
				<div class="border-t border-dark pt-4">
					<p class=" text-body text-dark">{b.description}</p>
				</div>
			</div>
		{/each}

		<!-- Stagiaires -->
		{#each stagiaires as s}
			<div class="flex flex-col">
				<p class="text-mobile-title-md xl:text-title-md text-dark mb-3">
					{s.title}
				</p>
				<div class="border-t border-dark pt-4">
					<p class="text-body text-dark">{s.description}</p>
				</div>
			</div>
		{/each}
	</div>
</section>
