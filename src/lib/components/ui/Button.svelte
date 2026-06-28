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
</script>

<!-- ── SPLIT ── -->
{#if variant === 'split'}
	{#if href}
		<a {href} class="group flex items-center gap-0.5 w-fit">
			<span
				class="inline-flex items-center rounded-full bg-dark px-5 py-3 text-button text-white group-hover:bg-primary transition-colors duration-200"
			>
				{label}
			</span>
			<span
				class="flex items-center justify-center w-10 h-10 rounded-full bg-dark text-white group-hover:bg-primary transition-colors duration-200 shrink-0"
			>
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M17 17V7H7M17 7L7 17"
						stroke="white"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</span>
		</a>
	{:else}
		<button {type} class="group flex items-center gap-0.5 w-fit">
			<span
				class="inline-flex items-center rounded-full bg-dark px-5 py-3 text-button text-white group-hover:bg-primary transition-colors duration-200"
			>
				{label}
			</span>
			<span
				class="flex items-center justify-center w-10 h-10 rounded-full bg-dark text-white group-hover:bg-primary transition-colors duration-200 shrink-0"
			>
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M17 17V7H7M17 7L7 17"
						stroke="white"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</span>
		</button>
	{/if}

	<!-- ── INLINE ── -->
{:else if variant === 'inline'}
	{#if href}
		<a
			{href}
			class="inline-flex items-center gap-1 rounded-full bg-dark pl-6 pr-2 py-1 text-button text-white hover:bg-primary transition-colors duration-200"
		>
			{label}
			<span
				class="flex items-center justify-center w-8.5 h-8.5 rounded-full bg-white/20 text-white shrink-0"
			>
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M17 17V7H7M17 7L7 17"
						stroke="white"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</span>
		</a>
	{:else}
		<button
			{type}
			class="inline-flex items-center gap-1 rounded-full bg-dark pl-6 pr-2 py-1 text-button text-white hover:bg-primary transition-colors duration-200"
		>
			{label}
			<span class="flex items-center justify-center w-8.5 h-8.5 rounded-full bg-white/20 shrink-0">
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M17 17V7H7M17 7L7 17"
						stroke="white"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</span>
		</button>
	{/if}

	<!-- ── PLAIN ── -->
{:else if variant === 'plain'}
	{#if href}
		<a
			{href}
			class="inline-flex items-center rounded-full bg-white px-7 py-3 text-button text-dark hover:bg-white/80 transition-colors duration-200"
		>
			{label}
		</a>
	{:else}
		<button
			{type}
			class="inline-flex items-center rounded-full bg-white px-7 py-3 text-button text-dark hover:bg-white/80 transition-colors duration-200"
		>
			{label}
		</button>
	{/if}
{/if}
