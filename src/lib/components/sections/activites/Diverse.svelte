<script lang="ts">
	import Tagline from '$lib/components/ui/Tagline.svelte';
	import gsap from 'gsap';

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

	let activeId = $state<number>(0);
	$effect(() => {
		activeId = activities[0]?.id ?? 1;
	});
	const active = $derived(activities.find((a) => a.id === activeId));

	let listEl = $state<HTMLElement | null>(null);
	let redLineEl = $state<HTMLElement | null>(null);

	function moveRedLine(cardEl: HTMLElement) {
		if (!listEl || !redLineEl) return;
		const listTop = listEl.getBoundingClientRect().top;
		const cardTop = cardEl.getBoundingClientRect().top;
		const cardHeight = cardEl.getBoundingClientRect().height;
		// Instantané — suit l'accordion frame par frame
		gsap.set(redLineEl, {
			top: cardTop - listTop,
			height: cardHeight
		});
	}

	function animateRedLine(cardEl: HTMLElement) {
		if (!listEl || !redLineEl) return;
		const listTop = listEl.getBoundingClientRect().top;
		const cardTop = cardEl.getBoundingClientRect().top;
		const cardHeight = cardEl.getBoundingClientRect().height;
		// Animé — pour le déplacement d'un item à l'autre
		gsap.to(redLineEl, {
			top: cardTop - listTop,
			height: cardHeight,
			duration: 0.5,
			ease: 'expo.inOut'
		});
	}

	function toggleActivity(id: number, card: HTMLElement) {
		if (activeId === id) return;

		// Ferme le précédent
		const prevCard = document.querySelector(`[data-card="${activeId}"]`) as HTMLElement;
		if (prevCard) {
			const prevAnswer = prevCard.querySelector('[data-answer]') as HTMLElement;
			const prevArrow = prevCard.querySelector('[data-arrow]') as HTMLElement;
			gsap.killTweensOf(prevAnswer);
			gsap.to(prevAnswer, { height: 0, opacity: 0, duration: 0.5, ease: 'expo.inOut' });
			gsap.to(prevArrow, { rotation: 0, duration: 0.35, ease: 'expo.inOut' });
		}

		// Déplace la ligne vers la nouvelle card (animé)
		animateRedLine(card);

		// Ouvre le nouveau
		activeId = id;
		const answerEl = card.querySelector('[data-answer]') as HTMLElement;
		const arrowEl = card.querySelector('[data-arrow]') as HTMLElement;
		gsap.killTweensOf(answerEl);
		gsap.fromTo(
			answerEl,
			{ height: 0, opacity: 0 },
			{
				height: 'auto',
				opacity: 1,
				duration: 0.65,
				ease: 'expo.inOut',
				onUpdate: () => moveRedLine(card),
				onComplete: () => moveRedLine(card)
			}
		);
		gsap.to(arrowEl, { rotation: 90, duration: 0.35, ease: 'expo.inOut' });
	}

	$effect(() => {
		if (!listEl || !redLineEl) return;
		const firstCard = listEl.querySelector('[data-card]') as HTMLElement;
		if (firstCard) {
			const firstAnswer = firstCard.querySelector('[data-answer]') as HTMLElement;
			const firstArrow = firstCard.querySelector('[data-arrow]') as HTMLElement;
			gsap.set(firstAnswer, { height: 'auto', opacity: 1 });
			gsap.set(firstArrow, { rotation: 90 });
			setTimeout(() => moveRedLine(firstCard), 0);
		}
	});
</script>

