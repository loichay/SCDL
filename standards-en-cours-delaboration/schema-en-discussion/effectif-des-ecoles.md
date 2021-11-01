# Effectif Scolaire

## Contexte <a href="contexte" id="contexte"></a>

Les effectifs des écoles sont des données souvent publiées par les communes et appréciées par les parents : suivi de l'évolution, choix d'un établissement ou d'un lieu de vie en fonction des établissements à proximité, etc.

De nombreuses collectivités publient ces données dans des formats trés différents, plus ou moins détaillés.

## Sources

Il semblerait que les données sont produites par les chefs d'établissement, transmises au ministère de l'éducation nationale. Elles peuvent, sous certaines conditions, être récupérées par la commune.

### Référentiel national&#x20;

A notre connaissance, les données des établissements (Base Centrale de Pilotage), sans distinction de classe ni de genre, est disponible sur le site :&#x20;

Premier degré : [https://data.education.gouv.fr/explore/dataset/fr-en-effectifs-premier-degre/table/?disjunctive.departement\&disjunctive.code\_departement\&disjunctive.code\_postal\&disjunctive.localite\_acheminement](https://data.education.gouv.fr/explore/dataset/fr-en-effectifs-premier-degre/table/?disjunctive.departement\&disjunctive.code\_departement\&disjunctive.code\_postal\&disjunctive.localite\_acheminement)

Les données essentielles sont : Année scolaire, académie (liste fermée), région (Libellé +Code), département (Libellé +Code), numéro de l’école, nom de l’école (établissement), type Etablissement Public/Privé), Nb d’élèves, Adresse de l’Etablissement + CP+Commune

