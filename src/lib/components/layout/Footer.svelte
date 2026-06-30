<script lang="ts">
	let {
		logo,
		tagline,
		instagram,
		facebook,
		contact,
		liens,
		legal
	}: {
		logo: string;
		tagline: string;
		instagram: { href: string };
		facebook: { href: string };
		contact: { email: string; adresse: string };
		liens: { links: { label: string; href: string }[] };
		legal: { label: string; href: string }[];
	} = $props();
</script>

<footer
	class="grid-section bg-background pt-12 pb-8 xl:pt-16 xl:pb-10 3xl:container 3xl:mx-auto px-5 sm:px-8 md:px-10 lg:px-12"
>
	<!-- Logo + tagline + socials : pleine largeur mobile, 4 cols xl -->
	<div class="col-span-8 xl:col-span-4 xl:col-start-1 flex flex-col gap-5 mb-10 xl:mb-0">
		<a href="/"><img src={logo} alt="Entraide Bruxelles" class="h-10 w-auto" /></a>
		<p class="text-body text-dark">{tagline}</p>
		<div class="flex items-center gap-4">
			<a
				href={instagram.href}
				aria-label="Instagram"
				class="text-dark hover:text-primary transition-colors"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="28"
					height="28"
					fill="currentColor"
					viewBox="0 0 256 256"
				>
					<path
						d="M128,82a46,46,0,1,0,46,46A46.06,46.06,0,0,0,128,82Zm0,80a34,34,0,1,1,34-34A34,34,0,0,1,128,162ZM176,26H80A54.06,54.06,0,0,0,26,80v96a54.06,54.06,0,0,0,54,54h96a54.06,54.06,0,0,0,54-54V80A54.06,54.06,0,0,0,176,26Zm42,150a42,42,0,0,1-42,42H80a42,42,0,0,1-42-42V80A42,42,0,0,1,80,38h96a42,42,0,0,1,42,42ZM190,76a10,10,0,1,1-10-10A10,10,0,0,1,190,76Z"
					></path>
				</svg>
			</a>
			<a
				href={facebook.href}
				aria-label="Facebook"
				class="text-dark hover:text-primary transition-colors"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="28"
					height="28"
					fill="currentColor"
					viewBox="0 0 256 256"
				>
					<path
						d="M128,26A102,102,0,1,0,230,128,102.12,102.12,0,0,0,128,26Zm6,191.8V150h26a6,6,0,0,0,0-12H134V112a18,18,0,0,1,18-18h16a6,6,0,0,0,0-12H152a30,30,0,0,0-30,30v26H96a6,6,0,0,0,0,12h26v67.8a90,90,0,1,1,12,0Z"
					></path>
				</svg>
			</a>
		</div>
	</div>

	<!-- Liens : col gauche sur mobile, 1 col xl -->
	<div class="col-span-4 xl:col-span-1 xl:col-start-6 flex flex-col gap-4 mb-10 xl:mb-0">
		<p class="font-fustat font-semibold text-body text-primary">Liens</p>
		<nav class="flex flex-col gap-2 xl:gap-3">
			{#each liens.links as link}
				<a
					href={link.href}
					class="font-fustat text-body text-dark hover:text-primary transition-colors"
				>
					{link.label}
				</a>
			{/each}
		</nav>
	</div>

	<!-- Legal : col droite sur mobile, 1 col xl -->
	<div class="col-span-4 xl:col-span-1 xl:col-start-7 flex flex-col gap-4 mb-10 xl:mb-0">
		<p class="font-fustat font-semibold text-body text-primary">Legal</p>
		<nav class="flex flex-col gap-2 xl:gap-3">
			{#each legal as item}
				<a
					href={item.href}
					class="font-fustat text-body text-dark hover:text-primary transition-colors"
				>
					{item.label}
				</a>
			{/each}
		</nav>
	</div>

	<!-- Contact : pleine largeur mobile, 1 col xl -->
	<div class="col-span-8 xl:col-span-1 xl:col-start-8 flex flex-col gap-4 mb-10 xl:mb-0">
		<p class="font-fustat font-semibold text-body text-primary">Contactez-nous</p>
		<div class="flex flex-col gap-2 xl:gap-3">
			<a
				href="mailto:{contact.email}"
				class="font-fustat text-body text-dark hover:text-primary transition-colors"
			>
				{contact.email}
			</a>
			<a
				href="https://www.google.com/maps/search/?api=1&query={encodeURIComponent(contact.adresse)}"
				target="_blank"
				rel="noopener noreferrer"
				class="font-fustat text-body text-dark hover:text-primary transition-colors"
			>
				<span class="whitespace-pre-line">{contact.adresse}</span>
			</a>
		</div>
	</div>

	<!-- Bottom bar -->
	<div class="col-span-8 mt-16 xl:mt-32 flex flex-col gap-1 xl:flex-row xl:justify-end xl:gap-12">
		<p class="font-fustat text-p-small text-dark-accent">
			Entraide Bruxelles {new Date().getFullYear()} © Tous droit réservés
		</p>
		<p class="font-fustat text-p-small text-dark-accent">
			Made with love by
			<a
				href="https://unixcreativestudio.com/"
				target="_blank"
				rel="noopener noreferrer"
				class="hover:text-primary transition-colors underline">Unix</a
			>
		</p>
	</div>
</footer>
