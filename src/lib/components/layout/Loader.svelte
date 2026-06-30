<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { loaderDone } from '$lib/stores/loader';

	let loaderEl = $state<HTMLElement | null>(null);
	let entraideEl = $state<HTMLElement | null>(null);
	let bruxellesEl = $state<HTMLElement | null>(null);
	let pentagonEl = $state<HTMLElement | null>(null);

	let visible = $state(true);

	function lockScroll() {
		const scrollY = window.scrollY;
		document.body.style.position = 'fixed';
		document.body.style.top = `-${scrollY}px`;
		document.body.style.left = '0';
		document.body.style.right = '0';
		document.body.style.width = '100%';
		document.documentElement.style.overflow = 'hidden';
	}

	function unlockScroll() {
		const scrollY = document.body.style.top;
		document.body.style.position = '';
		document.body.style.top = '';
		document.body.style.left = '';
		document.body.style.right = '';
		document.body.style.width = '';
		document.documentElement.style.overflow = '';
		window.scrollTo(0, parseInt(scrollY || '0') * -1);
	}

	onMount(() => {
		lockScroll();

		const tl = gsap.timeline({
			defaults: { ease: 'expo.out' },
			onComplete: () => {
				unlockScroll();
				visible = false;
				loaderDone.set(true);
			}
		});

		tl.fromTo(entraideEl, { x: -80, opacity: 0 }, { x: 0, opacity: 1, duration: 0.9 })
			.fromTo(bruxellesEl, { x: 80, opacity: 0 }, { x: 0, opacity: 1, duration: 0.9 }, '-=0.6')
			.fromTo(
				pentagonEl,
				{ scale: 0, opacity: 0, rotate: -180 },
				{ scale: 1, opacity: 1, rotate: 0, duration: 0.8, ease: 'back.out(1.7)' },
				'-=0.2'
			)
			.to({}, { duration: 0.4 })
			.to(loaderEl, {
				yPercent: -100,
				duration: 0.8,
				ease: 'expo.inOut'
			});
	});
</script>

{#if visible}
	<div
		bind:this={loaderEl}
		class="fixed inset-0 z-200 bg-background flex items-center justify-center overflow-hidden"
	>
		<div class="flex items-center gap-2 xl:gap-3">
			<span
				bind:this={entraideEl}
				class="font-bobbyjones font-bold text-primary text-mobile-title-xl xl:text-title-2xl leading-none"
				style="opacity: 0;"
			>
				ENTRAIDE
			</span>

			<div bind:this={pentagonEl} style="opacity: 0;">
				<img
					src="/assets/svg/Pentagon_Entraide.svg"
					alt=""
					aria-hidden="true"
					class="w-10 h-10 xl:w-14 xl:h-14"
				/>
			</div>

			<span
				bind:this={bruxellesEl}
				class="font-bobbyjones font-bold text-[#266500] text-mobile-title-xl xl:text-title-2xl leading-none"
				style="opacity: 0;"
			>
				BRUXELLES
			</span>
		</div>
	</div>
{/if}
