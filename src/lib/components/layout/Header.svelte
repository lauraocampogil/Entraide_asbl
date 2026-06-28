<script lang="ts">
	import { page } from '$app/stores';

	let {
		logo,
		navigation
	}: {
		logo: string;
		navigation: { links: { label: string; href: string }[] };
	} = $props();

	let menuOpen = $state(false);

	// Ferme le menu quand on navigue
	$effect(() => {
		$page.url.pathname;
		menuOpen = false;
	});
</script>

<!-- ── Header ── -->
<header class="sticky top-0 z-50 bg-background">
	<div class="flex items-center justify-between px-5 py-3 xl:px-20 xl:py-0 xl:h-[72px]">
		<!-- Logo -->
		<a href="/" class="shrink-0">
			<img src={logo} alt="Entraide Bruxelles" class="h-10 w-auto" />
		</a>

		<!-- Nav desktop -->
		<nav class="hidden xl:flex items-center gap-10">
			{#each navigation.links as link}
				<a
					href={link.href}
					class="font-fustat text-body text-dark hover:text-primary transition-colors duration-200
					{$page.url.pathname === link.href ? 'text-primary' : ''}"
				>
					{link.label}
				</a>
			{/each}
		</nav>

		<!-- Burger mobile -->
		<button
			type="button"
			onclick={() => (menuOpen = !menuOpen)}
			aria-label={menuOpen ? 'Fermer le menu' : 'Ouvrir le menu'}
			aria-expanded={menuOpen}
			class="xl:hidden flex flex-col gap-[5px] p-1"
		>
			<!-- Ligne 1 — longue -->
			<span
				class="block h-[1.5px] w-[27px] bg-dark transition-all duration-300 origin-center
				{menuOpen ? 'rotate-45 translate-y-[6.5px]' : ''}"
			>
			</span>
			<!-- Ligne 2 — longue -->
			<span
				class="block h-[1.5px] w-[27px] bg-dark transition-all duration-300 origin-center
				{menuOpen ? '-rotate-45' : 'translate-y-0'}"
			>
			</span>
			<!-- Ligne 3 — courte (14px comme dans le Figma) -->
			<span
				class="block h-[1.5px] bg-dark transition-all duration-300
				{menuOpen ? 'w-0 opacity-0' : 'w-[14px]'}"
			>
			</span>
		</button>
	</div>
</header>

<!-- ── Drawer mobile (3/4 largeur, depuis la droite) ── -->
{#if menuOpen}
	<!-- Overlay -->
	<button
		type="button"
		class="xl:hidden fixed inset-0 z-40 bg-dark/30 backdrop-blur-sm"
		onclick={() => (menuOpen = false)}
		aria-label="Fermer le menu"
	></button>

	<!-- Drawer -->
	<div
		class="xl:hidden fixed top-0 right-0 z-50 h-full w-3/4 bg-background flex flex-col px-8 pt-8 pb-12 shadow-2xl"
	>
		<!-- Bouton fermer -->
		<button
			type="button"
			onclick={() => (menuOpen = false)}
			aria-label="Fermer"
			class="self-end mb-12 p-1"
		>
			<svg
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M6 6L18 18M6 18L18 6"
					stroke="var(--color-dark)"
					stroke-width="1.5"
					stroke-linecap="round"
				/>
			</svg>
		</button>

		<!-- Liens -->
		<nav class="flex flex-col gap-8">
			{#each navigation.links as link}
				<a
					href={link.href}
					class="font-fustat font-bold text-mobile-title-xl text-dark hover:text-primary transition-colors duration-200
					{$page.url.pathname === link.href ? 'text-primary' : ''}"
				>
					{link.label}
				</a>
			{/each}
		</nav>
	</div>
{/if}