Second degré : [https://data.education.gouv.fr/explore/dataset/fr-en-effectifs-second-degre/table/?disjunctive.libelle\_departement\&disjunctive.code\_departement\&disjunctive.code\_postal\&disjunctive.localite\_acheminement](https://data.education.gouv.fr/explore/dataset/fr-en-effectifs-second-degre/table/?disjunctive.libelle\_departement\&disjunctive.code\_departement\&disjunctive.code\_postal\&disjunctive.localite\_acheminement)

Les académies sont aussi capables de publier les données détaillées des effectifs scolaires. Cela nous semble une des meilleures sources pour présenter les données au niveau communal.&#x20;

Exemple de l'académie de Montpellier :&#x20;

{% embed url="https://www.ac-montpellier.fr/cid88644/premier-degre.html" %}



### Exemples de publication

De nombreuses villes publient les effectifs des écoles en open data.&#x20;

Exemple :&#x20;

* [https://www.data.gouv.fr/fr/datasets/effectif-des-ecoles-550874](https://www.data.gouv.fr/fr/datasets/effectif-des-ecoles-550874)
* [https://data.grandpoitiers.fr/explore/dataset/education-effectifs-des-ecoles-publiques-elementaires/table/](https://data.grandpoitiers.fr/explore/dataset/education-effectifs-des-ecoles-publiques-elementaires/table/)&#x20;
* [https://data.metropolegrenoble.fr/ckan/dataset/les-effectifs-scolaires-de-grenoble-de-2015-a-2016](https://data.metropolegrenoble.fr/ckan/dataset/les-effectifs-scolaires-de-grenoble-de-2015-a-2016)&#x20;
* [https://www.data.gouv.fr/fr/datasets/effectifs-par-ecole/](https://www.data.gouv.fr/fr/datasets/effectifs-par-ecole/)
* [https://data.stmalo-agglomeration.fr/explore/dataset/effectifs-scolaires/information/?disjunctive.annee\&disjunctive.nom\&sort=-annee](https://data.stmalo-agglomeration.fr/explore/dataset/effectifs-scolaires/information/?disjunctive.annee\&disjunctive.nom\&sort=-annee)

## Proposition de modèle de données <a href="modele-de-donnees" id="modele-de-donnees"></a>

### Introduction

Schéma permettant de décrire les effectifs scolaires des écoles primaires gérées ou soutenues par les collectivités locales, établissements publics et privés. Il permet de préciser le nombre d'enfant par dégré et par an. Pour décrire un établissement, il est possible d'utiliser une table indépendante pour éviter les répétions pour chaque année.

* Schéma créé le : 31/10/2021
* Site web : (git)
* Version : 0.2

(à terme, ce modèle de données fera partie et respectera les exigences du [Socle Commun des Données Locales](broken-reference))

### **Liste des propriétés**

| Propriété                                       | Type                 | Obligatoire |
| ----------------------------------------------- | -------------------- | ----------- |
| Numéro de l'établissement                       | Chaîne de caractères | Oui         |
| Nom de l'établissement                          | Chaîne de caractères | Oui         |
| Type de l'établissement                         | Liste (public/privé) | Oui         |
| Adresse de l'établissement (ad1&2, CP, Commune) | Chaîne de caractères | Oui         |
| Année                                           | Nombre entier        | Oui         |
| Effectif en Petite Section                      | Nombre entier        | Non         |
| Effectif en Moyenne Section                     | Nombre entier        | Non         |
| Effectif en Grande Section                      | Nombre entier        | Non         |
| Effectif  en UEMA                               | Nombre entier        | Non         |
| Effectif  en CP                                 | Nombre entier        | Non         |
| Effectif  en CE1                                | Nombre entier        | Non         |
| ​ Effectif en CE2                               | Nombre entier        | Non         |
| ​ Effectif en CM1                               | Nombre entier        | Non         |
| ​ Effectif en CM2                               | Nombre entier        | Non         |
| ​ Effectif en ULIS                              | Nombre entier        | Non         |

#### **Bloc général**

| effscolaireCollNom                                               |
| ---------------------------------------------------------------- |
| Objet : **Nom de la collectivité**                               |
| Description** : ** Nom de la collectivité qui publie les données |
| Exemple : Montpellier                                            |
| Valeur : Obligatoire                                             |
| Type : Chaîne de caractères                                      |
| Valeurs autorisées (si liste) :                                  |
| Motif :                                                          |
| Infos. complémentaires :                                         |

| effscolaireCollNom                                                                 |
| ---------------------------------------------------------------------------------- |
| Objet : **Code INSEE de la collectivité**                                          |
| Description** : ** Code INSEE (ou SIRET) de la collectivité qui publie les données |
| Exemple : 34 789                                                                   |
| Valeur : Obligatoire                                                               |
| Type : Chaîne de caractères                                                        |
| Valeurs autorisées (si liste) :                                                    |
| Motif :                                                                            |
| Infos. complémentaires : voir s'il est plus cohérent de mettre le SIRET            |

#### ****

#### **Bloc Etablissement**

| effscolaireEtablNum                                                                                                                     |
| --------------------------------------------------------------------------------------------------------------------------------------- |
| Objet : **Numéro de l'établissement**                                                                                                   |
| Description** : ** numéro de l'établissement attribué par le ministère ou l'académie. Il contient une chaine de 7 chifffre et 1 lettre  |
| Exemple : 1234567A                                                                                                                      |
| Valeur : Obligatoire                                                                                                                    |
| Type : Chaîne de caractères                                                                                                             |
| Valeurs autorisées (si liste) :                                                                                                         |
| Motif : NNNNNNNL                                                                                                                        |
| Infos. complémentaires :                                                                                                                |

| effscolaireEtablNom                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------- |
| Objet : **Nom de l'établissement**                                                                                          |
| Description** : ** nom de l'établissement                                                                                   |
| Exemple : Vila Clara ou Ecole Primaire Vila Clara                                                                           |
| Valeur : Obligatoire                                                                                                        |
| Type : Chaîne de caractères                                                                                                 |
| Valeurs autorisées (si liste) :                                                                                             |
| Motif :                                                                                                                     |
| Infos. complémentaires : le terme Ecole primaire est-il redondant ? ou bien un type d'école EM, EP, ..) est-il nécessaire ? |

| effscolaireEtablType                                      |
| --------------------------------------------------------- |
| Objet : **Type de l'établissement**                       |
| Description** : ** Caractère juridique de l'établissement |
| Exemple : Public                                          |
| Valeur : Obligatoire                                      |
| Type : Liste                                              |
| Valeurs autorisées (si liste) : Public, Privé             |
| Motif :                                                   |
| Infos. complémentaires :                                  |

####

| effscolaireEtablAdr1                                               |
| ------------------------------------------------------------------ |
| Objet : **Adresse de l'établissement (groupe adresse)**            |
| Description** : ** première partie de l'adresse de l'établissement |
| Exemple : Les Escanauds                                            |
| Valeur : Obligatoire                                               |
| Type : Chaîne de caractères                                        |
| Valeurs autorisées (si liste) :                                    |
| Motif :                                                            |
| Infos. complémentaires :                                           |

| effscolaireEtablAdr2                                               |
| ------------------------------------------------------------------ |
| Objet : **Adresse de l'établissement (groupe adresse)**            |
| Description** : ** deuxième partie de l'adresse de l'établissement |
| Exemple : 16 rue Beltcaguy                                         |
| Valeur : Facultatif                                                |
| Type : Chaîne de caractères                                        |
| Valeurs autorisées (si liste) :                                    |
| Motif :                                                            |
| Infos. complémentaires :                                           |

| effscolaireEtablCP                                          |
| ----------------------------------------------------------- |
| Objet : **Code poste de l'établissement  (groupe adresse)** |
| Description** : **Code Postal de l'établissement            |
| Exemple : 34 002                                            |
| Valeur : Obligatoire                                        |
| Type : Chaîne de caractères                                 |
| Valeurs autorisées (si liste) :                             |
| Motif :                                                     |
| Infos. complémentaires :                                    |

| effscolaireEtablCommune                                          |
| ---------------------------------------------------------------- |
| Objet : **Commune de l'établissement(groupe adresse)**           |
| Description** : **Nom de la commune où est situé l'établissement |
| Exemple : 34 002                                                 |
| Valeur : Obligatoire                                             |
| Type : Chaîne de caractères                                      |
| Valeurs autorisées (si liste) :                                  |
| Motif :                                                          |
| Infos. complémentaires :                                         |



#### Bloc Effectif

Le jeu de données peut être construit à partir de 2 tables : une qui détaille l'établissement et une une qui énumère les effectifs par année pour chaque établissement. La clé pour relier les deux tables est **effscolaireEtablNum**



| effscolaireAnnee                                                    |
| ------------------------------------------------------------------- |
| Objet : Année                                                       |
| Description** : Année considérée pour l'énumération des effectifs** |
| Exemple : 2010                                                      |
| Valeur : Obligatoire                                                |
| Type : Numérique entier                                             |
| Valeurs autorisées (si liste) :                                     |
| Motif :                                                             |
| Infos. complémentaires :                                            |

| effscolairePS                                                                        |
| ------------------------------------------------------------------------------------ |
| Objet : **Effectif scolaire en Petite Section**                                      |
| Description** : **Nombre d'enfant en classe de Petite Section pour l'année considéré |
| Exemple : 8                                                                          |
| Valeur : Facultatif                                                                  |
| Type : Numérique entier                                                              |
| Valeurs autorisées (si liste) :                                                      |
| Motif :                                                                              |
| Infos. complémentaires :                                                             |

| effscolaireMS                                                                          |
| -------------------------------------------------------------------------------------- |
| Objet : **Effectif scolaire en Moyenne Section**                                       |
| Description** : **Nombre d'enfant en classe de Moyenne Section pour l'année considérée |
| Exemple : 6                                                                            |
| Valeur : Facultatif                                                                    |
| Type : Numérique entier                                                                |
| Valeurs autorisées (si liste) :                                                        |
| Motif :                                                                                |
| Infos. complémentaires :                                                               |

| effscolaireGS                                                                         |
| ------------------------------------------------------------------------------------- |
| Objet : **Effectif scolaire en Grande Section**                                       |
| Description** : **Nombre d'enfant en classe de Grande Section pour l'année considérée |
| Exemple : 7                                                                           |
| Valeur : Facultatif                                                                   |
| Type : Numérique entier                                                               |
| Valeurs autorisées (si liste) :                                                       |
| Motif :                                                                               |
| Infos. complémentaires :                                                              |



| effscolaireUEMA                                                                |
| ------------------------------------------------------------------------------ |
| Objet : **Effectif scolaire en UEMA**                                          |
| Description** : **Nombre d'enfant en classe de Unité d'Enseignement MAternelle |
| Exemple : 4                                                                    |
| Valeur : Facultatif                                                            |
| Type : Numérique entier                                                        |
| Valeurs autorisées (si liste) :                                                |
| Motif :                                                                        |
| Infos. complémentaires :                                                       |



| effscolaireCP                                                     |
| ----------------------------------------------------------------- |
| Objet : **Effectif scolaire en CP**                               |
| Description** : **Nombre d'enfant en classe de Cours Préparatoire |
| Exemple : 4                                                       |
| Valeur : Facultatif                                               |
| Type : Numérique entier                                           |
| Valeurs autorisées (si liste) :                                   |
| Motif :                                                           |
| Infos. complémentaires :                                          |



| effscolaireCE1                                                     |
| ------------------------------------------------------------------ |
| Objet : **Effectif scolaire en CE1**                               |
| Description** : **Nombre d'enfant en classe de Cours Elémentaire 1 |
| Exemple : 4                                                        |
| Valeur : Facultatif                                                |
| Type : Numérique entier                                            |
| Valeurs autorisées (si liste) :                                    |
| Motif :                                                            |
| Infos. complémentaires :                                           |



| effscolaireCE1                                                     |
| ------------------------------------------------------------------ |
| Objet : **Effectif scolaire en CE2**                               |
| Description** : **Nombre d'enfant en classe de Cours Elémentaire 2 |
| Exemple : 4                                                        |
| Valeur : Facultatif                                                |
| Type : Numérique entier                                            |
| Valeurs autorisées (si liste) :                                    |
| Motif :                                                            |
| Infos. complémentaires :                                           |



| effscolaireCM1                                               |
| ------------------------------------------------------------ |
| Objet : **Effectif scolaire en CM1**                         |
| Description** : **Nombre d'enfant en classe de Cours Moyen 1 |
| Exemple : 4                                                  |
| Valeur : Facultatif                                          |
| Type : Numérique entier                                      |
| Valeurs autorisées (si liste) :                              |
| Motif :                                                      |
| Infos. complémentaires :                                     |



| effscolaireCM2                                               |
| ------------------------------------------------------------ |
| Objet : **Effectif scolaire en CM2**                         |
| Description** : **Nombre d'enfant en classe de Cours Moyen 2 |
| Exemple : 4                                                  |
| Valeur : Facultatif                                          |
| Type : Numérique entier                                      |
| Valeurs autorisées (si liste) :                              |
| Motif :                                                      |
| Infos. complémentaires :                                     |

## Eléments de travail (a supprimer à terme)&#x20;

#### Bloc Description de la commune

* effscolaireCollNom : MONTPELLIER
* effscolaireCollINSEE : 34 789

Ne seront pas indiquées dans ce jeu de données les données suivantes :&#x20;

* Académie (Libellé) : Montpellier
* Région (Code et Libellé) : 13, Occitanie
* Département (Code et Libellé) : 34, Hérault

#### Bloc Etablissement (ou Groupe Scolaire ?)

* effscolaireEtablNum : NNNNNNNL (ex : 1234567A)
* effscolaireEtablNom : Texte (ex : Ecole Primaire Villa Clara)
* effscolaireEtablType : Public, Privé (autre?)
* effscolaireEtablAdr1 & Adr2 (ex : Les Escanaux, 26 rue Bleacauy)
* effscolaireEtablCP (ex 34156)
* effscolaireEtablCommune (égale ou différente de la commune qui publie)

**Année scolaire**

* effscolaireAnnee (exemple  : 2019. On pourrait aussi dire 2019-2020 ?)

#### Bloc Effectifs

* effscolairetPS : Effectif relevé pour le niveau Petite Section. Facultatif, ex : 26
* effscolaireMS : Effectif relevé pour le niveau Moyenne Section. Facultatif.
* effscolaireGS : Effectif relevé pour le niveau Grande Section, Facultatif
* effscolaireUEMA : Effectif relevé pour l’UEMA (Unité d'Enseignement Maternelle)
* effscolaireCP : Effectif relevé pour le niveau CP, Facultatif
* effscolaireCE1 : Effectif relevé pour le niveau CE1, Facultatif
* effscolaireCE2 :  Effectif relevé pour le niveau CE2, Facultatif
* effscolaireCM1 : Effectif relevé pour le niveau CM1, Facultatif
* effscolaireCM2 : Effectif relevé pour le niveau CM2, Facultatif
* effscolaireULIS : Effectif relevé pour l’ULIS Numérique (Unités localisées l'inclusion scolaire), Facultatif

## Gabarit

{% embed url="https://docs.google.com/spreadsheets/d/1jdDSvVufF8Om5zrXz6nAyyswAtvsnhOHWLgzoeTiujU/edit?usp=sharing" %}

## Exemple d'utilisation&#x20;

#### Tableau de consultation

{% embed url="https://airtable.com/shrnw6AyWpbqaBevK" %}







&#x20;
