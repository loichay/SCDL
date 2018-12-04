---
description: >-
  Draft de la spécification du modèle de données relatif aux points d'eau
  incendie (PEI) d'une collectivité
---

# Points d'eau incendie

## Version 1.0.0 du 12/06/2018 <a id="version-0-0-0-du-jj-mm-aaaa"></a>

## Contexte <a id="contexte"></a>

En France, les Points d’Eau Incendie \(PEI\) - également appelés [hydrants](https://fr.wikipedia.org/wiki/Hydrant) \(borne incendie, poteau incendie et autres points d'eau\) - sont recensés par les [Services Départementaux d'Incendie et de Secours](https://fr.wikipedia.org/wiki/Service_d%C3%A9partemental_d%27incendie_et_de_secours) \(SDIS\), les collectivités territoriales et/ou les délégataires de service public. La gestion de ces données est effectuée à un échelon départemental. Les "bases de données hydrants" constituent un enjeu majeur pour la gestion des risques incendie et doivent être partagées entre départements limitrophes.

En 2018, dans le cadre de son [groupe de travail "Open Data"](http://www.afigeo.asso.fr/pole-entreprise/groupe-dinteret-ogc/2117-modele-minimal-hydrants-3.html), l'Association Française pour l'Information GEOgraphique \(AFIGEO\) a défini un [modèle minimal de données relatif aux points d'eau incendie](http://www.afigeo.asso.fr/images/BD-Entreprises/OGC_-_Open_Data/Modele_minimal_donn%C3%A9es_PEI.pdf) en se référant aux textes réglementaires suivants :

* [Article R2225-1 du Code général des collectivités territoriales](https://www.legifrance.gouv.fr/affichCodeArticle.do?cidTexte=LEGITEXT000006070633&idArticle=LEGIARTI000030299532) \(CGCT\) créé par le [Décret n° 2015-235 du 27 février 2015 relatif à la défense extérieure contre l'incendie - Article 2](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000030296571)
* [Le référentiel national de la défense extérieure contre l'incendie fixé par l'arrêté du 15 décembre 2015](https://www.interieur.gouv.fr/Le-ministere/Securite-civile/Documentation-technique/La-defense-exterieure-contre-l-incendie)

La spécification SCDL du modèle de données relatif aux points d'eau incendie \(PEI\) a donc été élaborée à partir du modèle minimal de données proposé par l'AFIGEO. Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

Dès qu'elle se justifie, la [correspondance avec les attributs d'OpenStreetMap relatifs aux hydrants](https://wiki.openstreetmap.org/wiki/FR:Tag:emergency%3Dfire_hydrant#Correspondance_avec_le_mod.C3.A8le_PEI_de_l.27Afigeo) est notée en référence dans les champs concernés.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`28 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `insee`

Numéro INSEE de la commune sur laquelle le PEI est situé. Dans le cas d’un plan d’eau et des cours d’eau plusieurs points d’aspiration peuvent y être associés. On prend alors en compte la localisation du point d’aspiration pour identifier la commune.

#### `id_sdis`

Identifiant interne du PEI pour le SDIS

#### `id_gestion`

Identifiant interne du PEI pour le gestionnaire

#### `nom_gest`

Nom du gestionnaire responsable de distribution

#### `ref_terr`

Numéro ou référence du point d’eau visible sur le terrain

#### `type_pei`

Type de point d’eau incendie. 

Valeurs possibles : PI, BI, PA, CI Signification : PI \(Poteau d’Incendie\), BI \(Prise d’eau sous pression, notamment bouche d’incendie\), PA \(Point d’aspiration aménagé \(point de puisage…\)\), CI \(Citerne aérienne ou enterrée\) Cette typologie est issue du règlement national \(p. 39\) . Si ce dernier évoluait, cette typologie évoluerait en conséquence.

#### `type_rd`

Précision sur le type de point d’eau incendie défini dans le règlement départemental DECI Typologie utilisée au niveau local pour caractériser le type de point d’eau

#### `diam_pei`

Diamètre intérieur du poteau ou de la bouche

Valeurs possibles : 80, 100, 150

Norme européenne : Poteau Incendie NF EN 14384 \(Février 2006\) NF S 61 213 CN \(Avril 2007\) \(valeurs possibles : 80, 100 ou 150 ; 80 = 1 prise de 65 - 100 = 2 prises de diamètre 65, 1 prise de diamètre 100 - 150 = 2 prises de diamètre 100\) Bouche Incendie NF EN 14339 \(Février 2006\) NF S 61 211 CN \(Avril 2007\) \(valeur possible : 1 prise de diamètre 100\).

#### `diam_cana`

Diamètre de la canalisation exprimé en mm pour les PI et BI

#### `source_pei`

Source du point d’eau  
Valeurs possibles : citerne, plan\_eau, piscine, puits, cours\_eau, reseau\_aep, reseau\_irrigation

#### `statut`

Statut du point d’eau  
Valeurs possibles : public, prive  
Le statut du point d’eau est décrit dans le règlement national \(p. 43\)

#### `nom_etab`

Dans le cas d’un statut privé, nom de l’établissement propriétaire

#### `situation`

Situation du PEI  
Adresse ou informations permettant de faciliter la localisation du point d’eau sur le terrain.

#### `press_dyn`

Pression dynamique en bars au débit nominal

#### `press_stat`

Pression statique en bars

#### `debit`

Valeur de débit mesuré exprimé en m3/h sous une pression de 1 bar

#### `volume`

Capacité volumique utile de la source d’eau en m3  
Si la source est inépuisable, ne pas renseigner ce champ \(cours d’eau ou plan d’eau pérenne\)

#### `disponible`

0 ou 1. Valide à la date de dernière mise à disposition des données

#### `date_dispo`

Date de dernier changement d’état de disponibilité

#### `date_mes`

Date de mise en service du PEI

#### `date_maj`

Date de dernière mise à jour de la donnée au format aaaa-mm-jj

#### `date_ct`

Date du dernier contrôle technique au format aaaa-mm-jj

#### `date_ro`

Date de la dernière reconnaissance opérationnelle au format aaaa-mm-jj

#### `prec`

Classes de précision :

* 01 \(0 à 1 m\)
* 05 \(de 1 à 5 m\)
* 10 \(de 5 à 10 m\)
* 99 \(plus de 10 m\)
* vide si inconnu

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

* Exemple de fichier
* Schéma de validation​
* Documentation générée à partir du schéma​​

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à scdl@opendatafrance.email
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance​](https://git.opendatafrance.net/scdl/equipements/issues/new)



