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
			<p class="mb-1 text-sm font-bold text-white">
				<i class="ph-light ph-cookie"></i> Ce site utilise des cookies
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
