<script lang="ts">
	let { label }: { label: string } = $props();
</script>

<div class="flex items-center gap-1.5">
	<svg
		width="15"
		height="15"
		viewBox="0 0 15 15"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
		aria-hidden="true"
		class="shrink-0 opacity-50"
	>
		<path d="M7.5 0.5L14.5 5.5L12 14H3L0.5 5.5L7.5 0.5Z" fill="var(--color-primary)" />
	</svg>

	<span class="uppercase text-mobile-tag xl:text-tag">
		{label}
	</span>
</div>
