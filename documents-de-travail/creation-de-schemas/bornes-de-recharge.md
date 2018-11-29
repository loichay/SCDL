# Infrastructures de Recharge de Véhicules Electriques\*

## Version 1.1.0 du 10/09/2018 <a id="version-0-0-0-du-jj-mm-aaaa"></a>

{% page-ref page="bornes-de-recharge.md" %}

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

#### `n_amenageur`

* Titre : Nom de l'aménageur
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

le nom de l'aménageur, c'est à dire de l'entité publique ou privée propriétaire des infrastructures, par exemple \(entreprise\) ABC ou SDE xx ;

#### `n_operateur`

* Titre : Nom de l'opérateur
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

le nom de l'opérateur qui opère le réseau d'infrastructure \(l'aménageur ou un tiers auquel a été confié la responsabilité par délégation\) ;

#### `n_enseigne`

* Titre : Nom commercial du réseau
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

#### `id_station`

* Titre : Identifiant de la station
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

l'identifiant de la station délivré selon les modalités définies à l'article 10 du décret n° 2017-26 du 12 janvier 2017, par exemple FR _123_ P456\* AB789 ;

#### `n_station`

* Titre : Nom de la station
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

le nom de la station, par exemple parking X ou centre commercial Z ;

#### `ad_station`

* Titre : Adresse de la station
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

l'adresse complète \(a minima, les noms de la voie ou du lieu-dit et de la commune\) de la station, par exemple 3, rue de la Gare, Belmont ;

#### `code_insee`

* Titre : Code INSEE
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

le code INSEE de la commune d'implantation ;

#### `Xlongitude`

* Titre : Longitude
* Description : 
* Type : nombre décimal
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

la longitude en degrés décimaux \(point comme séparateur décimal, avec au moins 4 chiffres après le point décimal\) de la localisation de la station exprimée dans le système de coordonnées WGS84, par exemple 1.452323 ;

#### `Ylatitude`

* Titre : Latitude
* Description : 
* Type : nombre décimal
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

la latitude en degrés décimaux \(point comme séparateur décimal, avec au moins 4 chiffres après le point décimal\) de la localisation de la station exprimée le système de coordonnées WGS84, par exemple 46.59698 ;

#### `nbre_pdc`

* Titre : Nombre de points de recharge
* Description : 
* Type : nombre entier
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

le nombre de points de recharge sur la station ;

#### `id_pdc`

* Titre : Identifiant du point de recharge
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

l'identifiant du point de recharge délivré selon les modalités définies à l'article 10 du décret n° 2017-26 du 12 janvier 2017, par exemple FR _123_ E456\* BCGT5 ;

#### `puiss_max`

* Titre : Puissance maximale
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

la puissance maximale délivrée à chaque point de recharge, exprimée en kW, en fonction du contrat d'abonnement de puissance de la station et du type de connecteur ;

#### `type_prise`

* Titre : Types de prises ou de connecteurs
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

les types de prises ou de connecteurs disponibles sur chaque point de charge, par exemple T2-Combo2-CHAdeMO, séparés par des tirets \(-\) ;

#### `acces_recharge`

* Titre : Modalités d'accès à la recharge
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

modalités d'accès à la recharge \(gratuit, payant\) -- les détails sont précisés dans le champ « observations » ;

#### `accessibilité`

* Titre : Accessibilité
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

amplitude d'ouverture de la station, par exemple 24/24 7/7 jours -- les détails sont précisés dans le champ « observations » ;

#### `observations`

* Titre : Observations
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

champ destiné à préciser les modalités d'accès à la recharge, l'accessibilité, le tarif, les horaires d'ouverture, …

#### `date_maj`

* Titre : Date de mise à jour
* Description : 
* Type : date
* Exemple : 
* Valeur : **obligatoire**
* Taille : 

date de mise à jour des données au format AAAA/MM/JJ, par exemple 2016/10/31

Dans le but de constituer un répertoire national des IRVE, ouvert et accessible à tous, les collectivités porteuses d'un projet d'installation d'IRVE doivent, au fur et à mesure de la mise en service des stations, transmettre systématiquement, sous forme de tableau mis à jour, à la plateforme ouverte des données publiques \([www.data.gouv.fr](https://www.data.gouv.fr/)\) statiques relatives aux caractéristiques des installations comprenant :

* `n_amenageur` : le nom de l'aménageur, c'est à dire de l'entité publique ou privée propriétaire des infrastructures, par exemple _\(entreprise\) ABC_ ou _SDE xx_ ;
* `n_operateur` : le nom de l'opérateur qui opère le réseau d'infrastructure \(l'aménageur ou un tiers auquel a été confié la responsabilité par délégation\) ;
* `n_enseigne` : le nom commercial du réseau ;
* `id_station` : l'identifiant de la station délivré selon les modalités définies à l'article 10 du décret n° 2017-26 du 12 janvier 2017, par exemple _FR\* 123\* P456\* AB789_ ;
* `n_station` : le nom de la station, par exemple _parking X_ ou _centre commercial Z_ ;
* `ad_station` : l'adresse complète \(a minima, les noms de la voie ou du lieu-dit et de la commune\) de la station, par exemple _3, rue de la Gare, Belmont_ ;
* `code_insee` : le code INSEE de la commune d'implantation ;
* `Xlongitude` : la longitude en degrés décimaux \(point comme séparateur décimal, avec au moins 4 chiffres après le point décimal\) de la localisation de la station exprimée dans le système de coordonnées WGS84, par exemple _1.452323_ ;
* `Ylatitude`: la latitude en degrés décimaux \(point comme séparateur décimal, avec au moins 4 chiffres après le point décimal\) de la localisation de la station exprimée le système de coordonnées WGS84, par exemple _46.59698_ ;
* `nbre_pdc` : le nombre de points de recharge sur la station ;

Et, sur autant de lignes que nécessaires ayant en dénominateur commun les données ci-dessus, les caractéristiques de chacun des points de recharge :

* `id_pdc` : l'identifiant du point de recharge délivré selon les modalités définies à l'article 10 du décret n° 2017-26 du 12 janvier 2017, par exemple _FR\* 123\* E456\* BCGT5_ ;
* `puiss_max` : la puissance maximale délivrée à chaque point de recharge, exprimée en kW, en fonction du contrat d'abonnement de puissance de la station et du type de connecteur ;
* `type_prise` : les types de prises ou de connecteurs disponibles sur chaque point de charge, par exemple _T2-Combo2-CHAdeMO_, séparés par des tirets \(`-`\) ;
* `acces_recharge` : modalités d'accès à la recharge \(_gratuit_, _payant_\) -- les détails sont précisés dans le champ « observations » ;
* `accessibilité` : amplitude d'ouverture de la station, par exemple _24/24 7/7 jours_ -- les détails sont précisés dans le champ « observations » ;
* `observations` : champ destiné à préciser les modalités d'accès à la recharge, l'accessibilité, le tarif, les horaires d'ouverture, …
* `date_maj` : date de mise à jour des données au format `AAAA/MM/JJ`, par exemple _2016/10/31_

Le fichier doit être encodé en **UTF-8** et utiliser le **point-virgule** comme séparateur de colonnes. Aucune valeur ne peut contenir le caractère « point-virgule » choisi comme séparateur. L'**en-tête de colonne** sur la première ligne est obligatoire. Tous les champs sont obligatoires ; si la donnée n'est pas disponible, la colonne doit être présente et vide.

**Nom du fichier** : `IRVE_nom_AAAAMMJJ.csv` avec `nom` étant le nom de l'aménageur ou le nom commercial du réseau, par exemple _IRVE\_SDExx\_20161013.csv_ ou _IRVE\_reseaucharge\_20161013.csv_.

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Exemple de fichier
* [Schéma de validation​](https://github.com/etalab/schema.data.gouv.fr/blob/master/irve/schema.json)
* Documentation générée à partir du schéma​

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à scdl@opendatafrance.email
* ouvrir un ticket sur le dépôt Github de la mission Etalab

