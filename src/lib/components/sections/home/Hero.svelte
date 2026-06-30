<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { loaderDone } from '$lib/stores/loader';
	import Button from '$lib/components/ui/Button.svelte';

	let {
		ctaLabel,
		ctaHref,
		stats,
		images
	}: {
		ctaLabel: string;
		ctaHref: string;
		stats: { value: string; label: string }[];
		images: { src: string; alt: string }[];
	} = $props();

	let titleEl = $state<HTMLElement | null>(null);
	let textEl = $state<HTMLElement | null>(null);
	let buttonEl = $state<HTMLElement | null>(null);
	let statsEls = $state<HTMLElement[]>([]);
	let statValueEls = $state<HTMLElement[]>([]);
	let starEl = $state<HTMLElement | null>(null);
	let bolEl = $state<HTMLElement | null>(null);
	let photo1El = $state<HTMLElement | null>(null);
	let photo2El = $state<HTMLElement | null>(null);

	function parseStat(value: string) {
		const prefix = value.match(/^\+/) ? '+' : '';
		const suffix = !prefix && value.match(/\+$/) ? '+' : '';
		const number = parseInt(value.replace(/[^\d]/g, ''), 10) || 0;
		return { prefix, suffix, number };
	}

	function runHeroAnimation() {
		const tl = gsap.timeline({ defaults: { ease: 'expo.out' } });

		tl.fromTo(titleEl, { y: 50, opacity: 0 }, { y: 0, opacity: 1, duration: 1.3 })
			.fromTo(textEl, { y: 35, opacity: 0 }, { y: 0, opacity: 1, duration: 1.1 }, '-=0.85')
			.fromTo(buttonEl, { y: 25, opacity: 0 }, { y: 0, opacity: 1, duration: 1.0 }, '-=0.7')
			.fromTo(
				statsEls,
				{ y: 35, opacity: 0 },
				{ y: 0, opacity: 1, duration: 1.0, stagger: 0.16 },
				'-=0.55'
			)
			.fromTo(photo1El, { y: 50, opacity: 0 }, { y: 0, opacity: 1, duration: 1.2 }, '-=1.6')
			.fromTo(photo2El, { y: 50, opacity: 0 }, { y: 0, opacity: 1, duration: 1.2 }, '-=1.05')
			.fromTo(
				starEl,
				{ scale: 0.6, opacity: 0, rotate: -15 },
				{ scale: 1, opacity: 1, rotate: 0, duration: 1.0 },
				'-=1.0'
			)
			.fromTo(
				bolEl,
				{ scale: 0.6, opacity: 0, rotate: 15 },
				{ scale: 1, opacity: 1, rotate: 0, duration: 1.0 },
				'-=0.85'
			);

		statValueEls.forEach((el, i) => {
			if (!el) return;
			const raw = stats[i].value;
			const { prefix, suffix, number } = parseStat(raw);
			const counter = { val: 0 };

			gsap.to(counter, {
				val: number,
				duration: 2.0,
				delay: 1.4 + i * 0.16,
				ease: 'power2.out',
				onUpdate: () => {
					el.textContent = `${prefix}${Math.floor(counter.val)}${suffix}`;
				}
			});
		});
	}

	onMount(() => {
		const unsubscribe = loaderDone.subscribe((done) => {
			if (done) {
				runHeroAnimation();
			}
		});
		return unsubscribe;
	});
</script>

<section
	class="grid-section sm-grid-section bg-background px-5 sm:px-8 md:px-10 lg:px-12 pt-14 pb-10 xl:pt-30 xl:pb-30 3xl:container 3xl:mx-auto"
>
	<!-- Col 1-4 -->
	<div
		class="col-span-8 sm:col-span-8 md:col-span-4 xl:col-span-4 xl:col-start-1 flex flex-col gap-7 xl:py-8"
	>
		<div class="flex flex-col gap-3 xl:gap-4 xl:pt-8">
			<h1
				bind:this={titleEl}
				class="font-bobbyjones text-mobile-title-3xl xl:text-title-3xl text-dark"
				style="opacity:0"
			>
				<span class="text-primary">APPRENDRE, S'INTÉGRER</span><br />
				<span class="font-fustat">et&nbsp;</span><span class="text-primary">BIEN VIVRE</span><span
					class="font-fustat">&nbsp;à Bruxelles</span
				>
			</h1>

			<p
				bind:this={textEl}
				class="text-description xl:text-subtitle text-dark xl:max-w-lg"
				style="opacity:0"
			>
				Cours de français, aide aux devoirs, démarches administratives et bien plus, pour les
				adultes et les enfants.
			</p>
		</div>

		<div bind:this={buttonEl} style="opacity:0">
			<Button href={ctaHref} label={ctaLabel} variant="split" />
		</div>

		<div class="grid grid-cols-3 gap-2 xl:gap-3">
			{#each stats as stat, i}
				<div
					bind:this={statsEls[i]}
					class="bg-white rounded-2xl xl:rounded-3xl flex flex-col items-center justify-center gap-1 xl:gap-2 py-4 xl:h-33.75"
					style="opacity:0"
				>
					<span
						bind:this={statValueEls[i]}
						class="text-mobile-large xl:text-large text-dark leading-none text-center"
					>
						0
					</span>
					<span
						class="font-fustat text-p-small xl:text-description text-dark text-center leading-snug px-3 whitespace-pre-line"
					>
						{stat.label}
					</span>
				</div>
			{/each}
		</div>
	</div>

	<!-- Col 5-8 — identique à l'original, juste col-span ajouté -->
	<div
		class="col-span-8 sm:col-span-8 md:col-span-4 xl:col-span-4 xl:col-start-5 relative h-105 xl:h-160 mt-4 xl:mt-0 overflow-visible"
	>
		<img
			bind:this={starEl}
			src="/assets/svg/Star.svg"
			alt=""
			aria-hidden="true"
			class="absolute z-0
			top-2.5 left-[5%]
			w-32 h-auto
			xl:top-5 xl:left-[calc(25%-100px)] xl:w-50"
			style="opacity:0"
		/>

		{#if images?.[0]}
			<div
				bind:this={photo1El}
				class="absolute bottom-0 left-0
				w-[47%] h-67.5
				xl:w-[calc(50%-8px)] xl:h-100
				rounded-2xl xl:rounded-[50px] overflow-hidden z-10 shadow-md"
				style="opacity:0"
			>
				<img src={images[0].src} alt={images[0].alt} class="w-full h-full object-cover" />
			</div>
		{/if}

		{#if images?.[1]}
			<div
				bind:this={photo2El}
				class="absolute top-0 right-0
				w-[47%] h-67.5
				xl:w-[calc(50%-8px)] xl:h-100
				rounded-2xl xl:rounded-[50px] overflow-hidden z-10 shadow-md"
				style="opacity:0"
			>
				<img src={images[1].src} alt={images[1].alt} class="w-full h-full object-cover" />
			</div>
		{/if}

		<img
			bind:this={bolEl}
			src="/assets/svg/Bol.svg"
			alt=""
			aria-hidden="true"
			class="absolute z-0
			bottom-2.5 right-[5%]
			w-32 h-auto
			xl:bottom-2 xl:right-[calc(25%-95px)] xl:w-50"
			style="opacity:0"
		/>
	</div>
</section>
