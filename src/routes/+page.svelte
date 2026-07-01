<script lang="ts">
	import Builder from '$lib/components/Builder.svelte';

	const blocks = [
		{
			type: 'HeroBlock',
			props: {
				ctaLabel: 'Découvrir nos activités',
				ctaHref: '/nos-activites',
				stats: [
					{ value: '+550', label: 'Adultes\nformés' },
					{ value: '70', label: 'Enfants\naccompagnés' },
					{ value: '20+', label: 'Nationalités\ndifférentes' }
				],
				images: [
					{ src: '/assets/images/asbl6.webp', alt: 'Cours de français à Entraide Bruxelles' },
					{ src: '/assets/images/asbl7.webp', alt: 'Bibliothèque Entraide Bruxelles' }
				]
			}
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
		},
		{
			type: 'ProgrammesBlock',
			props: {
				title: "Qu'est-ce qu'on peut faire pour vous ?",
				ctaLabel: 'En savoir plus',
				ctaHref: '/nos-activites',
				cards: [
					{
						id: 1,
						title: 'Apprendre le français',
						description:
							'Nos cours sont faits pour vous accueillir là où vous en êtes, sans jugement et à votre propre rythme.'
					},
					{
						id: 2,
						title: 'Aide pour les devoirs',
						description:
							"Un endroit calme et bienveillant pour aider votre enfant à avancer et reprendre confiance à l'école"
					},
					{
						id: 3,
						title: 'Utiliser internet',
						description:
							'Mails, démarches en ligne, smartphone... On vous montre comment faire, doucement et sans vous perdre'
					},
					{
						id: 4,
						title: 'Aide pour les papiers',
						description:
							'Un formulaire, une lettre, une inscription ? On prend le temps de vous écouter et de vous aider'
					}
				]
			}
		},
		{
			type: 'CTABlock',
			props: {
				title: 'Vous voulez nous rejoindre?',
				description:
					'Que ce soit pour suivre une formation, donner un coup de main en tant que bénévole ou faire un stage — vous êtes les bienvenus. On sera heureux de vous accueillir.',
				ctaLabel: 'Nous contactez',
				ctaHref: '/info-pratique'
			}
		}
	];
</script>

<svelte:head>
	<title>Entraide Bruxelles | Apprendre, s'intégrer et bien vivre</title>
	<meta
		name="description"
		content="Cours de français, aide aux devoirs, démarches administratives et bien plus à Laeken, Bruxelles."
	/>
</svelte:head>

<Builder {blocks} />
