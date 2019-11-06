# Introduction du sujet pour INF3080 A2019 

### Description des travaux pratiques

  Nous voulons dans ce travail, à l'aide d'un sujet d'actualité, construire, implémenter et optimiser
  une application dans le domaine du transport de marchandises.  Votre mandat est de construire un
  système de gestion de tarification dynamique. Le sujet sera réalisé à l'aide de deux travaux pratiques (TP1 + TP2).

### Description informative (qui n'est pas à faire dans ce travail)

  Le système (complet) est dit centralisé.  Ce qui veut dire que la base de données est centrale et accessible de partout.
  Évidemment, ceci est vrai seulement à l'aide d'une composante vitale, une application Web (qui n'est pas développée dans ce cours).

#### Screen capture 
  - UI/UX demande de voyage : [ici](https://github.com/guyfrancoeur/INF3080_A2019_TP/raw/master/ecran1.png)
  - UI/UX résultat de soumission : [ici](https://github.com/guyfrancoeur/INF3080_A2019_TP/raw/master/ecran2.png)

### TP1 (ci-bas)

  Vous aurez à modéliser et scripter un schéma afin de créer une base de données.  Par la suite vous devrez créer et 
  exécuter des requêtes qui rempliront votre base de données.  Un `script` pour nous, est un fichier texte qui contient
  des instructions SQL qui seront exécutées séquentiellement.
  
### TP2 (un autre énoncé sera fourni)
  Dans la deuxième portion du travail, vous aurez à programmer et implémenter des procédures et fonctions afin de réaliser des
  fonctionnalités requises par les utilisateurs.

----

# Travail pratique 1 - Modélisation et Conception d'une BD

## Objectif

 L'objectif est de réaliser par la pratique la conception, la modélisation, la construction et l'exploitation de bases de données dans un SGBDR. 
 
 + Concevoir un modèle conceptuel;
 + Concevoir un modèle relationnel normalisé;
 + Concevoir un schéma sous forme de script SQL;
 + Concevoir et exécuter des requêtes afin de charger votre BD;
 + Concevoir et exécuter des requêtes afin de vérifier le contenu votre BD;
 + Devenir familier avec la construction d'une BD dans un SGBDR;

## Les acteurs

  Votre client est une compagnie de transport avec plusieurs camions.  Les clients de
  celle-ci sont principalement des manufacturiers qui ont besoin d'un transporteur pour 
  livrer des marchandises. Le système est utilisable par des utilisateurs non informaticiens
  qui sont externes. Ils ne sont pas des employés. Ils utiliseront une interface Web pour
  faire leurs demandes et recevoir les résultats.

## Lexique

#### Synonymes
 + trajet  :arrow_right: route
 + remorque :arrow_right: equipement
 + voyage :arrow_right: chargement
 + manufacturier :arrow_right: client
 + proposition de tarification :arrow_right: soumission
 + transporteur :arrow_right: compagnie
 + ...
 
 Les mots à droite du symbole :arrow_right: devraient être ceux utilisés dans votre modèle; 

## Détails pour la réalisation

- Les donneurs de voyage sont appelés manufacturiers;
- Le transporteur peut avoir plusieurs camions;
- Un camion implique deux parties, le tracteur et la remorque;
- Un tracteur est actif (1) ou inactif (0); 
- Les camions appartiennent à une compagnie;
- Une compagnie fait toujours le même profit (un pourcentage : 1.18) sur tous les voyages;
- Un camion est disponible lorsqu'il n'est pas en voyage;
- Drybox et flatbed sont des types de remorques;
- Il y a un coût différent par type d'équipements;
- Les camions sont toujours situés à un endroit (latitude, longitude);
- Un trajet est constitué d'une origine vers une destination;
- Les propositions de tarification sont des estimations de prix à payer pour un trajet;
- La proposition de tarification est créée à une date;
- Les facteurs qui servent à calculer le prix à payer d'un voyage sont:
  + le prix du carburant;
  + la distance du trajet;
  + la consommation de carburant du tracteur;
  + le poids du chargement;
  + l'espace occupé dans la remorque;
  + le type de remorque;
  + la marge de profit du transporteur;
- Le prix du carburant est au litre;
- La consommation du tracteur est en litre pour 1 Km;

## Guide pour la création des attributs

  - La notation hongroise est d'usage pour nommer vos attributs.

### Abréviations acceptées (à utiliser)
| Mot | Abréviation | Colonne  |
| :----------- |:------------ | :------|
| Latitude     | Lat   | nLat  |
| Longitude    | Long  | nLong |
| Origine      | Ori   |       |
| Destination  | Des   |        |
| Latitude d'origine | LatOri | nLatOri |
| Longitude destination | LongDes | nLongDes |

## Les entités


### Une remorque comporte les attributs suivants : 
 + capacité
 + longueur
 + largeur
 + hauteur

### Tables

Les tables listées
  - devront apparaître dans votre modèle conceptuel;
  - devront être créés par votre script `01_schema.sql` tel que fourni;

#### Position
 + Position
   - La table contiendra les positions des équipements ainsi que la disponibilité
 
| Colonne | Grandeur/Taille | Description  |
| :----------- |:------------ | :------|
| pPosition    |     | pk|
| cPosition    | 30  | |
| nLat         | 8,5 | |
| nLong        | 8,5 | |
| bDisponible  |     |  Le camion est disponible pour prendre des voyages |
| pCamion      |     | fk |

#### Route
 + Route
   - La table contient des routes et le nombre de km entre l'origine et la destination

| Colonne | Grandeur/Taille | Description  |
| :----------- |:------------ | :------|
| pRoute |    | pk|
| cRoute | 30 | |
| nLatOri   | 8,5 | Coordonnée latitude d'origine |
| nLongOri  | 8,5 | Coordonnée longitude d'origine |
| nLatDes   | 8,5 | Coordonnée latitude destination |
| nLongDes  | 8,5 | Coordonnée longitude destination |
| nDistance | | Distance en KM |

#### TypeEquipement
 + TypeEquipement
   - La table contiendra les types d'équipements
 
| Colonne | Grandeur/Taille | Description  |
| :----------- |:------------ | :------|
| pTypeEquipement    |     | pk|
| cTypeEquipement    | 30  | |
| nCout    | 8,2  | Coût par KM |

# Livrables

### 00_modele.pdf
  Vous devez modéliser le sujet conceptuellement et produire le fichier `00_modele.pdf`;

### 01_schema.sql
  Votre schéma doit être dans un fichier de type texte (souvent appelé *script*) 
  nommé `01_schema.sql` et devra contenir des commandes qui créera votre base de données alias
  schéma. Toutes les commandes utilisées sont celles du DDL.  Le fichier sera exécuté 2 fois.
  Assurez-vous qu'il n'y a pas d'erreur.
  
### 02_charger.sql
  Vous devez ensuite créer un deuxième *script* nommé `02_charger.sql` qui remplira votre BD.
  Ce dernier doit contenir des commandes INSERT principalement. Le DML est d'usage pour
  compléter ce fichier.
  ~~Certaines données peuvent être importées depuis un fichier CSV ou TSV.~~

### 03_tester.sql
  Vous devez dans un fichier nommé `03_tester.sql` écrire des requêtes qui vous aident 
  à réaliser un travail de qualité.  Il est toujours important de faire des tests. Puisque
  nous ne voulons pas perdre nos tests, je vous invite à les sauvegarder dans `03_tester.sql`.
  Ce fichier n'est pas facultatif.  Mais son contenu est de votre création.  Auncune directive
  ne vous sera imposée pour sa réalisation.

### 04a_query.sql
 + Écrire une requête qui retourne les soumissions générées
   - seulement les datées du 2019-09-30; 
   - pour le pClient { 4 };

### 04b_query.sql
 + Écrire une requête qui liste les camions qui sont présentement en voyage;

### 04c_query.sql
 + Écrire une requête qui retourne le nom des tables en minuscule de mon schéma en ordre décroissant;
 
### 04d_query.sql
 + Écrire une requête qui retourne les attributs des entités E = { Tracteur, Camion, Equipement };
 + Exemple de retour (projection en Algèbre relationnelle :wink: ) :

| Entité | Attribut | Type  |
| :----------- |:------------ | :------|
| TRACTEUR    | pTracteur    | NUMERIC   |
| ...  |   |   |

### 05_algebre-tp1.pdf
 + Réaliser, écrire en utilisant l'algèbre relationnelle :
   - a. la requête `04a_query.sql`;
   - b. la requête `04b_query.sql`;

### README.md

  Le fichier nommé `README.md` qui décrit le contenu et qui **respecte le format Markdown**.
  Il doit minimalement contenir les informations ci-bas :

~~~~
   # Travail pratique 1

   ## Description

   <description du projet en quelques phrases>
   <mentionner le contexte (cours, sigle, université, etc.)>

   ## Auteur

   <prénom et nom> (<code permanent>)

   ## Fonctionnement

   <expliquez brièvement comment faire fonctionner votre projet, en inscrivant
   au moins deux exemples d'utilisation (commande lancée et résultat affiché)>

   ## Contenu du projet

   <décrivez brièvement chacun des fichiers contenus dans le projet (une phrase
   par fichier)>

   ## Références

   <citez vos sources ici>

   ## Statut

   <indiquez si le projet est complété ou s'il y a des bogues>
   
   ## Auto-évaluation de votre travail
   
   <j'évalue mon livrable à x points>
~~~~

# Remise

  La totalité de votre travail doit être remis au plus tard le **22 octobre 2019** à **23h59**. 
  À partir de cette date/heure, une pénalité de **5 points par jour** de retard sera appliquée.

  La remise se fait **obligatoirement** par l'intermédiaire de l'une des plateformes de gestion de version suivantes :
  + `GitHub https://github.com/`___;
  + `GitLab https://gitlab.com/`___.
  
  **Aucune remise par courriel ne sera acceptée** (le travail sera considéré comme non remis).

Le nom de votre projet doit être `inf3080-a2019-tp1` (en minuscules). Vous devez donner un accès 
  en mode **lecture/écriture** (pas **admin**) à l'utilisateur 
  + `guyfrancoeur` pour les gens de INF3080-030 A2019;
  + `ammarhamad` pour les gens de INF3080-031 A2019; GitHub seulement;
  
  Il sera ainsi possible pour le/les enseignants de commenter et noter votre travail de façon discrète.

  La branche `master` sera celle `clonée` et sera celle qui sera évaluée.

  En plus de la section `Livrable`, votre projet devrait idéalement contenir les fichiers suivants :
  - Un fichier `cp.txt` contenant votre code permanent en majuscule et complet (requis pour la publication des résultats);
  - Un fichier ``.gitignore``. Ça aide beaucoup;
  - Aucune structure de répertoire nécessaire.

# Correction et évaluation

Les travaux seront corrigés sur le serveur __*Zeta2*__. Vous devez donc vous assurer que votre livrable
fonctionne **sans modification** sur celui-ci.
  
Votre travail sera évalué de façon automatisée.  Ce qui implique que vos dépôts seront clonés
et un pull sera effectué de façon automatique. Un `pull` par jour pendant 5 jours.
Il n'y aura pas d'humain pour faire fonctionner le programme. 
Votre travail sera soumis à plusieurs cas et les résultats seront évalués par un script `bash`.
Assurez-vous de bien lire toutes les directives et les requis.

La réflexion est un élément essentiel qu'il faut pratiquer. Vous devez donc réfléchir et réaliser
un travail qui soit à la hauteur de ce que vous désirez.  Soyez beau, soyez bon, soyez fier.

> > Les fichiers seront soumis au détecteur de plagiat. Faites attention à la provenance de vos idées.

# Barème de correction (à titre indicatif)

| Critère | Sous-critère | Points |
| ------- |:------------ | ------:|
| Modèle            | Modèle conceptuel                                | 1.0 |
| Algèbre           | Algèbre relationnel                              | 1.0 |
| Schéma            | Script de création du schéma                     | 5.0 |
| Chargement        | Script de chargement des tables                  | 2.0 |
| Fonctionnalité    | Fonctionnalité, respect et complétude            | 5.0 |
| Git clone         | récupération (droit lecture, écriture)           | 1.0 |
| Markdown          | README.md                                        | 1.0 |
| **Total**         |                                                  | 16.0 / 15.0 |

La note maximale possible dans résultat est 15 points. 

----
##### Auteur :copyright: 2019 Guy Francoeur
