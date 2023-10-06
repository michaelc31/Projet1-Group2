# Projet1-Groupe-2 
# [Keepass](https://keepass.info/)
 
**L’outil Keepass est un gestionnaire de mots de passe qualifié par l’ANSSI (Agence nationale de la sécurité des systèmes d'information) utilisable à la fois dans le cadre professionnel et dans la sphère privée.**.

Il permet aux utilisateurs d’enregistrer dans un seul fichier entièrement protégé leurs différents mots de passe utilisés sur Internet.


## Besoins Initiaux

Demande initiale : créer une base de données (ou _Database_ ou **BDD**) sécurisée par "Clé" stockée sur un serveur et utilisable par un client.

Une BDD sécurisée par clé est une BDD à laquelle nous ajoutons, lors de sa création, un fichier clé contenant une clé de cryptage générée aléatoirement. Cela permet la liaison entre la BDD et le mot de passe maître (_Master Password_).


## Étapes d'installation et de configuration

Vous trouverez un fichier [Install.md](https://github.com/iliasssss/Projet-Groupe-2/blob/main/Install.md), qui vous servira d'instruction d'installation étape par étape.

Vous trouverez un fichier [USER_GUIDE.md](https://github.com/iliasssss/Projet-Groupe-2/blob/main/USER_GUIDE.md), pour vous aider à configurer le logiciel Keepass pas à pas.


##  Rôles par semaine

### Semaine 1 
| NOM | Roles | Description |
| :-- |:----- | :---------- |
| Ilias    | Scrum Master      | Garant de la progression et de l'application de la méthode scrum   |
|  Michael   | Product Owner   |  Garant de la qualité du produit final et représentant du client   |
|  Jérôme  |       | Tests et travail sur présentation  |

### Semaine 2 
| NOM | Roles | Description |
| :-- |:----- | :---------- |
|  Michael | Scrum Master     |  Garant de la progression et de l'application de la méthode scrum   |
|  Jérôme  |  Product Owner   |  Garant de la qualité du produit final et représentant du client    |


##  Choix Techniques

Pour notre projet Keepass, nous avons besoin d'un client et d'un serveur. Notre équipe a choisi de prendre un client **Windows 10** et un serveur **Windows server 2022**.
La version du logiciel Keepass2 est la **2.54** qui est à ce jour (05/10/2023) la dernière version de Keepass.

Pour pouvoir accéder à la BDD sur le client depuis le serveur, nous avons besoin que nos machines soient sur le même réseau, la BDD sera stockée sur un fichier partagé. 


##  Les difficultés rencontrées

Durant nos différents tests, nous avons été confronté aux incidents suivants: 

 -  Partage de dossiers/fichiers entre VM impossible : une fois les machines bien configurées au niveau réseau (adressage et parefeu), le partage de fichier n’était pas toujours disponible.  
 
 -  Droit d'accès de fichier impossible à la BDD sur le serveur : une fois la BDD sur le serveur, le client se connecte dessus après modification de la BDD mais il était impossible de la sauvegarder.

 -  Incident avec "AutoType" : selon les sites et leur mode d'authentification "l'AutoType" ne fonctionne pas systématiquement.


##  Les solutions 

Pour résoudre les différents incidents rencontrés nous avons effectué de nombreux tests pour parvenir aux solutions suivantes :
 
 -  Partage de dossiers/fichiers entre VM impossible : l'impossibilité de se connecter au dossier partagé venait d'un conflit de carte réseau sur les VM. Après différents tests il s'est avéré que les cartes réseaux devaient être configurées de la manière suivante pour le client: 1 première carte Nat avec connexion à internet et 1 seconde carte interne avec la configuration réseau paramétrer dessus et pour le serveur nous avons activé qu'une seule carte réseau interne (Intnet).
 
 -  Droit d'accès de fichier impossible à la BDD sur le serveur : après plusieurs vérifications des propriétés réseaux et de partage nous avions omis les droits pour l'utilisateur en mode écriture, ce qui empêchait la sauvegarde de la BDD.
 
 -  Il faut selon le site faire un réglage dans les commandes AutoType pour que celle-ci fonctionne et remplace la ligne {USERNAME}{TAB}{PASSWORD}{ENTER} par {USERNAME}{TAB}{TAB}{PASSWORD}{ENTER} ou {USERNAME}{ENTER}{DELAY=1000}{PASSWORD}{ENTER} 


##  Les tests réalisés

Durant les 2 dernières semaines nous avons réalisé les tests suivants:

-- Création de VM avec OS Windows10 et Windows22 server.

-- Mise en réseau des VM : configuration IP, vérification de communication avec la commande `Ping`.

-- Téléchargement du Logiciel Keepass2 et test en local : Création BDD classique, création d'entrée, test AutoType, Réglage AutoType.

-- Création et Test de BDD Finale du Projet : création d'une BDD sécurisée par Clé, création d'un utilisateur, création des diverses entrées de la BDD.

-- Mise en Réseau de la BDD : création du dossier partagé pour la liaison entre le client et le serveur.

-- Test de récupération de la BDD sur le serveur.

-- Utilisation de Keepass en condition réelle.

-- Test démonstration pour la présentation.

##  Futures améliorations

Durant nos 2 semaines de projet : nous avons réussi à créer la database sécurisée par clé stockée sur le serveur et utilisable par le client sur son PC, et nous avons pensé à améliorer le projet en ajoutant les Add-on suivants :

  -  KEEFORM : extension permettant la saisie automatique des données sans passer par l'interface Keepass rendant l'utilisation optimale selon le navigateur. (réglage a faire en fonction du navigateur internet).

  -  KEEPASS AUTO UNLOCK : Extension administrative permettant le dévérrouillage de la Database sans identification (identification verouillée sur un fichier permettant la liaison entre Keepass et la Database).

  - KPGoogleSync : Extension permettant la synchronisation avec Google Drive.

Ce qui permettrait à l'utilisateur une utilisation quotidienne plus simple de Keepass tout en gardant un maximun de Sécurité.

## Alternatives 

Quelques gestionnaires gratuits et open source de mots de passe :

[Bitwarden](https://bitwarden.com) : mots de passe stockés sur leurs serveurs, gratuit jusqu'à 1000 mots de passe.

[Buttercup](https://buttercup.pw/) :  bonne alternative et multiplateformes (IOS, Android, macos, Linux, Windows)

[Passky](https://passky.org/?utm_source=bdmtools&utm_medium=siteweb&utm_campaign=passky) :  moderne et gratuit multiplateformes entièrement gratuit
