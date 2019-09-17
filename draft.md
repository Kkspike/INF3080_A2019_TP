# Travail pratique 1

  L'objectif est de vous initier à la construction et l'exploitation de bases de données dans un SGBDR. 
  
### TP1
  Vous aurez à modéliser et scripter un schéma afin de créer une base de données.  Par la suite vous devrez créer et 
  exécuter des requêtes qui rempliront votre base de données.
  
### TP2
  Dans la deuxième portion du travail, vous aurez à programmer et implémenter des procédures et fonctions afin de réaliser des
  fonctionnalités requises par les utilisateurs.

# Description du travail

  Nous voulons dans ce travail, à l'aide d'un sujet d'actualité, construire, implémenter et optimiser une application dans le
  domaine du transport de marchandises.  Votre mandat construire un système de gestion de tarification dynamique.
  
## Description informative (qui n'est pas à faire dans ce travail)

  Le système (complet) est dit centralisé.  Ce qui veut dire que la base de données est centrale et accessible de partout.
  Évidemment, ceci est vrai seulement à l'aide d'une composante vitale, une application Web (qui n'est pas développée dans ce cours).
  
## Les acteurs

  Votre client est une compagnie de transport avec plusieurs camions.  Les clients de
  celle-ci sont principalement des manufacturiers qui ont besoin d'un transporteur pour livrer des marchandises.
  Le système est utilisable par des utilisateurs non informaticiens qui sont externes. Ils ne sont pas des employés.  
  Ils utiliseront une interface Web pour faire leurs demandes et recevoir les résultats.

## Détails pour la réalisation

- Les donneurs de voyage sont appelés manufacturiers;
- Le transporteur peut avoir plusieurs camions;
- Un camion implique deux parties, le tracteur et la remorque;
- Les camions appartiennent à une compagnie;
- Une compagnie fait toujours le même profit sur tous les voyages;
- Un camion est disponible lorsqu'il n'est pas en voyage;
- Drybox et flatbed sont des types de remorques;
- Les camions sont toujours situés à un endroit (latitude, longitude);
- Un trajet est constinué d'une origine vers une destination;
- Les propositions de tarification sont des estimations de prix à payer pour un trajet faites à une date;
- Les facteurs qui servent à calculer le prix à payer d'un transport sont:
  + le prix du carburant;
  + la distance du trajet;
  + la consommation de carburant du tracteur;
  + le poids du chargement;
  + l'espace occupé dans la remorque;
  + le type de remorque;
  + la marge de profit du transporteur;
  
#### Une remorque comporte les attributs suivants : 
 + capacité
 + longueur
 + largeur
 + hauteur
 
#### Synonymes
 + trajet  :arrow_right: route
 + remorque :arrow_right: equipement
 + voyage :arrow_right: chargement
 + manufacturier :arrow_right: client
 + proposition de tarification :arrow_right: soummission
 + transporteur :arrow_right: compagnie

#### Abréviations acceptées
| Mot | Abréviation | Colonne  |
| :----------- |:------------ | :------|
| Latitude     | Lat   | nLat  |
| Longitude    | Long  | nLong |
| Origine      | Ori   |       |
| Destination  | Des   |        |
| Latitude d'origine | LatOri | nLatOri |
| Longitude destination | LongDes | nLongDes |


#### Tables fournies
 + Position
   - La table contiendra les positions des équipements ainsi que la disponibilité
 
| Colonne | Grandeur | Description  |
| :----------- |:------------ | :------|
| pPosition    |     | pk|
| cPosition    | 30  | |
| nLat         | 8,5 | |
| nLong        | 8,5 | |
| bDisponible  |     | |
| pCamion      |     | fk |

+ Route
  - La table contient des routes et le nombre de km entre l'origine et la destination

| Colonne | Grandeur | Description  |
| :----------- |:------------ | :------|
| pRoute |    | pk|
| cRoute | 30 | |
| nLatOri   | 8,5 | Coordonnée latitude d'origine |
| nLongOri  | 8,5 | Coordonnée longitude d'origine |
| nLatDes   | 8,5 | Coordonnée latitude destination |
| nLongDes  | 8,5 | Coordonnée longitude destination |
| nDistance | | Distance en KM |

# Livrables

### algebre-tp1.pdf
 + Realiser en utilisant l'algèbre relationnel
   - a. 
   - b.

### 04a_query.sql
 + Écrire une requête qui retourne les soumissions génerés avec un filtre sur la clé primaire avec une valeur égal à 3

### 04b_query.sql
 + Écrire une requête qui liste les camions qui sont présentement en voyage
  
# README.md

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
   
   ## Auto-évaluation
~~~~

# Remise

  La totalité de votre travail doit être remis au plus tard le **22 octobre 2019** à **23h59**. 
  À partir de cette date/heure, une pénalité de **5 points par jour** de retard sera appliquée.

  La remise se fait **obligatoirement** par l'intermédiaire de l'une des plateformes de gestion de version suivantes :
  + `GitHub https://github.com/`___;
  + `GitLab https://gitlab.com/`___.
  
  **Aucune remise par courriel ne sera acceptée** (le travail sera considéré comme non remis).

Le nom de votre projet doit être `inf3080-a2019-tp1` (en minuscules). Vous devez donner un accès 
  en mode **lecture/écriture** (pas **admin**) à l'utilisateur `guyfrancoeur` (moi-même). Ceci me 
  permettra de déposer directement dans vos projets votre note pour le travail ainsi que mes commentaires si nécessaire.
  
  La branche `master` sera celle `clonée` et sera celle qui sera évaluée.

  Votre projet devrait minimalement contenir les fichiers suivants :

- Un fichier `cp.txt` contenant votre code permanent en majuscule et complet (requis pour la publication des résultats);
- Un fichier `modele.pdf` contenant votre diagramme, modèle Entité-Association Relationnel _ERM - Entity Relation Model_
- Un fichier `01_create.sql` contenant la création de votre schéma;
- Un fichier `02_load.sql` contenant les directives pour charger votre base de données;
- Un fichier `03_test.sql` contenant des vérifications que vous jugez appropriées;
- Un fichier `README.md` avec le titre du projet, les auteurs, les exemples, etc;
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
un logiciel qui soit à la hauteur de ce que vous voulez.  Soyez beau, soyez bon, soyez fier.

> > Les fichiers seront soumis au détecteur de plagiat. Faites attention à la provenance de vos idées.

# Barème de correction (à titre indicatif)

| Critère | Sous-critère | Points |
| ------- |:------------ | ------:|
| Modèle            | Modèle conceptuel                                | 1.0 |
| Algèbre           | Algèbre relationnel                              | 1.0 |
| Schéma            | Script de création du schéma                     | 5.0 |
| Chargement        | Script de chargement des tuples                  | 2.0 |
| Fonctionnalité    | Fonctionnalité, respect et complétude            | 5.0 |
| Git clone         | récupération (droit lecture, écriture)           | 1.0 |
| Markdown          | README.md                                        | 1.0 |
| **Total**         |                                                  | 16.0 / 15.0 |

----
##### Auteur Guy Francoeur
