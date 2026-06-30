<svelte:head>
	<title>Politique de Confidentialité</title>
	<meta name="description" content="Politique de confidentialité d'Entraide Bruxelles." />
	<meta name="robots" content="noindex" />
</svelte:head>

<main class="min-h-screen bg-background px-5 py-16 xl:px-20 xl:py-24">
	<div class="mx-auto max-w-3xl">
		<a
			href="/"
			class="mb-8 inline-flex items-center gap-2 text-sm text-dark/50 transition-colors hover:text-primary"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="16"
				height="16"
				fill="currentColor"
				viewBox="0 0 256 256"
			>
				<path
					d="M224,128a8,8,0,0,1-8,8H59.31l58.35,58.34a8,8,0,0,1-11.32,11.32l-72-72a8,8,0,0,1,0-11.32l72-72a8,8,0,0,1,11.32,11.32L59.31,120H216A8,8,0,0,1,224,128Z"
				/>
			</svg>
			Retour
		</a>

		<h1 class="mb-2 text-mobile-title-2xl text-dark xl:text-title-2xl">
			Politique de Confidentialité
		</h1>
		<p class="mb-10 text-sm text-dark/40">Dernière mise à jour: Juin 2026</p>

		<div class="flex flex-col gap-8 text-dark">
			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">1. Responsable du traitement</h2>
				<p class="text-mobile-body leading-relaxed">
					<strong>Entraide Bruxelles ASBL</strong>, Rue Moorslede 54, 1020 Bruxelles – Laeken.<br />
					Contact :
					<a href="mailto:anasta5853@gmail.com" class="text-primary underline"
						>anasta5853@gmail.com</a
					>
				</p>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">
					2. Données personnelles collectées
				</h2>
				<p class="text-mobile-body leading-relaxed">
					Dans le cadre du formulaire de contact, Entraide Bruxelles collecte les données suivantes:
				</p>
				<ul class="flex flex-col gap-1 pl-4">
					{#each ['Prénom', 'Contenu du message envoyé via le formulaire de contact'] as item}
						<li class="flex items-start gap-2 text-mobile-body">
							<span class="mt-1 text-primary">•</span>
							<span>{item}</span>
						</li>
					{/each}
				</ul>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">3. Mode de collecte</h2>
				<p class="text-mobile-body leading-relaxed">
					Les données personnelles sont collectées via le formulaire de contact disponible sur le
					site, géré par le service Formspree.
				</p>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">4. Finalités du traitement</h2>
				<ul class="flex flex-col gap-1 pl-4">
					{#each ['Répondre aux demandes envoyées via le formulaire de contact', 'Mesurer la fréquentation du site (Google Analytics)'] as item}
						<li class="flex items-start gap-2 text-mobile-body">
							<span class="mt-1 text-primary">•</span>
							<span>{item}</span>
						</li>
					{/each}
				</ul>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">5. Base légale</h2>
				<p class="text-mobile-body leading-relaxed">
					Le traitement des données est fondé sur le consentement de la personne lors de l'envoi du
					formulaire et sur l'intérêt légitime de l'association à répondre aux demandes des
					visiteurs.
				</p>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">6. Durée de conservation</h2>
				<p class="text-mobile-body leading-relaxed">
					Les messages reçus via le formulaire de contact sont conservés 12 mois maximum, sauf
					nécessité de conservation plus longue pour le suivi d'une demande.
				</p>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">7. Destinataires des données</h2>
				<p class="text-mobile-body leading-relaxed">Les données peuvent être partagées avec :</p>
				<ul class="flex flex-col gap-1 pl-4">
					{#each ['Formspree (traitement du formulaire de contact) — États-Unis, conforme RGPD', "Google Analytics (mesure d'audience) — avec garanties RGPD", 'Cloudflare (hébergement du site)'] as item}
						<li class="flex items-start gap-2 text-mobile-body">
							<span class="mt-1 text-primary">•</span>
							<span>{item}</span>
						</li>
					{/each}
				</ul>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">8. Vos droits</h2>
				<p class="text-mobile-body leading-relaxed">
					Conformément au RGPD, vous disposez des droits suivants :
				</p>
				<ul class="flex flex-col gap-1 pl-4">
					{#each ["Droit d'accès à vos données", 'Droit de rectification', "Droit à l'effacement", 'Droit à la limitation du traitement', 'Droit à la portabilité des données', "Droit d'opposition"] as item}
						<li class="flex items-start gap-2 text-mobile-body">
							<span class="mt-1 text-primary">•</span>
							<span>{item}</span>
						</li>
					{/each}
				</ul>
				<p class="text-mobile-body leading-relaxed">
					Pour exercer ces droits :
					<a href="mailto:anasta5853@gmail.com" class="text-primary underline"
						>anasta5853@gmail.com</a
					><br />
					Vous pouvez également introduire une réclamation auprès de l'
					<a
						href="https://www.autoriteprotectiondonnees.be"
						target="_blank"
						rel="noopener noreferrer"
						class="text-primary underline">Autorité de protection des données</a
					>.
				</p>
			</section>

			<div class="border-t border-dashed border-dark/10"></div>

			<section class="flex flex-col gap-3">
				<h2 class="text-mobile-title-lg font-medium text-dark">9. Modifications</h2>
				<p class="text-mobile-body leading-relaxed">
					Entraide Bruxelles ASBL se réserve le droit de mettre à jour cette politique à tout
					moment. Toute modification sera publiée sur cette page.
				</p>
			</section>
		</div>
	</div>
</main>
