Key / Value = Redis
    Utilisation d'une hash table contenant une clé unique et un pointeur vers un élément particulier des datas.
    Récupération des données via le "get" "put" et "delete" => Hautes performances.
Utilisé par Pinterest: List des utilisateurs, followers, boards, etc ..

Wide Column = Cassandra & HBase     
Ressemble fortement à une BDR. La clé identifie la ligne consistant en multiples colonnes.
Les lignes ne doivent pas avoir le même nombre de colonnes, on peut ajouter une colonne à une ligne à n'importe quel moment sans avoir besoin de l'ajouter aux autres lignes.
Spotify utilise Cassandra pour les attributs des profils utilisateurs et les metadonnées.

Document = MongoDB & CouchDB
Documents en JSON, XML ou BSON (encodage binaire d'un JSON).
ça ressemble à un bd clé/valeur mais consiste en des données semi-structurées.
Un seul document sert à conserver les enregistrements et ses données. Il n'y a pas de relation ou de jointure.
Sega utilise MongDB pour gérer 11 millions de comptes en ligne.

Graph = Neo4J
Les noeuds et les relations constituent l'essentiel d'une base de donnée graph.
Un noeud représente une entité, la relation représente comment deux noeuds sont associés.
Les données doivent être enregistrées qu'une seule fois (le noeud) Les différents types de relations (les bords ou "edges") sont spécifiés aux données enregistrées.
Les relations entre les noeuds sont prédéterminés; non pas lors de la requête.
Les relations persistantes sont plus rapides mais c'est aussi plus difficile de changer une relation entre deux noeuds.
