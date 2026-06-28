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

<section class="grid-section bg-background px-5 py-10 xl:py-16 3xl:container 3xl:mx-auto">
	<!-- Card pleine largeur col 1-8 -->
	<div
		class="xl:col-span-8 relative overflow-hidden rounded-3xl bg-primary-dark xl:h-102.25
		flex flex-col items-center justify-center text-center px-8 py-14 xl:px-20"
	>
		<!-- Gradient diamant vertical -->
		<div
			class="pointer-events-none absolute inset-0 z-0"
			style="background: radial-gradient(ellipse 20% 100% at 50% 50%, #FFDFDF 0%, #FF9C9D 50%, #FE9698 100%);"
		></div>

		<!-- Bol — haut gauche, déborde -->
		<img
			src="/assets/svg/Bol.svg"
			alt=""
			aria-hidden="true"
			class="absolute z-0 -top-14 -left-12 xl:-top-8 xl:-left-8 w-30 xl:w-45 h-auto"
		/>

		<!-- Star — bas droite, bien à droite -->
		<img
			src="/assets/svg/Star.svg"
			alt=""
			aria-hidden="true"
			class="absolute z-0 -bottom-7 -right-6 xl:-bottom-20 xl:-right-10 w-25 xl:w-50 h-auto"
		/>

		<!-- Contenu -->
		<div class="relative z-10 flex flex-col items-center gap-6">
			<h2
				class="text-mobile-title-xl xl:text-title-2xl text-dark leading-snug xl:whitespace-nowrap"
			>
				{title}
			</h2>
			<p
				class="font-fustat text-description xl:text-body text-dark leading-relaxed max-w-95 xl:max-w-120"
			>
				{description}
			</p>
			<Button href={ctaHref} label={ctaLabel} variant="plain" />
		</div>
	</div>
</section>
