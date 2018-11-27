---
description: >-
  Draft de la spécification du modèle de données relatif aux points d'eau
  incendie (PEI)
---

# Points d'eau incendie

## Version 1.0.0 du 12/06/2018 <a id="version-0-0-0-du-jj-mm-aaaa"></a>

{% page-ref page="points-deau-incendie.md" %}

## Contexte <a id="contexte"></a>

En France, les Points d’Eau Incendie \(PEI\) - également appelés [hydrants](https://fr.wikipedia.org/wiki/Hydrant) \(borne incendie, poteau incendie et point d’aspiration\) - sont recensés par les [Services Départementaux d'Incendie et de Secours](https://fr.wikipedia.org/wiki/Service_d%C3%A9partemental_d%27incendie_et_de_secours) \(SDIS\), les collectivités territoriales et/ou les délégataires de service public. La gestion de ces données est effectuée à un échelon départemental. Les "bases de données hydrants" constituent un enjeu majeur pour la gestion des risques incendie et doivent être partagées entre départements limitrophes.

En 2018, dans le cadre de son [groupe de travail "Open Data"](http://www.afigeo.asso.fr/pole-entreprise/groupe-dinteret-ogc/2117-modele-minimal-hydrants-3.html), l'Association Française pour l'Information GEOgraphique \(AFIGEO\) a défini un [Modèle minimal de données relatif aux points d'eau incendie](http://www.afigeo.asso.fr/images/BD-Entreprises/OGC_-_Open_Data/Modele_minimal_donn%C3%A9es_PEI.pdf) en se référant aux textes réglementaires suivants :

* [Article R2225-1 du Code général des collectivités territoriales](https://www.legifrance.gouv.fr/affichCodeArticle.do?cidTexte=LEGITEXT000006070633&idArticle=LEGIARTI000030299532) \(CGCT\) créé par le [Décret n° 2015-235 du 27 février 2015 relatif à la défense extérieure contre l'incendie - Article 2](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000030296571)
* [Le référentiel national de la défense extérieure contre l'incendie fixé par l'arrêté du 15 décembre 2015](https://www.interieur.gouv.fr/Le-ministere/Securite-civile/Documentation-technique/La-defense-exterieure-contre-l-incendie)

La spécification SCDL du modèle de données relatif aux points d'eau incendie \(PEI\) a donc été élaborée à partir du modèle minimal de données proposé par l'AFIGEO. Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir de cette même source.

Dès qu'elle se justifie, la [correspondance avec les attributs d'OpenStreetMap relatifs aux hydrants](https://wiki.openstreetmap.org/wiki/FR:Tag:emergency%3Dfire_hydrant#Correspondance_avec_le_mod.C3.A8le_PEI_de_l.27Afigeo) est notée en référence dans les champs concernés.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`28 champs`** suivants correspondant aux colonnes du fichier tabulaire.

#### `insee`



#### `id_sdis`



#### `id_gestion`



#### `nom_gest`



#### `ref_terr`



#### `type_pei`



#### `type_rd`



#### `diam_pei`



#### `diam_cana`



#### `source_pei`



#### `statut`



#### `nom_etab`



#### `situation`



#### `press_dyn`



#### `press_stat`



#### `debit`



#### `volume`



#### `disponible`



#### `date_dispo`



#### `date_mes`



#### `date_maj`



#### `date_ct`



#### `date_ro`



#### `prec`



#### `x`



#### `y`



#### `lon`



#### `lat`



## Voir aussi <a id="voir-aussi"></a>





