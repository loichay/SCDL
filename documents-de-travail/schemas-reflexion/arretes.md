# Arrétés pour Panneau d'affichage

## 

**Version** 

n° : 0.2  
Date de création : février 2020 - Date de mise à jour : 7 juillet 2020   
Auteur : jm bourgogne - ODF    
Contributeurs : GFII 

## Contexte

Elaboration dans une document de travail externe &gt; [https://annuel2.framapad.org/p/fsj0gxc6py-9hod](https://annuel2.framapad.org/p/fsj0gxc6py-9hod)







### MODELE DE DONNEES  **COLL\_NOM**

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

  
**ARR\_TYPE**

* Titre : Type de l’arrêté
* Description : ? codification \(temporaire, permanent, spécifique selon le sujet \(RH, Occupation de l’espace publics, Sécurité, …\)
* Type : 
* Exemple : 
* Valeur : obligatoire

  
**ARR\_MATIERE\_CODE**

* Titre : Si cela est pertinent \(nomenclature ACTES, .. ?\) 
* Description : 
* Type : 
* Exemple :
* Valeur : 
* Motif : 

  
**ARR\_MATIERE\_NOM**

* Titre : Si cela est pertinent \(nomenclature ACTES, .. ?\) 
* Description : 
* Type : chaîne de caractères
* Exemple : 
* Valeur : obligatoire

  
**ARR\_OBJET**

* Titre : Objet de l’arrêté
* Description : Description de l'objet de l’arrêté
* Type : chaîne de caractères
* Exemple : 
* Valeur : obligatoire

  
**PREF\_ID ???**

* Titre : Identifiant de l'entité exerçant le contrôle de légalité
* Description : Cet identifiant dépend de l'entité concernée. Pour les préfectures, il est codé 'PREFNNN' sur 7 caractères. Pour les sous-préfectures, il est codé 'SPREFNNNM' sur 9 caractères. Pour les SGAR, il est codé 'SGARNNN' sur 7 caractères. 'NNN' correspond au numéro sur 3 caractères du département préfixé par '0' et inclant 'A' et 'B' pour les départements corses. 'M' correspond au numéro sur un chiffre de l'arrondissement.
* Type : chaîne de caractères
* Exemple : PREF038
* Valeur : optionnelle

  
**PREF\_DATE ???**

* Titre : Date d'enregistrement de la délibération auprès du contrôle de légalité
* Description : Date d'enregistrement de la délibération au contrôle de légalité au format AAAA-MM-JJ suivant la norme internationale ISO 8601. Ce champ ne peut être renseigné que si la délibération a effectivement été transmise et que sa date d'enregistrement est connue.
* Type : date
* Exemple : 2017-02-03
* Valeur : optionnelle

  
**CHAMPS SPECIFIQUES POUR PANNEAU D'AFFICHAGE**

* Titre : 
* Description : 
* Type : 
* Exemple : 
* Valeur : 

  
**ARR\_URL**

* Titre : Lien vers le document de l’arrêté
* Description : Si la collectivité dispose d'une version électronique de l’arrêté et le publie en ligne, ce lien correspond à l'adresse permettant de consulter ou de télécharger le document.
* Type : chaîne de caractères \(format uri\)
* Exemple : [https://data.maville.fr/deliberations/files/200417\_1.pdf](https://data.maville.fr/deliberations/files/200417_1.pdf)
* Valeur : optionnelle

  




