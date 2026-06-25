<script lang="ts">
	import { format } from 'path';
	import Builder from '$lib/components/builder.svelte';

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
				polygon: '/assets/svg/Polygon.svg',
				title: 'Une association de quartier à Laeken, active depuis 1985.'
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
		},
		{
			type: 'ActivitéBlock',
			props: {
				polygon: '/assets/svg/Polygon.svg',
				title: 'Des Formation et de L’aide, pensées pour vous.'
			}
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
							{
								id: 1,
								src: '/assets/images/asbl2.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 2,
								src: '/assets/images/asbl20.png',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 3,
								src: '/assets/images/asbl8.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							}
						]
					},
					{
						id: 2,
						title: 'Parcours d’accueil',
						description:
							'Accompagnement complet pour les nouveaux arrivants (COCOF). 16 à 20h par semaine dédiées au français, aux démarches et aux liens sociaux.',
						images: [
							{
								id: 1,
								src: '/assets/images/asbl12.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 2,
								src: '/assets/images/asbl10.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 3,
								src: '/assets/images/asbl19.png',
								alt: 'Cours de français à Entraide Bruxelles'
							}
						]
					},
					{
						id: 3,
						title: 'L’école des devoirs',
						description:
							'De la 1ère à la 6ème primaire. Un cadre calme pour la préparation du CEB et des activités culturelles épanouissantes.',
						images: [
							{
								id: 1,
								src: '/assets/images/asbl7.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 2,
								src: '/assets/images/asbl17.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 3,
								src: '/assets/images/asbl3.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							}
						]
					},
					{
						id: 4,
						title: 'Ateliers numériques',
						description:
							'Apprenez à maîtriser Internet et les outils essentiels : Itsme, Actiris, e-mails, Word et vos démarches en ligne en toute autonomie.',
						images: [
							{
								id: 1,
								src: '/assets/images/asbl6.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 2,
								src: '/assets/images/asbl5.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 3,
								src: '/assets/images/permanence_informatique_3.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							}
						]
					},
					{
						id: 5,
						title: 'Permance sociale',
						description:
							"Besoin d'aide pour le logement, une inscription scolaire, le CPAS ou une administration ? Un accueil confidentiel et respectueux.",
						images: [
							{
								id: 1,
								src: '/assets/images/permanence_sociale_1.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 2,
								src: '/assets/images/permanence_sociale_2.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 3,
								src: '/assets/images/permanence_sociale_3.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							}
						]
					},
					{
						id: 6,
						title: 'Vivre ensemble',
						description:
							"Parce que l'intégration passe aussi par le plaisir et la rencontre: sorties culturelles, fêtes de quartier et ateliers de débat citoyen.",
						images: [
							{
								id: 1,
								src: '/assets/images/asbl9.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 2,
								src: '/assets/images/asbl1.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							},
							{
								id: 3,
								src: '/assets/images/asbl18.jpeg',
								alt: 'Cours de français à Entraide Bruxelles'
							}
						]
					}
				]
			}
		},
		{
			type: 'FooterBlock',
			props: {
				logo: '/assets/svg/Logo_Entraide_horizontal.svg',
				title: 'Apprendre, s’intégrer<br>et bien vivre à Bruxelles',
				instagram: {
					icon: `<svg xmlns="http://www.w3.org/2000/svg" width="21" height="21" viewBox="0 0 21 21" fill="none">
  <path d="M11.4881 0C12.66 0.003125 13.2548 0.009375 13.7683 0.0239583L13.9704 0.03125C14.2037 0.0395833 14.4339 0.0499999 14.7121 0.0624999C15.8204 0.114583 16.5766 0.289583 17.2402 0.546875C17.9277 0.811458 18.5068 1.16979 19.086 1.74792C19.6159 2.26847 20.0258 2.89841 20.2871 3.59375C20.5443 4.25729 20.7193 5.01354 20.7714 6.12292C20.7839 6.4 20.7943 6.63021 20.8027 6.86458L20.8089 7.06667C20.8246 7.57917 20.8308 8.17396 20.8329 9.34583L20.8339 10.1229V11.4875C20.8365 12.2473 20.8285 13.0071 20.81 13.7667L20.8037 13.9687C20.7954 14.2031 20.785 14.4333 20.7725 14.7104C20.7204 15.8198 20.5433 16.575 20.2871 17.2396C20.0258 17.9349 19.6159 18.5649 19.086 19.0854C18.5655 19.6153 17.9355 20.0252 17.2402 20.2865C16.5766 20.5437 15.8204 20.7187 14.7121 20.7708L13.9704 20.8021L13.7683 20.8083C13.2548 20.8229 12.66 20.8302 11.4881 20.8323L10.711 20.8333H9.34747C8.58732 20.836 7.82718 20.828 7.06726 20.8094L6.86518 20.8031C6.6179 20.7938 6.37067 20.783 6.12351 20.7708C5.01518 20.7187 4.25893 20.5437 3.59434 20.2865C2.89937 20.0251 2.2698 19.6152 1.74955 19.0854C1.21929 18.565 0.809039 17.935 0.547468 17.2396C0.290176 16.576 0.115176 15.8198 0.0630924 14.7104L0.0318425 13.9687L0.0266343 13.7667C0.00743222 13.0071 -0.00124927 12.2473 0.000592497 11.4875V9.34583C-0.00229073 8.58604 0.00534897 7.82625 0.0235092 7.06667L0.0308009 6.86458C0.0391342 6.63021 0.0495508 6.4 0.0620508 6.12292C0.114134 5.01354 0.289134 4.25833 0.546426 3.59375C0.808607 2.89812 1.21958 2.26816 1.75059 1.74792C2.27054 1.21828 2.89975 0.80841 3.59434 0.546875C4.25893 0.289583 5.01413 0.114583 6.12351 0.0624999C6.40059 0.0499999 6.63184 0.0395833 6.86518 0.03125L7.06726 0.0249999C7.82684 0.0064924 8.58663 -0.00149448 9.34643 0.00104159L11.4881 0ZM10.4173 5.20833C9.03592 5.20833 7.71116 5.75707 6.73441 6.73382C5.75766 7.71057 5.20893 9.03533 5.20893 10.4167C5.20893 11.798 5.75766 13.1228 6.73441 14.0995C7.71116 15.0763 9.03592 15.625 10.4173 15.625C11.7986 15.625 13.1234 15.0763 14.1001 14.0995C15.0769 13.1228 15.6256 11.798 15.6256 10.4167C15.6256 9.03533 15.0769 7.71057 14.1001 6.73382C13.1234 5.75707 11.7986 5.20833 10.4173 5.20833ZM10.4173 7.29167C10.8276 7.2916 11.234 7.37236 11.6132 7.52934C11.9924 7.68633 12.3369 7.91646 12.6271 8.20659C12.9174 8.49672 13.1476 8.84118 13.3047 9.2203C13.4618 9.59942 13.5427 10.0058 13.5428 10.4161C13.5428 10.8265 13.4621 11.2329 13.3051 11.6121C13.1481 11.9912 12.918 12.3358 12.6279 12.626C12.3377 12.9162 11.9933 13.1465 11.6141 13.3036C11.235 13.4607 10.8287 13.5416 10.4183 13.5417C9.5895 13.5417 8.79464 13.2124 8.20859 12.6264C7.62254 12.0403 7.2933 11.2455 7.2933 10.4167C7.2933 9.58786 7.62254 8.79301 8.20859 8.20696C8.79464 7.62091 9.5895 7.29167 10.4183 7.29167M15.8871 3.64583C15.5417 3.64583 15.2105 3.78302 14.9663 4.0272C14.7222 4.27139 14.585 4.60258 14.585 4.94792C14.585 5.29325 14.7222 5.62444 14.9663 5.86863C15.2105 6.11282 15.5417 6.25 15.8871 6.25C16.2324 6.25 16.5636 6.11282 16.8078 5.86863C17.052 5.62444 17.1891 5.29325 17.1891 4.94792C17.1891 4.60258 17.052 4.27139 16.8078 4.0272C16.5636 3.78302 16.2324 3.64583 15.8871 3.64583Z" fill="currentColor"/>
</svg>`,
					href: '/'
				},
				facebook: {
					icon: `<svg xmlns="http://www.w3.org/2000/svg" width="21" height="21" viewBox="0 0 24 24"><!-- Icon from BoxIcons by Atisa - https://creativecommons.org/licenses/by/4.0/ --><path d="M13.397 20.997v-8.196h2.765l.411-3.209h-3.176V7.548c0-.926.258-1.56 1.587-1.56h1.684V3.127A22.336 22.336 0 0 0 14.201 3c-2.444 0-4.122 1.492-4.122 4.231v2.355H7.332v3.209h2.753v8.202h3.312z" fill="currentColor"/></svg>`,
					href: '/'
				},
				contact: {
					title: 'Contactez-nous',
					email: 'anasta5853@gmail.com',
					adresse: 'Rue Moorslede 54, 1020 Bruxelles - Laeken'
				},
				liens: {
					title: 'Liens',
					links: [
						{ label: 'Accueil', href: '/home' },
						{ label: 'Qui sommes-nous', href: '/qui-sommes-nous' },
						{ label: 'Nos activités', href: '/nos-activites' },
						{ label: 'Info-pratique', href: '/info-pratique' }
					],
					button: 'Réserver un lavage'
				},
				legal: [
					{ label: 'Mentions Légales', href: '/mentions-legales' },
					{ label: 'Politique de confidentialité', href: '/politique-de-confidentialite' },
					{ label: 'Cookies', href: '/cookies' }
				]
			}
		}
	];
</script>

<Builder {blocks} />
