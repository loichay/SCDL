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

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](broken-reference).&#x20;

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









&#x20;
