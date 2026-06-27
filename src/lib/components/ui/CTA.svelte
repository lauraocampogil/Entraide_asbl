<script lang="ts">
	import Button from '$lib/components/ui/Button.svelte';

	let {
		title,
		description,
		ctaLabel,
		ctaHref
	}: {
		title: string;
		description: string;
		ctaLabel: string;
		ctaHref: string;
	} = $props();
</script>

<section class="bg-background px-5 py-10 xl:px-20 xl:py-16">
	<!-- Card -->
	<div
		class="relative overflow-hidden rounded-3xl bg-primary-dark px-8 py-14 xl:px-20 xl:py-20 flex flex-col items-center text-center"
	>
		<!-- Gradient radial central -->
		<div
			class="pointer-events-none absolute inset-0"
			aria-hidden="true"
			style="background: radial-gradient(ellipse 60% 70% at 50% 50%, rgba(255,255,255,0.25) 0%, transparent 70%);"
		></div>

		<!-- Blob jaune — haut gauche -->
		<div
			class="absolute -top-6 -left-6 w-[130px] h-[130px] xl:w-[160px] xl:h-[160px] text-tertiary z-0"
			aria-hidden="true"
		>
			<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
				<path
					d="M38.9,-64.1C50.2,-55.5,59.2,-44.3,65.1,-31.5C71,-18.7,73.7,-4.4,71.7,9.4C69.7,23.3,63,36.6,53.1,47.2C43.2,57.9,30.1,65.9,15.7,70.3C1.4,74.7,-14.2,75.4,-27.8,70.2C-41.4,65,-52.9,54,-60.2,40.9C-67.5,27.8,-70.5,12.6,-69.3,-2.1C-68.1,-16.8,-62.6,-31,-53.4,-42C-44.2,-53,-31.3,-60.8,-17.8,-65.8C-4.3,-70.8,9.8,-72.9,22.8,-71.3C35.8,-69.6,27.6,-72.7,38.9,-64.1Z"
					transform="translate(100 100) scale(0.88)"
				/>
			</svg>
		</div>

		<!-- Blob vert — bas droite -->
		<div
			class="absolute -bottom-4 -right-4 w-[100px] h-[100px] xl:w-[130px] xl:h-[130px] text-secondary z-0"
			aria-hidden="true"
		>
			<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
				<path
					d="M43.3,-67.9C55.7,-58.8,64.8,-45.6,69.7,-31.1C74.6,-16.5,75.2,-0.7,71.8,14.4C68.3,29.5,60.7,43.8,49.5,54.2C38.2,64.6,23.2,71,7.1,72.8C-9,74.6,-26.2,71.7,-40.3,63.4C-54.4,55.1,-65.4,41.3,-70.6,25.7C-75.8,10.1,-75.2,-7.3,-69.2,-22.3C-63.1,-37.4,-51.7,-50.1,-38.4,-59C-25.1,-67.9,-9.9,-73,4.4,-78.8C18.7,-84.6,30.9,-77,43.3,-67.9Z"
					transform="translate(100 100) scale(0.88)"
				/>
			</svg>
		</div>

		<!-- Contenu -->
		<div class="relative z-10 flex flex-col items-center gap-6 max-w-2xl">
			<h2
				class="font-fustat font-medium text-mobile-title-xl xl:text-title-2xl text-dark leading-snug"
			>
				{title}
			</h2>
			<p class="font-fustat text-description xl:text-body text-dark-accent leading-relaxed">
				{description}
			</p>
			<Button href={ctaHref} label={ctaLabel} variant="plain" />
		</div>
	</div>
</section>
