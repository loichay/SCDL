---
description: >-
  Draft de la spécification du modèle de données relatif aux points d'eau
  incendie (PEI) d'une collectivité
---

# Points d'eau incendie

## Contexte <a id="contexte"></a>

En France, les Points d’Eau Incendie \(PEI\) - également appelés [hydrants](https://fr.wikipedia.org/wiki/Hydrant) \(borne incendie, poteau incendie et autres points d'eau\) - sont recensés par les [Services Départementaux d'Incendie et de Secours](https://fr.wikipedia.org/wiki/Service_d%C3%A9partemental_d%27incendie_et_de_secours) \(SDIS\), les collectivités territoriales et/ou les délégataires de service public. La gestion de ces données est effectuée à un échelon départemental. Les "bases de données hydrants" constituent un enjeu majeur pour la gestion des risques incendie et doivent être partagées entre départements limitrophes.

En 2018, dans le cadre de son [groupe de travail "Open Data"](http://www.afigeo.asso.fr/pole-entreprise/groupe-dinteret-ogc/2117-modele-minimal-hydrants-3.html), l'Association Française pour l'Information GEOgraphique \(AFIGEO\) a défini un [modèle minimal de données relatif aux points d'eau incendie](http://www.afigeo.asso.fr/images/BD-Entreprises/OGC_-_Open_Data/Modele_minimal_donn%C3%A9es_PEI.pdf) en se référant aux textes réglementaires suivants :

* [Article R2225-1 du Code général des collectivités territoriales](https://www.legifrance.gouv.fr/affichCodeArticle.do?cidTexte=LEGITEXT000006070633&idArticle=LEGIARTI000030299532) \(CGCT\) créé par le [Décret n° 2015-235 du 27 février 2015 relatif à la défense extérieure contre l'incendie - Article 2](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000030296571)
* [Le référentiel national de la défense extérieure contre l'incendie fixé par l'arrêté du 15 décembre 2015](https://www.interieur.gouv.fr/Le-ministere/Securite-civile/Documentation-technique/La-defense-exterieure-contre-l-incendie)

La spécification SCDL du modèle de données relatif aux points d'eau incendie \(PEI\) a donc été élaborée à partir du modèle minimal de données proposé par l'AFIGEO. Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

En complément, un [tableau permet d'établir la correspondance](https://wiki.openstreetmap.org/wiki/FR:Tag:emergency%3Dfire_hydrant#Correspondance_avec_le_mod.C3.A8le_PEI_de_l.27Afigeo) entre les champs de ce modèle et les attributs utilisés dans OpenStreetMap pour qualifier les hydrants.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`28 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `insee`

* Titre : Code INSEE de la commune
* Description : Ce champ permet d'identifier la commune sur laquelle le PEI est situé à partir de son code INSEE. Dans le cas des plans et cours d’eau, plusieurs points d’aspiration peuvent y être associés. On prend alors en compte la localisation du point d’aspiration pour identifier la commune. Issu du Code Officiel Géographique, le [code INSEE de la commune](https://fr.wikipedia.org/wiki/Code_Insee) est composé de 5 caractères alphanumériques \(les deux premiers correspondent au département et peuvent donc contenir les lettres 'A' et 'B' utilisées pour la Corse\).
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
* Description : Identifiant interne du point d'eau respectant le formalisme propre au gestionnaire. Sa composition dépend des pratiques en vigueur au sein de chaque organisme de gestion \(collectivité ou délégataire\). Sa taille ne peut pas excéder 70 caractères.
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Taille : 70 maximum

#### `nom_gest`

* Titre : Nom du gestionnaire
* Description : Ce champ permet de désigner par son nom l'organisme en charge de la gestion du point d'eau \(collectivité ou délégataire\). Sa taille ne peut pas excéder 140 caractères.
* Type : chaîne de caractères
* Exemple : 'Veolia'
* Valeur : **optionnelle**
* Taille : 140 maximum

#### `ref_terr`

* Titre : Numéro ou référence du point d’eau visible sur le terrain
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Taille : 70 maximum

#### `type_pei`

* Titre : Type de point d’eau incendie
* Description : 4 abrévations issues du référentiel national DECI \(p.39\)
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Valeurs autorisées :  PI, BI, PA, CI

Valeurs possibles : PI, BI, PA, CI Signification : PI \(Poteau d’Incendie\), BI \(Prise d’eau sous pression, notamment bouche d’incendie\), PA \(Point d’aspiration aménagé \(point de puisage…\)\), CI \(Citerne aérienne ou enterrée\) Cette typologie est issue du règlement national \(p. 39\) . Si ce dernier évoluait, cette typologie évoluerait en conséquence.

#### `type_rd`

* Titre : Précision sur le type de point d’eau incendie
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Précision sur le type de point d’eau incendie défini dans le règlement départemental DECI. Typologie utilisée au niveau local pour caractériser le type de point d’eau

#### `diam_pei`

* Titre : Diamètre intérieur du poteau ou de la bouche
* Description : 
* Type : nombre entier
* Exemple : 
* Valeur : **optionnelle**
* Valeurs autorisées : 80, 100, 150

Valeurs possibles : 80, 100, 150

Norme européenne : Poteau Incendie NF EN 14384 \(Février 2006\) NF S 61 213 CN \(Avril 2007\) \(valeurs possibles : 80, 100 ou 150 ; 80 = 1 prise de 65 - 100 = 2 prises de diamètre 65, 1 prise de diamètre 100 - 150 = 2 prises de diamètre 100\) Bouche Incendie NF EN 14339 \(Février 2006\) NF S 61 211 CN \(Avril 2007\) \(valeur possible : 1 prise de diamètre 100\).

#### `diam_cana`

* Titre : Diamètre de la canalisation du poteau ou de la bouche
* Description : 
* Type : nombre entier
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Diamètre de la canalisation exprimé en mm pour les PI et BI

#### `source_pei`

* Titre : Source du point d’eau
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Valeurs autorisées : citerne, plan\_eau, piscine, puits, cours\_eau, reseau\_aep, reseau\_irrigation

Valeurs possibles : citerne, plan\_eau, piscine, puits, cours\_eau, reseau\_aep, reseau\_irrigation

#### `statut`

* Titre : Statut du point d’eau
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Valeurs autorisées : public, prive

Valeurs possibles : public, prive  
Le statut du point d’eau est décrit dans le règlement national \(p. 43\)

#### `nom_etab`

* Titre : Nom de l’établissement propriétaire
* Description : Dans le cas d’un statut privé, nom de l’établissement propriétaire
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Taille :

#### `situation`

* Titre : Situation du PEI
* Description : Adresse ou informations permettant de faciliter la localisation du point d’eau sur le terrain.
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

#### `press_dyn`

* Titre : Pression dynamique
* Description : 
* Type : nombre réel
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Pression dynamique en bars au débit nominal

#### `press_stat`

* Titre : Pression statique
* Description : 
* Type : nombre réel
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Pression statique en bars

#### `debit`

* Titre : Débit
* Description : 
* Type : nombre réel
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Valeur de débit mesuré exprimé en m3/h sous une pression de 1 bar

#### `volume`

* Titre : Volume
* Description : 
* Type : nombre entier
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Capacité volumique utile de la source d’eau en m3  
Si la source est inépuisable, ne pas renseigner ce champ \(cours d’eau ou plan d’eau pérenne\)

#### `disponible`

* Titre : Etat de disponibilité
* Description : 
* Type : booléen
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

0 ou 1. Valide à la date de dernière mise à disposition des données

#### `date_dispo`

* Titre : Date du dernier changement d'état de disponibilité
* Description : 
* Type : date
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Date de dernier changement d’état de disponibilité

#### `date_mes`

* Titre : Date de mise en service du PEI
* Description : 
* Type : date
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Date de mise en service du PEI

#### `date_maj`

* Titre : Date de dernière mise à jour des données
* Description : 
* Type : date
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Date de dernière mise à jour de la donnée au format aaaa-mm-jj

#### `date_ct`

* Titre : Date du dernier contrôle technique
* Description : 
* Type : date
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Date du dernier contrôle technique au format aaaa-mm-jj

#### `date_ro`

* Titre : Date de la dernière reconnaissance opérationnelle
* Description : 
* Type : date
* Exemple : 
* Valeur : **optionnelle**
* Taille : 

Date de la dernière reconnaissance opérationnelle au format aaaa-mm-jj

#### `prec`

* Titre : Précision de la mesure de localisation
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **optionnelle**
* Valeurs autorisées : 

Classes de précision : 01 \(0 à 1 m\), 05 \(de 1 à 5 m\), 10 \(de 5 à 10 m\), 99 \(plus de 10 m\), vide si inconnu

#### `x`

x en lambert 93 \(précision de 2 décimales\)

#### `y`

y en lambert 93 \(précision de 2 décimales\)

#### `lon`

longitude en degrés décimaux en WGS 84 \(précision de 8 décimales\)

#### `lat`

latitude en degrés décimaux en WGS 84 \(précision de 8 décimales\)

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Fichier gabarit à exporter
* Schéma de validation​

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à [scdl@opendatafrance.email](mailto:scdl@opendatafrance.email?subject=PEI)
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance​](https://git.opendatafrance.net/scdl/equipements/issues/new)



