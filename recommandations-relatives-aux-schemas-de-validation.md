# Recommandations relatives aux schémas de validation

## Recommandations pour la création des schémas

Dès que le draft d'une spécification du Socle Commun des Données Locales est suffisamment mûr, son contenu est implémenté, ajusté si nécessaire, et stabilisé dans un schéma json au format [_Table Schema_](https://frictionlessdata.io/specs/table-schema/). Ce format a été défini dans le cadre du projet [Frictionless Data](https://frictionlessdata.io/) porté par [Open Knowledge International](https://okfn.org/). En s'y conformant, les schémas du SCDL peuvent être utilisés pour valider des données tabulaires.

## Recommandations pour la mise à jour des schémas

Quand une spécification est implémentée, son schéma est référencé sur le [GitLab d'OpenDataFrance](https://git.opendatafrance.net/scdl). Certains schémas sont hébergés dans des dépôts dédiés et d'autres dans des dépôts distants, notamment sur Github. Les éventuelles modifications à leur apporter sont alors directement opérées par leur\(s\) auteur\(s\).

Pour signaler un problème ou suggérer une amélioration, il est recommandé d'utiliser le système de tickets \('issues'\) de chaque dépôt.

## Recommandations pour le versionnage des schémas

Pour assurer le versionnage des schémas, et par conséquent celui de la documentation qui décrit chaque modèle de données, les règles de gestion s'appuient sur les principes de la [Gestion sémantique de version 2.0.0](https://semver.org/lang/fr/)

Étant donné un numéro de version **majeur.mineur.correctif**, il faut incrémenter :

* le numéro de version **majeur** quand il y a des changements non rétrocompatibles,
* le numéro de version **mineur** quand il y a des changements rétrocompatibles,
* le numéro de version de **correctif** quand il y a des corrections d’anomalies rétrocompatibles.

