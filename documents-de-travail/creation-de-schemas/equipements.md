---
description: >-
  Draft de la spécification du modèle de données relatif aux équipements
  collectifs publics d'une collectivité locale
---

# Equipements

## Version 1.0.0 du 30/01/2018 <a id="version-0-0-0-du-jj-mm-aaaa"></a>

{% hint style="info" %}
Lien permanent vers le [document actuellement publié](http://www.opendatafrance.net/SCDL_Equipements_Publics) sur GDrive
{% endhint %}

{% page-ref page="equipements.md" %}

## Contexte <a id="contexte"></a>

Les données géolocalisées permettant de dresser l'inventaire et de cartographier les équipements collectifs publics implantés sur leurs territoires représentent un enjeu majeur de connaissance pour toutes les strates de collectivités locales.

Reformulée et affinée à l'issue de plusieurs expérimentations de terrain, la [définition proposée par le groupe de travail EquipCo](https://docs.google.com/spreadsheets/d/1x_8TKmdBVXiBBkwf4ZWSHMhbNgeTGiXuQraiHP5d7pU/) du CRIGE PACA énonce qu'un équipement collectif public est "_un équipement proposant un service au public : structures ou bâtiments, publics ou privés, répondant aux besoins de la population sur un territoire_". Les travaux de ce groupe de travail, démarrés dès 2008, ont consisté à concevoir, tester et améliorer un modèle de données et une nomenclature en vue de construire une base de données régionale à partir de sources multiples.

* [Modèle de données des équipements collectifs publics](http://www.crige-paca.org/index.php?eID=tx_crigedocuments&hash=2eb4b236&fid=3117) - Version 2.0 - CRIGE PACA \([Tableur en ligne](https://docs.google.com/spreadsheets/d/1QDydwJ17gPLm71rKC5cNXO5w93PKaC3MmOLYhGfWJWU/edit#gid=652816451)\)
* [Nomenclature des équipements collectifs publics](http://www.crige-paca.org/index.php?eID=tx_crigedocuments&hash=97632e80&fid=3118) - Version 2.0 - CRIGE PACA \([Tableur en ligne](https://docs.google.com/spreadsheets/d/157WPWMUDC6w58Aep1dgWzzunKEjzSd-QmyuEHa8RFqc/)\)

S'appuyant sur ces travaux, de nombreuses collectivités françaises ont pu constituer leur propre base locale et pour certaines les publier en open data. La spécification du modèle de données relatif aux équipements collectifs publics d'une collectivité locale s'inscrit dans cette dynamique. Elle a été élaborée à partir des documents issus du groupe de travail EquipCo. Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`20 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `COLL_NOM`

* Titre : Nom de la collectivité
* Description : Nom officiel de la collectivité sur le territoire de laquelle sont situés les équipements collectifs publics répertoriés dans le jeu de données. Ce nom est limité à 140 caractères maximum.
* Type : chaîne de caractères
* Exemple : 'Département du Val-de-Marne'
* Valeur : **obligatoire**
* Taille : 140 maximum

#### `COLL_SIRET`

* Titre : Code SIRET de la collectivité
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) de la collectivité sur le territoire de laquelle sont situés les équipements collectifs publics répertoriés dans le jeu de données. Il est composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : '22940028800010'
* Valeur : **obligatoire**
* Motif : `^\d{14}$`

#### `EQUIP_UID`

* Titre : Identifiant unique de l'équipement
* Description : Cet identifiant unique est constitué du [code INSEE de la commune](https://fr.wikipedia.org/wiki/Code_Insee) où est implanté l'équipement sur 5 caractères \(incluant 'A' ou 'B' pour la Corse\) suivi du [code d'identification de l'équipement](equipements.md#equip_code), séparés par un tiret du milieu. Il s'agit donc d'une chaîne de 18 caractères qui permet d'identifier chacun des équipements référencés de manière univoque.
* Type : chaîne de caractères \(format `uuid`\)
* Exemple : '94059-01010401-001'
* Valeur : **obligatoire**
* Taille : 18 maximum
* Motif : ?

#### `EQUIP_THEME`

* Titre : Thème de classement de l'équipement
* Description : Les entrées de la [nomenclature des équipements collectifs publics](https://docs.google.com/spreadsheets/d/157WPWMUDC6w58Aep1dgWzzunKEjzSd-QmyuEHa8RFqc) sont divisées en 10 grandes familles. Les intitulés de ces grandes familles sont utilisés pour classer les équipements par thème. Ce champ doit donc être renseigné à partir d'une des valeurs suivantes : 'Equipement administratif', 'Equipement de justice', 'Equipement sanitaire', 'Equipement social et d'animation', 'Equipement sportif et de loisirs', 'Equipement d'enseignement', 'Equipement cultuel', 'Equipement culturel', 'Equipement de mobilité', ou 'Autre équipement'.
* Type : chaîne de caractères
* Exemple : 'Equipement administratif'
* Valeur : **obligatoire**
* Valeurs autorisées : 'Equipement administratif', 'Equipement de justice', 'Equipement sanitaire', 'Equipement social et d'animation', 'Equipement sportif et de loisirs', 'Equipement d'enseignement', 'Equipement cultuel', 'Equipement culturel', 'Equipement de mobilité', 'Autre équipement'

#### `EQUIP_CODE`

* Titre : Code d'identification de l'équipement
* Description : Le code d'identification de l'équipement est constitué du code sur 8 chiffres des niveaux 3 ou 4 \(quand il existe\) de la [nomenclature des équipements collectifs publics](https://docs.google.com/spreadsheets/d/157WPWMUDC6w58Aep1dgWzzunKEjzSd-QmyuEHa8RFqc), suivi d'un numéro d'ordre sur 3 chiffres \(de '001' minimum à '999' maximum\), séparés par un tiret du milieu. Il est utilisé pour construire [l'identifiant unique de l'équipement](equipements.md#equip_uid). En fonction du niveau et donc du code choisi dans la nomenclature, un des termes associés doit être reporté en tant que valeur pour définir le [type d'équipement](equipements.md#equip_type).
* Type : chaîne de caractères
* Exemple : '01010401-001'
* Valeur : **obligatoire**
* Taille : 12 maximum
* Motif : ?

#### `EQUIP_TYPE`

* Titre : Type d'équipement
* Description : Le type d'équipement correspond à un des termes associés au code choisi dans la [nomenclature des équipements collectifs publics](https://docs.google.com/spreadsheets/d/157WPWMUDC6w58Aep1dgWzzunKEjzSd-QmyuEHa8RFqc) pour identifier l'équipement dans [`EQUIP_CODE`](equipements.md#equip_code). Il s'agit donc de renseigner ce champ avec une valeur, jugée la plus pertinente pour désigner l'équipement, dans la limite de 140 caractères maximum [en prenant soin d'échapper ou de supprimer les éventuelles virgules](../../recommandations-relatives-aux-jeux-de-donnees.md#recommandations-pour-le-formatage-des-fichiers).
* Type : chaîne de caractères
* Exemple : 'Mairie'
* Valeur : **obligatoire**
* Taille : 140 maximum

#### `EQUIP_NOM`

* Titre : Nom complet de l'équipement
* Description : Ce champ permet de nommer l'équipement collectif public par son nom d'usage complet afin de préciser ou compléter, si nécessaire, le terme utilisé pour désigner le type, dans la limite de 256 caractères maximum.
* Type : chaîne de caractères
* Exemple : 'Hôtel de ville du Plessis-Trévise'
* Valeur : **obligatoire**
* Taille : 256 maximum

#### `ADR_NUMERO`

* Titre : Numéro d’adresse complet
* Description : Ce champ désigne le numéro d’adresse dans la voie suivi, si nécessaire, d'une information suffixée qui complète et précise le numéro d’adresse. Cette information suffixée peut être un indice de répétition \('bis', 'ter', 'qua', 'qui', etc... codés sur 3 caractères en minuscules\) ou un complément comme le nom d'entrée d'immeuble \('a', 'b', 'c', 'a1', 'b2', 'lesmimosas', etc... codés en minuscules non accentuées, sans espace ni limite du nombre de caractères\). Dans le cas des voies ou des lieux-dits sans adresse, la valeur '99999' est attendue. Dans le cas d'une adresse indiquant un intervalle entre deux numéros, ces derniers sont séparés par une barre oblique.
* Type : chaîne de caractères
* Exemple : '36' pour un numéro sans suffixe ou '36 bis' pour un numéro avec un indice de répétition ou '36/38' pour un intervalle entre deux numéros
* Valeur : **obligatoire**
* Taille : 70 maximum

#### `ADR_NOMVOIE`

* Titre : Nom complet de la voie
* Description : Ce champ contient la concaténation du type et du nom de la voie ou le nom d'un lieu-dit, exprimés en majuscules et minuscules accentuées.
* Type : chaîne de caractères
* Exemple : 'Avenue Ardouin'
* Valeur : **obligatoire**
* Motif : `^[a-zA-Z0-9\-\'\s\d\u00C0-\u00FF]+$`

#### `ADR_CODEPOSTAL`

* Titre : Code postal
* Description : Elément de l'adresse qui désigne le code postal de la commune où est implanté l'équipement collectif public.
* Type : chaîne de caractères
* Exemple : '94420'
* Valeur : **obligatoire**

#### `ADR_COMMUNE`

* Titre : Commune
* Description : Elément de l'adresse qui désigne le nom de la commune où est implanté l'équipement collectif public.
* Type : chaîne de caractères
* Exemple : 'Le Plessis-Trévise'
* Valeur : **obligatoire**

#### `ADR_CLE_INTEROP`

* Titre : Clé d'interopérabilité de l'adresse
* Description : Cette clé est identique à celle décrite dans le modèle [Base adresse locale](../amelioration-de-schemas-1/base-adresse-locale.md#cleinterop). Elle combine le [code INSEE de la commune](https://fr.wikipedia.org/wiki/Code_Insee) sur 5 caractères \(incluant 'A' ou 'B' pour la Corse\) + le code de voie issu du [FANTOIR](https://fr.wikipedia.org/wiki/FANTOIR) de la DGFiP sur 4 caractères + le numéro d’adresse sur 5 caractères préfixé par des zéros + un suffixe s'il existe, qui peut être un indice de répétition \('bis', 'ter', 'qua', 'qui', etc... codés sur 3 caractères\) et/ou un complément \('a', 'b', 'c', 'a1', 'b2', 'lesmimosas', etc... sans limitation du nombre de caractères\). Chaque élément est séparé par un tiret du bas et les lettres sont en minuscules.
* Type : chaîne de caractères
* Exemple : '94059\_0040\_00036'
* Valeur : **optionnelle**
* Motif : `^[A-Za-z0-9_]+$`

#### `ERP_TYPE`

* Titre : Type d'Etablissement Recevant du Public
* Description : Les [Etablissements Recevant du Public](https://fr.wikipedia.org/wiki/%C3%89tablissement_recevant_du_public_en_droit_fran%C3%A7ais) \(ERP\) installés dans un bâtiment et les établissements spéciaux sont classés par type en fonction de leur activité ou de la nature de leur exploitation. Le type est symbolisé par une à trois lettre\(s\) en majuscule dans le respect de [l'article GN1 de l'Arrêté du 25 juin 1980](https://www.legifrance.gouv.fr/affichTexte.do;?cidTexte=LEGITEXT000020303557). Si l'équipement collectif public est un ERP, ce champ peut être renseigné à partir d'une des valeurs suivantes :  'J', 'L', 'M', 'N', 'O', 'P', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y' pour les ERP installés dans un bâtiment et 'PA', 'CTS', 'SG', 'PS', 'GA', 'OA', 'EF', 'REF' pour les établissements spéciaux. Dans le cas d'un ERP couvrant plusieurs types, les valeurs sont séparées par un point-virgule.
* Type : chaîne de caractères
* Exemple : 'W' ou 'W;L'
* Valeur : **optionnelle**
* Taille : 10 maximum
* Motif : ?

#### `ERP_CATEGORIE`

* Titre : Catégorie d'Etablissement Recevant du Public
* Description : Les [Etablissements Recevant du Public](https://fr.wikipedia.org/wiki/%C3%89tablissement_recevant_du_public_en_droit_fran%C3%A7ais) \(ERP\) sont classés par catégorie en fonction de leur capacité d'accueil. La catégorie est symbolisée par un chiffre de 1 à 5 dans le respect de [l'article R123-19 du Code de la construction et de l'habitation](https://www.legifrance.gouv.fr/affichCodeArticle.do?cidTexte=LEGITEXT000006074096&idArticle=LEGIARTI000006896108). Si l'équipement collectif public est un ERP, ce champ peut être renseigné.
* Type : nombre entier
* Exemple : '5'
* Valeur : **optionnelle**
* MinMax : 1 minimum et 5 maximum

#### `EQUIP_LAT`

* Titre : Latitude
* Description : Coordonnée de latitude exprimée en [WGS 84](https://fr.wikipedia.org/wiki/WGS_84) permettant de localiser l'équipement collectif public. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '48.808989'
* Valeur : **obligatoire**

#### `EQUIP_LONG`

* Titre : Longitude
* Description : Coordonnée de longitude exprimée en [WGS 84](https://fr.wikipedia.org/wiki/WGS_84) permettant de localiser l'équipement collectif public. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre décimal
* Exemple : '2.572875'
* Valeur : **obligatoire**

#### `EQUIP_OUVERTURE`

* Titre : Jours et horaires d'ouverture
* Description : Ce champ permet de renseigner, si l'information est connue, les jours et horaires d'ouverture de l'équipement en respectant le [format utilisé pour la clé 'opening\_hours'](https://wiki.openstreetmap.org/wiki/FR:Key:opening_hours) dans OpenStreetMap. Un outil comme [YoHours](http://projets.pavie.info/yohours/) facilite la transformation des jours et horaires d'ouverture dans ce format. Celui-ci pouvant contenir des virgules comme signes de séparation, il est nécessaire d'[entourer les valeurs de la chaîne de caractères par des guillemets doubles](../../recommandations-relatives-aux-jeux-de-donnees.md#recommandations-pour-le-formatage-des-fichiers).
* Type : chaîne de caractères
* Exemple : "Mo-Fr 08:30-12:00,13:30-17:30; Sa 08:30-12:00"
* Valeur : **optionnelle**

#### `EQUIP_TEL`

* Titre : Téléphone
* Description : Ce champ permet de renseigner, si l'information est connue, le numéro de téléphone \(du gestionnaire\) de l'équipement exprimé sous la forme d'une chaîne de caractère de 8 chiffres d'un seul tenant.
* Type : chaîne de caractères
* Exemple : '0149622525'
* Valeur : **optionnelle**
* Motif : ?

#### `EQUIP_EMAIL`

* Titre : Email
* Description : Ce champ permet de renseigner, si l'information est connue, l'adresse email \(du gestionnaire\) de l'équipement.
* Type : chaîne de caractères \(format `email`\)
* Exemple : 'contact@leplessistrevise.fr'
* Valeur : **optionnelle**

#### `EQUIP_WEB`

* Titre : Site web
* Description : Ce champ permet de renseigner, si l'information est connue, l'url d'accès au site web \(du gestionnaire\) de l'équipement.
* Type : chaîne de caractères \(format `uri`\)
* Exemple : 'https://www.leplessistrevise.fr'
* Valeur : **optionnelle**

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Exemple de fichier
* Schéma de validation​
* Documentation générée à partir du schéma​​

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à scdl@opendatafrance.email
* ouvrir un ticket sur le dépôt GitLab d’OpenDataFrance​

