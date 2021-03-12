---
description: Inventaire des bornes wifi déployées dans la commune ou l'interco.
---

# Bornes Wifi public

**Version** n° : 0.0.1   
Date de dernière mise à jour : juin 2020   
Auteur : jm bourgogne -ODF / AVICCA  
Contributeurs : participants du Hackathon T'Dat'Hack \(Tours et DataSud\)  


### **Contexte**

Dans le domaine des données Télécom, de nombreuses données sont produites par de nombreux acteurs, dans des formats et de logiques de partage et de publication aussi très différents.Si les données relatives aux infrastructures de services télécom de type GSM et Haut-Débit \(Fibre\) sont à la charge de l'état et des opérateurs, les données relatives aux Bornes Wifi sont sous le contrôle des collectivités territoriales qui déploient ces équipements \(et services\). Ce sont ces données qui sont l'objet de ce projet de standard.Les bornes d'accès wifi privé \(gratuites ou pas\), dans les hôtels, les bar/restaurants, les centres commerciaux, les gares, etc. ne sont pas concernées, à l'exception des services opérés dans le cadre d'une mission de service publics \(Transport en Commun\). A compléter/préciser   
A l'issue du Hackathon T.Dat'Hack du 31 janvier 2020, un draft de schéma a été proposé par les groupes de travail. C'est cette contribution qui a servi de base au format présenté :     [https://docs.google.com/spreadsheets/d/1GGyrnYYnS4V-PHvmzb9ozuCpcqxDbP\_cvH8qbH6tzvE/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1GGyrnYYnS4V-PHvmzb9ozuCpcqxDbP_cvH8qbH6tzvE/edit?usp=sharing)      


### Analyse de l'existant

Il existe quelques exemples de publication de données des bornes Wifi gratuit ici : 

