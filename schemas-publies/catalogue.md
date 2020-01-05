---
description: >-
  Draft de la spécification du modèle de données relatif au catalogue des jeux
  de données publiés en opendata par une collectivité
---

# Catalogue simplifié

{% hint style="success" %}
[https://scdl.opendatafrance.net/docs/schemas/scdl-catalogue.html](https://scdl.opendatafrance.net/docs/schemas/scdl-catalogue.html)
{% endhint %}

## Version 0.1.1

* Auteur : OpenDataFrance
* Contributeurs : Thomas Bekkers, Loïc Haÿ
* Schéma créé le : 20/11/2018
* Schéma mis à jour le : 28/01/2019
* Site web : [https://git.opendatafrance.net/scdl/catalogue](https://git.opendatafrance.net/scdl/catalogue)
* [Gabarit au format Excel \(xlsx\)](https://scdl.opendatafrance.net/docs/templates/scdl-catalogue.xlsx)
* Valeurs manquantes : `""`

## Contexte <a id="contexte"></a>

Le catalogue opendata d'une collectivité rassemble les métadonnées de description des jeux de données qu'elle publie. Il peut être généré automatiquement par la plateforme qui les héberge ou qui les moissonne. Plusieurs standards permettent de normaliser les métadonnées d'un catalogue \(INSPIRE pour les données géographiques, DCAT et ses déclinaisons pour tout type de données ouvertes\), mais les catalogues locaux, lorsqu'ils existent, qu'ils soient exposés via une API ou extraits sous forme de fichiers, dépendent souvent de la capacité technique de la solution utilisée et de son paramétrage \(formats différents, plus ou moins riches ou étendus, en fonction de la plateforme, catalogue unique et pas pour chaque producteur quand la plateforme est mutualisée, distinction ou non entre jeux de données et ressources, etc\). Sans compter que de nombreuses collectivités utilisent de simples sites web pour mettre à disposition leurs données.

La spécification d'un modèle de données simplifié doit permettre d'harmoniser ces catalogues locaux dans un format accessible à toutes les collectivités et faciliter leur consolidation dans un inventaire national, le "catalogue des catalogues des données locales ouvertes".

Cette spécification a été élaborée à partir des sources suivantes :

* [Guide de saisie des éléments de métadonnées INSPIRE](http://cnig.gouv.fr/wp-content/uploads/2014/01/Guide-de-saisie-des-%C3%A9l%C3%A9ments-de-m%C3%A9tadonn%C3%A9es-INSPIRE-v1.1-final-light.pdf) - Recommandation du Conseil National de l'Information Géographique \(2013\)
* [Guide de mise en oeuvre du schéma DCAT-AP](https://docs.google.com/document/d/1qMDqBjrTJVu3t9RH94aLSW7Z3jhH1SjoBrWhW9PZkJ4/) rédigé par Pascal Romain du Département de la Gironde pour OpenDataFrance à partir du draft final de la spécification de la Commission Européenne \(2014\)
* [Data Catalog Vocabulary \(DCAT\)](https://www.w3.org/TR/vocab-dcat/) - Recommandation W3C relative au vocabulaire des catalogues de données publiés sur le web \(2014\)
* [DCAT Application Profile for data portals in Europe](https://joinup.ec.europa.eu/solution/dcat-application-profile-data-portals-europe/releases) \([DCAT-AP v1.1](https://github.com/SEMICeu/DCAT-AP/raw/master/releases/1.1/dcat-ap_1.1.pdf) en 2015 et [DCAT-AP v1.2](https://joinup.ec.europa.eu/sites/default/files/distribution/access_url/2018-11/014bde52-eb3c-4060-8c3c-fcd0dfc07a8a/DCAT_AP_1.2.pdf) en 2018\) - Spécification de la Commission Européenne, basée sur le vocabulaire DCAT, visant à décrire les jeux de données du secteur public en Europe, également disponible sur le [dépôt Github de l'initiative SEMICeu](https://github.com/SEMICeu/DCAT-AP)

## Modèle de données

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`20 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `COLL_NOM` <a id="collnom"></a>

* Titre : Nom de la collectivité
* Description : Nom officiel de la collectivité qui publie le catalogue simplifié de jeux de données limité à 140 caractères maximum.
* Type : chaîne de caractères
* Exemple : Rennes Métropole
* Valeur : obligatoire

#### `COLL_SIRET` <a id="collsiret"></a>

* Titre : Code SIRET de la collectivité
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) de la collectivité qui publie le catalogue simplifié de jeux de données, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : 24350013900189
* Valeur : obligatoire
* Motif : `^\d{14}$`

#### `ID` <a id="id"></a>

* Titre : Identifiant du jeu de donnée
* Description : Cet identifiant est une chaîne de caractères qui correspond soit au nom du jeu de données, exprimé en minuscules sans accent ni espace \(identifiant texte ou 'slug'\), soit à un code d'identification généré automatiquement \(identifiant machine ou 'hash'\).
* Type : chaîne de caractères
* Exemple : prenoms-des-nouveaux-nes-a-rennes-en-2017 ou 53699116a3a729239d203b7f
* Valeur : obligatoire

#### `TITRE` <a id="titre"></a>

* Titre : Titre du jeu de données
* Description : Ce titre doit être un intitulé caractéristique et univoque permettant de désigner le jeu de données. Il est recommandé d'y faire figurer une indication de la zone géographique couverte et, lorsqu'elle se justifie, une indication de version ou de millésime.
* Type : chaîne de caractères
* Exemple : Prénoms des nouveaux-nés à Rennes en 2017
* Valeur : obligatoire

#### `DESCRIPTION` <a id="description"></a>

* Titre : Description du jeu de données
* Description : Cette description doit fournir un bref résumé narratif du contenu du jeu de données, rédigé de façon compréhensible pour l’utilisateur.
* Type : chaîne de caractères
* Exemple : Liste annuelle des prénoms des nouveaux-nés enregistrés à l'état-civil de la ville de Rennes pour l'année 2017.
* Valeur : obligatoire

#### `THEME` <a id="theme"></a>

* Titre : Thème du jeu de données
* Description : En l'absence d'une nomenclature de classement par thèmes satisfaisante et adaptée au contexte local, le thème est exprimé sous la forme d'une chaîne de caractères libre dans la limite de 140 caractères maximum. Le manque de pertinence du [thésaurus EuroVoc](https://publications.europa.eu/fr/web/eu-vocabularies/th-dataset/-/resource/dataset/eurovoc) ou des [thèmes INSPIRE](https://inspire.ec.europa.eu/Themes/Data%20Specifications/2892) implique d'élaborer collectivement une [nomenclature spécifique](https://docs.google.com/document/d/1oDJsHw3bmABfto6HPgCPG1ztrV3CihuHjcfU8tQpvPc/) à partir d'un appariement des termes les plus utilisés sur les plateformes territoriales de données ouvertes.
* Type : chaîne de caractères
* Exemple : Administration locale
* Valeur : obligatoire

#### `PRODUCTEUR_NOM` <a id="producteurnom"></a>

* Titre : Nom du producteur
* Description : Nom officiel ou raison sociale du producteur du jeu de données limité à 140 caractères maximum.
* Type : chaîne de caractères
* Exemple : Ville de Rennes
* Valeur : obligatoire

#### `PRODUCTEUR_SIRET` <a id="producteursiret"></a>

* Titre : Code SIRET du producteur
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) du producteur du jeu de données, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : 21350238800019
* Valeur : obligatoire
* Motif : `^\d{14}$`

#### `COUV_SPAT_MAILLE` <a id="couvspatmaille"></a>

* Titre : Maille de couverture spatiale
* Description : La maille de couverture spatiale correspond à l'echelle territoriale que couvre le jeu de données. Pour simplifier le renseignement de ce champ, elle est désignée en choisissant une valeur parmi une liste pré-établie de valeurs possibles : 'Infracommunale', 'Communale', 'Intercommunale', 'Cantonale', 'Départementale', 'Régionale' ou 'Autre'.
* Type : chaîne de caractères
* Exemple : Communale
* Valeur : obligatoire
* Valeurs autorisées : Infracommunale, Communale, Intercommunale, Cantonale, Départementale, Régionale, Autre

#### `COUV_SPAT_NOM` <a id="couvspatnom"></a>

* Titre : Nom de couverture spatiale
* Description : Le nom de couverture spatiale correspond au nom de l'échelle territoriale que couvre le jeu de données. Il est exprimé sous la forme d'une chaîne de caractères limitée à 140 caractères maximum.
* Type : chaîne de caractères
* Exemple : Rennes
* Valeur : obligatoire

#### `COUV_TEMP_DEBUT` <a id="couvtempdebut"></a>

* Titre : Date de début de la couverture temporelle
* Description : La couverture temporelle correspond à la période que couvre le jeu de données. Cette période est un intervalle entre deux dates. La date de début est donc le premier terme utilisé pour désigner cet intervalle, exprimé au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : 2017-01-01
* Valeur : obligatoire

#### `COUV_TEMP_FIN` <a id="couvtempfin"></a>

* Titre : Date de fin de la couverture temporelle
* Description : La couverture temporelle correspond à la période que couvre le jeu de données. Cette période est un intervalle entre deux dates. La date de fin est donc le second terme utilisé pour désigner cet intervalle, exprimé au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : 2017-12-31
* Valeur : obligatoire

#### `DATE_PUBL` <a id="datepubl"></a>

* Titre : Date de la première publication
* Description : Date de la publication initiale du contenu du jeu de données. Elle est exprimée au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : 2017-06-01
* Valeur : obligatoire

#### `FREQ_MAJ` <a id="freqmaj"></a>

* Titre : Fréquence de la mise à jour
* Description : La fréquence de mise à jour correspond à la périodicité suivant laquelle des modifications sont apportées au jeu de données. Pour simplifier le renseignement de ce champ, elle est désignée en choisissant une valeur parmi une liste pré-établie de valeurs possibles : 'Inconnue', 'Ponctuelle', 'Irrégulière', 'Continuelle', 'Toutes les heures', 'Quotidienne ou plusieurs fois par jour', 'Hebdomadaire ou plusieurs fois par semaine', 'Mensuelle ou plusieurs fois par mois', 'Bimestrielle', 'Trimestrielle', 'Semestrielle', 'Annuelle', 'Biennale', 'Triennale', ou 'Quinquennale'.
* Type : chaîne de caractères
* Exemple : Semestrielle
* Valeur : obligatoire
* Valeurs autorisées : Inconnue, Ponctuelle, Irrégulière, Continuelle, Toutes les heures, Quotidienne ou plusieurs fois par jour, Hebdomadaire ou plusieurs fois par semaine, Mensuelle ou plusieurs fois par mois, Bimestrielle, Trimestrielle, Semestrielle, Annuelle, Biennale, Triennale, Quinquennale

#### `DATE_MAJ` <a id="datemaj"></a>

* Titre : Date de la dernière mise à jour
* Description : Date de la dernière modification effective du contenu du jeu de données. Elle est exprimée au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : 2018-01-14
* Valeur : obligatoire

#### `MOTS_CLES` <a id="motscles"></a>

* Titre : Mots clés
* Description : Un ou plusieurs mot\(s\) clé\(s\) utilisé\(s\) pour décrire le jeu de données en minuscules non accentuées. S'il y en a plusieurs, le séparateur est le point-virgule.
* Type : chaîne de caractères
* Exemple : scdl;prenoms;etat-civil
* Valeur : obligatoire

#### `LICENCE` <a id="licence"></a>

* Titre : Licence appliquée sur le jeu de données
* Description : Désignation de la licence qui encadre la réutilisation du jeu de données. En France, le [décret n° 2017-638 du 27 avril 2017](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000034502557) restreint le choix exclusivement à deux licences. D'autres sont néanmoins utilisées par quelques producteurs ou acteurs territoriaux pour encadrer la réutilisation de certains jeux de données. Pour simplifier le renseignement de ce champ, la licence du jeu de données est désignée en choisissant une valeur parmi une liste pré-établie de valeurs possibles : 'Licence Ouverte-LO', 'Open Database License-ODBL', 'Creative Commons-CC', 'Spécifique ou autre'.
* Type : chaîne de caractères
* Exemple : Licence Ouverte-LO
* Valeur : obligatoire
* Valeurs autorisées : Licence Ouverte-LO, Open Database License-ODBL, Creative Commons-CC, Spécifique ou autre

#### `NOMBRE_RESSOURCES` <a id="nombreressources"></a>

* Titre : Nombre de ressource\(s\)
* Description : Nombre de ressource\(s\) mise\(s\) à disposition dans le jeu de données.
* Type : nombre entier
* Exemple : 3
* Valeur : obligatoire
* Valeur minimale : 1

#### `FORMAT_RESSOURCES` <a id="formatressources"></a>

* Titre : Format\(s\) des ressources
* Description : Format\(s\) dans le\(s\)quel\(s\) la \(ou les\) ressource\(s\) du jeu de données est \(sont\) mise\(s\) à disposition. Ce\(s\) format\(s\) est \(sont\) exprimé\(s\) en minuscules non accentuées. S'il y en a plusieurs, le séparateur est le point-virgule.
* Type : chaîne de caractères
* Exemple : csv;xls;json
* Valeur : obligatoire

#### `URL` <a id="url"></a>

* Titre : URL d'accès
* Description : Cet élément fournit un lien, une adresse web la plus stable possible, vers la page du jeu de données \(ou de la ressource si le jeu de données n'en comprend qu'une\) et/ou vers des informations complémentaires le concernant.
* Type : chaîne de caractères \(format `uri`\)
* Exemple : [https://data.rennesmetropole.fr/explore/dataset/prenoms-des-nouveaux-nes-a-rennes-en-2017](https://data.rennesmetropole.fr/explore/dataset/prenoms-des-nouveaux-nes-a-rennes-en-2017)
* Valeur : obligatoire

## Voir aussi

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* [Fichier gabarit à télécharger au format xlsx](https://scdl.opendatafrance.net/docs/templates/scdl-catalogue.xlsx)
* [Schéma de validation](https://git.opendatafrance.net/scdl/catalogue/blob/master/schema.json)

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=Catalogue%20simplifi%C3%A9)
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance](https://git.opendatafrance.net/scdl/catalogue/issues/new)

