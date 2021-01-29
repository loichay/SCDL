# Modèles

Cette page a comme objectif de décrire des modules de données élémentaires standards. Il sera ainsi plus facile de décrire les données essentielles, courantes et générales, contenues dans un jeu de données. Cela garantira l'interopérabilité et la cohérence de traitement de tels champs.  

Les données spécifiques à une activité ne sont pas décrites de façon générique ici mais l'on tâchera de se rapprocher des principes et de la syntaxe présentés ici. 

### 1. Champs Identitiant d'une collectivité

#### 1.1 Nom de la collectivité

Ce champ est nécessaire pour rendre plus explicite la descrption de la collectivité. Plus clair qu'un numéro \(SIRET ou INSEE\), il ne peut cependant pas servir de clé d'interopérabilité en raison du manqe de normalisation du nom d'une collectivité. Par exemple, nous pouvons trouver plusieurs noms compréhensibles et utilisés pour Cesson-Sévigné, CESSON SEVIGNE, Marie de Cesson Sévigné, Ville de Cesson-Sévigné, etc.

#### COLL\_NOM

> * Titre : Nom de la collectivité
> *  Description : Nom officiel de la collectivité.
> * Type : chaîne de caractères
> * Exemple : Commune de Bordeaux
> * Valeur : **obligatoire**
> * Motif :

#### 1.2 Identifiant de la collectivité

On peut identifier une collectivité par son numéro SIRET \(lorsqu'il y a une incidence juridique ou budgétaire\) ou par son numéro INSEE.

#### COLL\_SIRET

> * Titre : code SIRET de la collectivité
> * Description : cette zone permet de déterminer le code SIRET de la collectivité ou de l'établissement public concerné, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant. \([http://xml.insee.fr/schema/siret.html\#SIRET\_stype](http://xml.insee.fr/schema/siret.html#SIRET_stype)\)
> * Type : integer
> * Exemple : 22192720500197
> * Valeur : **obligatoire**
> * Motif : ^\[0-9\]{14}$

#### COLL\_INSEE

> * Titre : code INSEE de la collectivité
> * Description : cette zone permet de déterminer le code INSEE de la collectivité ou de l'établissement public concerné 
> * Type : integer
> * Exemple : 
> * Valeur : 
> * Motif :

### 2. Champs Date

#### Date

#### Date avec heure

#### Dates avec début et fin

### 3. Champs Adresse

Le champ Adresse est composés de 3 blocs. Il a été retenu ce format en raison des usages ou formats les plus courament rencontrés et de la facilité de production. La codification de la poste \(AFNOR NF Z 10-011\) peut être réduite à ce format  par agrégation, par exemple : 

```text
Complément d'adresse : 
Numéro dans la voie : 11
Type de voie : Allée
Nom de la voie : des Roses
Lieu-dit : 
Boite Postale : BP 77 
CP : 59 370
Commune : Mons en Baroeul
Pays : France
```

devient : 

```text
11 Allée des Roses
BP 77
59370 MONS en BAROEUL
```

#### XXX\_ADD\_VOIE1

#### XXX\_ADD\_VOIE2

#### XXX\_ADD\_COMMUNE

### 4. Champs Géolocalisation

Le choix retenu est d'indiquer une localisation compatible avec les systèmes GPS \(\)

#### GEOLOC\_LAT

#### GEOLOC\_LONG

Lorsque le jeu de donnée décide de compléter par le système d'adresse francais \(ISO..\)

#### GEOLOC\_X

#### GEOLOC\_Y

### 5. Champs Montant

Sauf indications contraires, justifiées et clairement indiquées, les montants sont exprimés en KEuro \(1 000 euro = 1 keuro\). Le séparateur de décimale est le point \("."\). 

On rappelle que ce choix est fait car la virgule \(","\) est utilisée dans de nombreux formats, par exemple .csv, comme le séparateur de champs. 

#### Montant 

### 6. Champ Description

La description est un champ alpha-numérique libre. Nous n'avons pas retenu la distinction entre un libellé court ou un libellé long. Le libellé retenu est plutôt long, avec nnn caractères. 

#### XXX\_LIB 





