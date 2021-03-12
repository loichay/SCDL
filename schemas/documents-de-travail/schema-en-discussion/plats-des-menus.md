---
description: >-
  Description des plats proposés par des collectivités locales dans le cadre de
  l'offre de restauration collective. Il permet de préciser les modalités de
  fabrication des plats.
---

# Plats des menus

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](). 

Il est composé de **`14 champs`** obligatoires et **`9 champs`** optionnels suivants correspondant aux colonnes du fichier tabulaire.  
Il est complété d'un schéma sur la [composition des menus ](https://opendatafrance.gitbook.io/scdl/documents-de-travail/schema-en-discussion/menus)auquel les données pourront être reliées via l'utilisation du champ platCode.

#### platCode

**Titre** : Code du plat servi  
**Description** : Code unique par plat éventuellement issu d'une base de données de gestion. Ce code permet de faire le lien avec l'identifiant des plats \(menuCodePlat\) dans le schéma des menus.  
**Exemple** : 46657345  
**Valeur** : obligatoire

#### platNom

**Titre** : Nom du plat servi  
**Description** : Le nom du plat dans la limite de 140 caractères maximum.  
**Exemple** : Cordon bleu  
**Valeur** : obligatoire

#### platOGM

**Titre** : Présence d'OGM dans le plat  
**Description** : Indique la présence d'OGM dans le plat à partir des informations issues du détail des produits et ingrédients ayant permis de le confectionner.  
**Exemple** : non  
**Valeur** : obligatoire  
**Liste de valeurs autorisées: oui, non**

#### platIonisation

**Titre** : Indication de l'utilisation du procédé d'ionisation  
**Description** : Indique l'utilisation du procédé d'ionisation consistant à exposer des aliments à des rayonnements ionisants afin de réduire le nombre de micro-organismes qu'ils contiennent.  
**Exemple** : non  
**Valeur** : obligatoire  
**Liste de valeurs autorisées: oui, non**

#### platNutri-score

**Titre** : Indiquation de l'indice nutritif du plat  
**Description** : Indique la valeur nutritive du plat en fonction des valeur de l'indicateur nutriscore.  
**Exemple** : C  
**Valeur** : obligatoire  
**Liste de valeurs autorisées: A, B, C, D, E**

#### platAdditif

**Titre** : Liste des additifs alimentaires présents dans le plat  
**Description** : Les additifs alimentaires sont des produits ajoutés aux denrées alimentaires dans le but d'en améliorer la conservation, le goût et l'aspect. Les éventuels additifs peuvent être listés dans ce champ en les séparant par une virgule.  
**Exemple** : Silicate de sodium  
**Valeur** : obligatoire

#### platProduitNom

**Titre** : Produit entrant dans la composition du plat  
**Description** : Afin de décrire le contenu d'un plat, la liste des produits entrant dans sa composition permet d'identifier les apports nutritifs, les éventuels allergènes et les aspects diététiques associés. Ces éléments sont généralement issus de la fiche recette.  
**Exemple** : champignon  
**Valeur** : obligatoire

#### platProduitCode

**Titre** : Code attribué au produit  
**Description** : Code unique par plat éventuellement issu d'une base de données de gestion. Ce code permet de faire le lien avec l'identifiant des plats \(menuCodePlat\) dans le schéma des menus.  
**Exemple** : 46657345  
**Valeur** : optionnelle

#### platProduitFournisseurNom

**Titre** : Nom du fournisseur du produit  
**Description** : Producteur du produit entrant dans la composition du plat ou fourni comme matière brute.  
**Exemple** : Salger  
**Valeur** : obligatoire

#### platProduitFournisseurSiret

**Titre** : Code SIRET de l'entreprise qui a fourni le produit  
**Description** : Identifiant du Système d'Identification du Répertoire des Etablissements \(SIRET\) de l'entreprise qui a fourni le produit, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.  
**Exemple** : 25330618700035  
**Valeur** : obligatoire

#### platProduitCategorie

