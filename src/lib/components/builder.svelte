<script lang="ts">
	import Hero from '$lib/components/sections/home/Hero.svelte';
	import Partenaires from '$lib/components/ui/Partenaires.svelte';
	import Programmes from '$lib/components/sections/home/Programmes.svelte';
	import CTA from '$lib/components/ui/CTA.svelte';
	import APropos from '$lib/components/sections/about/APropos.svelte';
	import Histoire from '$lib/components/sections/about/Histoire.svelte';
	import Valeurs from '$lib/components/sections/about/Valeurs.svelte';
	import PourQui from '$lib/components/sections/about/PourQui.svelte';
	import Equipe from '$lib/components/sections/about/Equipe.svelte';
	import ActivitesHero from '$lib/components/sections/activites/ActivitesHero.svelte';
	import Diverse from '$lib/components/sections/activites/Diverse.svelte';

	let { blocks = [] }: { blocks: { type: string; props: Record<string, any> }[] } = $props();

	const components: Record<string, any> = {
		HeroBlock: Hero,
		PartenairesBlock: Partenaires,
		ProgrammesBlock: Programmes,
		CTABlock: CTA,
		AProposBlock: APropos,
		HistoireBlock: Histoire,
		ValeursBlock: Valeurs,
		PourquiBlock: PourQui,
		EquipeBlock: Equipe,
		ActivitéBlock: ActivitesHero,
		DiverseBlock: Diverse
	};
</script>

{#each blocks as block}
	{@const Component = components[block.type]}
	{#if Component}
		<Component {...block.props} />
	{/if}
{/each}
