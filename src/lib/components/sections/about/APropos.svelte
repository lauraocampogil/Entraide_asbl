<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';
</script>

<section
	class="bg-background px-5 pt-14 pb-10 xl:px-20 xl:pt-20 xl:pb-16 flex flex-col items-center text-center"
>
	<!-- Grand pentagone -->
	<div class="mb-8 xl:mb-10" aria-hidden="true">
		<svg
			width="120"
			height="114"
			viewBox="0 0 120 114"
			fill="none"
			xmlns="http://www.w3.org/2000/svg"
			class="xl:w-[140px] xl:h-auto"
		>
			<path d="M60 4L114 42.3L93.3 110H26.7L6 42.3L60 4Z" fill="var(--color-primary-dark)" />
		</svg>
	</div>

	<!-- Tagline -->
	<div class="mb-5">
		<Tagline label="A propos de nous" />
	</div>

	<!-- Titre mixte Fustat + BobbyJones -->
	<h1
		class="font-fustat font-medium text-mobile-title-xl xl:text-title-2xl text-dark leading-snug max-w-3xl"
	>
		Une <span class="font-bobbyjones font-bold text-primary">ASSOCIATION</span> de quartier à
		<span class="font-bobbyjones font-bold text-primary">LAEKEN</span>, active depuis
		<span class="font-bobbyjones font-bold text-primary">1985</span>.
	</h1>
</section>