**Titre** : Catégorie du produit  
**Description** : Catégorisation du produit entrant dans la composition du plat.  
**Exemple** : huile  
**Valeur** : obligatoire

#### platProduitPrix

**Titre** : Coût de revient du produit  
**Description** : Le prix de revient pour la structure de restauration collective est utilisé pour composer les plats et les menus en combinaison avec les impératifs d'équilibre nutritionnel.  
**Exemple** : 10 €/kg  
**Valeur** : obligatoire

#### platProduitConditionnementType

**Titre** : Type de conditionnement du produit  
**Description** : Le type de conditionnement du produit dépend du lieu de fabrication, il s'agit ici de renseigner le mode de conditionnement du produit ou de l'ingrédient lors de sa réception sur le lieu du service ou de la transformation \(seau, boîte, carton, bouteille\).  
**Exemple** : seau de 5l  
**Valeur** : obligatoire

#### platIngredientNom

**Titre** : Ingrédient entrant dans la composition du plat  
**Description** : Afin de décrire le contenu d'un plat la liste des ingrédients entrant dans sa composition permet d'identifier les apports nutritifs, les éventuels allergènes et les aspects diététiques associés. Ces éléments sont généralement issus de la fiche recette.  
**Exemple** : crème fraîche  
**Valeur** : optionnelle

#### platIngredientCode

**Titre** : Code attribué à l'ingrédient  
**Description** : Code unique par ingrédient éventuellement issu d'une base de données.  
**Exemple** : 674487  
**Valeur** : optionnelle

#### platIngredientFournisseurNom

**Titre** : Nom du fournisseur de l'ingrédient  
**Description** : Producteur de l'ingrédient entrant dans la composition du plat ou fourni comme matière brute.  
**Exemple** : Ferme des Jarouilles  
**Valeur** : optionnelle

#### platIngredientFournisseurSiret

**Titre** : Code SIRET de l'entreprise qui a produit l'ingrédient  
**Description** : Identifiant du Système d'Identification du Répertoire des Etablissements \(SIRET\) de l'entreprise qui a fourni l'ingrédient, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.  
**Exemple** : 46657345  
**Valeur** : optionnelle

#### platIngredientCategorie

**Titre** : Catégorie de l'ingrédient  
**Description** : Catégorisation de l'ingrédient entrant dans la composition du plat.  
**Exemple** : crème  
**Valeur** : optionnelle

#### platIngredientPrix

**Titre** : Coût de revient de l'ingrédient  
**Description** : Le prix de revient pour la structure de restauration collective est utilisé pour composer les plats et les menus en combinaison avec les impératifs d'équilibre nutritionnel.  
**Exemple** : 13,34 €/l  
**Valeur** : optionnelle

#### platIngredientConditionnementType

**Titre** : Type de conditionnement de l'ingrédient  
**Description** : Le type de conditionnement de l'ingrédient dépend du lieu de fabrication, il s'agit ici de renseigner le mode de conditionnement du produit ou de l'ingrédient lors de sa réception sur le lieu du service ou de la transformation \(seau, boîte, carton, bouteille\).  
**Exemple** : seau de 5l  
**Valeur** : optionnelle

#### platIngredientNutrimentNom

**Titre** : Nom des nutriments présents dans l'ingrédient  
**Description** : Les ingrédients composant les produits contiennent différents nutriments. Cette information est notamment utilisée pour composer des menus équilibrés du point de vue diététique.  
**Exemple** : glucide 10g/l, lipide 100 g/l  
**Valeur** : optionnelle

#### collectiviteNom

Titre : Nom de la collectivité  
Description : Nom officiel de la collectivité.  
Type : chaîne de caractères  
Exemple : Commune de Bordeaux  
Valeur : obligatoire

#### collectiviteSiret

**Titre** : Code SIRET de la collectivité  
**Description** : Identifiant du Système d'Identification du Répertoire des Etablissements \(SIRET\) de la collectivité qui a adopté la délibération, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.  
**Type** : chaîne de caractères  
**Exemple** : 21330063500017  
**Valeur** : obligatoire  
**Motif** : ^\d{14}$

