<script lang="ts">
	import { format } from 'path';

	const blocks = [
		{
			type: 'HeaderBlock',
			props: {
				logo: '/assets/svg/Logo-Entraide.svg',
				menu: `<svg width="27" height="11" viewBox="0 0 27 11" fill="none" xmlns="http://www.w3.org/2000/svg">
<line x1="0.5" y1="0.5" x2="26.5" y2="0.5" stroke="black" stroke-linecap="round"/>
<line x1="0.5" y1="5.3" x2="26.5" y2="5.3" stroke="black" stroke-linecap="round"/>
<line x1="0.5" y1="10.1" x2="13.9" y2="10.1" stroke="black" stroke-linecap="round"/>
</svg>`,
				closeButton: '',
				navigation: {
					links: [
						{ label: 'Qui sommes-nous?', href: '/qui-sommes-nous' },
						{ label: 'Nos activités', href: '/nos-activites' },
						{ label: 'Info pratique', href: '/info-pratique' }
					]
				}
			}
		},
		{
			type: 'HeroBlock',
			props: {
				ctaLabel: 'Découvrir nos activités',
				ctaHref: '/nos-activites',
				stats: [
					{ value: '+550', label: 'Adultes formés en 2024' },
					{ value: '70', label: 'Enfants accompagnés' },
					{ value: '20+', label: 'Nationalités différentes' }
				],
				images: [
					{ src: '/assets/images/asbl6.jpeg', alt: 'Cours de français à Entraide Bruxelles' },
					{ src: '/assets/images/asbl7.jpeg', alt: 'Bibliothèque Entraide Bruxelles' }
				]
			}
		},
		{
			type: 'PartenairesBlock',
			props: {
				description:
					"Ce que nous faisons, nous ne pourrions pas le faire sans l'aide de nos partenaires.",
				images: [
					{
						id: 1,
						src: '/assets/images/part_logo1.png',
						alt: "La ville de Bruxelles, partenaire d'Entraide Bruxelles"
					},
					{
						id: 2,
						src: '/assets/images/part_logo2.jpg',
						alt: "Maison des enfants de l'horizon, partenaire d'Entraide Bruxelles"
					},
					{
						id: 3,
						src: '/assets/images/part_logo3.png',
						alt: "CPAS OCMW, partenaire d'Entraide Bruxelles"
					},
					{
						id: 4,
						src: '/assets/images/part_logo4.jpg',
						alt: "Article 27, partenaire d'Entraide Bruxelles"
					},
					{
						id: 5,
						src: '/assets/images/part_logo5.jpg',
						alt: "Bravvo, partenaire d'Entraide Bruxelles"
					},
					{
						id: 6,
						src: '/assets/images/part_logo6.png',
						alt: "Fondation Roi Baudoin, partenaire d'Entraide Bruxelles"
					},
					{
						id: 7,
						src: '/assets/images/part_logo7.jpg',
						alt: "One, partenaire d'Entraide Bruxelles"
					},
					{
						id: 8,
						src: '/assets/images/part_logo8.png',
						alt: "COCOF, partenaire d'Entraide Bruxelles"
					},
					{
						id: 9,
						src: '/assets/images/part_logo9.jpeg',
						alt: "APA, partenaire d'Entraide Bruxelles"
					},
					{
						id: 10,
						src: '/assets/images/part_logo10.jpeg',
						alt: "Convivial, partenaire d'Entraide Bruxelles"
					},
					{
						id: 11,
						src: '/assets/images/part_logo11.jpeg',
						alt: "VIA, partenaire d'Entraide Bruxelles"
					}
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
							'Un formulaire, une lettre, une inscription? On prend le temps de vous écouter et de vous aider'
					}
				]
			}
		},
		{
			type: 'CTABlock',
			props: {
				title: 'Vous voulez nous rejoindre?',
				description:
					'Que ce soit pour suivre une formation, donner un coup de main en tant que bénévole ou faire un stage, vous êtes les bienvenus. On sera heureux de vous accueillir. ',
				ctaLabel: 'Nous contactez',
				ctaHref: '/info-pratique'
			}
		},
		{
			type: 'AProposBlock',
			props: {
				title: 'Une association de quartier à Laeken, active depuis 1985.',
				polygon: '/assets/svg/Polygon.svg'
			}
		},
		{
			type: 'HistoireBlock',
			props: {
				title: 'Comment tout a commencé',
				text: '<strong>Entraide Bruxelles</strong>, active depuis 1982 à Laeken, est une association qui œuvre pour l’inclusion sociale et l’intégration des personnes les plus vulnérables, notamment les réfugiés, demandeurs d’asile et personnes issues de l’immigration. Elle propose un cadre d’accueil convivial favorisant l’apprentissage du français, l’autonomie et le vivre-ensemble dans un contexte interculturel En 2022, l’association a également accueilli des femmes et des jeunes ukrainiens touchés par la guerre en Ukraine. À travers ses activités et formations, elle encourage la mixité sociale, culturelle et de genre, tout en promouvant des valeurs d’inclusion, de respect et de tolérance. Ses actions se concentrent principalement sur trois axes : <strong>l’intégration sociale et citoyenne, l’insertion socioprofessionnelle et l’accompagnement des enfants et des familles dans leur parcours scolaire</strong>.'
			}
		},
		{
			type: 'ValeursBlock',
			props: {
				title: 'Ce qui nous guide',
				valeurs: [
					{
						id: 1,
						svg: '/assets/svg/valeurs1.svg',
						item: 'Inclusion'
					},
					{
						id: 2,
						svg: '/assets/svg/valeurs2.svg',
						item: 'Respect'
					},
					{
						id: 3,
						svg: '/assets/svg/valeurs3.svg',
						item: 'Tolérance'
					},
					{
						id: 4,
						svg: '/assets/svg/valeurs4.svg',
						item: 'Interculture'
					},
					{
						id: 5,
						svg: '/assets/svg/valeurs5.svg',
						item: 'Mixité'
					},
					{
						id: 6,
						svg: '/assets/svg/valeurs6.svg',
						item: 'Egalité'
					}
				]
			}
		},
		{
			type: 'PourquiBlock',
			props: {
				title: 'Pour qui?',
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
					{
						id: 1,
						title: 'Anastasia Papadopoulos',
						description: 'Directrice'
					},
					{
						id: 2,
						title: 'Fadi Zoghlami',
						description: 'Coordinatrice'
					}
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
						description:
							"Un réseau dynamique de citoyens engagés qui nous épaulent au quotidien pour le soutien scolaire et l'accueil."
					}
				],
				stagiaires: [
					{
						title: 'Stagiaires',
						description:
							'Nous accueillons chaque année des étudiants en assistant social et éducateur spécialisé pour leur première expérience.'
					}
				]
			}
		}
	];
</script>
