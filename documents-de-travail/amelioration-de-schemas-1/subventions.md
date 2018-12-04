---
description: >-
  Draft de la spécification du modèle de données relatif aux subventions
  attribuées par une collectivité
---

# Subventions

## Version 1.1.0 du 27/04/2018

{% hint style="info" %}
Lien permanent vers le [document actuellement publié](http://www.opendatafrance.net/SCDL_Subventions) sur GDrive
{% endhint %}

## Contexte

Dans le but de renforcer la transparence financière des aides octroyées par les personnes publiques, les collectivités locales, de plus de 3500 habitants et plus de 50 agents, qui attribuent des subventions dont le montant annuel est supérieur à 23 000€ ont l’obligation, à compter du 1er août 2017, de rendre accessibles, sous forme électronique, dans un standard ouvert aisément réutilisable et exploitable par un système de traitement automatisé, les données essentielles de leurs conventions de subvention. La nature et les modalités de diffusion de ces données essentielles ont été fixées par voie réglementaire.

De fait, la spécification SCDL du modèle de données relatif aux subventions attribuées par une collectivité locale a été élaborée à partir des sources suivantes :

* **Documents de cadrage juridique**

  * [Décret n° 2017-779 du 5 mai 2017 relatif à l'accès sous forme électronique aux données essentielles des conventions de subvention](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000034600552)
  * [Arrêté du 17 novembre 2017 relatif aux conditions de mises à disposition des données essentielles des conventions de subvention](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000036040528)

* **Document de cadrage technique**
  * [Format réglementaire pour la publication des données essentielles des conventions de subventions sur le dépôt Github de la mission Etalab](https://github.com/etalab/format-subventions)

Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir des mêmes sources.

#### `Avertissement !`

L'utilisation de cette spécification requiert de prêter une attention toute particulière aux points suivants :

* Dans l'attente d'une [éventuelle modification](https://github.com/etalab/format-subventions/issues/2) mais contrairement à ce qui est pour le moment prévu dans le format réglementaire, cette spécification énonce que le [séparateur de dates pour une période](subventions.md#datesperiodeversement) est une barre oblique et pas un tiret du bas afin de respecter la norme internationale ISO 8601.
* Pour s'y conformer, elle nécessite de créer une ligne par bénéficiaire et non une ligne par subvention. Dans le cas d'une subvention attribuée à plusieurs bénéficiaires, toutes les données de la subvention doivent être répétées à l'identique sur autant de lignes qu'il y a de bénéficiaires, à l'exception des champs suivants dont les valeurs varient : **nomBeneficiaire**, **idBeneficiaire**, et **pourcentageSubvention**. Dans certains cas, les champs **conditionsVersement** et **datesPeriodeVersement** peuvent également varier d'un bénéficiaire à un autre, pour une même subvention.

## Modèle de données

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`14 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `nomAttribuant`

* Titre : Nom de l'attribuant
* Description : Nom officiel de la collectivité attribuant la subvention limité à 140 caractères maximum.
* Type : chaîne de caractères
* Exemple : 'Région Bretagne'
* Valeur : **obligatoire**
* Taille : 140 maximum

#### `idAttribuant` <a id="idattribuant"></a>

* Titre : Identification de l'attribuant
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) de la collectivité attribuant la subvention, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : '23350001600040'
* Valeur : **obligatoire**
* Motif : `^\d{14}$`

#### `dateConvention` <a id="dateconvention"></a>

* Titre : Date de la convention de subvention
* Description : Date de la convention au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : '2017-06-27'
* Valeur : **obligatoire**

#### `referenceDecision` <a id="referencedecision"></a>

* Titre : Référence de la décision
* Description : Identifiant interne de l’acte matérialisant la décision d’attribution de la subvention. Sa composition dépend des pratiques propres à la collectivité.
* Type : chaîne de caractères
* Exemple : '2017-03-103'
* Valeur : **optionnelle**

#### `nomBeneficiaire` <a id="nombeneficiaire"></a>

* Titre : Nom du bénéficiaire
* Description : Nom officiel ou raison sociale du bénéficiaire de la subvention limité à 140 caractères maximum.
* Type : chaîne de caractères
* Exemple : 'Association Les Petits Débrouillards Bretagne'
* Valeur : **obligatoire**
* Taille : 140 maximum

#### `idBeneficiaire` <a id="idbeneficiaire"></a>

* Titre : Identification du bénéficiaire
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) du bénéficiaire de la subvention, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : '38047555800058'
* Valeur : **obligatoire**
* Motif : `^\d{14}$`

#### `objet` <a id="objet"></a>

* Titre : Objet de la subvention
* Description : Description de l'objet de la subvention attribuée limitée à 356 caractères maximum.
* Type : chaîne de caractères
* Exemple : 'Animations “Climat-énergie” dans les lycées de la région'
* Valeur : **obligatoire**
* Taille : 356 maximum

#### `montant` <a id="montant"></a>

* Titre : Montant total de la subvention
* Description : Montant total de la subvention attribuée, exprimé en euros et calculé avant répartition entre les bénéficiaires dans le cas de bénéficaires multiples. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '47800.20'
* Valeur : **obligatoire**

#### `nature` <a id="nature"></a>

* Titre : Nature de la subvention attribuée
* Description : Plusieurs choix possibles en combinant les valeurs 'aide en numéraire' et/ou 'aide en nature'. Les valeurs autorisées sont 'aide en numéraire', 'aide en nature', 'aide en numéraire;aide en nature', 'aide en nature;aide en numéraire'. Quand la nature de la subvention est à la fois en numéraire et en nature, le signe de séparation des valeurs est le point-virgule.
* Type : chaîne de caractères
* Exemple : 'aide en numéraire;aide en nature'
* Valeur : **obligatoire**
* Valeurs autorisées : 'aide en numéraire', 'aide en nature', 'aide en numéraire;aide en nature', 'aide en nature;aide en numéraire'

#### `conditionsVersement` <a id="conditionsversement"></a>

* Titre : Conditions de versement de la subvention attribuée
* Description : Choix unique parmi plusieurs valeurs possibles : 'unique', 'échelonné', ou 'autre'. La valeur 'autre' correspond à une description libre des modalités de versement de la subvention dans la limite de 356 caractères maximum.
* Type : chaîne de caractères
* Exemple : 'échelonné'
* Valeur : **obligatoire**
* Taille : 356 maximum

#### `datesPeriodeVersement` <a id="datesperiodeversement"></a>

* Titre : Date ou période de versement de la subvention
* Description : Si le versement est unique et que la date précise est connue, alors il s'agit d'une date au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601). Si le versement est échelonné \(ou que la date précise de versement unique est inconnue\), alors il s'agit d'une période exprimée au format AAAA-MM-JJ/AAAA-MM-JJ où le séparateur entre la première et la seconde date de l'intervalle est la barre oblique suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : chaîne de caractères
* Exemple : '2017-03-14' pour une date ou '2017-03-14/2018-03-14' pour une période
* Valeur : **obligatoire**
* Motif : `^[0-9]{4}\-[0-9]{2}\-[0-9]{2}(\/[0-9]{4}\-[0-9]{2}\-[0-9]{2})?$`

#### `idRAE` <a id="idrae"></a>

* Titre : Identifiant RAE de l’aide au titre de laquelle la subvention est attribuée
* Description :  Numéro unique de référencement dans le [Répertoire des Aides aux Entreprises](https://aides-entreprises.fr/). Ce champ ne concerne que les subventions attribuées au titre d’une aide référencée dans le RAE \([base de données gérée par l'Institut Supérieur des Métiers](https://data.aides-entreprises.fr/documentation)\).
* Type : chaîne de caractères
* Exemple : '12345'
* Valeur : **optionnelle**
* Taille : 5 maximum

#### `notificationUE` <a id="notificationue"></a>

* Titre : Aide d'Etat notifiée à la Commission Européenne
* Description : Subvention attribuée au titre d’une aide de minimis notifiée à la Commission Européenne en vertu des dispositions du [règlement n° 1407/2013](http://circulaire.legifrance.gouv.fr/pdf/2015/10/cir_40085.pdf) du 18 décembre 2013. Seules les valeurs 'oui' ou 'non' sont autorisées.
* Type : booléen
* Exemple : 'non'
* Valeur : **obligatoire**

#### `pourcentageSubvention` <a id="pourcentagesubvention"></a>

* Titre : Pourcentage du montant total de la subvention attribuée au bénéficiaire
* Description : Pourcentage exprimé sous la forme d'un nombre décimal. Dans le cas d’un bénéficiaire unique, le pourcentage est 100%, soit '1.00' en nombre décimal. Dans le cas de bénéficiaires multiples, le pourcentage du montant attribué au bénéficiaire correspond à la part qui lui est versée : par exemple 45%, soit '0.45' en nombre décimal. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '0.45'
* Valeur : **obligatoire**
* MinMax : 0.01 minimum et 1.00 maximum

## Voir aussi

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Exemple de fichier
* [Schéma de validation](https://git.opendatafrance.net/scdl/subventions/blob/master/schema.json)
* [Documentation générée à partir du schéma](https://scdl.opendatafrance.net/docs/schemas/scdl-subventions.html)

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=Subventions)
* participer au [fil de discussion dédié sur le forum de la mission Etalab](https://forum.etalab.gouv.fr/t/cadre-juridique-et-technique-de-louverture-des-donnees-de-subventions/4004)
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance](https://git.opendatafrance.net/scdl/subventions/issues) à propos de ce schéma
* ouvrir un ticket sur le [dépôt Github de la mission Etalab](https://github.com/etalab/format-subventions/issues/new) à propos du format réglementaire

