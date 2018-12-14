---
description: >-
  Draft de la spécification du modèle de données relatif aux adresses locales
  d’une collectivité
---

# Base Adresse Locale

## Contexte <a id="contexte"></a>

En France, la création des voies et des adresses est une compétence exercée par les communes et s'appuie sur des décisions prises par les conseils municipaux. La mise en oeuvre de cette compétence peut néanmoins être déléguée à un [Etablissement Public de Coopération Intercommunale](https://fr.wikipedia.org/wiki/%C3%89tablissement_public_de_coop%C3%A9ration_intercommunale) \(EPCI\). Le regroupement de tout ou partie des adresses d’une collectivité dans une base de données permet d'outiller la gestion et la publication de cette ressource.

En 2016, dans le cadre du [groupe de travail "SIG et Topographie"](http://www.aitf.fr/groupe-travail/sig-topographie) rassemblant des ingénieurs territoriaux de différentes collectivités locales, l’Association des Ingénieurs Territoriaux de France \(AITF\) a défini un modèle d'échange de données entre les bases voie-adresse gérées localement et la Base Adresse Nationale \(BAN\). En l'absence d'un cadre réglementaire précis, cette spécification d'un modèle de données simple applicable à une Base Adresse Locale \(BAL\) permet de standardiser la publication en open data des adresses d'une collectivité.

La spécification SCDL du modèle de données relatif aux adresses locales d’une collectivité a donc été élaborée à partir de la proposition d’un [modèle de données simple visant à alimenter la BAN par des fichiers](https://cms.geobretagne.fr/sites/default/files/documents/aitf-sig-topo-adresse-fichier-echange-simplifie-v_1.1_0.pdf) de l'AITF. Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

#### `Avertissement !`

L'utilisation de cette spécification requiert de prêter une attention toute particulière aux points suivants :

* Contrairement aux recommandations applicables à toutes les spécifications SCDL, le modèle de l'AITF prévoit que le séparateur de colonnes du fichier tabulaire doit être le point-virgule et pas la virgule.
* De même, les règles de nommage sont légèrement différentes : le nom du fichier comporte la date de création du jeu de données, la désignation du producteur et son code SIREN. Le tout sans espace ni accent et en minuscules, soit : AAAAMMJJ\_producteur\_siren.csv. Exemple : '20151004\_rennes\_213502388.csv'

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`13 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `cle_interop` <a id="cleinterop"></a>

* Titre : Clé d'interopérabilité
* Description : Cette clé combine le [code INSEE de la commune](https://fr.wikipedia.org/wiki/Code_Insee) sur 5 caractères \(incluant 'A' ou 'B' pour la Corse\) + le code de voie issu du [FANTOIR](https://fr.wikipedia.org/wiki/FANTOIR) de la DGFiP sur 4 caractères + le numéro d’adresse sur 5 caractères préfixé par des zéros + un suffixe s'il existe, qui peut être un indice de répétition \('bis', 'ter', 'qua', 'qui', etc... codés sur 3 caractères\) et/ou un complément \('a', 'b', 'c', 'a1', 'b2', 'lesmimosas', etc... sans limitation du nombre de caractères\). Chaque élément est séparé par un tiret du bas et les lettres sont en minuscule.
* Type : chaîne de caractères
* Exemple : '35238\_3961\_00007\_bis'
* Valeur : **obligatoire**
* Motif : `^[A-Za-z0-9_]+$`

#### `uid_adresse` <a id="uidadresse"></a>

* Titre : Identifiant unique national d’adresse
* Description : Cet identifiant unique d’adresse est géré et attribué par le service "guichet national d’identification" de la Base Adresse Nationale. Dans l'attente de la mise en place de ce service, les règles de création ou de gestion de cet identifiant ne sont pas connues. La valeur de ce champ est donc optionnelle et sera laissée vide aussi longtemps que le service d'identification ne sera pas opérationnel.
* Type : chaîne de caractères \(format `uuid`\)
* Valeur : **optionnelle**

#### `voie_nom` <a id="voienom"></a>

* Titre : Nom complet de la voie
* Description : Ce champ contient la concaténation du type et du nom de la voie ou le nom d'un lieu-dit, exprimés en majuscules et minuscules accentuées.
* Type : chaîne de caractères
* Exemple : 'Allée de Bréhat' pour une concaténation ou 'Le pré aux grenouilles' pour un lieu-dit
* Valeur : **obligatoire**
* Motif : `^[a-zA-Z0-9\-\'\s\d\u00C0-\u00FF]+$`

#### `numero` <a id="numero"></a>

* Titre : Numéro d’adresse
* Description : Ce champ désigne le numéro d’adresse dans la voie et, dans le cas des voies ou des lieux-dits sans adresse, la valeur '99999' est attendue.
* Type : nombre entier
* Exemple : '127'
* Valeur : **obligatoire**
* MinMax : 0 minimum et 99999 maximum

#### `suffixe` <a id="suffixe"></a>

* Titre : Information suffixée qui complète et précise le numéro d’adresse
* Description : Cette information peut être un indice de répétition \('bis', 'ter', 'qua', 'qui', etc... codés sur 3 caractères en minuscules\) ou un complément comme le nom d'entrée d'immeuble \('a', 'b', 'c', 'a1', 'b2', 'lesmimosas', etc... codés en minuscules non accentuées, sans espace ni limite du nombre de caractères\).
* Type : chaîne de caractères
* Exemple : 'ter' pour un indice de répétition ou 'lesmimosas' pour un nom d'entrée d'immeuble
* Valeur : **obligatoire**
* Motif : `^[a-z\d\u00DF-\u00FF]+$`

#### `commune_nom` <a id="communenom"></a>

* Titre : Nom officiel de la commune
* Description : Ce champ doit permettre d’identifier rapidement le territoire concerné et d'éviter les quiproquos.
* Type : chaîne de caractères
* Exemple : 'Rennes'
* Valeur : **obligatoire**
* Motif : `^[A-Za-z\s\-\u00C0-\u00FF]+$`

#### `position` <a id="position"></a>

* Titre : Code de position de l’adresse
* Description : Ce code décrit la position d’une adresse à partir d’une liste de valeurs qui provient de la spécification INSPIRE v 3.1 sur le thème "Adresses". Les valeurs attendues sont, au choix, 'délivrance postale', 'entrée', 'bâtiment', 'cage d’escalier', 'logement', 'parcelle', 'segment', ou 'service technique'.
* Type : chaîne de caractères
* Exemple : 'cage d'escalier'
* Valeur : **obligatoire**
* Valeurs autorisées : ****'délivrance postale', 'entrée', 'bâtiment', 'cage d’escalier', 'logement', 'parcelle', 'segment', 'service technique'

#### `x` <a id="x"></a>

* Titre : Coordonnée X
* Description : Coordonnée X du système légal en vigueur sur le territoire concerné, conformément à l’article 1 du [décret n° 2006-272](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000000813996) du 3 mars 2006. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '145377.55'
* Valeur : **optionnelle**

#### `y` <a id="y"></a>

* Titre : Coordonnée Y
* Description : Coordonnée Y du système légal en vigueur sur le territoire concerné, conformément à l’article 1 du [décret n° 2006-272](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000000813996) du 3 mars 2006. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '6835665.67'
* Valeur : **optionnelle**

#### `long` <a id="long"></a>

* Titre : Longitude
* Description : Coordonnée de longitude exprimée en [WGS 84](https://fr.wikipedia.org/wiki/WGS_84). Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '-4.502217943385534'
* Valeur : **optionnelle**

#### `lat` <a id="lat"></a>

* Titre : Latitude
* Description : Coordonnée de latitude exprimée en [WGS 84](https://fr.wikipedia.org/wiki/WGS_84). Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '48.383985827041485'
* Valeur : **optionnelle**

#### `source` <a id="source"></a>

* Titre : Nom de la source
* Description : Ce nom peut désigner, au choix, la collectivité ayant créé juridiquement l’adresse \(par délibération\), l'entité ayant créé la donnée, ou l’entité ayant diffusé / publié la donnée.
* Type : chaîne de caractères
* Exemple : 'Rennes Métropole'
* Valeur : **obligatoire**
* Motif : `[a-zA-Z0-9\-\d\s\u00C0-\u00FF]+`

#### `date_der_maj` <a id="datedermaj"></a>

* Titre : Date de dernière mise à jour
* Description : Cette date est celle de la dernière mise à jour connue de la donnée. Elle ne correspond pas à la date de publication du jeu de données en open data. Elle est exprimée au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : '2014-10-01'
* Valeur : **obligatoire**

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Fichier gabarit à exporter
* [​Schéma de validation​](https://git.opendatafrance.net/scdl/adresses/blob/master/schema-scdl-adresses.json)

Pour faciliter la production et améliorer la qualité des données au format Base Adresse Locale, la mission Etalab de la DINSIC, met à disposition des outils dédiés sur le portail adresse.data.gouv.fr :

* [Le validateur BAL](https://adresse.data.gouv.fr/bases-locales/validateur) permet de vérifier la conformité d'un fichier BAL
* [L'éditeur BAL](https://adresse.data.gouv.fr/bases-locales/editeur) permet de créer et/ou de modifier un fichier BAL

Les sources de ces outils sont disponibles sur le [dépôt Github de la mission Etalab](https://github.com/etalab/adresse.data.gouv.fr).

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=Base%20Adresse%20Locale)​
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance​](https://git.opendatafrance.net/scdl/adresses/issues)



