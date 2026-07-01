<script lang="ts">
	let {
		src,
		alt,
		class: className = '',
		width,
		height,
		eager = false
	}: {
		src: string;
		alt: string;
		class?: string;
		width?: number;
		height?: number;
		eager?: boolean;
	} = $props();

	const webpSrc = $derived(src.replace(/\.(jpeg|jpg|png)$/i, '.webp'));
</script>

<picture>
	<source srcset={webpSrc} type="image/webp" />
	<img
		{src}
		{alt}
		{width}
		{height}
		loading={eager ? 'eager' : 'lazy'}
		decoding="async"
		class={className}
	/>
</picture>
