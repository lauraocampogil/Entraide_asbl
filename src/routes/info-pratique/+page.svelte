<script lang="ts">
	import Builder from '$lib/components/Builder.svelte';

	const blocks = [
		{
			type: 'ContactBlock',
			props: {}
		},
		{
			type: 'PartenairesBlock',
			props: {
				description:
					"Ce que nous faisons, nous ne pourrions pas le faire sans l'aide de nos partenaires.",
				images: [
					{ id: 1, src: '/assets/images/part_logo1.webp', alt: 'La ville de Bruxelles' },
					{ id: 2, src: '/assets/images/part_logo2.webp', alt: "Maison des enfants de l'horizon" },
					{ id: 3, src: '/assets/images/part_logo3.webp', alt: 'CPAS OCMW' },
					{ id: 4, src: '/assets/images/part_logo4.webp', alt: 'Article 27' },
					{ id: 5, src: '/assets/images/part_logo5.webp', alt: 'Bravvo' },
					{ id: 6, src: '/assets/images/part_logo6.webp', alt: 'Fondation Roi Baudoin' },
					{ id: 7, src: '/assets/images/part_logo7.webp', alt: 'One' },
					{ id: 8, src: '/assets/images/part_logo8.webp', alt: 'COCOF' },
					{ id: 9, src: '/assets/images/part_logo9.webp', alt: 'APA' },
					{ id: 10, src: '/assets/images/part_logo10.webp', alt: 'Convivial' },
					{ id: 11, src: '/assets/images/part_logo11.webp', alt: 'VIA' }
				]
			}
		}
	];
</script>

<svelte:head>
	<title>Info pratique | Entraide Bruxelles</title>
	<meta
		name="description"
		content="Contactez Entraide Bruxelles — Rue Moorslede 54, 1020 Bruxelles – Laeken."
	/>
</svelte:head>

<Builder {blocks} />
