<script lang="ts">
	let {
		href,
		label,
		variant = 'split',
		type = 'button'
	}: {
		href?: string;
		label: string;
		variant?: 'split' | 'inline' | 'plain';
		type?: 'button' | 'submit';
	} = $props();

	const arrowIcon = `<svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
		<path d="M3 13L13 3M13 3H6M13 3V10" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
	</svg>`;
</script>

<!-- ── SPLIT : deux pills côte à côte ── -->
{#if variant === 'split'}
	<div class="flex items-center gap-3">
		{#if href}
			<a
				{href}
				class="inline-flex items-center rounded-full bg-dark px-6 py-3.5
				font-fustat font-medium text-button text-white
				hover:bg-primary transition-colors duration-200"
			>
				{label}
			</a>
			<a
				{href}
				aria-hidden="true"
				tabindex="-1"
				class="flex items-center justify-center w-12 h-12 rounded-full bg-dark text-white
				hover:bg-primary transition-colors duration-200 shrink-0"
			>
				{@html arrowIcon}
			</a>
		{:else}
			<button
				{type}
				class="inline-flex items-center rounded-full bg-dark px-6 py-3.5
				font-fustat font-medium text-button text-white
				hover:bg-primary transition-colors duration-200"
			>
				{label}
			</button>
			<button
				{type}
				aria-hidden="true"
				tabindex="-1"
				class="flex items-center justify-center w-12 h-12 rounded-full bg-dark text-white
				hover:bg-primary transition-colors duration-200 shrink-0"
			>
				{@html arrowIcon}
			</button>
		{/if}
	</div>

	<!-- ── INLINE : label + icône dans un seul pill ── -->
{:else if variant === 'inline'}
	{#if href}
		<a
			{href}
			class="inline-flex items-center gap-3 rounded-full bg-dark pl-6 pr-2 py-2
			font-fustat font-medium text-button text-white
			hover:bg-primary transition-colors duration-200"
		>
			{label}
			<span
				class="flex items-center justify-center w-9 h-9 rounded-full bg-white/20 text-white shrink-0"
			>
				{@html arrowIcon}
			</span>
		</a>
	{:else}
		<button
			{type}
			class="inline-flex items-center gap-3 rounded-full bg-dark pl-6 pr-2 py-2
			font-fustat font-medium text-button text-white
			hover:bg-primary transition-colors duration-200"
		>
			{label}
			<span
				class="flex items-center justify-center w-9 h-9 rounded-full bg-white/20 text-white shrink-0"
			>
				{@html arrowIcon}
			</span>
		</button>
	{/if}

	<!-- ── PLAIN : fond blanc, texte sombre ── -->
{:else if variant === 'plain'}
	{#if href}
		<a
			{href}
			class="inline-flex items-center rounded-full bg-white px-8 py-3.5
			font-fustat font-medium text-button text-dark
			hover:bg-white/80 transition-colors duration-200"
		>
			{label}
		</a>
	{:else}
		<button
			{type}
			class="inline-flex items-center rounded-full bg-white px-8 py-3.5
			font-fustat font-medium text-button text-dark
			hover:bg-white/80 transition-colors duration-200"
		>
			{label}
		</button>
	{/if}
{/if}