* **Paris** : 

  liste des hotspot wifi : [https://www.data.gouv.fr/fr/datasets/liste-des-sites-des-hotspots-paris-wifi-prs/](https://www.data.gouv.fr/fr/datasets/liste-des-sites-des-hotspots-paris-wifi-prs/)

  et [https://opendata.paris.fr/explore/dataset/sites-disposant-du-service-paris-wi-fi/information/?disjunctive.cp&disjunctive.etat2](https://opendata.paris.fr/explore/dataset/sites-disposant-du-service-paris-wi-fi/information/?disjunctive.cp&disjunctive.etat2)

* **La Rochelle** : liste des hotspots Wifi : [https://opendata.larochelle.fr/dataset/telecommunication-hotspot-wifi-ville-de-la-rochelle/](https://opendata.larochelle.fr/dataset/telecommunication-hotspot-wifi-ville-de-la-rochelle/)
* **SICTIAM** : réseau national wifi : [https://catalogue.sictiam.fr/wifi-public-cigale/](https://catalogue.sictiam.fr/wifi-public-cigale/)

Par ailleurs, il existe des données dans OpenStreetMap : 

* [https://geodatamine.fr/data/internet\_access/-35738?format=csv&aspoint=true&metadata=true](https://geodatamine.fr/data/internet_access/-35738?format=csv&aspoint=true&metadata=true)



### **Modèle de données** 

Ce modèle de données fait partie et respecte les exigences du Socle Commun des Données Locales. Il repose sur les 23 champs suivants correspondant aux colonnes du fichier tabulaire.  


**COLL\_NOM**  
Titre : Nom de la collectivité  
Description : Nom officiel de la collectivité qui reçoit la borne wifi  
Type : chaîne de caractères  
Exemple : Ville de Poitiers  
Valeur : obligatoire  
  
**COLL\_SIRET \(ou INSEE\)**  
Titre : Code SIRET de la collectivité  
****Description : Identifiant du Système d'Identification du Répertoire des Etablissements \(SIRET\) de la collectivité qui reçoit la borne wifi, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.  
Type : chaîne de caractères  
Exemple : 21860194600013  
Valeur : obligatoire  
Motif : ^\d{14}$

**WIFI\_Id**  
Titre : Identifiant de la borne Wifi  
Description : Identifiant interne de l'équipement respectant le formalisme propre à la collectivité. Sa composition dépend des pratiques en vigueur au sein de chaque collectivité.   
Type : chaîne de caractères  
Exemple : 1DL15494  
Valeur : obligatoire

**WIFI\_Nom**  
Tire : nom de l'antenne  
Description : exprime le nom de l'antenne  
Type : alpha-numériqueExemple : Médiathèque  
Valeur : obligatoire

**WIFI\_SSID\_1**  
Tire : Nom 1 du réseau Wifi  
Description : exprime le nom du service wifi \(peut-être différent du nom de l'antenne\)  
Type : alpha-numérique  
Exemple : MEDIA\_INTERNE  
Valeur : obligatoire

**WIFI\_SSID\_2**  
Tire : Nom 2 du réseau Wifi  
Description : exprime le nom du service wifi \(peut-être différent du nom de l'antenne\)  
Type : alpha-numérique  
Exemple : MEDIA\_PUBLIC  
Valeur : facultatif

**WIFI\_SSID\_3**  
Titre : Nom 2 du réseau Wifi  
Description : exprime le nom du service wifi \(peut-être différent du nom de l'antenne\)  
Type : alpha-numérique  
Exemple : MEDIA\_DIR  
Valeur : facultatif

**WIFI\_LAT**  
Titre : Latitude de la borne Wifi  
Description : Coordonnée de latitude exprimée en WGS 84 permettant de localiser le panneau. Le signe de séparation entre les parties entière et décimale du nombre est le point.  
Type : nombre réel  
Exemple : 48.808989  
Valeur : obligatoire

**WIFI\_LONG**  
Titre : Longitude de la borne Wifi  
Description : Un ou plusieurs mot\(s\) clé\(s\) utilisé\(s\) pour décrire le jeu de données en minuscules non accentuées. S'il y en a plusieurs, le séparateur est le point-virgule.  
Type : nombre réel  
Exemple : 2.572875  
Valeur : obligatoire

**WIFI\_Proprietaire**  
Titre : Propriétaire de la borne  
Description : Nom du propriétaire de la borne  
Type : texte   
Exemple : Mairie  
Valeur : obligatoire  
  
**WIFI\_Modele**  
Titre : Modèle de la borne Wifi  
Description :   
Type :   
Exemple : DX6544  
Valeur : obligatoire

**WIFI\_InOut**  
Titre : intérieur / exterieur  
Description : Distinction sur l'emplacement géographique de la borne wifi \(intérieur / exterieur\)  
Type : liste fermée : intérieur/extérieur  
Exemple : intérieur  
Valeur : obligatoire  
  
**WIFI\_Puissance**  
Titre : Puissance de la borne Wifi  
Description : Exprime la puissance théorique de la borne WIFI + antennes  
Type : numérique exprimé en MW \(Unité\)  
Exemple : 100  
Valeur : obligatoire  
  
**WIFI\_Protocole**  
Titre : Protocole de la borne Wifi  
Description : Exprime la génération qui permet de déduire des informations comme le nombre de connexions possible, les fréquences  
Type : alphanumérique  
Exemple : 802.11 AX  
Valeur : facultatif  
  
**WIFI\_Direction**  
Titre : Direction d'émission de la borne  
Description : Exprime l'angle de couverture de la borne WIFIType : alphanumérique \(ou liste prédéterminée\)  
Exemple : 360  
Valeur : facultatif  
  
**WIFI\_Hauteur**  
Titre : Hauteur de l'antenne  
Description : Exprime la hauteur  
Type : numérique exprimé en mètre \(Unité\)  
Exemple : 12  
Valeur : facultatif 

**WIFI\_ID\_OSM**  
Titre : Identifiant dans la base OpenStreetMap  
Description : la borne Wifi peut avoir été enregistrée dans OSM. Ce champ permet donc de faire le lien avec le jeux de données WIfi : [https://wiki.openstreetmap.org/wiki/Key:wifi](https://wiki.openstreetmap.org/wiki/Key:wifi)  
L'outil GeoDataMine permet d'extraire les données relatives à ces équipements : [https://geodatamine.fr](https://geodatamine.fr)  
Type : alphanumérique   
Exemple : node/2349939399  
Valeur : factultatif  
  
**WIFI\_Date\_MES**  
Titre : Date de première mise en service de la borne  
Description : Nom du propriétaire de la borne  
Type : Date \(YY-MM-JJ\)  
Exemple : 19-21-31  
Valeur : facultatif  
  
**WIFI\_Debit\_Qualité**  
Qualité du débit de la borne  
Type : texte  
Exemple : HD  
Valeur : facultatif  
  
**WIFI\_Service\_Cout**  
Identification du coût de serviceConnexion payante ou gratuite  
Type : texte \(par défaut Gratuit\)  
Exemple : Gratuit  
Valeur : obligatoire  
  
**WIFI\_Frequence**  
Fréquence\(s\) utilisées pour la diffusion du réseau \(2,4 ou 5 Ghz\)   
Type : liste fermée  
Exemple : 5 Ghz  
Valeur : facultatif  
  
**WIFI\_\_MacAdress**  
MacAdress de la borne \(parfois nommée **adresse physique\)**  
Type : xx.xx.xx.xx.xx  
Exemple : 5E:FF:56:A2:AF:15  
Valeur : facultatif  
  
**WIFI\_Emission**  
Horaire d'émission de la borne  
Type : &lt; time &gt; ?  
Exemple : ?  
Valeur : facultatif  
  
**WIFI\_Connexion**  
Temps limite de connexion à la borne \(format osm\)?  
Valeur : facultatif

## Exemples

_Créer un exemple de fichier standardisé_

### Lien vers le validateur

\(validata\)



