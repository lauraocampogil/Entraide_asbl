<script lang="ts">
	let nom = $state('');
	let message = $state('');
	let sending = $state(false);
	let sent = $state(false);

	async function handleSubmit() {
		if (!nom.trim() || !message.trim()) return;
		sending = true;
		// TODO: brancher sur un endpoint /api/contact ou Resend
		await new Promise((r) => setTimeout(r, 800));
		sending = false;
		sent = true;
		nom = '';
		message = '';
	}
</script>

<section class="bg-background px-5 py-12 xl:px-20 xl:py-20">
	<!-- Titre -->
	<h2
		class="font-fustat font-medium text-mobile-title-2xl xl:text-title-2xl text-dark mb-8 xl:mb-12"
	>
		Venez nous voir
	</h2>

	<!-- ══ Layout ══ -->
	<div class="flex flex-col gap-10 xl:grid xl:grid-cols-2 xl:gap-10 xl:items-start">
		<!-- Col gauche : carte + adresse -->
		<div class="flex flex-col gap-6">
			<!-- Google Maps embed -->
			<div class="rounded-2xl overflow-hidden h-[280px] xl:h-[380px] shadow-sm">
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

			<!-- Adresse -->
			<div class="flex flex-col gap-2">
				<p class="font-fustat font-medium text-title-sm text-dark">Notre adresse</p>
				<p class="font-fustat text-body text-dark">Rue Moorslede 54, 1020 Bruxelles – Laeken</p>
				<p class="font-fustat text-body text-dark-accent">Région de Bruxelles-Capitale</p>
			</div>
		</div>

		<!-- Col droite : formulaire -->
		<div class="relative">
			<!-- Blob vert — haut droite -->
			<div
				class="absolute -top-6 -right-4 xl:-right-8 w-16 h-16 text-secondary z-0"
				aria-hidden="true"
			>
				<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M43.3,-67.9C55.7,-58.8,64.8,-45.6,69.7,-31.1C74.6,-16.5,75.2,-0.7,71.8,14.4C68.3,29.5,60.7,43.8,49.5,54.2C38.2,64.6,23.2,71,7.1,72.8C-9,74.6,-26.2,71.7,-40.3,63.4C-54.4,55.1,-65.4,41.3,-70.6,25.7C-75.8,10.1,-75.2,-7.3,-69.2,-22.3C-63.1,-37.4,-51.7,-50.1,-38.4,-59C-25.1,-67.9,-9.9,-73,4.4,-78.8C18.7,-84.6,30.9,-77,43.3,-67.9Z"
						transform="translate(100 100) scale(0.88)"
					/>
				</svg>
			</div>

			<!-- Blob jaune — bas gauche -->
			<div class="absolute -bottom-4 left-4 w-14 h-14 text-tertiary z-0" aria-hidden="true">
				<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M38.9,-64.1C50.2,-55.5,59.2,-44.3,65.1,-31.5C71,-18.7,73.7,-4.4,71.7,9.4C69.7,23.3,63,36.6,53.1,47.2C43.2,57.9,30.1,65.9,15.7,70.3C1.4,74.7,-14.2,75.4,-27.8,70.2C-41.4,65,-52.9,54,-60.2,40.9C-67.5,27.8,-70.5,12.6,-69.3,-2.1C-68.1,-16.8,-62.6,-31,-53.4,-42C-44.2,-53,-31.3,-60.8,-17.8,-65.8C-4.3,-70.8,9.8,-72.9,22.8,-71.3C35.8,-69.6,27.6,-72.7,38.9,-64.1Z"
						transform="translate(100 100) scale(0.88)"
					/>
				</svg>
			</div>

			<!-- Card formulaire -->
			<div class="relative z-10 bg-primary-dark rounded-3xl px-6 py-8 xl:px-8 xl:py-10">
				<h3 class="font-fustat font-medium text-mobile-title-lg xl:text-title-md text-dark mb-2">
					Envoyez-nous un message
				</h3>
				<p class="font-fustat text-description text-dark-accent mb-6 leading-relaxed">
					Nous lisons tous les messages et vous répondron dès que possible
				</p>

				{#if sent}
					<div class="flex flex-col items-center gap-3 py-8 text-center">
						<svg width="40" height="40" viewBox="0 0 40 40" fill="none">
							<circle cx="20" cy="20" r="19" stroke="var(--color-dark)" stroke-width="1.5" />
							<path
								d="M12 20l6 6 10-12"
								stroke="var(--color-dark)"
								stroke-width="1.5"
								stroke-linecap="round"
								stroke-linejoin="round"
							/>
						</svg>
						<p class="font-fustat font-medium text-title-sm text-dark">Message envoyé !</p>
						<p class="font-fustat text-description text-dark-accent">
							Nous vous répondrons dès que possible.
						</p>
						<button
							type="button"
							onclick={() => (sent = false)}
							class="mt-2 font-fustat text-p-small text-dark underline"
						>
							Envoyer un autre message
						</button>
					</div>
				{:else}
					<div class="flex flex-col gap-5">
						<!-- Prénom -->
						<div class="flex flex-col gap-2">
							<label for="nom" class="font-fustat text-p-small font-medium text-dark">
								Prénom
							</label>
							<input
								id="nom"
								type="text"
								bind:value={nom}
								placeholder="Votre prénom"
								class="w-full bg-white rounded-xl px-4 py-3 font-fustat text-body text-dark placeholder:text-dark-accent/50
								border border-transparent focus:outline-none focus:border-dark/20 transition-colors"
							/>
						</div>

						<!-- Message -->
						<div class="flex flex-col gap-2">
							<label for="message" class="font-fustat text-p-small font-medium text-dark">
								Message
							</label>
							<textarea
								id="message"
								bind:value={message}
								placeholder="Comment pouvons-nous vous aider?"
								rows="6"
								class="w-full bg-white rounded-xl px-4 py-3 font-fustat text-body text-dark placeholder:text-dark-accent/50
								border border-transparent focus:outline-none focus:border-dark/20 transition-colors resize-none"
							></textarea>
						</div>

						<!-- Submit -->
						<button
							type="button"
							onclick={handleSubmit}
							disabled={sending || !nom.trim() || !message.trim()}
							class="self-end inline-flex items-center rounded-full bg-dark px-7 py-3 font-fustat font-medium text-button text-white
							hover:bg-primary transition-colors duration-200 disabled:opacity-50 disabled:cursor-not-allowed"
						>
							{sending ? 'Envoi...' : 'Envoyer mon message'}
						</button>
					</div>
				{/if}
			</div>
		</div>
	</div>
</section>
