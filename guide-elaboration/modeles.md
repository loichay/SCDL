# Modèles de données élémentaires courantes

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

#### `xxx_DATE` <a id="delibdate"></a>

* Description : Date au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : 2017-10-15
* Motif : 

#### Date avec heure

* Description : Date au format aaaa-mm-jjThh:mi:ssZZZZZZ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601). On considérera que ZZZZZZ \(+ou- décalage horaire GMT\), est par défaut +01:00 en France et qu'il est inutile de le préciser dans les formats. 
* Type : date et heure format étendu
* Exemple : 1997−07−16T19:20:00
* Motif : 

#### Dates avec début et fin

* Description : Date au format aaaa-mm-jjThh:mi/hh:mi suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601). Ce format s'applique pour un créneau horaire dans la même journée, sans les secondes. Pour une extension de ces conditions, voir la norme ISO8601.
* Type : date et heure format étendu
* Exemple : 1997−07−16T08:30/17:30
* Motif : 

### 3. Champs Adresse

Le champ Adresse est composés de 3 blocs. Il a été retenu ce format en raison des usages ou formats les plus couramment rencontrés et de la facilité de production. La codification de la poste \(AFNOR NF Z 10-011\) peut être réduite à ce format  par agrégation, par exemple : 

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

* Titre : premier élément de l'adresse
* Description : 
* Type : chaîne de caractères
* Exemple : 11 Allée des Roses
* Motif : 

#### XXX\_ADD\_VOIE2

* Titre : deuxième élément de l'adresse
* Description : 
* Type : chaîne de caractères
* Exemple : BP 77
* Motif : 

#### XXX\_ADD\_CP

* A conserver ?
* Description : Elément de l'adresse qui désigne le Code Postal 

   de la commune 

* Type : chaîne de caractères NN séparation par blanc NNNN \(le type "numérique" n'aurait pas été compatible avec les départements de Corse 2A et 2B\)
* Exemple : 59 370
* Motif : 

#### XXX\_ADD\_COMMUNE

* Titre : Commune
* Description : Elément de l'adresse qui désigne le nom de la commune 
* Type : chaîne de caractères
* Exemple : 59 370 Le Plessis-Trévise
* Motif : ... /`^[A-Za-z\s\-\u00C0-\u00FF]+$`

### 4. Champs Géolocalisation

Le choix retenu est d'indiquer une localisation compatible avec les systèmes GPS \(\)

#### XXX\_LAT

* Titre : Latitude
* Description : Coordonnée de latitude exprimée en [WGS 84](https://fr.wikipedia.org/wiki/WGS_84) permettant de localiser l'équipement. Le signe de séparation entre les parties entière et décimale du nombre est le point. Précision : 6 décimales max.
* Type : nombre réel
* Exemple : 48.808989
* Motif : 

#### `XXX_LONG` <a id="equiplong"></a>

* Titre : Longitude
* Description : Coordonnée de latitude exprimée en [WGS 84](https://fr.wikipedia.org/wiki/WGS_84) permettant de localiser l'équipement. Le signe de séparation entre les parties entière et décimale du nombre est le point. Précision : 6 décimales max.
* Type : nombre réel
* Exemple : 2.572875
* Motif : 

Lorsque le jeu de donnée décide de compléter par le système d'adresse francais \(ISO..\)

#### GEOLOC\_X

#### GEOLOC\_Y

### 5. Champs Montant

Sauf indications contraires, justifiées et clairement indiquées, les montants sont exprimés en euro. Le séparateur de décimale est le point \("."\). 

On rappelle que ce choix est fait car la virgule \(","\) est utilisée dans de nombreux formats, par exemple .csv, comme le séparateur de champs. 

#### XXX\_Montant 

* Description : Montant exprimé en euros et calculé. Le signe de séparation entre les parties entière et décimale du nombre est le point.
* Type : nombre réel
* Exemple : 47800.20
* Motif : 

### 6. Champ Description

La description est un champ alpha-numérique libre. Nous n'avons pas retenu la distinction entre un libellé court ou un libellé long. Le libellé retenu est plutôt long, avec 256 caractères. 

#### XXX\_Description

* Description : champ d'information 
* Type : alphanumérique, sur 256 caractères \(on plus ?\)
* Exemple : _Ce champ contient une information dans un format alphanumérique_
* Motif : 





