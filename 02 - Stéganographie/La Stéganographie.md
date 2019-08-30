[Slide 1]
La stéganographie
ou
l'art de dissimuler des données

Alors que la cryptographie repose sur le fait que le message ne soit pas compris, la stéganographie repose sur le fait que le message ne soit pas trouvé.
[Slide 2]
steganos (=couvert) et graphein (=écrire)

La stéganographie existe depuis longtemps
Une lettre attribuée à Georges Sand et envoyée à Alfred de Musset est un premier exemple de stéganographie
[voir: Lettre George Sand à Alfred de Musset - 19ème siècle]

Au 16ème siècle, un scientifique italien réussit à cacher un message dans un oeuf dur.
En écrivant sur la coquille avec un mélange d'alun et de vinaigre, la solution pénètre la coquille et dépose sur la surface du blanc d'oeuf le message qu'on saura facilement lire une fois l'oeuf épluché.
Un autre exemple est la lettre de démission de Daniel Kammen pour le président américain Donald Trump en août 2017 
[voir: Lettre démission to Trump]

[Slide 3]
Pour terminer les exemples, les espions allemands de la seconde guerre mondiale utilisaient aussi des micropoints pour transmettre discrètement leurs informations.
Le micropoint est une image de la taille d'un point de ponctuation qu'il suffit d'agrandir pour voir apparaitre clairement le message (comme pour un microfilm).

[Slide 4]
Méthode LSB (Least Significant Bit) [Le bit le moins significatif]
Les documents "porteurs" / "conteneurs" sont généralement à base d'images (BMP,GIF, videos, ..) ou de sons (WAV, ..)
Pour "cacher" un texte dans une image, il faut comprendre ce qu'est le bit de poids faible

Une image (bitmap != image vectorielle) est composée d'une combinaison de pixels.
Nous connaissons tous ce modèle additif (lumière) des couleurs primaires. Le RVB (ou RedGreenBlue).
Chaque pixel est enregistré comme une combinaison des 3 composants avec des valeurs de 0 à 100%
Pour coder ces valeurs, on utilise 8 bits (un octet) -> Un pixel est codé sur 24 bits, 0% =0 (8x0) / 100% = 255
Ce qui donne 256x256x256 = 16,777,216 possibilités de combinaisons de couleurs par pixel.

Prenez ces deux pixels colorés (et agrandis) rgb(40,150,255) et rgb(40,150,254)
Voyez-vous une différence?
[Slide 5]
Vos yeux non.
Et c'est ce qui sera utilisé pour masquer des informations dans une image.

[Slide 6]
En informatique le LSB dans un système octal (en 8 bits ou 1 byte/octet) est le bit le plus à droite de l'octet.
[Slide 7]
Exemple: On change la valeur du G = 10010111 en base 2(binaire) = 151 en base 10(décimal) 
La valeur de G a changé en 10010110 = 150


Le fonctionnement en pratique:
Nous avons une image de 1*10px , tous blanc {rgb(255,255,255)}
Pour y cacher les caractères "AB" ,nous allons utiliser la table de caractère ASCII qui est la plus commune pour coder les caractères:
"A" = 65 en décimal => 01000001 en binaire
"B" = 66 en décimal => 01000010 en binaire

Pour stocker l'image, il suffit d'enregistrer 01000001 01000010 dans les bits de poids faible des valeurs RGB

Les valeurs RGB vont varier de 255 à 254 ce qui fait que la différence est invisible à l'oeil.

Sur une image de 50*50px -> 2500 pixels, comme il y a 3 couleurs -> x3 = Stockés sur 7500bits => 7500/8= 937 octets. Et comme un caractère est codé sur un octet, celà donne 937 caractères possibles.
Mais ce n'est que la théorie.

Pour que vous puissiez mieux comprendre le fonctionnement de cette modification, je vais présenter les caractéristiques d'un programme: Steganosaurus

Le programme Steganosaurus utilise 16bits pour encoder chaque caractère (UTF-8) pour pouvoir utiliser l'accentuation ou les caractères spéciaux.
Il faut également ajouter un header et un footer au message pour donner certaines infos dont par exemple la fin de message.

Le "support" est important également. Il ne faut pas prendre un format qui serait compressé avec pertes (courte explication ... vraiment courte) comme le format jpeg.
Privilégier des formats comme PNG qui ne modifient pas les valeurs RGB lors de la compression.

PNG utilise des pixels codés sur 24bits (8 pour chaque couleur) et ajoute à celà une 4ème valeur, le Alpha Channel, codé en 8 bits également.
(PNG est capable de coder des images de 1 à 48bits, mais couramment c'est 24bits(+8bits =32bits))
L'Alpha Channel détermine l'opacité du pixel; pour simplifier, Steganosaurus n'utilise pas les LSB de l'Alpha Channel (problème de conversion de RGB)

Pour permettre la reconnaissance par le programme d'un fichier ayant un contenu caché, on ajoutera un header/entête, une signature ainsi qu'un footer/bas de page.

Décomposition:
[Slide 10]
Signature: (permet la détection d'un message caché dès la lecture du premier octet)
 �!#RSTG# qui, traduit en code ASCII donne 255 33 35 82 83 84 71 35
Header: (infos importantes concernant le message)
 █ █ █ # -> ? ? 0/128 35
Les deux premiers octets contiennent la longueur du message (0-65535) en termes de caractères (codés en 2 octets)
3ème octet est un octet de configuration. Déclare si le message est crypté ou non. Possibilités d'autres futurs réglages.
Message Data:
Le message crypté ou non.
Footer:
 #� -> 35 3
Juste là pour valider la structure du format.

En reprenant le message non crypté à cacher "AB" nous avons ces infos:
"A" 01000001
"B" 01000010
Message length: 2
Data to save: "01000001 01000010"

[Slide 11]
La structure complète du message avec signature, header et footer:

11111111 00100001 00100011 01010010 01010011 01010100 01000111 00100011 00000000 00000010 00000000 00100011 01000001 01000010 00100011 00000011

Le programme Stegosaurus propose également une encryption par message. Le mécanisme est assez simpliste (méthode XOR par la clé) et symétrique, donc pas du tout sécurisé.
Il est codé en Javascript.
[Présentation du programme Steganosaurus]

[Slide Sources]
