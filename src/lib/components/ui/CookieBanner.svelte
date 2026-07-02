<script lang="ts">
	import { onMount } from 'svelte';

	let visible = $state(false);

	onMount(() => {
		const consent = localStorage.getItem('cookie-consent');
		if (!consent) {
			(window as any)['ga-disable-G-5JY8TCGVVZ'] = true;
			setTimeout(() => (visible = true), 1000);
		} else if (consent === 'declined') {
			(window as any)['ga-disable-G-5JY8TCGVVZ'] = true;
		} else if (consent === 'accepted') {
			(window as any)['ga-disable-G-5JY8TCGVVZ'] = false;
			if (typeof window !== 'undefined' && (window as any).dataLayer) {
				(window as any).dataLayer.push({ event: 'cookie_consent_accepted' });
			}
		}
	});

	function accept() {
		localStorage.setItem('cookie-consent', 'accepted');
		(window as any)['ga-disable-G-5JY8TCGVVZ'] = false;
		visible = false;
		if (typeof window !== 'undefined' && (window as any).dataLayer) {
			(window as any).dataLayer.push({ event: 'cookie_consent_accepted' });
		}
	}

	function decline() {
		localStorage.setItem('cookie-consent', 'declined');
		(window as any)['ga-disable-G-5JY8TCGVVZ'] = true;
		visible = false;
	}
</script>

{#if visible}
	<div class="fixed right-4 bottom-4 left-4 z-999 xl:right-6 xl:left-auto xl:max-w-md">
		<div class="rounded-2xl bg-dark p-5 shadow-2xl">
			<p class="mb-1 flex items-center gap-1.5 text-sm font-bold text-white">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					width="20"
					height="20"
					fill="#ffffff"
					viewBox="0 0 256 256"
					><path
						d="M163.07,164.93a10,10,0,1,1-14.14,0A10,10,0,0,1,163.07,164.93Zm-78.14-8a10,10,0,1,0,14.14,0A10,10,0,0,0,84.93,156.93Zm6.14-41.86a10,10,0,1,0-14.14,0A10,10,0,0,0,91.07,115.07Zm33.86,1.86a10,10,0,1,0,14.14,0A10,10,0,0,0,124.93,116.93ZM230,128A102,102,0,1,1,128,26a6,6,0,0,1,6,6,42,42,0,0,0,42,42,6,6,0,0,1,6,6,42,42,0,0,0,42,42A6,6,0,0,1,230,128Zm-12.18,5.65A54.09,54.09,0,0,1,170.3,85.7a54.09,54.09,0,0,1-48-47.53,90,90,0,1,0,95.47,95.48Z"
					></path></svg
				>
				Ce site utilise des cookies
			</p>
			<p class="mb-4 text-xs leading-relaxed text-white/60">
				Nous utilisons des cookies analytiques (Google Analytics) pour améliorer votre expérience.
				<a href="/cookies" class="text-primary underline underline-offset-2">En savoir plus</a>
			</p>
			<div class="flex gap-2">
				<button
					onclick={decline}
					class="flex-1 cursor-pointer rounded-full border border-white/20 py-2 text-xs font-semibold text-white/70 transition-colors hover:border-white/40 hover:text-white"
				>
					Refuser
				</button>
				<button
					onclick={accept}
					class="flex-1 cursor-pointer rounded-full bg-primary py-2 text-xs font-semibold text-white transition-opacity hover:opacity-90"
				>
					Accepter
				</button>
			</div>
		</div>
	</div>
{/if}
