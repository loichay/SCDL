---
description: >-
  Draft de la spécification du modèle de données relatif aux points d'eau
  incendie (PEI) d'une collectivité
---

# Points d'Eau Incendie

## Contexte <a href="contexte" id="contexte"></a>

En France, les Points d’Eau Incendie (PEI) - également appelés [hydrants](https://fr.wikipedia.org/wiki/Hydrant) (borne incendie, poteau incendie et autres points d'eau) - sont recensés par les [Services Départementaux d'Incendie et de Secours](https://fr.wikipedia.org/wiki/Service\_d%C3%A9partemental\_d'incendie\_et\_de\_secours) (SDIS), les collectivités territoriales et/ou les délégataires de service public. La gestion de ces données s'effectue à un échelon départemental. Les "bases de données hydrants" constituent un enjeu majeur pour la gestion des risques incendie et doivent être partagées entre départements limitrophes.

En 2018, dans le cadre de son [groupe de travail "Open Data"](http://www.afigeo.asso.fr/pole-entreprise/groupe-dinteret-ogc/2117-modele-minimal-hydrants-3.html), l'Association Française pour l'Information GEOgraphique (AFIGEO) a défini un [modèle minimal de données relatif aux points d'eau incendie](http://www.afigeo.asso.fr/images/BD-Entreprises/OGC\_-\_Open\_Data/Modele\_minimal\_donn%C3%A9es\_PEI.pdf) en se référant aux textes réglementaires suivants :

* [Article R2225-1 du Code général des collectivités territoriales](https://www.legifrance.gouv.fr/affichCodeArticle.do?cidTexte=LEGITEXT000006070633\&idArticle=LEGIARTI000030299532) (CGCT) créé par le [Décret n° 2015-235 du 27 février 2015 relatif à la défense extérieure contre l'incendie - Article 2](https://www.legifrance.gouv.fr/jo\_pdf.do?id=JORFTEXT000030296571)
* [Le référentiel national de la défense extérieure contre l'incendie fixé par l'arrêté du 15 décembre 2015](https://www.interieur.gouv.fr/Le-ministere/Securite-civile/Documentation-technique/La-defense-exterieure-contre-l-incendie)

La spécification SCDL du modèle de données relatif aux points d'eau incendie (PEI) a donc été élaborée à partir du modèle minimal de données proposé par l'AFIGEO. Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

En complément, un [tableau permet d'établir la correspondance](https://wiki.openstreetmap.org/wiki/FR:Tag:emergency%3Dfire\_hydrant#Correspondance\_avec\_le\_mod.C3.A8le\_PEI\_de\_l.27Afigeo) entre les champs de ce modèle et les attributs utilisés dans OpenStreetMap pour qualifier les hydrants.

## Modèle de données <a href="modele-de-donnees" id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](broken-reference). Il repose sur les **`28 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `insee`

* Titre : Code INSEE de la commune
* Description : Ce champ permet d'identifier la commune sur laquelle le PEI est situé à partir de son code INSEE. Dans le cas des plans et cours d’eau, plusieurs points d’aspiration peuvent y être associés. On prend alors en compte la localisation du point d’aspiration pour identifier la commune. Issu du Code Officiel Géographique, le [code INSEE de la commune](https://fr.wikipedia.org/wiki/Code\_Insee) est composé de 5 caractères alphanumériques (les deux premiers correspondent au département et peuvent donc contenir les lettres 'A' et 'B' utilisées pour la Corse).
* Type : chaîne de caractères
* Exemple : '34164'
* Valeur : **obligatoire**
* Motif : `^([013-9]\d|2[AB1-9])\d{3}$`

#### `id_sdis`

* Titre : Identifiant interne pour le SDIS
* Description : Identifiant interne du point d'eau respectant le formalisme propre au Service Départemental d'Incendie et de Secours. Sa composition dépend des pratiques en vigueur au sein de chaque SDIS. Sa taille ne peut pas excéder 70 caractères.
* Type : chaîne de caractères
* Exemple : '34164.00001'
* Valeur : **obligatoire**
* Taille : 70 maximum

#### `id_gestion`

* Titre : Identifiant interne pour le gestionnaire
* Description : Identifiant interne du point d'eau respectant le formalisme propre au gestionnaire. Sa composition dépend des pratiques en vigueur au sein de chaque organisme de gestion (collectivité ou délégataire). Sa taille ne peut pas excéder 70 caractères.
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille : 70 maximum

#### `nom_gest`

* Titre : Nom du gestionnaire
* Description : Ce champ permet de désigner par son nom l'organisme en charge de la gestion du point d'eau (collectivité ou délégataire). Sa taille ne peut pas excéder 140 caractères.
* Type : chaîne de caractères
* Exemple : 'Veolia'
* Valeur : **optionnelle**
* Taille : 140 maximum

#### `ref_terr`

* Titre : Numéro ou référence du point d’eau visible sur le terrain
* Description : Si le point d'eau est physiquement marqué par un numéro ou une référence (plaque, étiquette, etc), ce champ permet de reporter la valeur correspondante.
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille : 70 maximum

#### `type_pei`

* Titre : Type de point d’eau incendie
* Description : Ce champ permet de typer un point d'eau en choisissant une valeur parmi une liste pré-établie de 4 abrévations possibles issues du [référentiel national DECI](https://www.interieur.gouv.fr/content/download/91185/709898/file/r%C3%A9f%20nat%20DECI%20du%2015%20d%C3%A9c%202015.pdf) (voir la typologie p.39) : 'PI' pour désigner un poteau d’incendie, 'BI' pour désigner une prise d’eau sous pression notamment une bouche d’incendie, 'PA' pour désigner un point d’aspiration aménagé (point de puisage...),  'CI' pour désigner une citerne aérienne ou enterrée.
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **obligatoire**
* Valeurs autorisées :  PI, BI, PA, CI

#### `type_rd`

* Titre : Précision sur le type de point d’eau incendie
* Description : Si le réglement départemental DECI prévoit des compléments ou détails par rapport à la typologie du référentiel national,  ce champ permet de préciser le type de point d'eau à partir des nomenclatures établies au niveau local.
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

#### `diam_pei`

* Titre : Diamètre intérieur du poteau ou de la bouche
* Description : Pour les points d'eau de type poteau incendie (PI) et bouche d'incendie (BI), ce champ permet d'indiquer leur diamètre intérieur, exprimé en millimètres, en choisissant une valeur parmi une liste pré-établie de 3 valeurs possibles : '80', '100' ou '150'. Cette liste correspond à des classes de diamètres définies à partir des normes européennes fixant les caractéristiques techniques des PI (NF EN 14384 - Février 2006 et NFS 61-213 + CN - Avril 2007) et des BI (NF EN 14339 - Février 2006 et NFS 61-211 + CN - Avril 2007). La classe '80' regroupe les PI équipés d'1 sortie de 65 mm et éventuellement de 2 sorties de 40 mm. La classe '100' regroupe les PI équipés d'1 sortie de 100 mm ou de 2 sorties de 65 mm et les BI équipés d'1 sortie de 100 mm. La classe '150' regroupe les PI équipés de 2 sorties de 100 mm.
* Type : nombre entier
* Exemple :&#x20;
* Valeur : **optionnelle**
* Valeurs autorisées : 80, 100, 150

#### `diam_cana`

* Titre : Diamètre de la canalisation du poteau ou de la bouche
* Description : Ce champ permet de renseigner le diamètre, exprimé en millimètres, de la canalisation sur laquelle sont implantés les points d'eau de type poteau incendie (PI) et bouche d'incendie (BI).
* Type : nombre entier
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Diamètre de la canalisation exprimé en mm pour les PI et BI

#### `source_pei`

* Titre : Source du point d’eau
* Description :&#x20;
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Valeurs autorisées : citerne, plan\_eau, piscine, puit, cours\_eau, reseau\_aep, reseau\_irrigation

Valeurs possibles : citerne, plan\_eau, piscine, puit, cours\_eau, reseau\_aep, reseau\_irrigation

#### `statut`

* Titre : Statut du point d’eau
* Description :&#x20;
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Valeurs autorisées : public, prive

Valeurs possibles : public, prive\
Le statut du point d’eau est décrit dans le règlement national (p. 43)

#### `nom_etab`

* Titre : Nom de l’établissement propriétaire
* Description : Dans le cas d’un statut privé, nom de l’établissement propriétaire
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :

#### `situation`

* Titre : ~~Situation du PEI~~
* Description : Adresse ou informations permettant de faciliter la localisation du point d’eau sur le terrain.
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

#### `press_dyn`

* Titre : ~~Pression dynamique~~
* Description :&#x20;
* Type : nombre réel
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Pression dynamique en bars au débit nominal

#### `press_stat`

* Titre : ~~Pression statique~~
* Description :&#x20;
* Type : nombre réel
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Pression statique en bars

#### `debit`

* Titre : Débit ~~risque~~
* Description :&#x20;
* Type : nombre réel
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Valeur de débit mesuré exprimé en m3/h sous une pression de 1 bar

#### `volume`

* Titre : Volume
* Description :&#x20;
* Type : nombre entier
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Capacité volumique utile de la source d’eau en m3\
Si la source est inépuisable, ne pas renseigner ce champ (cours d’eau ou plan d’eau pérenne)

#### `disponible`

* Titre : ~~Etat de disponibilité~~
* Description :&#x20;
* Type : booléen
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

0 ou 1. Valide à la date de dernière mise à disposition des données

#### `date_dispo`

* Titre : ~~Date du dernier changement d'état de disponibilité~~
* Description :&#x20;
* Type : date
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Date de dernier changement d’état de disponibilité

#### `date_mes`

* Titre : Date de mise en service du PEI
* Description :&#x20;
* Type : date
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Date de mise en service du PEI

#### `date_maj`

* Titre : Date de dernière mise à jour des données
* Description :&#x20;
* Type : date
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Date de dernière mise à jour de la donnée au format aaaa-mm-jj

#### `date_ct`

* Titre : ~~Date du dernier contrôle technique~~
* Description :&#x20;
* Type : date
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Date du dernier contrôle technique au format aaaa-mm-jj

#### `date_ro`

* Titre : ~~Date de la dernière reconnaissance opérationnelle~~
* Description :&#x20;
* Type : date
* Exemple :&#x20;
* Valeur : **optionnelle**
* Taille :&#x20;

Date de la dernière reconnaissance opérationnelle au format aaaa-mm-jj

#### `prec`

* Titre : ~~Précision de la mesure de localisation~~
* Description : Qualité de positionnement
* Type : chaîne de caractères
* Exemple :&#x20;
* Valeur : **optionnelle**
* Valeurs autorisées :&#x20;

Classes de précision : 01 (0 à 1 m), 05 (de 1 à 5 m), 10 (de 5 à 10 m), 99 (plus de 10 m), vide si inconnu

#### `x`

x en lambert 93 (précision de 2 décimales)

#### `y`

y en lambert 93 (précision de 2 décimales)

#### `lon`

longitude en degrés décimaux en WGS 84 (précision de 8 décimales)

#### `lat`

latitude en degrés décimaux en WGS 84 (précision de 8 décimales)

## Voir aussi <a href="voir-aussi" id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Fichier gabarit à exporter
* Schéma de validation​

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=PEI)
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance​](https://git.opendatafrance.net/scdl/equipements/issues/new)

