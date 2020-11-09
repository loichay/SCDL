---
description: >-
  Information de description de la composition de l'offre de restauration
  collective
---

# Menus Collectifs

## Contexte <a id="contexte"></a>

Cette initiative vide à standardiser la publication des jeux de données relatifs aux offres de restauration collective. Elle concerne la restauration scolaire mais peut s'étendre aux offres de restauration pour les personnes âgées, les restaurants administratifs ou les centres de loisirs. Elle s'articule autour des notions de menus, des plats qui les composent et des denrées utilisées pour les fabriquer. Afin de permettre de décrire plus en détails les plats un schéma additionnel dédié est proposé [ici](https://opendatafrance.gitbook.io/scdl/documents-de-travail/schema-en-discussion/plats-des-menus).

En utilisant ce niveau de granularité, les organismes publics qui souhaitent uniquement publier leurs menus peuvent le faire et ceux qui peuvent fournir plus d'informations disposent des champs de description nécessaires.

En décrivant les denrées qui constituent les plats proposés dans les menus de restauration collective il sera possible de relier ces données à celle d'open food facts ou de calculer le bilan carbone des plats fabriqués.

### Cadre réglementaire

La loi impose actuellement un certain pourcentage de produits bio et labellisés dans l'offre de restauration collective : 50% dont 20% issu de l'agriculture biologique \(standard européen ou français ?\)    - 50% de produits durables ou sous signes d'origine et de qualité \(dont des produits bio\) dans la restauration collective publique à partir du 1er janvier 2022 :[https://www.legifrance.gouv.fr/affichTexte.do?cidTexte=JORFTEXT000037547946&categorieLien=id\#JORFARTI000037547961](https://www.legifrance.gouv.fr/affichTexte.do?cidTexte=JORFTEXT000037547946&categorieLien=id#JORFARTI000037547961)

### Quels usages ?

* en tant que parent je veux savoir ce que mange mon enfant à la cantine :     
  * afin de coordonner avec les repas à la maison
  * afin de connaître la part du local    
  * afin de connaître la quantité de protéines animales    
  * afin de vérifier l'adéquation avec la réglementation en matière de pourcentage d'aliments issus de l'agriculture biologique    
  * afin de connaître les types d'allergènes contenus dans les repas    
  * afin de calculer le bilan carbone des repas    
  * afin de limiter le gaspillage alimentaire en mettant en relation avec les quantités de nourriture non consommées
* en tant qu'élu je veux savoir comment sont composés les menus scolaires :    
  * afin d'évaluer la part du bio dans l'alimentation \(volume et pourcentage\)   
  *  afin d'évaluer la part de production labellisée dans l'alimentation \(légalement : la part du bio est estimée en coût et pas en volume\)    
  * afin d'évaluer la part de la production locale dans les menus    
  * afin d'évaluer l'impact de ma politique publique en matière de restauration collective \(anticiper l'impact carbone, le soutien aux filières locales, la tarification\)    
  * afin de connaître le nombre de repas par type de population \(voir publics plus haut\)
* en tant que producteur je veux savoir comment sont composés les menus scolaires :     
  * afin de proposer des produits à la restauration collective en fonction des besoins    
  * afin de favoriser le regroupement avec d'autres producteurs 
* en tant qu'organisme de labellisation je souhaite avoir les informations qui me permettront de vérifier si la cantine à labelliser entre dans les critères.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). 

Il est composé de **`10 champs`** obligatoires et **`10 champs`** optionnels suivants correspondant aux colonnes du fichier tabulaire.  
Il sera complété d'un schéma sur la composition des plats auquel les données pourront être reliées via l'utilisation du champ codePlat.

### Composition des menus

#### collectiviteNom

Titre : Nom de la collectivité  
Description : Nom officiel de la collectivité.  
Type : chaîne de caractères  
Exemple : Commune de Bordeaux  
Valeur : obligatoire

#### collectiviteSiret

**Titre** : Code SIRET de la collectivité  
**Description** : Identifiant du Système d'Identification du Répertoire des Établissements \(SIRET\) de la collectivité qui a adopté la délibération, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.  
**Type** : chaîne de caractères  
**Exemple** : 21330063500017  
**Valeur** : obligatoire  
**Motif** : ^\d{14}$

#### etablissementNom

**Titre** : Nom de l'établissement ou entreprise qui a produit le repas servi  
**Description** : Nom officiel de l'établissement.  
**Type** : chaîne de caractères  
**Exemple** : Syndicat intercommunale à vocation unique de Bordeaux-Mérignac  
**Valeur** : optionnelle

#### etablissementSiret

**Titre** : Code SIRET de l'établissement ou entreprise qui a produit le repas servi  
**Description** : Identifiant du Système d'Identification du Répertoire des Établissements \(SIRET\) de la collectivité qui a produit le repas, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.  
**Type** : chaîne de caractères  
**Exemple** : 25330618700035   
**Valeur** : optionnelle  
**Motif** : ^\d{14}$

#### restaurantNom

**Titre** : Nom du restaurant où le repas est servi  
**Description** : Nom officiel de l'établissement.  
**Type** : chaîne de caractères  
**Exemple** : École élémentaire Flornoy  
**Valeur** : obligatoire

#### restaurantId

**Titre** : Identifiant du restaurant où le repas est servi.  
**Description** : Identifiant du restaurant dans lequel a été servi le menu soit en utilisant le code SIREN soit le numéro d'identification fourni par l'Éducation Nationale pour les établissements scolaires soit un identifiant interne. Le champ restaurantidType permet de caractériser le type de système d'identification auquel cet identifiant fait référence.  
**Type** : chaîne de caractères  
**Exemple** : "25330618700017"   
**Valeur** : optionnelle

#### restaurantIdType

**Titre** : Type d'identifiant utilisé pour caractérisé un restaurant collectif.  
**Description** : Afin de permettre d'identifier de manière unique chaque restaurant, plusieurs systèmes d'identification peuvent être utilisé en l'absence d'une attribution systématique d'un code SIRET. Pour les établissements scolaires le numéro UID délivré par l'Éducation Nationale \(EN\) peut être utilisé. Dans le cas des autres \(identifiant interne par exemple\), la valeur autre doit être sélectionnée. Enfin en l'absence d'identifiant la valeur "Sans" peut-être sélectionnée.  
**Type** : chaîne de caractères  
**Exemple** : "Siret"   
**Valeur** : optionnelle  
**Valeurs autorisées** : Siret, EN, Autre, Sans

#### restaurantType

**Titre** : Type de client auquel le menu est proposé  
**Description** : Permet de préciser le type d'établissement destinataire du menu proposé parmi les valeurs disponibles  \(Crèche, École maternelle, École élémentaire, Foyer de personnes âgées, Collège, Lycée, Administration locale, RPA, EHPAD, Repas à domicile\)  
**Exemple** : Collège  
**Valeur** : obligatoire  
Valeurs autorisées : Crèche, École maternelle, École élémentaire, Foyer de personnes âgées, Collège, Lycée, Administration locale, RPA, EHPAD, Repas à domicile

#### restaurantConvive

**Titre** : Type de convive auquel le menu est proposé  
**Description** : Permet de préciser le type de personnes destinataires du menu proposé parmi les valeurs disponibles  \(bébé, scolaire, adulte, sénior …\)  
**Exemple** : Collège  
**Valeur** : obligatoire  
Valeurs autorisées : bébé, scolaire, adulte, sénior

#### restaurantNombreConvive

**Titre** : Nombre de convives destinataires du menu proposé  
**Description** : Ce champ permet de renseigner le nombre \(approximatif\) de convives qui vont manger le menu proposé dans le restaurant.  
**Exemple** : 130  
**Valeur** : optionnelle

#### menuDate

**Titre** : Date du menu  
**Description** : Date de du jour où le menu est servi dans l'établissement au format AAAA-MM-JJ suivant la norme internationale ISO 8601.  
**Type** : date  
**Exemple** : 2017-10-15  
**Valeur** : obligatoire

#### menuTypeRepas

**Titre** : type du repas servi  
**Description** : Permet de spécifier le type du repas parmi les valeurs possible \(déjeuner, goûter, dîner, collation, pique-nique\)  
**Type** : string  
**Exemple** : déjeuner  
**Valeur** : obligatoire  
**Valeurs autorisées:** déjeuner, goûter, dîner, collation, pique-nique

#### menuTypePlat

**Titre** : Type de plat servi  
**Description** : Le type de plat correspond à un des éléments disponibles dans la liste \(entrée, plat principal, garniture, dessert, produit laitier, collation matinale, goûter, pain\).  
**Type** : chaîne de caractères  
**Exemple** : Entrée  
**Valeur** : obligatoire.   
**Liste de valeurs autorisées** : entrée, plat principal, garniture, dessert, produit laitier, collation matinale, goûter, pain.

#### menuNomPlat

**Titre** : Nom du plat servi  
**Description** : Le nom du plat permet de désigner dans la limite de 140 caractères maximum les éléments composant le menu.  
**Type** : chaîne de caractères  
**Exemple** : Cordon bleu  
**Valeur** : obligatoire

#### menuCodePLat

**Titre** : Code attribué au plat  
**Description** : Code unique par plat dans la base de données  
**Type** : chaîne de caractères  
**Exemple** : 0001  
**Valeur** : optionnelle

#### menuSiqoPlat

**Titre** : Indication de signe officiel de la qualité et de la qualité  
**Description** : Des cahiers des charges permettent de reconnaître les produits qui bénéficient d’un signe officiel d'identification de la qualité et de l’origine \(SIQO\) : Agriculture biologique, Appellation d'origine protégée/contrôlée, Indication géographique protégée, Spécialité traditionnelle garantie, Label rouge.  
**Type** : chaîne de caractères  
**Exemple** : Agriculture biologique  
**Valeur** : optionnelle  
**Valeurs autorisées** : "Agriculture biologique", "Appellation d'origine protégée/contrôlée", "Indication géographique protégée", "Spécialité traditionnelle garantie", "Label rouge".

#### menuLabelPlat

**Titre** : Indication de labels complémentaires liés à des approvisionnements locaux ou à des marques de fabrication  
**Description** : Des labels complémentaires permettent d'identifier la production locale ou des marques associées à un territoire ou à une démarche de qualité. La saisie dans ce champ est libre. A titre d'exemple OpenFoodFacts propose un liste des labels existant dans sa base de données : [https://fr.openfoodfacts.org/labels](https://fr.openfoodfacts.org/labels)  
**Type** : chaîne de caractères  
**Exemple** : Ferme des Jarouilles  
**Valeur** : optionnelle

#### menuAllergenePlat

**Titre** : Nom des allergènes présents dans le plat  
**Description** : Énumération des éventuels allergènes \(séparés par des virgules\) présents dans le plat proposé. Actuellement la distinction n'est pas faite entre les allergènes présents du fait de la recette \(fiche technique\) ou sous forme de traces \(lieu de production\).  
**Type** : chaîne de caractères  
**Exemple** : Fruits à coques  
**Valeur** : optionnelle  
**Valeurs autorisées** : "Céréales contenant du gluten", "Crustacés", "Oeufs", "Poissons", "Arachides", "Soja", "Lait", "Fruits à coques", "Céleri", "Moutarde", "Graines de sésame", "Anhydride sulfureux et sulfites", "Lupin", "Mollusques"

#### menuPrecisionPlat

**Titre** : Précision \(régime ou thématique\) associée au plat ou à l'ensemble des plats d'un menu  
**Description** : Lors d'évènements \(semaine du goût, repas de noël, etc.\) des menus spéciaux peuvent être proposés. Ce champ peut également permettre d'indiquer si un plat est destiné à un régime particulier \(sans viande, végétarien, etc.\)  
**Type** : chaîne de caractères  
**Exemple** : semaine asiatique  
**Valeur** : optionnelle

#### menuModificationDate

Titre : Date de dernière modification de l'enregistrement  
Description : Lors de la publication ou d'éventuelles modifications ce champ d'horodatage permet d'indiquer la date de dernière modification de la donnée présente dans le fichier.  
Type : datetime  
Exemple : 2020-05-11T14:08:32Z  
Valeur : obligatoire

#### menuModificationActivite

Titre : Nature de l'activité ayant entraîné une mise à jour de la donnée  
Description : Afin de renseigner les usagers de la donnée, il est possible de préciser dans ce champ la raison de la mise à jour effectuée.  
Type : chaîne de caractères  
Exemple : 2020-05-11T14:08:32Z  
Valeur : optionnelle



## Voir aussi <a id="voir-aussi"></a>

**Applications de production ou de réutilisation des données de la restauration collective**

* Open Food Facts : [https://openfoodfacts.org](https://openfoodfacts.org)
* QuiDitMiam : [https://quiditmiam.fr](https://quiditmiam.fr/)
* Yadesfrites : [http://www.sylvinfo.com/ya-d-frites/](http://www.sylvinfo.com/ya-d-frites/)
* Datameal : [http://www.datameal.fr](http://www.datameal.fr/)

### **Exemples**

* [Département des Hautes-Pyrénées](https://opendata.ha-py.fr/explore/dataset/departementdeshautespyrenees_menus_cantines_colleges_publics/table/?disjunctive.rep_nom_col&sort=-rep_jour)
* [Ville de la Rochelle](https://opendata.larochelle.fr/dataset/restauration-enfance-menus-des-restaurants-scolaires-allergenes/)
* [Ville de Rennes](https://data.rennesmetropole.fr/explore/dataset/menus-cantines/information/)
* [Ville de Montpellier](https://data.montpellier3m.fr/dataset/menu-des-cantines-de-montpellier)
* [Ville de Dignes-les-Bains](https://www.data.gouv.fr/fr/datasets/menus-des-cantines-scolaires-a-digne-les-bains/)
* [Ville d'Angers](https://www.data.gouv.fr/fr/datasets/menus-restaurations-scolaires-angers/)
* Ville de Toulouse
  * [menus](https://data.toulouse-metropole.fr/explore/dataset/menus/table/)
  * [plats](https://data.toulouse-metropole.fr/explore/dataset/plats-extrait-de-datameal)
  * [produits](https://data.toulouse-metropole.fr/explore/dataset/denrees-extrait-de-datameal)
* [Ville de Saint-Paul-les-Dax](https://www.data.gouv.fr/fr/datasets/menus-de-cantines-des-ecoles/)