<section class="bg-background px-5 py-12 grid-section xl:py-20 3xl:container 3xl:mx-auto">
	<!-- Tagline + titre : pleine largeur -->
	<div class="col-span-8 flex flex-col items-center gap-3 mb-10 xl:mb-12 text-center">
		<Tagline label="Diverse activités" />
		<h2 class="text-mobile-title-xl xl:text-title-xl text-dark">
			{title}
		</h2>
	</div>

	<!-- ══ MOBILE : accordion ══ -->
	<div class="xl:hidden col-span-8 flex flex-col divide-y divide-black/10">
		{#each activities as activity}
			<div>
				<button
					type="button"
					onclick={() => (activeId = activeId === activity.id ? -1 : activity.id)}
					class="w-full flex items-center justify-between py-4 text-left"
				>
					<span class="text-mobile-title-md text-dark">{activity.title}</span>
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
				{#if activeId === activity.id}
					<div class="pb-6 flex flex-col gap-4">
						<p class="text-body text-dark">{activity.description}</p>
						<div class="grid grid-cols-2 gap-2">
							{#each activity.images.slice(0, 2) as img}
								<div class="rounded-2xl overflow-hidden h-36">
									<img src={img.src} alt={img.alt} class="w-full h-full object-cover" />
								</div>
							{/each}
							{#if activity.images[2]}
								<div class="col-span-2 rounded-2xl overflow-hidden h-36">
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

	<!-- ══ DESKTOP ══ -->

	<!-- Col gauche : liste -->
	<div bind:this={listEl} class="hidden xl:block col-span-3 relative self-start">
		<div class="absolute left-0 top-0 bottom-0 w-0.5 bg-black/10"></div>
		<div
			bind:this={redLineEl}
			class="absolute left-0 top-0 w-0.5 bg-primary"
			style="height: 0px;"
		></div>

		{#each activities as activity}
			<div
				data-card={activity.id}
				role="button"
				tabindex="0"
				class="relative cursor-pointer group pl-5 py-5"
				onclick={(e) => toggleActivity(activity.id, e.currentTarget as HTMLElement)}
				onkeydown={(e) =>
					e.key === 'Enter' && toggleActivity(activity.id, e.currentTarget as HTMLElement)}
			>
				<div class="flex items-start justify-between gap-3">
					<div class="flex flex-col gap-2">
						<span
							class="text-title-sm xl:text-title-md transition-colors duration-200 {activeId ===
							activity.id
								? 'text-primary'
								: 'text-dark group-hover:text-primary'}"
						>
							{activity.title}
						</span>
						<div
							data-answer={activity.id}
							class="overflow-hidden text-body text-dark"
							style="height: 0; opacity: 0"
						>
							<p class="pt-1 pb-2 max-w-xs">{activity.description}</p>
						</div>
					</div>
					<svg
						data-arrow={activity.id}
						width="16"
						height="16"
						viewBox="0 0 16 16"
						fill="none"
						class="shrink-0 mt-1 transition-colors duration-200 {activeId === activity.id
							? 'text-primary'
							: 'text-dark'}"
						style="transform-origin: center;"
					>
						<path
							d="M6 3L11 8L6 13"
							stroke="currentColor"
							stroke-width="1.5"
							stroke-linecap="round"
							stroke-linejoin="round"
						/>
					</svg>
				</div>
			</div>
		{/each}
	</div>

	<!-- Col droite : images — même hauteur que la liste -->
	<div class="hidden xl:flex col-span-5 col-start-4 gap-3 self-start h-135">
		{#if active}
			<div class="flex flex-col gap-3 flex-1">
				{#if active.images[0]}
					<div class="rounded-[30px] overflow-hidden flex-1">
						<img
							src={active.images[0].src}
							alt={active.images[0].alt}
							class="w-full h-full object-cover"
						/>
					</div>
				{/if}
				{#if active.images[1]}
					<div class="rounded-[30px] overflow-hidden flex-1">
						<img
							src={active.images[1].src}
							alt={active.images[1].alt}
							class="w-full h-full object-cover"
						/>
					</div>
				{/if}
			</div>
			{#if active.images[2]}
				<div class="rounded-[30px] overflow-hidden flex-1">
					<img
						src={active.images[2].src}
						alt={active.images[2].alt}
						class="w-full h-full object-cover"
					/>
				</div>
			{/if}
		{/if}
	</div>
</section>
