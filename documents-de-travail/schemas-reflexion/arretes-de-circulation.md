---
description: >-
  Standardisation des données élaborés dans le cadre de la Fabrique de la
  Logistique
---

# Arrêtés de circulation

## Version 0.0.0

* Auteur : 
* Contributeurs : 
* Schéma créé le : 
* Schéma mis à jour le : 
* Site web : [https://opendatafrance.gitbook.io/fablog/](https://opendatafrance.gitbook.io/fablog/)

## Contexte

En cours d'élaboration sur le document de travail : 

{% embed url="https://annuel2.framapad.org/p/fablog-arretes-9ha8" %}

## Eléments de références

### Réglementaire

### Exemples et sources d'inspiration

### Analyse de l'existant

#### Arrêté provisoire pour autorisation de travaux

- exemple de la liste des travaux sur la voirie de Saint-Paul-les-Dax : [https://carte.st-paul-les-dax.fr/liste/](https://carte.st-paul-les-dax.fr/liste/)

Chaque chantier est associé à un arrêté \(format pdf\), dans lequel on trouve les données  suivantes :     \(ex. [https://carte.st-paul-les-dax.fr/wp-content/uploads/2018/12/0000600B.pdf\)](https://carte.st-paul-les-dax.fr/wp-content/uploads/2018/12/0000600B.pdf%29)  

 - url du texte de l'arrêté \(fichier .pdf\). Ex. : .../2018/12/0000600B.pdf      
- Nature de l'acte \(Code et Libellé\). Ex. 6   
- Libertés publiques et pouvoirs de Police      
- Référence interne. Ex. : 2018/PM/6/007093+Numéro de page : P1, P2, P3...      
- Date de prise de l'arrête. Ex. : 22/10/18      
- Date de publication \(affiché, publié, notifié, certifié exécutable\). Ex. : 23/10/18      
- Nom du Département. Ex: DEPARTEMENT DES LANDES      
- Nom de la Commune. Ex : VILLE DE SAINT-PAUL-LES-DAX      
- Type d'arrêté : ARRETE DE MAIRE      
- Sous-type de l'arrêté : ARRETE PROVISOIRE DE CIRCULATION      
\(parmi les différents considérants, la demande de l'opérateur. Ex.:Vu la demande en date du xx/xx/xx formulée par l'entreprise XXX, adresse de l'entreprise, chargée de procéder aux travaux de traversée de route par fonçage horizontal, et de fouille sous trottoir pour raccordement électrique, au 345 rue de Loustalot à Saint-Paul-les-Dax\).      
- date de début. Ex. : 22 octobre 2019      
- date de fin. Ex. : 26 octobre 2019       
- objet. Ex. : travaux \(pas de description hormi celle présentée dans le considérant \(travaux de traversée de route par fonçage horizontal, etc.,\)      
- type de travaux. Ex1 : branchement électricité / Ex2 : Travaux sur réseau Free / Ex3 : Branchement gaz / Ex4 : Construction de Batiment/Chantier      
- Identification de l'opérateur. Ex. : Entreprise Sud Réseau      
- type de localisation. Ex : Exacte/Approximative     
 - adresse du point principal des travaux. Ex1 : 345 rue de Loustalot, \(sous-entendu Saint-Paul-les-Dax\) / Ex2 : au droit du chantier sis Rue du 14 juillet et Avenue Pierre Benoit / Ex3 :     - \(dont on peut déduire la géolocalisation GPS Lat., Long. Ex. 43.727127227549, -1.0762739181519\)     
- impact. Ex. La circulation sera provisoirement ralentie au droit du chantier + limitation de vitesse + circulation + restriction de stationnement \(ce qui peut être résumé en 3 types : stationnement interdit/vitesse limitée/circulation sur chaussée rétrécie\)     
- Longueur de impact en amont de la voie.  Ex. : 100m     
- Longueur de impact en aval de la voie.  Ex. : 100m   

#### Ressources sur les Arrétés \(et RAA\)

[https://drive.google.com/open?id=1qmYEjWqayAzY2IoRMXT7a0lbc\_yYJWJC](https://drive.google.com/open?id=1qmYEjWqayAzY2IoRMXT7a0lbc_yYJWJC)

* Exemple d'arrêtés diffusés en open data : - [https://opendata.paris-saclay.com/explore/dataset/esp\_arretes\_lin\_diffusion/table/?location=11,48.68919,2.2025](https://opendata.paris-saclay.com/explore/dataset/esp_arretes_lin_diffusion/table/?location=11,48.68919,2.2025)
* voir futur projet BAC \(Base des données des Arrétés de Circulation\) par le CR IDF avec MCLedger et Logicities     

### **Modèle de données** 

Ce modèle de données fait partie et respecte les exigences du Socle Commun des Données Locales. Il repose sur les x champs suivants correspondant aux colonnes du fichier tabulaire.  


### Typologie

#### Typologie générale

Individuel, ...

#### Typologie plus fine

  
  
**COLL\_NOM**

* Titre : Nom de la collectivité
* Description : Nom officiel de la collectivité délibérante.
* Type : chaîne de caractères
* Exemple : Ville de Poitiers
* Valeur : obligatoire

  
**COLL\_SIRET**

* Titre : Code SIRET de la collectivité
* Description : Identifiant du Système d'Identification du Répertoire des Etablissements \(SIRET\) de la collectivité qui a adopté la délibération, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : 21860194600013
* Valeur : obligatoire
* Motif : ^\d{14}$

  
**ARR\_ID**

* Titre : Identifiant de l’arrêté
* Description : Identifiant interne de l’arrêté respectant le formalisme propre à la collectivité. Sa composition dépend des pratiques en vigueur au sein de chaque collectivité. Cet identifiant peut être utilisé dans d'autres documents faisant référence à cette décision/arrêté.
* Type : chaîne de caractères
* Exemple : 1DL15494
* Valeur : obligatoire

  
**ARR\_DATE**

* Titre : Date d'adoption de l’arrêté
* Description : Date à laquelle l’arrêté a été adopté par la collectivité au format AAAA-MM-JJ suivant la norme internationale ISO 8601.
* Type : date
* Exemple : 2017-10-15
* Valeur : obligatoire

**Selon la codification normalisée d'un acte :**  

        **ARR\_DOMAINE**

        **ARR\_TYPE**

       **ARR\_MATIERE**

* Titre : Si cela est pertinent \(nomenclature ACTES, .. ?\) 
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : obligatoire

  
**ARR\_OBJET**

* Titre : Objet de l’arrêté
* Description : Description de l'objet de l’arrêté
* Type : chaîne de caractères
* Exemple : travaux de voirie au carrefour du Bd St-Antoine et la rue de la libeté
* Valeur : obligatoire

  
**CHAMPS SPECIFIQUES POUR AUTORISATION DE TRAVAUX** 

Début

Fin

Impacts

Opérateur

Emprise géographique \(données géographiques : point ou zone\)

  
**ARR\_URL**

* Titre : Lien vers le document de l’arrêté
* Description : Si la collectivité dispose d'une version électronique de l’arrêté et le publie en ligne, ce lien correspond à l'adresse permettant de consulter ou de télécharger le document.
* Type : chaîne de caractères \(format uri\)
* Exemple : url
* Valeur : optionnelle



