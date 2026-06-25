<script lang="ts">
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
							'Nos cours sont faits pour vous accueillir là où vous en êtes, sans jugement et à votre propre rythme..'
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
		}
	];
</script>
