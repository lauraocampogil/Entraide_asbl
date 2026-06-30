<script lang="ts">
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	let {
		logo,
		navigation
	}: {
		logo: string;
		navigation: { links: { label: string; href: string }[] };
	} = $props();

	let menuOpen = $state(false);
	let hidden = $state(false);
	let lastY = 0;

	$effect(() => {
		$page.url.pathname;
		menuOpen = false;
	});

	$effect(() => {
		if (menuOpen) {
			document.documentElement.style.overflow = 'hidden';
		} else {
			document.documentElement.style.overflow = '';
		}

		return () => {
			document.documentElement.style.overflow = '';
		};
	});

	onMount(() => {
		const handleScroll = () => {
			const currentY = window.scrollY;
			if (currentY < 80) {
				hidden = false;
			} else if (currentY > lastY) {
				hidden = true;
			} else {
				hidden = false;
			}
			lastY = currentY;
		};

		window.addEventListener('scroll', handleScroll, { passive: true });
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<!-- ── Header ── -->
<header
	class="fixed top-0 left-0 right-0 z-50 bg-background transition-transform duration-300"
	class:-translate-y-full={hidden}
>
	<div class="3xl:container 3xl:mx-auto">
		<div class="flex items-center justify-between px-5 py-3 xl:px-20 xl:py-2 xl:h-20">
			<!-- Logo -->
			<a href="/" class="shrink-0">
				<img src={logo} alt="Entraide Bruxelles" class="h-12 w-auto" />
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
				class="xl:hidden relative z-50 flex flex-col gap-1.25 p-1"
			>
				<span
					class="block h-[1.5px] w-6.75 bg-dark transition-all duration-300 origin-center
					{menuOpen ? 'rotate-45 translate-y-[6.5px]' : ''}"
				>
				</span>
				<span
					class="block h-[1.5px] w-6.75 bg-dark transition-all duration-300 origin-center
					{menuOpen ? '-rotate-45' : 'translate-y-0'}"
				>
				</span>
				<span
					class="block h-[1.5px] bg-dark transition-all duration-300
					{menuOpen ? 'w-0 opacity-0' : 'w-3.5'}"
				>
				</span>
			</button>
		</div>
	</div>
</header>

<!-- Spacer pour compenser le header devenu fixed -->
<div class="h-15 xl:h-20" aria-hidden="true"></div>

<!-- ── Drawer mobile (3/4 largeur, depuis la droite) ── -->
{#if menuOpen}
	<button
		type="button"
		class="xl:hidden fixed inset-0 z-40 bg-dark/30 backdrop-blur-sm"
		onclick={() => (menuOpen = false)}
		aria-label="Fermer le menu"
	></button>

	<div
		class="xl:hidden fixed top-0 right-0 z-45 h-full w-3/4 bg-background flex flex-col px-8 pt-24 pb-12 shadow-2xl"
	>
		<nav class="flex flex-col gap-8">
			{#each navigation.links as link}
				<a
					href={link.href}
					class="text-mobile-title-sm text-dark hover:text-primary transition-colors duration-200
					{$page.url.pathname === link.href ? 'text-primary' : ''}"
				>
					{link.label}
				</a>
			{/each}
		</nav>
	</div>
{/if}
