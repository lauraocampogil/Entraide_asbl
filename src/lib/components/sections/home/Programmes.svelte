<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';
	import Tagline from '$lib/components/ui/Tagline.svelte';
	import Button from '$lib/components/ui/Button.svelte';

	let {
		title,
		ctaLabel,
		ctaHref,
		cards
	}: {
		title: string;
		ctaLabel: string;
		ctaHref: string;
		cards: { id: number; title: string; description: string }[];
	} = $props();

	const icons: Record<number, string> = {
		1: `<svg width="70" height="70" viewBox="0 0 70 70" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M30.625 61.25L45.9375 28.4375L61.25 61.25M35 52.5H56.875M35.9742 15.645C32.7629 15.4233 29.5167 15.3125 26.25 15.3125C20.3999 15.3108 14.5553 15.6722 8.75 16.3946M26.25 15.3125V8.75M35.9742 15.645C32.5967 31.0858 22.4292 43.9833 8.75 51.0475M35.9742 15.645C38.5726 15.8219 41.1656 16.0719 43.75 16.3946M30.3654 41.1717C25.582 36.3085 21.7908 30.5608 19.2033 24.2492" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
</svg>`,
		2: `<svg width="70" height="70" viewBox="0 0 70 70" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M11.6667 55.4167V14.5833C11.6667 13.0362 12.2813 11.5525 13.3752 10.4585C14.4692 9.36458 15.9529 8.75 17.5 8.75H56.5834C57.0475 8.75 57.4926 8.93437 57.8208 9.26256C58.149 9.59075 58.3334 10.0359 58.3334 10.5V48.7492M17.5 49.5833H58.3334M17.5 61.25H58.3334" stroke="black" stroke-width="1.5" stroke-linecap="round"/>
<path d="M17.5 61.25C15.9529 61.25 14.4692 60.6355 13.3752 59.5415C12.2813 58.4475 11.6667 56.9638 11.6667 55.4167C11.6667 53.8696 12.2813 52.3859 13.3752 51.2919C14.4692 50.198 15.9529 49.5834 17.5 49.5834" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M26.25 20.4166H43.75" stroke="black" stroke-width="1.5" stroke-linecap="round"/>
</svg>`,
		3: `<svg width="70" height="70" viewBox="0 0 70 70" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M64.1666 35C64.1666 18.8913 51.1087 5.83337 35 5.83337C18.8912 5.83337 5.83331 18.8913 5.83331 35C5.83331 51.1088 18.8912 64.1667 35 64.1667" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M37.9167 5.97925C37.9167 5.97925 46.6667 17.5001 46.6667 35.0001M32.0833 64.0209C32.0833 64.0209 23.3333 52.5001 23.3333 35.0001C23.3333 17.5001 32.0833 5.97925 32.0833 5.97925M7.67084 45.2084H35M7.67084 24.7917H62.3292" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M63.8137 52.258C65.2545 53.1447 65.1641 55.3001 63.6825 55.4692L56.1954 56.318L52.8383 63.0613C52.1733 64.4001 50.117 63.7438 49.7758 62.0872L46.1154 44.2488C45.8266 42.8488 47.0866 41.968 48.3029 42.7176L63.8137 52.258Z" stroke="black" stroke-width="1.5"/>
</svg>`,
		4: `<svg width="70" height="70" viewBox="0 0 70 70" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M35 55C30.5567 52.7767 26.11 51.6667 21.6667 51.6667C17.2234 51.6667 12.7767 52.7767 8.33337 55V21.9667C12.7767 19.5467 17.2234 18.3334 21.6667 18.3334C26.11 18.3334 30.5567 19.5467 35 21.9667C39.4434 19.5467 43.89 18.3334 48.3334 18.3334C52.7767 18.3334 57.2234 19.5467 61.6667 21.9667V55C57.2234 52.7767 52.7767 51.6667 48.3334 51.6667C43.89 51.6667 39.4434 52.7767 35 55ZM35 21.9667V55" stroke="black" stroke-width="1.14286" stroke-linecap="round" stroke-linejoin="round"/>
</svg>`
	};

	let sectionEl = $state<HTMLElement | null>(null);
	let taglineWrapEl = $state<HTMLElement | null>(null);
	let buttonEl = $state<HTMLElement | null>(null);
	let cardsEls = $state<HTMLElement[]>([]);

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		const tl = gsap.timeline({
			defaults: { ease: 'none' },
			scrollTrigger: {
				trigger: sectionEl,
				start: 'top 95%',
				end: 'top 20%',
				scrub: 1
			}
		});

		tl.fromTo(taglineWrapEl, { y: 50, opacity: 0 }, { y: 0, opacity: 1, duration: 1 })
			.fromTo(buttonEl, { x: 30, opacity: 0 }, { x: 0, opacity: 1, duration: 1 }, '+=0.3')
			.fromTo(
				cardsEls,
				{ y: 60, opacity: 0 },
				{ y: 0, opacity: 1, duration: 1, stagger: 0.5 },
				'+=0.3'
			);

		return () => {
			ScrollTrigger.getAll().forEach((t) => t.kill());
		};
	});
</script>

<section
	bind:this={sectionEl}
	class="grid-section bg-background px-5 py-12 xl:py-20 3xl:container 3xl:mx-auto"
>
	<!-- Tagline + titre : col 1-8 centré -->
	<div
		bind:this={taglineWrapEl}
		class="xl:col-span-8 flex flex-col items-center gap-3 mb-10 xl:mb-6 text-center"
		style="opacity:0"
	>
		<Tagline label="Nos programmes" />
		<h2 class="text-mobile-title-xl xl:text-title-xl text-dark max-w-2xl">
			{title}
		</h2>
	</div>

	<!-- Bouton aligné à droite : col 1-8 -->
	<div
		bind:this={buttonEl}
		class="xl:col-span-8 flex justify-end mb-4 xl:mb-8 xl:mt-10"
		style="opacity:0"
	>
		<Button href={ctaHref} label={ctaLabel} variant="inline" />
	</div>

	<!-- Cards : col 1-8, 4 colonnes desktop -->
	<div class="xl:col-span-8 flex flex-col gap-4 xl:grid xl:grid-cols-4 xl:gap-5">
		{#each cards as card, i}
			<div
				bind:this={cardsEls[i]}
				class="bg-white rounded-[30px] px-8 py-8 flex flex-col items-center gap-4 text-center"
				style="opacity:0"
			>
				<div class="text-dark">
					{@html icons[card.id] ?? icons[1]}
				</div>
				<p class="font-fustat font-bold text-title-sm text-dark">
					{card.title}
				</p>
				<p class="text-body text-dark">
					{card.description}
				</p>
			</div>
		{/each}
	</div>
</section>
