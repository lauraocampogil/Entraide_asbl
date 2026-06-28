<script lang="ts">
	import Button from '$lib/components/ui/Button.svelte';

	let {
		ctaLabel,
		ctaHref,
		stats,
		images
	}: {
		ctaLabel: string;
		ctaHref: string;
		stats: { value: string; label: string }[];
		images: { src: string; alt: string }[];
	} = $props();
</script>

<section
	class="grid-section bg-background px-5 pt-8 pb-10 xl:pt-30 xl:pb-30 3xl:container 3xl:mx-auto"
>
	<!-- Col 1-4 -->
	<div class="xl:col-span-4 xl:col-start-1 flex flex-col gap-7 xl:py-8">
		<div class="flex flex-col gap-3 xl:gap-4 xl:pt-8">
			<h1 class="font-bobbyjones text-mobile-title-3xl xl:text-title-3xl text-dark">
				<span class="text-primary">APPRENDRE, S'INTÉGRER</span><br />
				<span class="font-fustat">et&nbsp;</span><span class="text-primary">BIEN VIVRE</span><span
					class="font-fustat">&nbsp;à Bruxelles</span
				>
			</h1>

			<p class="text-description xl:text-subtitle text-dark xl:max-w-lg">
				Cours de français, aide aux devoirs, démarches administratives et bien plus, pour les
				adultes et les enfants.
			</p>
		</div>

		<Button href={ctaHref} label={ctaLabel} variant="split" />

		<div class="grid grid-cols-3 gap-2 xl:gap-3">
			{#each stats as stat}
				<div
					class="bg-white rounded-2xl xl:rounded-3xl flex flex-col items-center justify-center gap-1 xl:gap-2 py-4 xl:h-33.75"
				>
					<span class="text-mobile-large xl:text-large text-dark leading-none text-center">
						{stat.value}
					</span>
					<span
						class="font-fustat text-p-small xl:text-description text-dark text-center leading-snug px-3 whitespace-pre-line"
					>
						{stat.label}
					</span>
				</div>
			{/each}
		</div>
	</div>

	<!-- Col 5-8 -->
	<div class="xl:col-span-4 xl:col-start-5 relative h-105 xl:h-160 mt-4 xl:mt-0 overflow-visible">
		<!-- Star -->
		<img
			src="/assets/svg/Star.svg"
			alt=""
			aria-hidden="true"
			class="absolute z-0
			top-2.5 left-[5%]
			w-32 h-auto
			xl:top-5 xl:left-[calc(25%-100px)] xl:w-50"
		/>

		<!-- Photo 1 — gauche bas -->
		{#if images?.[0]}
			<div
				class="absolute bottom-0 left-0
				w-[47%] h-67.5
				xl:w-[calc(50%-8px)] xl:h-100
				rounded-2xl xl:rounded-[50px] overflow-hidden z-10 shadow-md"
			>
				<img src={images[0].src} alt={images[0].alt} class="w-full h-full object-cover" />
			</div>
		{/if}

		<!-- Photo 2 — droite haut -->
		{#if images?.[1]}
			<div
				class="absolute top-0 right-0
				w-[47%] h-67.5
				xl:w-[calc(50%-8px)] xl:h-100
				rounded-2xl xl:rounded-[50px] overflow-hidden z-10 shadow-md"
			>
				<img src={images[1].src} alt={images[1].alt} class="w-full h-full object-cover" />
			</div>
		{/if}

		<!-- Bol -->
		<img
			src="/assets/svg/Bol.svg"
			alt=""
			aria-hidden="true"
			class="absolute z-0
			bottom-2.5 right-[5%]
			w-32 h-auto
			xl:bottom-2 xl:right-[calc(25%-95px)] xl:w-50"
		/>
	</div>
</section>
