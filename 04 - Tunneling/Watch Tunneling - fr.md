Le tunneling:


Un tunnel, en informatique, est une encapsulation de données d'un protocole réseau dans un autre.
Mais avant, il me faudra définir l'encapsulation et les couches OSI
// Schéma de l'encapsulation - page 2 //

L'encapsulation désigne le principe de regrouper des données brutes avec un ensemble de routines permettant de les lire ou de les manipuler. Ce principe est souvent accompagné du masquage de ces données brutes afin de s'assurer que l'utilisateur ne contourne pas l'interface qui lui est destinée.

Les couches ou modèle OSI (voir schéma)


Les tunnels peuvent être chiffrés ou non.
Le tunnel HTTP est le cas particulier qui consiste à faire passer une connexion interdite par un pare-feu (SSH par exemple) dans un protocole HTTP presque toujours autorisé.

Il y a eu différentes sortes de tunnel:
// Schéma Evolution des protocoles page 3 //

Couche 2 modèle OSI (Trame - Couche de liaison)
PPTP (Point-to-Point Tunneling Protocol) -> Protocole transportant des trames PPP - Développé par Microsoft, 3Com, Ascend, Us Robotics et ECI Telematics
L2F (Layer Two Forwarding) -> Pareil que PPTP mais développé par Cisco Systems, Nortel et Shiva.
L2TP (Layer Two Tunneling Protocol) -> Convergence des fonctionnalités de PPTP et L2F.

Couche 3 modèle OSI (Paquet - Couche réseau)
IPsec -> Transport de données chiffrées (protégées) pour les réseaux IP
L2TP/IPsec -> Association de deux protocoles pour faire passer du PPP sur L2TP


SSL/TLS Sécurité de la navigation web via HTTPS, permet également d'utiliser un navigateur internet comme client VPN / exemple: OpenVPN

// IPsec: Page 4 //
Transfert de données par IPsec:
Protocole n°51 [ AH - Authentification Header ]: Fournit l'intégrité et l'authentification. Signature unique des paquets
Protocole n°50 [ ESP - Encapsulating Security Payload ] Fournit la confidentialité via cryptographie

2 modes de fonctionnement: Mode transport (Host to Host) et mode tunnel:

En mode tunnel, c'est la totalité du paquet IP qui est chiffré et/ou authentifié. Le paquet est ensuite encapsulé dans un nouveau paquet IP avec un nouvel en-tête IP. Ce mode supporte donc bien la traversée de NAT avec le protocole ESP. Le mode tunnel est utilisé pour créer des réseaux privés virtuels (VPN) permettant la communication de réseau à réseau (entre deux sites distants), d'hôte à réseau (accès à distance d'un utilisateur) ou bien d'hôte à hôte (messagerie privée).

SSH - Intro:
Un protocole très simple, très basique, a été créé dans les années 80 : Telnet.
Il sert juste à échanger des messages simples d'une machine à une autre.
Mais le problème de ce protocole? c'est justement qu'il est trop simple. Les données sont transférées en clair sur le réseau. Il n'y a aucun chiffrement.
Comme on ne peut pas complètement empêcher quelqu'un d'intercepter les données qui transitent sur internet, il faut trouver un moyen pour que le client et le serveur communiquent de manière sécurisée.
// SSH page 5 //
Le SSH: Vous l'avez déja vu même si vous en rappelez pas forcément! Lors de l'installation de Git et du lien avec Github :)
SSH encryption:
// SSH 2 page 6 //
Symetrique et asymétrique (clés publique/privée) + algorithmes d'encryption variés (AES, Blowfish, 3DES, IDEA)
D'abord le chiffrement asymétrique pour créer la liaison, le reste de la communication se fera en chiffrement symétrique (plus léger à utiliser)

- Shell distant sécurisé (administration système sécurisé) [c'est ce qu'on utilise pour se connecter au server à configurer]
- Forwarding de port / tunneling (passe outre le firewall pour accéder un système distant)
- X11 ou session VNC (connection à un bureau distant, de manière sécurisé)


// References page 7 //
Bibliographie:

Wikipedia:
https://fr.wikipedia.org/wiki/Mod%C3%A8le_OSI
https://fr.wikipedia.org/wiki/Transport_Layer_Security
https://fr.wikipedia.org/wiki/Tunnel_(r%C3%A9seau_informatique)

Securité Info - Le Tunneling:
https://www.securiteinfo.com/cryptographie/tunnel.shtml

Guide de référence RedHat Entreprise Linux 4:
http://web.mit.edu/rhel-doc/4/RH-DOCS/rhel-rg-fr-4/ch-ssh.html

Openclassroom:
https://openclassrooms.com/en/courses/43538-reprenez-le-controle-a-laide-de-linux/41773-la-connexion-securisee-a-distance-avec-ssh

Schéma Evolution des protocoles: Avec Mermaid Live Editor
https://mermaidjs.github.io/mermaid-live-editor/
