<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	let nom = $state('');
	let message = $state('');
	let sending = $state(false);
	let sent = $state(false);

	let sectionEl = $state<HTMLElement | null>(null);
	let titleEl = $state<HTMLElement | null>(null);
	let shapesActive = $state(false);

	async function handleSubmit() {
		if (!nom.trim() || !message.trim()) return;
		sending = true;
		try {
			const res = await fetch('https://formspree.io/f/YOUR_FORM_ID', {
				method: 'POST',
				headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
				body: JSON.stringify({ nom, message })
			});
			if (res.ok) {
				sent = true;
				nom = '';
				message = '';
			}
		} catch (e) {
			console.error(e);
		} finally {
			sending = false;
		}
	}

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		const mm = gsap.matchMedia();

		mm.add(
			{
				isMobile: '(max-width: 1279px)',
				isDesktop: '(min-width: 1280px)'
			},
			(context) => {
				const { isMobile } = context.conditions as { isMobile: boolean };

				const tl = gsap.timeline({
					defaults: { ease: 'none' },
					scrollTrigger: {
						trigger: sectionEl,
						start: 'top 95%',
						end: isMobile ? 'top 5%' : 'top 25%',
						scrub: 1
					}
				});

				tl.fromTo(titleEl, { y: 40, opacity: 0 }, { y: 0, opacity: 1, duration: 1 });

				const shapeTrigger = ScrollTrigger.create({
					trigger: sectionEl,
					start: 'top 80%',
					end: isMobile ? 'bottom bottom' : 'bottom top',
					onEnter: () => (shapesActive = true),
					onLeave: () => (shapesActive = false),
					onEnterBack: () => (shapesActive = true),
					onLeaveBack: () => (shapesActive = false)
				});

				shapesActive = shapeTrigger.isActive;
			}
		);

		const handleLoad = () => ScrollTrigger.refresh();
		window.addEventListener('load', handleLoad);

		return () => {
			window.removeEventListener('load', handleLoad);
			mm.revert();
		};
	});
</script>

<section
	bind:this={sectionEl}
	class="bg-background px-5 py-12 grid-section xl:py-20 sm-grid-section 3xl:container 3xl:mx-auto"
