Le tunneling:


Un tunnel, en informatique, est une encapsulation de donn�es d'un protocole r�seau dans un autre.
Mais avant, il me faudra d�finir l'encapsulation et les couches OSI
// Sch�ma de l'encapsulation - page 2 //

L'encapsulation d�signe le principe de regrouper des donn�es brutes avec un ensemble de routines permettant de les lire ou de les manipuler. Ce principe est souvent accompagn� du masquage de ces donn�es brutes afin de s'assurer que l'utilisateur ne contourne pas l'interface qui lui est destin�e.

Les couches ou mod�le OSI (voir sch�ma)


Les tunnels peuvent �tre chiffr�s ou non.
Le tunnel HTTP est le cas particulier qui consiste � faire passer une connexion interdite par un pare-feu (SSH par exemple) dans un protocole HTTP presque toujours autoris�.

Il y a eu diff�rentes sortes de tunnel:
// Sch�ma Evolution des protocoles page 3 //

Couche 2 mod�le OSI (Trame - Couche de liaison)
PPTP (Point-to-Point Tunneling Protocol) -> Protocole transportant des trames PPP - D�velopp� par Microsoft, 3Com, Ascend, Us Robotics et ECI Telematics
L2F (Layer Two Forwarding) -> Pareil que PPTP mais d�velopp� par Cisco Systems, Nortel et Shiva.
L2TP (Layer Two Tunneling Protocol) -> Convergence des fonctionnalit�s de PPTP et L2F.

Couche 3 mod�le OSI (Paquet - Couche r�seau)
IPsec -> Transport de donn�es chiffr�es (prot�g�es) pour les r�seaux IP
L2TP/IPsec -> Association de deux protocoles pour faire passer du PPP sur L2TP


SSL/TLS S�curit� de la navigation web via HTTPS, permet �galement d'utiliser un navigateur internet comme client VPN / exemple: OpenVPN

// IPsec: Page 4 //
Transfert de donn�es par IPsec:
Protocole n�51 [ AH - Authentification Header ]: Fournit l'int�grit� et l'authentification. Signature unique des paquets
Protocole n�50 [ ESP - Encapsulating Security Payload ] Fournit la confidentialit� via cryptographie

2 modes de fonctionnement: Mode transport (Host to Host) et mode tunnel:

En mode tunnel, c'est la totalit� du paquet IP qui est chiffr� et/ou authentifi�. Le paquet est ensuite encapsul� dans un nouveau paquet IP avec un nouvel en-t�te IP. Ce mode supporte donc bien la travers�e de NAT avec le protocole ESP. Le mode tunnel est utilis� pour cr�er des r�seaux priv�s virtuels (VPN) permettant la communication de r�seau � r�seau (entre deux sites distants), d'h�te � r�seau (acc�s � distance d'un utilisateur) ou bien d'h�te � h�te (messagerie priv�e).

SSH - Intro:
Un protocole tr�s simple, tr�s basique, a �t� cr�� dans les ann�es 80 : Telnet.
Il sert juste � �changer des messages simples d'une machine � une autre.
Mais le probl�me de ce protocole? c'est justement qu'il est trop simple. Les donn�es sont transf�r�es en clair sur le r�seau. Il n'y a aucun chiffrement.
Comme on ne peut pas compl�tement emp�cher quelqu'un d'intercepter les donn�es qui transitent sur internet, il faut trouver un moyen pour que le client et le serveur communiquent de mani�re s�curis�e.
// SSH page 5 //
Le SSH: Vous l'avez d�ja vu m�me si vous en rappelez pas forc�ment! Lors de l'installation de Git et du lien avec Github :)
SSH encryption:
// SSH 2 page 6 //
Symetrique et asym�trique (cl�s publique/priv�e) + algorithmes d'encryption vari�s (AES, Blowfish, 3DES, IDEA)
D'abord le chiffrement asym�trique pour cr�er la liaison, le reste de la communication se fera en chiffrement sym�trique (plus l�ger � utiliser)

- Shell distant s�curis� (administration syst�me s�curis�) [c'est ce qu'on utilise pour se connecter au server � configurer]
- Forwarding de port / tunneling (passe outre le firewall pour acc�der un syst�me distant)
- X11 ou session VNC (connection � un bureau distant, de mani�re s�curis�)


// References page 7 //
Bibliographie:

Wikipedia:
https://fr.wikipedia.org/wiki/Mod%C3%A8le_OSI
https://fr.wikipedia.org/wiki/Transport_Layer_Security
https://fr.wikipedia.org/wiki/Tunnel_(r%C3%A9seau_informatique)

Securit� Info - Le Tunneling:
https://www.securiteinfo.com/cryptographie/tunnel.shtml

Guide de r�f�rence RedHat Entreprise Linux 4:
http://web.mit.edu/rhel-doc/4/RH-DOCS/rhel-rg-fr-4/ch-ssh.html

Openclassroom:
https://openclassrooms.com/en/courses/43538-reprenez-le-controle-a-laide-de-linux/41773-la-connexion-securisee-a-distance-avec-ssh

Sch�ma Evolution des protocoles: Avec Mermaid Live Editor
https://mermaidjs.github.io/mermaid-live-editor/
