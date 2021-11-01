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

Propriété **                 **Type                Obligatoire

| Propriété               | Descrription                                                                                                           | Type                 | Obligatoire |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------- | -------------------- | ----------- |
| effscolaireCollNom      | <p><em>Nom officiel de la collectivité accueillant les établissements scolaires.</em><br><em>Ex : Montpellier</em></p> | chaîne de caractères | Oui         |
| effscolaireCollINSEE    |                                                                                                                        | chaîne de caractères | Oui         |
| effscolaireEtablNum     |                                                                                                                        | chaîne de caractères | Oui         |
| effscolaireEtablNom     |                                                                                                                        | chaîne de caractères | Oui         |
| effscolaireEtablType    |                                                                                                                        | liste                | Oui         |
| effscolaireEtablAdr1    |                                                                                                                        | chaîne de caractères | Oui         |
| effscolaireEtablAdr2    |                                                                                                                        | chaîne de caractères | Non         |
| effscolaireEtablCP      |                                                                                                                        | chaîne de caractères | Oui         |
| effscolaireEtablCommune |                                                                                                                        | chaîne de caractères | Oui         |
| effscolaireAnnee        |                                                                                                                        | nombre réel          | Oui         |
| effscolairetPS          |                                                                                                                        | nombre réel          | Non         |
| effscolairetMS          |                                                                                                                        | nombre réel          | Non         |
| effscolairetGS          |                                                                                                                        | nombre réel          | Non         |
| effscolaireUEMA         |                                                                                                                        | nombre réel          | Non         |
| effscolaireCP           |                                                                                                                        | nombre réel          | Non         |
| effscolaireCE1          |                                                                                                                        | nombre réel          | Non         |
| effscolaireCE2          |                                                                                                                        | nombre réel          | Non         |
| effscolaireCM1          |                                                                                                                        | nombre réel          | Non         |
| effscolaireCM2          |                                                                                                                        | nombre réel          | Non         |
| effscolaireULIS         |                                                                                                                        | nombre réel          | Non         |



### Détail des propriétés

#### **effscolaireCollNom  : Nom de la collectivité qui produit les données**

> _Description : Nom officiel de la collectivité accueillant les établissements scolaires._\
> _Ex : Montpellier_

| effscolaireCollNom            | effscolaireCollNom                                                         |
| ----------------------------- | -------------------------------------------------------------------------- |
| _Description_                 | <h4><em>Nom de la collectivité qui produit les données</em></h4>           |
| Exemple                       | _Nom officiel de la collectivité accueillant les établissements scolaires_ |
| Valeur                        | _Montpellier_                                                              |
| Type                          |                                                                            |
| Valeurs autorisées (si liste) |                                                                            |
| Motif                         |                                                                            |
| Infos. complémentaires        |                                                                            |

#### ** **effscolaireCollINSEE (ou SIRET?) : **Code SIRET de la collectivité qui produit les données.**

> _Description : Identifiant du Système d'Identification du Répertoire des Etablissements (SIRET) de la collectivité. Ce code doit obligatoirement être composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant._\
> _Ex : _34 789

* Motif : `^\d{14}$`





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
* effscolaireULIS : Effectif relevé pour l’ULIS Numérique ((Unités localisées l'inclusion scolaire), Facultatif

### Gabarit

{% embed url="https://docs.google.com/spreadsheets/d/1jdDSvVufF8Om5zrXz6nAyyswAtvsnhOHWLgzoeTiujU/edit?usp=sharing" %}

### Utilisation&#x20;

#### Tableau de consultation

{% embed url="https://airtable.com/shrnw6AyWpbqaBevK" %}







&#x20;