>
	<!-- Titre pleine largeur -->
	<h2
		bind:this={titleEl}
		class="col-span-8 text-mobile-title-2xl xl:text-title-2xl text-dark mb-8 xl:mb-12"
		style="opacity:0"
	>
		Venez nous voir
	</h2>

	<!-- ══ MOBILE : empilé ══ -->
	<div class="xl:hidden col-span-8 flex flex-col gap-10">
		<!-- Carte + adresse -->
		<div class="flex flex-col gap-6">
			<div class="rounded-2xl overflow-hidden h-70 shadow-sm">
				<iframe
					title="Entraide Bruxelles — Rue Moorslede 54, Laeken"
					src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2517.5!2d4.3408!3d50.8785!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47c3c3c3c3c3c3c3%3A0x0!2sRue+Moorslede+54%2C+1020+Bruxelles!5e0!3m2!1sfr!2sbe!4v1"
					width="100%"
					height="100%"
					style="border:0;"
					allowfullscreen
					loading="lazy"
					referrerpolicy="no-referrer-when-downgrade"
				></iframe>
			</div>
			<div class="flex flex-col gap-2">
				<p class="text-title-md text-dark">Notre adresse</p>
				<div>
					<p class="text-body text-dark">Rue Moorslede 54, 1020 Bruxelles – Laeken</p>
					<p class="text-p-small text-dark-accent">Région de Bruxelles-Capitale</p>
				</div>
			</div>
		</div>

		<!-- Formulaire mobile -->
		<div class="relative pt-6">
			<div
				class="absolute top-4 -right-4 w-16 h-16 z-20 {shapesActive ? 'animate-spin-slow' : ''}"
				aria-hidden="true"
			>
				<img src="/assets/svg/Star.svg" alt="" class="w-full h-full object-contain" />
			</div>
			<div
				class="absolute -bottom-4 -left-4 w-16 h-16 z-20 {shapesActive ? 'animate-spin-slow' : ''}"
				aria-hidden="true"
			>
				<img src="/assets/svg/Bol.svg" alt="" class="w-full h-full object-contain" />
			</div>
			<div class="relative z-10 bg-pink rounded-[30px] px-6 py-8">
				{#if sent}
					<div class="flex flex-col items-center gap-3 py-8 text-center">
						<p class="text-title-sm text-dark">Message envoyé !</p>
						<p class="text-body text-dark opacity-75">Nous vous répondrons dès que possible.</p>
						<button
							type="button"
							onclick={() => (sent = false)}
							class="mt-2 text-p-small text-dark underline"
						>
							Envoyer un autre message
						</button>
					</div>
				{:else}
					<h3 class="text-mobile-title-lg text-dark mb-2">Envoyez-nous un message</h3>
					<p class="text-body text-dark opacity-75 mb-6">
						Nous lisons tous les messages et vous répondrons dès que possible
					</p>
					<div class="flex flex-col gap-5">
						<div class="flex flex-col gap-2">
							<label for="nom-mobile" class="text-p-small text-dark">Prénom</label>
							<input
								id="nom-mobile"
								type="text"
								bind:value={nom}
								placeholder="Votre prénom"
								class="w-full bg-white rounded-2xl px-4 py-3 text-body text-dark placeholder:text-dark-accent/50 border border-transparent focus:outline-none focus:border-dark/20 transition-colors"
							/>
						</div>
						<div class="flex flex-col gap-2">
							<label for="message-mobile" class="text-p-small text-dark">Message</label>
							<textarea
								id="message-mobile"
								bind:value={message}
								placeholder="Comment pouvons-nous vous aider?"
								rows="6"
								class="w-full bg-white rounded-2xl px-4 py-3 text-body text-dark placeholder:text-dark-accent/50 border border-transparent focus:outline-none focus:border-dark/20 transition-colors resize-none"
							></textarea>
						</div>
						<div class="flex justify-center">
							<button
								type="button"
								onclick={handleSubmit}
								disabled={sending || !nom.trim() || !message.trim()}
								class="inline-flex items-center rounded-full bg-dark px-7 py-3 font-medium text-button text-white enabled:hover:bg-primary transition-colors duration-200 disabled:cursor-not-allowed"
							>
								{sending ? 'Envoi...' : 'Envoyer mon message'}
							</button>
						</div>
					</div>
				{/if}
			</div>
		</div>
	</div>

	<!-- ══ DESKTOP : col 1-4 carte, col 5-8 formulaire ══ -->

	<!-- Col gauche : carte + adresse -->
	<div class="hidden xl:flex col-span-4 flex-col gap-6">
		<div class="rounded-2xl overflow-hidden h-95 shadow-sm">
			<iframe
				title="Entraide Bruxelles — Rue Moorslede 54, Laeken"
				src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2517.5!2d4.3408!3d50.8785!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47c3c3c3c3c3c3c3%3A0x0!2sRue+Moorslede+54%2C+1020+Bruxelles!5e0!3m2!1sfr!2sbe!4v1"
				width="100%"
				height="100%"
				style="border:0;"
				allowfullscreen
				loading="lazy"
				referrerpolicy="no-referrer-when-downgrade"
			></iframe>
		</div>
		<div class="flex flex-col gap-2">
			<p class="text-title-sm text-dark">Notre adresse</p>
			<div>
				<p class="text-body text-dark">Rue Moorslede 54, 1020 Bruxelles – Laeken</p>
				<p class="text-body text-dark-accent">Région de Bruxelles-Capitale</p>
			</div>
		</div>
	</div>

	<!-- Col droite : formulaire -->
	<div class="hidden xl:block col-span-4 col-start-5 relative">
		<!-- Star verte en haut à droite — au-dessus de la card -->
		<div
			class="absolute -top-10 -right-6 w-25 h-25 z-20 {shapesActive ? 'animate-spin-slow' : ''}"
			aria-hidden="true"
		>
			<img src="/assets/svg/Star.svg" alt="" class="w-full h-full object-contain" />
		</div>
		<!-- Bol jaune en bas à gauche — au-dessus de la card -->
		<div
			class="absolute -bottom-10 -left-10 w-25 h-25 z-20 {shapesActive ? 'animate-spin-slow' : ''}"
			aria-hidden="true"
		>
			<img src="/assets/svg/Bol.svg" alt="" class="w-full h-full object-contain" />
		</div>

		<!-- Card formulaire -->
		<div class="relative z-10 bg-pink rounded-[30px] px-8 py-10">
			{#if sent}
				<div class="flex flex-col items-center gap-3 py-8 text-center">
					<p class="text-title-sm text-dark">Message envoyé !</p>
					<p class="text-body text-dark opacity-75">Nous vous répondrons dès que possible.</p>
					<button
						type="button"
						onclick={() => (sent = false)}
						class="mt-2 text-p-small text-dark underline"
					>
						Envoyer un autre message
					</button>
				</div>
			{:else}
				<h3 class="text-title-md text-dark mb-2">Envoyez-nous un message</h3>
				<p class="text-body text-dark opacity-75 mb-6">
					Nous lisons tous les messages et vous répondrons dès que possible
				</p>
				<div class="flex flex-col gap-5">
					<div class="flex flex-col gap-2">
						<label for="nom" class="text-bodytext-dark">Prénom</label>
						<input
							id="nom"
							type="text"
							bind:value={nom}
							placeholder="Votre prénom"
							class="w-full bg-white rounded-2xl px-4 py-3 text-body text-dark placeholder:text-dark-accent/50 border border-transparent focus:outline-none focus:border-dark/20 transition-colors"
						/>
					</div>
					<div class="flex flex-col gap-2">
						<label for="message" class="text-body text-dark">Message</label>
						<textarea
							id="message"
							bind:value={message}
							placeholder="Comment pouvons-nous vous aider?"
							rows="6"
							class="w-full bg-white rounded-2xl px-4 py-3 text-body text-dark placeholder:text-dark-accent/50 border border-transparent focus:outline-none focus:border-dark/20 transition-colors resize-none"
						></textarea>
					</div>
					<div class="flex justify-center">
						<button
							type="button"
							onclick={handleSubmit}
							disabled={sending || !nom.trim() || !message.trim()}
							class="inline-flex items-center rounded-full bg-dark px-7 py-3 font-medium text-button text-white enabled:hover:bg-primary transition-colors duration-200 disabled:cursor-not-allowed"
						>
							{sending ? 'Envoi...' : 'Envoyer mon message'}
						</button>
					</div>
				</div>
			{/if}
		</div>
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
