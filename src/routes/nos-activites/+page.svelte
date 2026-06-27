<script lang="ts">
	import Builder from '$lib/components/Builder.svelte';

	const blocks = [
		{
			type: 'ActivitesHeroBlock',
			props: {}
		},
		{
			type: 'DiverseBlock',
			props: {
				title: 'Ce que nous proposons',
				activities: [
					{
						id: 1,
						title: 'Apprendre le français',
						description:
							'Atteignez le niveau A2 pour gagner en confiance dans votre vie quotidienne et professionnelle. Un apprentissage adapté à votre rythme.',
						images: [
							{ id: 1, src: '/assets/images/asbl2.jpeg', alt: 'Cours de français' },
							{ id: 2, src: '/assets/images/asbl20.png', alt: 'Cours de français' },
							{ id: 3, src: '/assets/images/asbl8.jpeg', alt: 'Cours de français' }
						]
					},
					{
						id: 2,
						title: "Parcours d'accueil",
						description:
							'Accompagnement complet pour les nouveaux arrivants (COCOF). 16 à 20h par semaine dédiées au français, aux démarches et aux liens sociaux.',
						images: [
							{ id: 1, src: '/assets/images/asbl12.jpeg', alt: "Parcours d'accueil" },
							{ id: 2, src: '/assets/images/asbl10.jpeg', alt: "Parcours d'accueil" },
							{ id: 3, src: '/assets/images/asbl19.png', alt: "Parcours d'accueil" }
						]
					},
					{
						id: 3,
						title: "L'école des devoirs",
						description:
							'De la 1ère à la 6ème primaire. Un cadre calme pour la préparation du CEB et des activités culturelles épanouissantes.',
						images: [
							{ id: 1, src: '/assets/images/asbl7.jpeg', alt: 'École des devoirs' },
							{ id: 2, src: '/assets/images/asbl17.jpeg', alt: 'École des devoirs' },
							{ id: 3, src: '/assets/images/asbl3.jpeg', alt: 'École des devoirs' }
						]
					},
					{
						id: 4,
						title: 'Ateliers numériques',
						description:
							'Apprenez à maîtriser Internet et les outils essentiels : Itsme, Actiris, e-mails, Word et vos démarches en ligne en toute autonomie.',
						images: [
							{ id: 1, src: '/assets/images/asbl6.jpeg', alt: 'Ateliers numériques' },
							{ id: 2, src: '/assets/images/asbl5.jpeg', alt: 'Ateliers numériques' },
							{
								id: 3,
								src: '/assets/images/permanence_informatique_3.jpeg',
								alt: 'Ateliers numériques'
							}
						]
					},
					{
						id: 5,
						title: 'Permanence sociale',
						description:
							"Besoin d'aide pour le logement, une inscription scolaire, le CPAS ou une administration ? Un accueil confidentiel et respectueux.",
						images: [
							{ id: 1, src: '/assets/images/permanence_sociale_1.jpeg', alt: 'Permanence sociale' },
							{ id: 2, src: '/assets/images/permanence_sociale_2.jpeg', alt: 'Permanence sociale' },
							{ id: 3, src: '/assets/images/permanence_sociale_3.jpeg', alt: 'Permanence sociale' }
						]
					},
					{
						id: 6,
						title: 'Vivre ensemble',
						description:
							"Parce que l'intégration passe aussi par le plaisir et la rencontre : sorties culturelles, fêtes de quartier et ateliers de débat citoyen.",
						images: [
							{ id: 1, src: '/assets/images/asbl9.jpeg', alt: 'Vivre ensemble' },
							{ id: 2, src: '/assets/images/asbl1.jpeg', alt: 'Vivre ensemble' },
							{ id: 3, src: '/assets/images/asbl18.jpeg', alt: 'Vivre ensemble' }
						]
					}
				]
			}
		},
		{
			type: 'CTABlock',
			props: {
				title: 'Vous voulez nous rejoindre ?',
				description:
					'Que ce soit pour suivre une formation, donner un coup de main en tant que bénévole ou faire un stage — vous êtes les bienvenus.',
				ctaLabel: 'Nous contacter',
				ctaHref: '/info-pratique'
			}
		}
	];
</script>

<svelte:head>
	<title>Nos activités | Entraide Bruxelles</title>
	<meta name="description" content="Des formations et de l'aide, pensées pour vous." />
</svelte:head>

<Builder {blocks} />
