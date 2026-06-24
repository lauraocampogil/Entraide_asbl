<script lang="ts">
	import './layout.css';
	let { children } = $props();
</script>

<svelte:head>
	<title>Entraide Bruxelles</title>
</svelte:head>

{@render children()}
