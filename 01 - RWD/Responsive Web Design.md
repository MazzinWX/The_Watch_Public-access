
[Slide 1] Aujourd'hui je vais vous parler du RWD ou Responsive Web Design
-> [Slide 2]
C'est un terme utilisé la première fois par Ethan Marcotte dans un article (A List Apart) publié en mai 2010.
Il décrira ensuite la théorie et la pratique dans son ouvrage Responsive Web Design publié en 2011.
C'est une approche de conception Web visant à offrir une expérience de navigation optimale pour l'utilisateur, quelle que soit sa gamme d'appareil!
=> redimensionnement, recadrage et défilement multidirectionnel des pages.

-> [Slide 3]

3 moyens pour diffuser.
Site dédié	Application native	version responsive


Site dédié: Un test (appli) est utilisé pour détecter le matériel de l'utilisateur et renvoie vers le site dédié.

Avantages:
	Affiner la structure du site
	Cibler et s'adapter à des fonctionnalités (Touch par exemple)
	Alternative "rapide" en attendant une autre solution, un mieux, une refonte.

Inconvénients:
	Duplication du contenu
	Maintenance lourde. -> Plusieurs versions du site => indexation limitée dans les moteurs de recherche
	Détection automatique de l'appareil pas toujours fiable (Résultats de l'UA Sniffing approximatifs)


Application native: Développé spécifiquement pour certaines plateformes (iOS / Android / etc..) et se référence auprès d'un "Store" (AppStore, etc  ..)

Avantages:
	Fonctions natives prises en charge plus facilement (Touch, GPS, etc ..)
	Installation sur le périphérique -> ergonomie, performance, etc ..

Inconvénients:
	Dev spécifique pour chaque plateforme
	Coût de dev, des licences et maintenance
	Pas indexé par un moteur de recherche classique
	MàJ liée à l'action de l'utilisateur


Version responsive: sensé s'adapter à tout type d'appareil de manière transparente pour l'utilisateur

Avantages:
	Coûts et délais inférieurs aux autres techniques
	Maintenance facilitée (1 feuille de style, 1 fichier HTML, etc ..)
	MàJ transparente et déploiement multi-plateformes
	Peut être concue après la conception initiale
	++: Google mets en avant les résultats de recherche "adapté aux mobiles"

Inconvénients:
	Bonne connaissances techniques nécessaires, veille technologique.
	Limites ergonomiques et de performances difficiles à contourner.
	Prévoir de nombreux tests (device labs, etc) => ça prends du temps (25% de supplément environ)

-> [Slide 4]
// Montrer les sites :D

-> [Slide 5]
// Expliquer le tableau

-> [Slide 6]

Distinguer 4 sortes de sites:

Static: tailles figées (en pixel), surtout avant 2010
Fluide (Liquid): Largeurs et hauteurs s'adaptent automatiquement à la taille de fenêtre (%, vh [viewport height], vw)
Adaptive: Amélioration du Static -> Largeurs fixes mais différentes en fonction de la taille de l'écran, détecté via CSS3 Media Queries.
Utilisation des "points de rupture" [Breakpoints]
Responsive: Amélioration du Liquid avec du "Media Queries"

-> [Slide 7]
Qu'est-ce que ça implique?

3 définitions:

->[Slide 8]
Media Queries: permet d'adapter le contenu (image, media, etc ..) pour qu'il ne déborde pasde leur parent quand celui-ci est restreint. ->[Slide 8]

->[Slide 9]
Fluid Grid: les largeurs des éléments de structure sont débarassés des unités de pixels. Adaptation au Viewport du terminal.

->[Slide 10]
Flexible Visuals: Philosophie "Mobile First" et "Enrichissement progressif" facilitant l'accessibilité, la compatibilité et la performance des pages produites.

Certaines solution combinent:
- Eventuellement des adaptations conditionnelles (menu Nav) côté client; basées sur JS ou jQuery
- Des parties détectées et générées côté serveur (RESS) pour accélérer l'affichage de certains composants ou ressources.

->[Slide 11]
Marcotte a dit, c'est juste le commencement!

“Des grilles fluides, des images flexibles et les media queries sont les 3 ingrédients techniques pour le Responsive Web Design, mais il faut également penser autrement. Plutôt que de se cantonner à un contenu disparate, expérience spécifiquement limitée à une sorte de matériel, nous pouvons utiliser ces outils pour progressivement améliorer notre travail dans ces différents contextes de lecture (viewing)"

->[Slide 12]
