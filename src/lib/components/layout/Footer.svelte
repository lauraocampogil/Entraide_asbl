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
	class="grid-section bg-background pt-12 pb-8 xl:pt-16 xl:pb-10 3xl:container 3xl:mx-auto px-5"
>
	<!-- Col 1-3 : Logo + tagline + socials -->
	<div class="xl:col-span-4 xl:col-start-1 flex flex-col gap-5 mb-10 xl:mb-0">
		<a href="/"><img src={logo} alt="Entraide Bruxelles" class="h-10 w-auto" /></a>
		<p class="font-fustat text-body text-dark leading-snug">{tagline}</p>
		<div class="flex items-center gap-4">
			<a
				href={instagram.href}
				aria-label="Instagram"
				class="text-dark hover:text-primary transition-colors"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="21"
					height="21"
					viewBox="0 0 21 21"
					fill="none"
				>
					<path
						d="M10.5 0C7.74 0 7.39.01 6.26.06 5.14.12 4.38.29 3.71.55a5.26 5.26 0 0 0-1.9 1.24A5.26 5.26 0 0 0 .57 3.7C.3 4.38.13 5.14.07 6.26.01 7.39 0 7.74 0 10.5s.01 3.11.06 4.24c.06 1.12.23 1.88.49 2.55.27.7.63 1.29 1.24 1.9a5.26 5.26 0 0 0 1.9 1.24c.68.26 1.44.43 2.56.49C7.39 20.99 7.74 21 10.5 21s3.11-.01 4.24-.06c1.12-.06 1.88-.23 2.55-.49a5.51 5.51 0 0 0 3.14-3.14c.26-.68.43-1.44.49-2.56.05-1.13.06-1.48.06-4.24s-.01-3.11-.06-4.24c-.06-1.12-.23-1.88-.49-2.55a5.26 5.26 0 0 0-1.24-1.9A5.26 5.26 0 0 0 17.29.55C16.62.3 15.86.13 14.74.07 13.61.01 13.26 0 10.5 0zm0 1.89c2.72 0 3.04.01 4.11.06.99.05 1.53.21 1.89.35.47.18.81.4 1.16.76.36.35.58.69.76 1.16.14.36.3.9.35 1.89.05 1.07.06 1.39.06 4.11s-.01 3.04-.06 4.11c-.05.99-.21 1.53-.35 1.89a3.14 3.14 0 0 1-.76 1.16 3.14 3.14 0 0 1-1.16.76c-.36.14-.9.3-1.89.35-1.07.05-1.39.06-4.11.06s-3.04-.01-4.11-.06c-.99-.05-1.53-.21-1.89-.35a3.14 3.14 0 0 1-1.16-.76 3.14 3.14 0 0 1-.76-1.16c-.14-.36-.3-.9-.35-1.89C1.9 13.54 1.89 13.22 1.89 10.5s.01-3.04.06-4.11c.05-.99.21-1.53.35-1.89.18-.47.4-.81.76-1.16.35-.36.69-.58 1.16-.76.36-.14.9-.3 1.89-.35C7.46 1.9 7.78 1.89 10.5 1.89zm0 3.21a5.4 5.4 0 1 0 0 10.8 5.4 5.4 0 0 0 0-10.8zm0 8.91a3.51 3.51 0 1 1 0-7.02 3.51 3.51 0 0 1 0 7.02zm6.88-9.12a1.26 1.26 0 1 1-2.52 0 1.26 1.26 0 0 1 2.52 0z"
						fill="currentColor"
					/>
				</svg>
			</a>
			<a
				href={facebook.href}
				aria-label="Facebook"
				class="text-dark hover:text-primary transition-colors"
			>
				<svg xmlns="http://www.w3.org/2000/svg" width="21" height="21" viewBox="0 0 24 24">
					<path
						d="M13.397 20.997v-8.196h2.765l.411-3.209h-3.176V7.548c0-.926.258-1.56 1.587-1.56h1.684V3.127A22.336 22.336 0 0 0 14.201 3c-2.444 0-4.122 1.492-4.122 4.231v2.355H7.332v3.209h2.753v8.202h3.312z"
						fill="currentColor"
					/>
				</svg>
			</a>
		</div>
	</div>

	<!-- Col 4-5 : Contact -->
	<div class="xl:col-span-2 xl:col-start-5 flex flex-col gap-4 mb-10 xl:mb-0">
		<p class="font-fustat font-semibold text-body text-primary">Contactez-nous</p>
		<div class="flex flex-col gap-3">
			<a
				href="mailto:{contact.email}"
				class="flex items-center gap-3 font-fustat text-body text-dark hover:text-primary transition-colors"
			>
				<svg width="18" height="18" viewBox="0 0 24 24" fill="none" class="shrink-0"
					><path
						d="M4 4h16a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2z"
						stroke="currentColor"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/><polyline
						points="22,6 12,13 2,6"
						stroke="currentColor"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/></svg
				>
				{contact.email}
			</a>
			<div class="flex items-start gap-3 font-fustat text-body text-dark">
				<svg width="18" height="18" viewBox="0 0 24 24" fill="none" class="shrink-0 mt-0.5"
					><path
						d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5a2.5 2.5 0 1 1 0-5 2.5 2.5 0 0 1 0 5z"
						stroke="currentColor"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/></svg
				>
				<span class="whitespace-pre-line">{contact.adresse}</span>
			</div>
		</div>
	</div>

	<!-- Col 7 : Liens -->
	<div class="xl:col-span-1 xl:col-start-7 flex flex-col gap-4 mb-10 xl:mb-0">
		<p class="font-fustat font-semibold text-body text-primary">Liens</p>
		<nav class="flex flex-col gap-3">
			{#each liens.links as link}
				<a
					href={link.href}
					class="font-fustat text-body text-dark hover:text-primary transition-colors"
					>{link.label}</a
				>
			{/each}
		</nav>
	</div>

	<!-- Col 8 : Legal -->
	<div class="xl:col-span-1 xl:col-start-8 flex flex-col gap-4 mb-10 xl:mb-0">
		<p class="font-fustat font-semibold text-body text-primary">Legal</p>
		<nav class="flex flex-col gap-3">
			{#each legal as item}
				<a
					href={item.href}
					class="font-fustat text-body text-dark hover:text-primary transition-colors"
					>{item.label}</a
				>
			{/each}
		</nav>
	</div>

	<!-- Bottom bar -->
	<div
		class="xl:col-span-8 mt-16 xl:mt-32 flex flex-col gap-1 xl:flex-row xl:justify-end xl:gap-12"
	>
		<p class="font-fustat text-p-small text-dark-accent">
			Entraide Bruxelles {new Date().getFullYear()} © Tous droit réservés
		</p>
		<p class="font-fustat text-p-small text-dark-accent">
			Made with love by <a
				href="https://unixcreativestudio.com/"
				target="_blank"
				rel="noopener noreferrer"
				class="hover:text-primary transition-colors underline">Unix</a
			>
		</p>
	</div>
</footer>
