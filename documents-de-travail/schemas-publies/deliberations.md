---
description: >-
  Draft de la spécification du modèle de données relatif aux délibérations
  adoptées par une collectivité locale
---

# Délibérations

{% hint style="success" %}
[https://scdl.opendatafrance.net/docs/schemas/scdl-deliberations.html](https://scdl.opendatafrance.net/docs/schemas/scdl-deliberations.html)
{% endhint %}

## Version 2.1.2

* Auteur : OpenDataFrance
* Schéma créé le : 23/05/2018
* Schéma mis à jour le : 25/01/2019
* Site web : [https://git.opendatafrance.net/scdl/deliberations](https://git.opendatafrance.net/scdl/deliberations)
* [Gabarit au format Excel \(xlsx\)](https://scdl.opendatafrance.net/docs/templates/scdl-deliberations.xlsx)
* Valeurs manquantes : `""`

## Contexte

Au-delà des obligations légales de transmission au contrôle de légalité et de publicité des actes des autorités locales définies dans le Code Général des Collectivités Territoriales, la mise à disposition en open data des données relatives aux délibérations adoptées par une collectivité locale doit permettre d'améliorer la transparence des décisions publiques prises par les différentes instances habilitées quelque soit l'échelon territorial considéré.

Parmi les nombreux actes administratifs qui matérialisent les décisions des autorités locales \(arrêtés réglementaires, arrêtés individuels, contrats et conventions, documents budgétaires et financiers, ou autres\), les délibérations sont très souvent adoptées à l'issue d'un vote en assemblée. La répartition des suffrages permet de mesurer le niveau d'adhésion des représentants élus à la décision concernée.

Les processus de documentation, de transmission dématérialisée au contrôle de légalité et/ou de diffusion publique \(publication web des documents\) des délibérations peuvent être outillés par des logiciels de gestion informatisée. Toutes les collectivités ne sont cependant pas équipées de tels outils.

De fait, la spécification SCDL du modèle de données relatif aux délibérations adoptées par une collectivité locale a été élaborée en cherchant à garantir son accessibilité pour un usage par toutes les collectivités, mais aussi à préserver leur capacité à automatiser la production du jeu de données attendu.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`17 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `COLL_NOM` <a id="collnom"></a>

* Titre : Nom de la collectivité
* Description : Nom officiel de la collectivité délibérante.
* Type : chaîne de caractères
* Exemple : Ville de Poitiers
* Valeur : obligatoire

#### `COLL_SIRET` <a id="collsiret"></a>

* Titre : Code SIRET de la collectivité
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) de la collectivité qui a adopté la délibération, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : 21860194600013
* Valeur : obligatoire
* Motif : `^\d{14}$`

#### `DELIB_ID` <a id="delibid"></a>

* Titre : Identifiant de la délibération
* Description : Identifiant interne de délibération respectant le formalisme propre à la collectivité. Sa composition dépend des pratiques en vigueur au sein de chaque collectivité.
* Type : chaîne de caractères
* Exemple : 1DL15494
* Valeur : obligatoire

#### `DELIB_DATE` <a id="delibdate"></a>

* Titre : Date d'adoption de la délibération
* Description : Date de décision de l'acte, celle à laquelle la délibération a été adopté par la collectivité au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : 2017-10-15
* Valeur : obligatoire

#### `DELIB_MATIERE_CODE` <a id="delibmatierecode"></a>

* Titre : Code de matière issu de la nomenclature ACTES
* Description : Ce code correspond à celui de l'indexation de niveau 2 dans la structure arborescente de classement en matières et sous-matières \(5 niveaux de profondeur\) de la nomenclature ACTES \(Aide au Contrôle de légaliTé dématErialiSé\). Les codes de matière peuvent contenir les valeurs suivantes : '1.1' à '1.7', '2.1' à '2.3', '3.1' à '3.6', '4.1' à '4.5', '5.1' à '5.8', '6.1' à '6.5', '7.1' à '7.10', '8.1' à 8.9', '9.1' à '9.4'. Si le champ est renseigné, sa valeur doit correspondre au nom de matière de `DELIB_MATIERE_NOM`.
* Type : chaîne de caractères
* Exemple : 8.4
* Valeur : obligatoire
* Motif : `^\d\.\d{1,2}$`

#### `DELIB_MATIERE_NOM` <a id="delibmatierenom"></a>

* Titre : Nom de matière
* Description : Ce nom peut être issu de la nomenclature ACTES ou d'un référentiel propre à la collectivité. S'il est issu de la nomenclature ACTES, le champ `DELIB_MATIERE_CODE` doit être renseigné avec une valeur qui représente effectivement la matière définie. Le nom est alors composé de l'intitulé de matière de niveau 1 suivi de l'intitulé de sous-matière de niveau 2 présents dans la [structure arborescente de classement de la nomenclature ACTES](http://www.moselle.gouv.fr/content/download/1107/7994/file/nomenclature.pdf) \(Aide au Contrôle de légaliTé dématErialiSé\). Les deux intitulés sont exprimés en minuscules accentuées, sans virgule ni parenthèse, et séparés par une barre oblique. S'il est issu d'un référentiel de thèmes propre à la collectivité, le nom de matière est alors une chaîne de caractères libre et sans contrainte particulière.
* Type : chaîne de caractères
* Exemple : 'domaines de compétences par thèmes/aménagement du territoire' pour un nom de matière issu de ACTES ou 'URBANISME' pour un nom de matière issu d'un référentiel propre à la collectivité
* Valeur : obligatoire

#### `DELIB_OBJET` <a id="delibobjet"></a>

* Titre : Objet de la délibération
* Description : Description de l'objet de la délibération.
* Type : chaîne de caractères
* Exemple : Lancement d'une démarche partenariale de définition d'une politique montagne et adhésion à l'association nationale des élus de la montagne
* Valeur : obligatoire

#### `BUDGET_ANNEE` <a id="budgetannee"></a>

* Titre : Année du budget
* Description : Année de l'exercice budgétaire sur lequel s'applique la décision si celle-ci a un impact budgétaire. Format AAAA pour une année ou AAAA/AAAA pour un intervalle entre deux années suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : chaîne de caractères
* Exemple : '2017' pour une année ou '2017/2018' pour un intervalle
* Valeur : optionnelle
* Motif : `^[0-9]{4}(\/[0-9]{4})?$`

#### `BUDGET_NOM` <a id="budgetnom"></a>

* Titre : Nom du budget
* Description : Ce champ ne peut être renseigné que si la délibération engendre une affection budgétaire.
* Type : chaîne de caractères
* Exemple : Budget annexe déchets-collecte et traitement
* Valeur : optionnelle

#### `PREF_ID` <a id="prefid"></a>

* Titre : Identifiant de l'entité exerçant le contrôle de légalité
* Description : Cet identifiant dépend de l'entité concernée. Pour les préfectures, il est codé 'PREFNNN' sur 7 caractères. Pour les sous-préfectures, il est codé 'SPREFNNNM' sur 9 caractères. Pour les SGAR, il est codé 'SGARNNN' sur 7 caractères. 'NNN' correspond au numéro sur 3 caractères du département préfixé par '0' et inclant 'A' et 'B' pour les départements corses. 'M' correspond au numéro sur un chiffre de l'arrondissement.
* Type : chaîne de caractères
* Exemple : PREF038
* Valeur : optionnelle

#### `PREF_DATE` <a id="prefdate"></a>

* Titre : Date d'enregistrement de la délibération auprès du contrôle de légalité
* Description : Date d'enregistrement de la délibération au contrôle de légalité au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601). Ce champ ne peut être renseigné que si la délibération a effectivement été transmise et que sa date d'enregistrement est connue.
* Type : date
* Exemple : 2017-02-03
* Valeur : optionnelle

#### `VOTE_EFFECTIF` <a id="voteeffectif"></a>

* Titre : Effectif théorique des votants
* Description : Décompte de l'effectif total des représentants élus susceptibles de participer au vote.
* Type : nombre entier
* Exemple : 43
* Valeur : optionnelle

#### `VOTE_REEL` <a id="votereel"></a>

* Titre : Effectif réel des votants
* Description : Décompte de l’effectif total des élus ayant réellement participé au vote \(exclusion des absents\)
* Type : nombre entier
* Exemple : 40
* Valeur : optionnelle

#### `VOTE_POUR` <a id="votepour"></a>

* Titre : Pour
* Description : Décompte du nombre total de votes 'Pour'.
* Type : nombre entier
* Exemple : 25
* Valeur : optionnelle

#### `VOTE_CONTRE` <a id="votecontre"></a>

* Titre : Contre
* Description : Décompte du nombre total de votes 'Contre'.
* Type : nombre entier
* Exemple : 10
* Valeur : optionnelle

#### `VOTE_ABSTENTION` <a id="voteabstention"></a>

* Titre : Abstention
* Description : Décompte du nombre total d'abstentions.
* Type : nombre entier
* Exemple : 5
* Valeur : optionnelle

#### `DELIB_URL` <a id="deliburl"></a>

* Titre : Lien vers le document de la délibération
* Description : Si la collectivité dispose d'une version électronique de la délibération et la publie en ligne, ce lien correspond à l'adresse permettant de consulter ou de télécharger le document.
* Type : chaîne de caractères \(format `uri`\)
* Exemple : [https://data.maville.fr/deliberations/files/200417\_1.pdf](https://data.maville.fr/deliberations/files/200417_1.pdf)
* Valeur : optionnelle

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* [Fichier gabarit à télécharger au format xlsx](https://scdl.opendatafrance.net/docs/templates/scdl-deliberations.xlsx)
* [Schéma de validation](https://git.opendatafrance.net/scdl/deliberations/blob/master/schema.json)

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=D%C3%A9lib%C3%A9rations)
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance](https://git.opendatafrance.net/scdl/deliberations/issues/new)

