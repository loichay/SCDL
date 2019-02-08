---
description: >-
  Draft de la spécification du modèle de données relatif aux infrastructures de
  recharge de véhicules électriques (IRVE) d'une collectivité
---

# Infrastructures de Recharge de Véhicules Electriques\*

{% hint style="success" %}
[https://scdl.opendatafrance.net/docs/schemas/scdl-irve.html](https://scdl.opendatafrance.net/docs/schemas/scdl-irve.html)
{% endhint %}

## Version Dev <a id="contexte"></a>

* Auteur : Alexandre Bulté pour Etalab
* Contributeurs : Charles Nepote, Pierre Dittgen
* Schéma créé le : 29/06/2018
* Schéma mis à jour le : 28/01/2019
* Site web : [https://github.com/OpenDataFrance/schema.data.gouv.fr/tree/master/irve](https://github.com/OpenDataFrance/schema.data.gouv.fr/tree/master/irve)
* [Gabarit au format Excel \(xlsx\)](https://scdl.opendatafrance.net/docs/templates/scdl-irve.xlsx)
* Valeurs manquantes : `""`
* Clé primaire : `id_pdc`

## Contexte <a id="contexte"></a>

Dans le but de constituer un répertoire national des Infrastructures de Recharge de Véhicules Electriques \(IRVE\), ouvert et accessible à tous, les collectivités locales porteuses d'un projet d'installation d'IRVE doivent, au fur et à mesure de la mise en service des stations, publier sur la plateforme data.gouv.fr les données statiques relatives à la localisation et aux caractéristiques techniques de ces installations selon les modalités définies dans [l'arrêté du 12 janvier 2017](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000033860733).

La spécification SCDL de ce modèle de données s'appuie donc sur les dispositions de cet arrêté et réutilise celle, déjà implémentée sous forme de schéma, disponible sur le [dépôt Github de la mission Etalab](https://github.com/etalab/schema.data.gouv.fr/tree/master/irve). Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

De fait, elle a été élaborée à partir des documents suivants :

* **Documents de cadrage juridique**
  * [Décret n° 2017-26 du 12 janvier 2017 relatif aux infrastructures de recharge pour véhicules électriques et portant diverses mesures de transposition de la directive 2014/94/UE du Parlement européen et du Conseil du 22 octobre 2014 sur le déploiement d’une infrastructure pour carburants alternatifs](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000033860620)
  * [Arrêté du 12 janvier 2017 relatif aux données concernant la localisation géographique et les caractéristiques techniques des stations et des points de recharge pour véhicules électriques](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000033860733)
  * [Arrêté du 12 janvier 2017 précisant les dispositions relatives aux identifiants des unités d’exploitation pour la recharge des véhicules électriques](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000033860743)
* **Documents de cadrage technique**
  * [Fichier de consolidation des stations de recharge de véhicules électriques sur data.gouv.fr](https://www.data.gouv.fr/fr/datasets/fichier-exemple-stations-de-recharge-de-vehicules-electriques/)
  * [Définition et structure des identifiants attribués par l'Association Française pour l'Itinérance de la Recharge Electrique des Véhicules \(AFIREV\)](http://www.afirev.fr/fr/informations-generales/)

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`17 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `n_amenageur` <a id="namenageur"></a>

* Description : Le nom de l'aménageur, c'est à dire de l'entité publique ou privée propriétaire des infrastructures.
* Type : chaîne de caractères
* Exemple : Société X, Entité Y
* Valeur : obligatoire

#### `n_operateur` <a id="noperateur"></a>

* Description : Le nom de l'opérateur qui opère le réseau d'infrastructure \(l'aménageur ou un tiers auquel a été confié la responsabilité par délégation\).
* Type : chaîne de caractères
* Exemple : Société X, Entité Y
* Valeur : obligatoire

#### `n_enseigne` <a id="nenseigne"></a>

* Description : Le nom commercial du réseau.
* Type : chaîne de caractères
* Exemple : Réseau de recharge ABC
* Valeur : obligatoire

#### `id_station` <a id="idstation"></a>

* Description : L'identifiant de la station délivré selon les modalités définies à l'article 10 du décret n° 2017-26 du 12 janvier 2017.
* Type : chaîne de caractères
* Exemple : FR_A68_P68021\*A
* Valeur : obligatoire

#### `n_station` <a id="nstation"></a>

* Description : le nom de la station.
* Type : chaîne de caractères
* Exemple : Picpus, Belleville, Villiers
* Valeur : obligatoire

#### `ad_station` <a id="adstation"></a>

* Description : L'adresse complète de la station : \[numéro\] \[rue\], \[code postal\] \[ville\].
* Type : chaîne de caractères
* Exemple : 1 avenue de la Paix, 75001 Paris
* Valeur : obligatoire

#### `code_insee` <a id="codeinsee"></a>

* Description : Le code INSEE de la commune d'implantation.
* Type : chaîne de caractères
* Exemple : 06088, 2B002 \(pour une commune corse\)
* Valeur : obligatoire
* Motif : `^([013-9]\d|2[AB1-9])\d{3}$`

#### `Xlongitude` <a id="xlongitude"></a>

* Description : La longitude en degrés décimaux \(point comme séparateur décimal\) de la localisation de la station exprimée dans le système de coordonnées WGS84.
* Type : nombre réel
* Exemple : 7.48710500
* Valeur : obligatoire

#### `Ylatitude` <a id="ylatitude"></a>

* Description : La latitude en degrés décimaux \(point comme séparateur décimal\) de la localisation de la station exprimée le système de coordonnées WGS84.
* Type : nombre réel
* Exemple : 47.63495500
* Valeur : obligatoire

#### `nbre_pdc` <a id="nbrepdc"></a>

* Description : Le nombre de points de recharge sur la station.
* Type : nombre entier
* Exemple : 1, 10
* Valeur : obligatoire

#### `id_pdc` <a id="idpdc"></a>

* Description : L'identifiant du point de recharge délivré selon les modalités définies à l'article 10 du décret n° 2017-26 du 12 janvier 2017.
* Type : chaîne de caractères
* Exemple : FR_A68_E68021_A_B1\*D
* Valeur : obligatoire

#### `puiss_max` <a id="puissmax"></a>

* Description : La puissance maximale délivrée à chaque point de recharge, exprimée en kW, en fonction du contrat d'abonnement de puissance de la station et du type de connecteur.
* Type : nombre réel
* Exemple : 22.00
* Valeur : obligatoire

#### `type_prise` <a id="typeprise"></a>

* Description : Les types de prises ou de connecteurs disponibles sur chaque point de charge.
* Type : chaîne de caractères
* Exemple : E/F, T2
* Valeur : obligatoire

#### `acces_recharge` <a id="accesrecharge"></a>

* Description : Modalités d'accès à la recharge.
* Type : chaîne de caractères
* Exemple : Payant, Gratuit, Sur abonnement
* Valeur : obligatoire

#### `accessibilité` <a id="accessibilit&#xE9;"></a>

* Description : Amplitude d'ouverture de la station.
* Type : chaîne de caractères
* Exemple : 24/24 7/7 jours
* Valeur : obligatoire

#### `observations` <a id="observations"></a>

* Description : Champ destiné à préciser les modalités d'accès à la recharge, l'accessibilité, le tarif, les horaires d'ouverture...
* Type : chaîne de caractères
* Exemple : Recharge uniquement disponible pendant les horaires d'ouverture du Centre Commercial XY
* Valeur : obligatoire

#### `date_maj` <a id="datemaj"></a>

* Description : Date de mise à jour des données.
* Type : date \(format `%Y/%m/%d`\)
* Exemple : 2018/08/08, 2015/12/30
* Valeur : obligatoire

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* [Fichier gabarit à télécharger au format xlsx](https://scdl.opendatafrance.net/docs/templates/scdl-irve.xlsx)
* [Schéma de validation](https://github.com/etalab/schema.data.gouv.fr/blob/master/irve/schema.json)

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=IRVE)
* ouvrir un ticket sur le [dépôt Github de la mission Etalab](https://github.com/etalab/schema.data.gouv.fr/issues/new)

