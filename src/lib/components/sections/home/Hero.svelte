<script lang="ts">
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
</script>

<section class="bg-background px-5 pt-8 pb-4 xl:px-20 xl:pt-16 xl:pb-16">
	<!-- ══ MOBILE ══ -->
	<div class="xl:hidden flex flex-col gap-7">
		<!-- Titre -->
		<h1 class="font-bobbyjones font-bold text-mobile-title-3xl leading-[1.15] text-dark">
			<span class="text-primary">APPRENDRE</span>,<br />
			<span class="text-primary">S'INTÉGRER</span> et<br />
			<span class="text-primary">BIEN VIVRE</span> à<br />
			Bruxelles
		</h1>

		<!-- Description -->
		<p class="font-fustat text-description text-dark-accent leading-relaxed">
			Cours de français, aide aux devoirs, démarches administratives et bien plus, pour les adultes
			et les enfants.
		</p>

		<!-- CTA -->
		<Button href={ctaHref} label={ctaLabel} variant="split" />

		<!-- Stats -->
		<div class="grid grid-cols-3 gap-3">
			{#each stats as stat}
				<div class="bg-white rounded-2xl px-3 py-4 flex flex-col gap-1 shadow-sm">
					<span class="font-fustat font-bold text-mobile-large text-dark leading-none">
						{stat.value}
					</span>
					<span class="font-fustat text-p-small text-dark-accent leading-snug">
						{stat.label}
					</span>
				</div>
			{/each}
		</div>

		<!-- Images + blobs -->
		<div class="relative h-[420px] mt-2">
			<!-- Blob vert — haut gauche -->
			<div class="absolute top-0 left-4 w-[130px] h-[130px] z-0 text-secondary" aria-hidden="true">
				<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M43.3,-67.9C55.7,-58.8,64.8,-45.6,69.7,-31.1C74.6,-16.5,75.2,-0.7,71.8,14.4C68.3,29.5,60.7,43.8,49.5,54.2C38.2,64.6,23.2,71,7.1,72.8C-9,74.6,-26.2,71.7,-40.3,63.4C-54.4,55.1,-65.4,41.3,-70.6,25.7C-75.8,10.1,-75.2,-7.3,-69.2,-22.3C-63.1,-37.4,-51.7,-50.1,-38.4,-59C-25.1,-67.9,-9.9,-73,4.4,-78.8C18.7,-84.6,30.9,-77,43.3,-67.9Z"
						transform="translate(100 100) scale(0.85)"
					/>
				</svg>
			</div>

			<!-- Blob jaune — bas droite -->
			<div
				class="absolute bottom-0 right-4 w-[110px] h-[110px] z-0 text-tertiary"
				aria-hidden="true"
			>
				<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M38.9,-64.1C50.2,-55.5,59.2,-44.3,65.1,-31.5C71,-18.7,73.7,-4.4,71.7,9.4C69.7,23.3,63,36.6,53.1,47.2C43.2,57.9,30.1,65.9,15.7,70.3C1.4,74.7,-14.2,75.4,-27.8,70.2C-41.4,65,-52.9,54,-60.2,40.9C-67.5,27.8,-70.5,12.6,-69.3,-2.1C-68.1,-16.8,-62.6,-31,-53.4,-42C-44.2,-53,-31.3,-60.8,-17.8,-65.8C-4.3,-70.8,9.8,-72.9,22.8,-71.3C35.8,-69.6,27.6,-72.7,38.9,-64.1Z"
						transform="translate(100 100) scale(0.85)"
					/>
				</svg>
			</div>

			<!-- Photo 1 — bas gauche -->
			{#if images?.[0]}
				<div
					class="absolute bottom-0 left-0 w-[165px] h-[230px] rounded-2xl overflow-hidden z-10 shadow-sm"
				>
					<img src={images[0].src} alt={images[0].alt} class="w-full h-full object-cover" />
				</div>
			{/if}

			<!-- Photo 2 — haut droite -->
			{#if images?.[1]}
				<div
					class="absolute top-0 right-0 w-[165px] h-[230px] rounded-2xl overflow-hidden z-10 shadow-sm"
				>
					<img src={images[1].src} alt={images[1].alt} class="w-full h-full object-cover" />
				</div>
			{/if}
		</div>
	</div>

	<!-- ══ DESKTOP ══ -->
	<div class="hidden xl:grid xl:grid-cols-2 xl:gap-16 xl:items-center xl:min-h-[680px]">
		<!-- Colonne gauche : texte + stats -->
		<div class="flex flex-col gap-8">
			<h1 class="font-bobbyjones font-bold text-title-3xl leading-[1.15] text-dark">
				<span class="text-primary">APPRENDRE, S'INTÉGRER</span><br />
				et <span class="text-primary">BIEN VIVRE</span> à Bruxelles
			</h1>

			<p class="font-fustat text-subtitle text-dark-accent leading-relaxed max-w-lg">
				Cours de français, aide aux devoirs, démarches administratives et bien plus, pour les
				adultes et les enfants.
			</p>

			<Button href={ctaHref} label={ctaLabel} variant="split" />

			<!-- Stats -->
			<div class="grid grid-cols-3 gap-4">
				{#each stats as stat}
					<div class="bg-white rounded-2xl px-5 py-5 flex flex-col gap-2 shadow-sm">
						<span class="font-fustat font-bold text-title-lg text-dark leading-none">
							{stat.value}
						</span>
						<span class="font-fustat text-p-small text-dark-accent leading-snug">
							{stat.label}
						</span>
					</div>
				{/each}
			</div>
		</div>

		<!-- Colonne droite : blobs + photos -->
		<div class="relative h-[580px]">
			<!-- Blob vert — haut centre -->
			<div
				class="absolute top-4 left-1/2 -translate-x-1/2 w-[200px] h-[200px] z-0 text-secondary"
				aria-hidden="true"
			>
				<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M43.3,-67.9C55.7,-58.8,64.8,-45.6,69.7,-31.1C74.6,-16.5,75.2,-0.7,71.8,14.4C68.3,29.5,60.7,43.8,49.5,54.2C38.2,64.6,23.2,71,7.1,72.8C-9,74.6,-26.2,71.7,-40.3,63.4C-54.4,55.1,-65.4,41.3,-70.6,25.7C-75.8,10.1,-75.2,-7.3,-69.2,-22.3C-63.1,-37.4,-51.7,-50.1,-38.4,-59C-25.1,-67.9,-9.9,-73,4.4,-78.8C18.7,-84.6,30.9,-77,43.3,-67.9Z"
						transform="translate(100 100) scale(0.85)"
					/>
				</svg>
			</div>

			<!-- Blob jaune — bas droite -->
			<div
				class="absolute bottom-8 right-0 w-[170px] h-[170px] z-0 text-tertiary"
				aria-hidden="true"
			>
				<svg viewBox="0 0 200 200" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
					<path
						d="M38.9,-64.1C50.2,-55.5,59.2,-44.3,65.1,-31.5C71,-18.7,73.7,-4.4,71.7,9.4C69.7,23.3,63,36.6,53.1,47.2C43.2,57.9,30.1,65.9,15.7,70.3C1.4,74.7,-14.2,75.4,-27.8,70.2C-41.4,65,-52.9,54,-60.2,40.9C-67.5,27.8,-70.5,12.6,-69.3,-2.1C-68.1,-16.8,-62.6,-31,-53.4,-42C-44.2,-53,-31.3,-60.8,-17.8,-65.8C-4.3,-70.8,9.8,-72.9,22.8,-71.3C35.8,-69.6,27.6,-72.7,38.9,-64.1Z"
						transform="translate(100 100) scale(0.85)"
					/>
				</svg>
			</div>

			<!-- Photo 1 — bas gauche (plus grande) -->
			{#if images?.[0]}
				<div
					class="absolute bottom-0 left-0 w-[260px] h-[340px] rounded-3xl overflow-hidden z-10 shadow-md"
				>
					<img src={images[0].src} alt={images[0].alt} class="w-full h-full object-cover" />
				</div>
			{/if}

			<!-- Photo 2 — haut droite -->
			{#if images?.[1]}
				<div
					class="absolute top-0 right-0 w-[260px] h-[340px] rounded-3xl overflow-hidden z-10 shadow-md"
				>
					<img src={images[1].src} alt={images[1].alt} class="w-full h-full object-cover" />
				</div>
			{/if}
		</div>
	</div>
</section>
