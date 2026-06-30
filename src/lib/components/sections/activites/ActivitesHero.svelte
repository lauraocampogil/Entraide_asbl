<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';
</script>

<section
	class="grid-section sm-grid-section bg-background px-5 sm:px-8 md:px-10 lg:px-12 pt-14 pb-10 xl:pt-20 xl:pb-16 3xl:container 3xl:mx-auto"
>
	<div class="col-span-8 sm:col-span-8 flex flex-col items-center text-center">
		<div class="mb-8 xl:mb-10" aria-hidden="true">
			<svg
				width="120"
				height="114"
				viewBox="0 0 120 114"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
				class="xl:w-35 xl:h-auto"
			>
				<path d="M60 4L114 42.3L93.3 110H26.7L6 42.3L60 4Z" fill="var(--color-primary-dark)" />
			</svg>
		</div>

		<!-- Tagline -->
		<div class="mb-5">
			<Tagline label="Nos activités" />
		</div>

		<!-- Titre -->
		<h1 class="text-mobile-title-2xl xl:text-title-2xl text-dark leading-snug max-w-3xl">
			Des <span class="font-bobbyjones font-bold text-primary">FORMATION</span> et de
			<span class="font-bobbyjones font-bold text-primary">L'AIDE</span>, pensées pour vous.
		</h1>
	</div>
</section>
