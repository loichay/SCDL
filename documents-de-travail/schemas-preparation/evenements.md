---
description: Proposition de schéma pour publier des informations sur les évènements locaux
---

# Evénements locaux

## Contexte <a id="contexte"></a>

* [Schéma 'Event' sur schema.org](https://schema.org/Event)
* [Structure des données d'OpenAgenda](https://openagenda.zendesk.com/hc/fr/articles/115002665145-Structure-des-donn%C3%A9es)
* Modèle des données de type « événement » dans l'[ontologie DATAtourisme v1.0](https://framagit.org/datatourisme/ontology/tree/master/Documentation)
* Données événementielles issues d'InfoLocale et [publiées sur DataGouv](https://www.data.gouv.fr/fr/organizations/infolocale/)

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les  **`15 champs`** suivants correspondant aux colonnes du fichier tabulaire.

| Nom | type | Description | Exemple | Propriétés |
| :--- | :--- | :--- | :--- | :--- |
| E\_title  | chaîne de caractères | le titre de l'évènement | Exposition "Arts et énergies renouvelables" | Valeur obligatoire, Motif : `^\d{1-256}$` |
| E\_desc | chaîne de caractères |  la description de l'évènement | Le Centre culturel Château Palmer accueille "Arts & énergies renouvelables", une exposition de Kamel Ghabte. | Valeur obligatoire, Motif : `^\d{1-256}$` |
| E\_URL | URL | l'identifiant de publication de l'évènement | [https://www.cenon.fr/a-la-une/evenements/ex](https://www.cenon.fr/a-la-une/evenements/exposition-arts-energies-renouvelables) | Valeur obligatoire, Motif : `^\d{1-256}$` |
|  E\_img | URL | une illustration de l'évènement | [https://cibul.com/image.jpg](https://cibul.s3.amazonaws.com/a4ff8c1566664ab08abe81376aa354ba.full.image.jpg) | Valeur optionnelle, Motif : `^\d{1-256}$` |
| E\_status | chaîne de caractères | le statut de l'évènement | [EventScheduled](https://schema.org/EventScheduled) | Valeur optionnelle, Valeurs autorisées : `Eventprogramme, EventAnnule, EventDeplace, EventReprogramme` |
| E\_location | chaîne de caractères | la localisation de l'évènement | Centre culturel Château Palmer | Valeur obligatoire, Motif : ^\[a-zA-Z0-9-\'\s\d\u00C0-\u00FF\]+$ |
| E\_organizer | chaîne de caractères | l'organisateur de l'évènement | Ville de Cenon | Valeur obligatoire, Motif : `^\d{1-256}$` |
| E\_startDate | [Date](https://fr.wikipedia.org/wiki/ISO_8601) | la date de démarrage de l'évènement | 2019-11-13T09:00Z | Valeur obligatoire, Motif : `^\d{1-256}$` |
| E\_endDate | [Date](https://fr.wikipedia.org/wiki/ISO_8601) | la date de clôture de l'évènement | 2019-11-15T12:30Z | Valeur obligatoire, Motif : `^\d{1-256}$` |
| E\_duration | [Duration](https://fr.wikipedia.org/wiki/ISO_8601) | la durée de l'évènement | 36:00:00 | Valeur optionnel, Motif : `^\d{1-256}$` |
| E\_isFree | booléen | la caractère gratuit ou payant de l'évènement | oui | Valeur obligatoire, Valeurs autorisées : oui, non |
| E\_tarif | URL | un lien vers les modalités d'inscription | [http://www.culture-cenon.fr/](http://www.culture-cenon.fr/) | Valeur facultative, Motif : `^\d{1-256}$` |
| E\_type | chaîne de caractères | typologie d'évènement | exposition | Valeur obligatoire, valeurs autorisées \(voir la liste des types d'évènements [schema.org](https://schema.org/Event) |
| E\_accessible | chaîne de caractères | le caractère accessible de l'évènement | mi | Valeur facultatif, valeur autorisées : mi \(handicap moteur, hi \(handicap auditif\), vi \(handicap visuel\), pi \(handicap psychique\), sl \(langue des signes\) |

### Discussion 

Les sources d'inspiration de cette proposition de schéma sont détaillées [ici](https://mypads.framapad.org/mypads/?/mypads/group/rhizome-data-w42m4k7vf/pad/view/agenda-bh2x2r79g)

Le choix a été fait de préfixer les intitulés des champs par un E majuscule suivi d'un \_ et de les écrire en anglais.

#### E\_location

On peut notamment vouloir préciser de manière plus fine la localisation des évènements en proposant plusieurs colonnes pour décrire de manière granulaire cette information : 

* Département : numéro du département
* Commune : libellé de la commune
* Code INSEE : code Insee de la commune
* Code Postal : code postal de la commune indiqué par l'organisme
* Lieu de l'événement : adresse et/ou nom du lieu \(salle, lieu remarquable\) où se déroule l'événement
* Coordonnées GPS : géo-localisation de l'événement \(WGS84\)

#### E\_type

Le type d'évènement décrit peut être défini en utilisant la liste des sous-type d'évènement disponibles dans l'ontologie [schema.org](https://schema.org/Event) ou par une autre liste d'autorité.

#### E\_accessible

Pour décrire le caractère accessible de l'évènement et faire la liste des publics qui peuvent y assister la liste établie par le projet OpenAgenda a été choisie

**Accessibilité - handicap** \[liste\] 

* mi = handicap moteur, motor impairment
* hi = handicap auditif, hearing impairment
* vi = handicap visuel, visual impairment
* pi = handicap psychique, psychic impairment
* sl = langue des signes, sign language

