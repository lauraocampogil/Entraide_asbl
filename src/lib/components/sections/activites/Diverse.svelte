<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';

	let {
		title,
		activities
	}: {
		title: string;
		activities: {
			id: number;
			title: string;
			description: string;
			images: { id: number; src: string; alt: string }[];
		}[];
	} = $props();

	let activeId = $state(activities[0]?.id ?? 1);

	const active = $derived(activities.find((a) => a.id === activeId));
</script>

<section class="bg-background px-5 py-12 xl:px-20 xl:py-20">
	<!-- Tagline + titre -->
	<div class="flex flex-col items-center gap-3 mb-10 xl:mb-12 text-center">
		<Tagline label="Diverse activités" />
		<h2
			class="font-fustat font-medium text-mobile-title-xl xl:text-title-2xl text-dark leading-snug"
		>
			{title}
		</h2>
	</div>

	<!-- ══ MOBILE : accordion full width ══ -->
	<div class="xl:hidden flex flex-col divide-y divide-black/10">
		{#each activities as activity}
			<div>
				<!-- Header accordion -->
				<button
					type="button"
					onclick={() => (activeId = activeId === activity.id ? -1 : activity.id)}
					class="w-full flex items-center justify-between py-4 text-left"
				>
					<span class="font-fustat font-medium text-mobile-title-sm text-dark">
						{activity.title}
					</span>
					<svg
						width="16"
						height="16"
						viewBox="0 0 16 16"
						fill="none"
						class="shrink-0 transition-transform duration-300 {activeId === activity.id
							? 'rotate-180'
							: ''}"
					>
						<path
							d="M3 6L8 11L13 6"
							stroke="currentColor"
							stroke-width="1.5"
							stroke-linecap="round"
							stroke-linejoin="round"
						/>
					</svg>
				</button>

				<!-- Contenu accordion -->
				{#if activeId === activity.id}
					<div class="pb-6 flex flex-col gap-4">
						<p class="font-fustat text-description text-dark-accent leading-relaxed">
							{activity.description}
						</p>
						<!-- Photos en grille 2+1 -->
						<div class="grid grid-cols-2 gap-2">
							{#each activity.images.slice(0, 2) as img}
								<div class="rounded-xl overflow-hidden h-36">
									<img src={img.src} alt={img.alt} class="w-full h-full object-cover" />
								</div>
							{/each}
							{#if activity.images[2]}
								<div class="col-span-2 rounded-xl overflow-hidden h-36">
									<img
										src={activity.images[2].src}
										alt={activity.images[2].alt}
										class="w-full h-full object-cover"
									/>
								</div>
							{/if}
						</div>
					</div>
				{/if}
			</div>
		{/each}
	</div>

	<!-- ══ DESKTOP : accordion gauche + photos droite ══ -->
	<div class="hidden xl:grid xl:grid-cols-8 xl:gap-x-5 xl:items-start">
		<!-- Col gauche : liste accordion -->
		<div class="col-span-3 flex flex-col divide-y divide-black/10">
			{#each activities as activity}
				<button
					type="button"
					onclick={() => (activeId = activity.id)}
					class="flex items-start justify-between py-5 text-left group"
				>
					<div class="flex flex-col gap-2">
						<span
							class="font-fustat font-medium text-title-sm text-dark group-hover:text-primary transition-colors
							{activeId === activity.id ? 'text-primary' : ''}"
						>
							{activity.title}
						</span>
						{#if activeId === activity.id}
							<p class="font-fustat text-p-small text-dark-accent leading-relaxed max-w-xs">
								{activity.description}
							</p>
						{/if}
					</div>
					<svg
						width="16"
						height="16"
						viewBox="0 0 16 16"
						fill="none"
						class="shrink-0 mt-1 transition-transform duration-300 {activeId === activity.id
							? 'rotate-90 text-primary'
							: 'text-dark-accent'}"
					>
						<path
							d="M6 3L11 8L6 13"
							stroke="currentColor"
							stroke-width="1.5"
							stroke-linecap="round"
							stroke-linejoin="round"
						/>
					</svg>
				</button>
			{/each}
		</div>

		<!-- Col droite : photos de l'activité active -->
		<div class="col-span-5 col-start-4 grid grid-cols-2 grid-rows-2 gap-3 h-[460px]">
			{#if active}
				<!-- Photo grande — haut gauche (2 rows) -->
				{#if active.images[0]}
					<div class="row-span-2 rounded-2xl overflow-hidden">
						<img
							src={active.images[0].src}
							alt={active.images[0].alt}
							class="w-full h-full object-cover"
						/>
					</div>
				{/if}
				<!-- Photo haut droite -->
				{#if active.images[1]}
					<div class="rounded-2xl overflow-hidden">
						<img
							src={active.images[1].src}
							alt={active.images[1].alt}
							class="w-full h-full object-cover"
						/>
					</div>
				{/if}
				<!-- Photo bas droite -->
				{#if active.images[2]}
					<div class="rounded-2xl overflow-hidden">
						<img
							src={active.images[2].src}
							alt={active.images[2].alt}
							class="w-full h-full object-cover"
						/>
					</div>
				{/if}
			{/if}
		</div>
	</div>
</section>
