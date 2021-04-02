---
description: >-
  Draft de la spécification du modèle de données relatif aux prénoms des
  nouveaux-nés déclarés à l’état-civil
---

# Prénoms des nouveaux-nés

{% hint style="success" %}
[https://scdl.opendatafrance.net/docs/schemas/scdl-prenoms.html](https://scdl.opendatafrance.net/docs/schemas/prenoms.html)
{% endhint %}

## Version 1.1.3

* Auteur : Charles Nepote [charles.nepote@fing.org](mailto:charles.nepote@fing.org)
* Contributeurs : Simon Chignard, Bernadette Kessler, Christian Quest, Christophe Benz, Pierre Dittgen
* Schéma créé le : 12/04/2018
* Schéma mis à jour le : 23/01/2019
* Site web : [https://github.com/OpenDataFrance/liste-prenoms-nouveaux-nes/](https://github.com/OpenDataFrance/liste-prenoms-nouveaux-nes/)
* [Gabarit au format Excel \(xlsx\)](https://scdl.opendatafrance.net/docs/templates/scdl-prenoms.xlsx)
* Valeurs manquantes : `""`

## Contexte  <a id="contexte"></a>

Le modèle de données relatif aux prénoms des nouveaux-nés déclarés à l’état-civil spécifie la structure et le contenu d'un jeu de données simple et très apprécié du public. Il consiste en une liste de prénoms déclarés à l'état-civil de la commune de naissance, avec l'occurrence de chacun pour une année donnée. Les prénoms listés correspondent au premier prénom donné dans chaque acte de naissance.

Il a été élaboré par [Charles Népote](mailto:charles.nepote@fing.org) à partir du recueil et de l'observation des fichiers produits en open data par plusieurs communes françaises, publiés dès 2012. Il s'est nourri de l'observation des usages et a puisé également dans les textes de lois ou textes de référence qui standardisent la forme des prénoms en français.

La source de cette spécification est disponible sur le [dépôt Github de Charles Nepote](https://github.com/CharlesNepote/liste-prenoms-nouveaux-nes). Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

## Modèle de données  <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](). Il repose sur les **`6 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `COMMUNE_NOM` <a id="communenom"></a>

* Titre : Nom de la commune d'enregistrement à l'état-civil
* Description : Nom de la commune où les prénoms sont enregistrés à l'état-civil, c'est-à-dire le lieu de naissance. Le lieu de naissance peut être différent du lieu de résidence des parents, comme cela peut être le cas pour les enfants nés dans une maternité. Le renseignement de ce champ est facultatif. Il permet cependant de faciliter l'usage des données, notamment par le grand public.
* Type : chaîne de caractères
* Valeur : optionnelle
* Motif : `^(Le |La |Les |Los |Aux |L'|)([A-ZÉÇŒÈÎ])(((-| | - |')[A-ZÉÇŒÈÎ])|('|-| |)[a-zàâéèêëïîÿôûüœç])*( \([A-Z][a-z]*\)|)$`

#### `COLL_INSEE` <a id="collinsee"></a>

* Titre : Code INSEE de la commune d'enregistrement à l'état-civil
* Description : Code INSEE de la commune où les prénoms sont enregistrés à l'état-civil, c'est-à-dire le lieu de naissance. Issu du Code Officiel Géographique, le [code INSEE de la commune](https://fr.wikipedia.org/wiki/Code_Insee) est composé de 5 caractères alphanumériques \(les deux premiers correspondent au département et peuvent donc contenir les lettres 'A' et 'B' utilisées pour la Corse\).
* Type : chaîne de caractères
* Valeur : obligatoire
* Motif : `^([013-9]\d|2[AB1-9])\d{3}$`

#### `ENFANT_SEXE` <a id="enfantsexe"></a>

* Titre : Sexe relatif au prénom
* Description : Sexe correspondant au prénom, codé 'M' ou 'F' ou 'I', respectivement pour Masculin, Féminin ou Intersexué/Indéterminé. L'information est importante car certains prénoms sont aussi bien masculins que féminins, comme 'Camille'. 'I' signale un genre spécifiquement intersexué ou indéterminé et, contrairement à ce qu'il pourrait laisser penser, il ne mentionne pas un sexe inconnu. 'I' n'est théoriquement pas encore utilisé en France mais plusieurs pays ont créé un tel statut et de nombreux éléments suggèrent une évolution prochaine du droit en France.
* Type : chaîne de caractères
* Valeur : obligatoire
* Valeurs autorisées : M, F, I

#### `ENFANT_PRENOM` <a id="enfantprenom"></a>

* Titre : Prénom
* Description : Prénom de nouveau\(x\)-né\(s\) constaté comme premier prénom dans les actes d'état-civil de l'année correspondante. Un acte de naissance peut désigner un nouveau-né avec plusieurs prénoms et le législateur a prévu que "[_tout prénom inscrit dans l'acte de naissance peut être choisi comme prénom usuel_](https://fr.wikipedia.org/wiki/Pr%C3%A9nom_usuel)_"_. La plupart du temps le premier prénom est le prénom d'usage initialement choisi par le\(s\) parent\(s\). Cette spécification ne retient donc que le premier prénom : si un nouveau-né est appelé 'Armelle Julia Blanche', seul 'Armelle' sera retenu pour constituer ce jeu de données. Un prénom composé comme 'Marie-Jeanne' compte pour un prénom complet. Attention, "[_l'alphabet utilisé doit être celui qui sert à l'écriture du français. Les caractères alphabétiques étrangers ne sont donc pas autorisés \(par exemple le « ñ »\)_](https://www.demarches.interieur.gouv.fr/particuliers/choix-prenom-enfant)". Outre les caractères alphabétiques, un prénom peut posséder un trait d'union, voire deux, comme dans 'Lou-Anne' ou 'Mohamed-El-Amine'. Des prénoms peuvent posséder une apostrophe comme dans Gwenc'Hlan ou N'Deye, voire peut-être deux. Nous considérons aussi qu'un prénom pourrait se terminer, voire débuter, par une apostrophe - cette dernière étant parfois utilisée en français pour marquer la suppression de la finale ou le début d'un mot, comme dans Boul' Mich'.
* Type : chaîne de caractères
* Valeur : obligatoire
* Motif : `^'?[A-ZÉÀÈÙÄËÏÖÜŸÂÊÎÔÛŶÇŒÆ][a-zéàèùäëïüöÿâêîôûŷçæœ]*(|'|(('[A-ZÉÀÈÙÄËÏÖÜŸÂÊÎÔÛŶÇŒÆa-zéàèùäëïüöÿâêîôûŷçæœ][a-zéàèùäëïüöÿâêîôûŷçæœ]*'?){1,2}|(-[A-ZÉÀÈÙÄËÏÖÜŸÂÊÎÔÛŶÇŒÆ][a-zéàèùäëïüöÿâêîôûŷçæœ]*'?){1,2}){1,5})$`

#### `NOMBRE_OCCURRENCES` <a id="nombreoccurrences"></a>

* Titre : Nombre d'occurrences
* Description : Nombre d'occurrences du prénom pour l'année correspondante. Tous les prénoms sont comptabilisés, y compris les prénoms uniques - un seuil minimum est exclu car il conduirait à passer sous silence une importante part des naissances, voire la totalité dans les petites communes. La valeur de ce champ est donc un nombre entier d'1 à 6 chiffres maximum, 0 étant exclu.
* Type : nombre entier
* Valeur : obligatoire
* Valeur minimale : 1
* Valeur maximale : 999999

#### `ANNEE` <a id="annee"></a>

* Titre : Année
* Description : Année de relevé, sur quatre chiffres, au format AAAA.
* Type : année
* Valeur : obligatoire
* Motif : `^[1-2]\d\d\d$`

## Voir aussi  <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* [Fichier gabarit à télécharger au format xlsx](https://scdl.opendatafrance.net/docs/templates/scdl-prenoms.xlsx)
* [Schéma de validation](https://github.com/CharlesNepote/liste-prenoms-nouveaux-nes/blob/v1.1.2/prenom-schema.json)

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=Pr%C3%A9noms)
* ouvrir un ticket sur le [dépôt Github de Charles Nepote](https://github.com/CharlesNepote/liste-prenoms-nouveaux-nes/issues/new)

