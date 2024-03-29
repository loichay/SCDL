---
description: Proposition de schéma pour publier des informations sur les évènements locaux
---

# Evénements locaux

## Contexte <a href="contexte" id="contexte"></a>

* [Schéma 'Event' sur schema.org](https://schema.org/Event)
* [Structure des données d'OpenAgenda](https://openagenda.zendesk.com/hc/fr/articles/115002665145-Structure-des-donn%C3%A9es)
* Modèle des données de type « événement » dans l'[ontologie DATAtourisme v1.0](https://framagit.org/datatourisme/ontology/tree/master/Documentation)
* Données événementielles issues d'InfoLocale et [publiées sur DataGouv](https://www.data.gouv.fr/fr/organizations/infolocale/)

## Modèle de données <a href="modele-de-donnees" id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](broken-reference). Il repose sur les**`12 champs`** obligatoires et **`3 champs`** optionnels suivants correspondant aux colonnes du fichier tabulaire.

**AGD\_TITRE**

* Titre : le nom de l'évènement
* Description : le nom affiché de l'évènement dans l'agenda local
* Type : chaîne de caractères
* Exemple : Exposition "Arts et énergies renouvelables"
* Valeur : **obligatoire**
* Motif : `^\d{1-256}$` &#x20;

**AGD\_DESC**

* Titre : description de l'évènement
* Description : description de l'évènement permettant de savoir ce qui est porposé au visiteur
* Type : chaîne de caractères
* Exemple : Le Centre culturel Château Palmer accueille "Arts & énergies renouvelables", une exposition de Kamel Ghabte.
* Valeur : **obligatoire**
* Motif : `^\d{1-256}$` &#x20;

**AGD\_TYPE**

* Titre : typologie d'évènement
* Description : catégorisation permettant d'indiquer le type d'évènement. Utile pour fournir des filtres aux agrégateurs d'évènements locaux
* Type : chaîne de caractère
* Exemple : Exposition
* Valeur : **obligatoire**&#x20;
* valeur autorisées : liste à définir&#x20;

**AGD\_URL**

* Titre : adresse de publication de l'évènement
* Description : lors de sa publication sur l'agenda local, chaque évènement dispose d'une adresse web qui peut servir d'identifiant pour cette ressource
* Type : URL
* Exemple : [https://openagenda.com/ville-de-cenon/events/exposition-arts-and-energies-renouvelables](https://openagenda.com/ville-de-cenon/events/exposition-arts-and-energies-renouvelables/action)
* Valeur : **obligatoire**
* Motif : débute par http ou https suivi de :// + chaine de caractères

**AGD\_ADDR**

* Titre : l'adresse du lieu de l'évènement
* Description : adresse à laquelle se déroule l'évènement comprenant le nom et le numéro de la voirie, le code postal et le nom de la commune
* Type : chaîne de caractère
* Exemple : Chateau Palmer, 33150 Cenon
* Valeur : **obligatoire**
* Motif : regex d'adresse postale

**AGD\_CODE-INSEE**

* Titre : le code insee de la commune sur laquelle se déroule l'évènement
* Description : le code INSEE permet de désambiguiser l'identification du lieu de l'évènement et sa faciliter sa localisation par les machines&#x20;
* Type : numérique
* Exemple : 33119
* Valeur : **obligatoire**
* Motif : 5 chiffres

**AGD\_COORDO**

* Titre : Les coordonnées de géolocalisation de l'évènement
* Description : les coordonnées de géolocalisation fournissent un moyen simple de référencement de l'évènement sur une carte
* Type : numérique
* Exemple : 44.86155,-0.52614
* Valeur : **obligatoire**
* Motif : un ou deux chiffres suivi d'un point puis de 5 décimales max pour la latitude une virgule et la même chose pour la longitude

**AGD\_ORG**

* Titre : Le nom de l'organisateur de l'évènement
* Description : l'identification de la structure organisatrice de l'évènement permet de faciliter la mise en place de filtre par organisateur sur les site d'agrégation d'évènements
* Type : chaîne de caractère
* Exemple : Rocher de Palmer
* Valeur : **obligatoire**
* Motif : lettre et chiffres jusqu'à 256 caractères

**AGD\_START**

* Titre : date de début de l'évènement
* Description : ce champ permet d'indiquer a minima la date de démarrage de l'évènement mais peut également être utilisée pour indiquer l'heure de début. L'information doit être saisie conformément à la norme ISO 8601&#x20;
* Type : Date
* Exemple : 2019-11-26 ou 2019-11-26T12:56:00Z
* Valeur : **obligatoire**
* Motif : date

**AGD\_END**

* Titre : date de fin de l'évènement
* Description : ce champ permet d'indiquer a minima la date de clôture de l'évènement mais peut également être utilisée pour indiquer l'heure de fin. L'information doit être saisie conformément à la norme ISO 8601
* type : Date
* Exemple : 2019-11-26 ou 2019-11-26T12:56:00Z
* Valeur : **obligatoire**
* Motif : date

**AGD\_GRATUIT**

* Titre : Le caractère gratuit de l'évènement
* Description : permet de renseigner directement sur le caractère gratuit ou non de l'évènement
* Type : booléen
* Exemple : oui
* Valeur : **obligatoire**
* Motif : oui ou non

**AGD\_STATUS**

* Titre : le statut courant de l'évènement
* Description : ce champ permet de maintenir la présence d'un évènement dans l'agenda même s'il a été annulé, reprogrammé ou déplacé ou de confirmer sa programmation
* Type : chaîne de caractère
* Exemple : programmé
* Valeur : **obligatoire**
* valeurs autorisés : programmé, annulé, reprogrammé, reporté

**AGD\_HOR**

* Titre : les horaires d'ouverture de l'évènement
* Description : ce champ permet de renseigner les différentes plage horaires auxquelles est accessible l'évènement. On propose ici d'adopter la syntaxe mise en place par Open Street Map [https://wiki.openstreetmap.org/wiki/FR:Key:opening\_hours/specification](https://wiki.openstreetmap.org/wiki/FR:Key:opening\_hours/specification)
* Type : Time
* Exemple : Mo 09:00-17:00; Tu 04:15-10:00; We 05:15-10:45; Th 11:15-18:45; Fr 10:00-11:30,14:30-18:00; Sa 06:45-10:45,14:15-18:15
* Valeur : **optionnelle**
* Motif : 2 lettres 1 heure avec 2x2 chiffres séparés par un : chaque jour séparé par un point virgule. Jusqu'à 7 jours&#x20;

**AGD\_ACCESSIBLE**

* Titre : les différents types d’accessibilité de l'évènement
* Description : ce champ permet de renseigner les personnes en situation de handicap sur le caractère accessible de l'évènement
* Type : chaine de caractère
* Exemple : mi:oui;hi:non, vi:non, pi:non;sl:non
* Valeur : **optionnelle à tendance obligatoire**
* valeurs autorisées : mi (handicap moteur, hi (handicap auditif), vi (handicap visuel), pi (handicap psychique), sl (langue des signes)

**AGD\_IMG**

* Titre : lien vers une image illustrant l'évènement
* Description : adresse url d'une image associée à l'évènement
* Type : URL
* Exemple : [https://cibul.s3.amazonaws.com/0c28a62bdcce437eb3134c6074590f35.full.image.jpg](https://cibul.s3.amazonaws.com/0c28a62bdcce437eb3134c6074590f35.full.image.jpg)
* Valeur : **optionnelle**
* Motif : URL

**AGD\_TARIF**

* Titre : information vers les modalités d'inscription
* Description : si l'évènement est soumis à réservation ou inscription, il est utile de fournir un lien permettant à l'utilisateur de renseigner sa participation et de prendre connaissance de la tarification éventuellement associée
* Type : chaîne de caractère
* Exemple : [https://lerocherdepalmer.fr/artistes/chaton/](https://lerocherdepalmer.fr/artistes/chaton/)
* Valeur : **optionnelle**
* Motif : url

****

### Discussion&#x20;

Les sources d'inspiration de cette proposition de schéma sont détaillées [ici](https://mypads.framapad.org/mypads/?/mypads/group/rhizome-data-w42m4k7vf/pad/view/agenda-bh2x2r79g)

#### E\_location

On peut notamment vouloir préciser de manière plus fine la localisation des évènements en proposant plusieurs colonnes pour décrire de manière granulaire cette information :&#x20;

* Département : numéro du département
* Commune : libellé de la commune
* Code INSEE : code Insee de la commune
* Code Postal : code postal de la commune indiqué par l'organisme
* Lieu de l'événement : adresse et/ou nom du lieu (salle, lieu remarquable) où se déroule l'événement
* Coordonnées GPS : géo-localisation de l'événement (WGS84)

#### E\_type

Le type d'évènement décrit peut être défini en utilisant la liste des sous-type d'évènement disponibles dans l'ontologie [schema.org](https://schema.org/Event) ou par une autre liste d'autorité.

#### E\_accessible

Pour décrire le caractère accessible de l'évènement et faire la liste des publics qui peuvent y assister la liste établie par le projet OpenAgenda a été choisie

**Accessibilité - handicap** \[liste]&#x20;

* mi = handicap moteur, motor impairment
* hi = handicap auditif, hearing impairment
* vi = handicap visuel, visual impairment
* pi = handicap psychique, psychic impairment
* sl = langue des signes, sign language
