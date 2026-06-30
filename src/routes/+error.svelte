<script lang="ts">
	import { page } from '$app/state';
	import { onMount } from 'svelte';
	import { httpErrors } from '$lib/utils/httpErrors';

	const message =
		httpErrors[page.status as number] ?? page.error?.message ?? 'Une erreur inconnue est survenue.';

	let spinning = $state(false);

	onMount(() => {
		spinning = true;
	});
</script>

<section
	class="min-h-dvh bg-background flex items-center justify-center px-5 relative overflow-hidden"
>
	<!-- Bol — haut gauche diagonal -->
	<div
		class="absolute -top-10 -left-10 w-32 xl:w-48 z-0 {spinning ? 'animate-spin-slow' : ''}"
		aria-hidden="true"
	>
		<img src="/assets/svg/Bol.svg" alt="" class="w-full h-full object-contain" />
	</div>

	<!-- Star — bas droite diagonal -->
	<div
		class="absolute -bottom-10 -right-10 w-28 xl:w-44 z-0 {spinning ? 'animate-spin-slow' : ''}"
		aria-hidden="true"
	>
		<img src="/assets/svg/Star.svg" alt="" class="w-full h-full object-contain" />
	</div>

	<!-- Contenu centré -->
	<div class="relative z-10 flex flex-col items-center text-center">
		<!-- Numéro d'erreur en grand en arrière-plan -->
		<p
			class="font-bobbyjones text-[25vw] xl:text-[15vw] leading-none text-tag select-none pointer-events-none mb-0"
		>
			{page.status}
		</p>

		<!-- Message -->
		<p class="text-mobile-title-md xl:text-title-md text-dark mb-2 mt-2 xl:-mt-2">
			{message}
		</p>

		<p class="text-body text-dark-accent mb-8">
			La page que vous cherchez n'existe pas ou a été déplacée.
		</p>

		<!-- Bouton retour -->
		<a
			href="/"
			class="inline-flex items-center rounded-full bg-dark px-7 py-3 font-medium text-button text-white hover:bg-primary transition-colors duration-200"
		>
			Retour à l'accueil
		</a>
	</div>
</section>

<style>
	@keyframes spin-slow {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}
	.animate-spin-slow {
		animation: spin-slow 15s linear infinite;
	}
</style>
