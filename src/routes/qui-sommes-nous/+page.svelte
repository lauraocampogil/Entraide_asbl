<script lang="ts">
	import Builder from '$lib/components/Builder.svelte';

	const blocks = [
		{
			type: 'AProposBlock',
			props: {}
		},
		{
			type: 'HistoireBlock',
			props: {
				title: 'Comment tout a commencé',
				text: "<p><strong>Entraide Bruxelles</strong>, active depuis 1982 à Laeken, est une association qui œuvre pour l'inclusion sociale et l'intégration des personnes les plus vulnérables, notamment les réfugiés, demandeurs d'asile et personnes issues de l'immigration. Elle propose un cadre d'accueil convivial favorisant l'apprentissage du français, l'autonomie et le vivre-ensemble dans un contexte interculturel.</p><p>En 2022, l'association a également accueilli des femmes et des jeunes ukrainiens touchés par la guerre en Ukraine. À travers ses activités et formations, elle encourage la mixité sociale, culturelle et de genre, tout en promouvant des valeurs d'inclusion, de respect et de tolérance.</p><p>Ses actions se concentrent principalement sur trois axes : <strong>l'intégration sociale et citoyenne, l'insertion socioprofessionnelle et l'accompagnement des enfants et des familles dans leur parcours scolaire</strong>.</p>"
			}
		},
		{
			type: 'ValeursBlock',
			props: {
				title: 'Ce qui nous guide',
				valeurs: [
					{ id: 1, svg: '/assets/svg/valeurs1.svg', item: 'Inclusion' },
					{ id: 2, svg: '/assets/svg/valeurs2.svg', item: 'Respect' },
					{ id: 3, svg: '/assets/svg/valeurs3.svg', item: 'Tolérance' },
					{ id: 4, svg: '/assets/svg/valeurs4.svg', item: 'Interculture' },
					{ id: 5, svg: '/assets/svg/valeurs5.svg', item: 'Mixité' },
					{ id: 6, svg: '/assets/svg/valeurs6.svg', item: 'Egalité' }
				]
			}
		},
		{
			type: 'PourquiBlock',
			props: {
				title: 'Pour qui ?',
				cards: [
					{
						id: 1,
						title: 'Pour les adultes',
						description:
							"Nous soutenons particulièrement les personnes issues de l'immigration et les chercheurs d'emploi à travers des formations linguistiques, civiques et un accompagnement vers l'autonomie."
					},
					{
						id: 2,
						title: 'Pour les enfants',
						description:
							"Pour les 6-12 ans du quartier de Laeken, nous proposons une école de devoirs et des activités créatives pour favoriser la réussite scolaire et l'épanouissement personnel."
					}
				]
			}
		},
		{
			type: 'EquipeBlock',
			props: {
				title: 'Notre belle famille',
				personnel: [
					{ id: 1, title: 'Anastasia Papadopoulos', description: 'Directrice' },
					{ id: 2, title: 'Fadi Zoghlami', description: 'Coordinatrice' }
				],
				formateurs: [
					{
						title: 'Formateurs',
						text1: 'Équipe pédagogique FLE',
						text2: 'Animateurs école de devoirs',
						text3: 'Formateurs en citoyenneté'
					}
				],
				benevoles: [
					{
						title: 'Bénévoles',
						description: 'Un réseau dynamique de citoyens engagés qui nous épaulent au quotidien.'
					}
				],
				stagiaires: [
					{
						title: 'Stagiaires',
						description: 'Nous accueillons chaque année des étudiants en assistant social.'
					}
				]
			}
		}
	];
</script>

<svelte:head>
	<title>Qui sommes-nous ? | Entraide Bruxelles</title>
	<meta name="description" content="Une association de quartier à Laeken, active depuis 1985." />
</svelte:head>

<Builder {blocks} />
