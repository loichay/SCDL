---
description: >-
  Draft de la spécification du modèle de données relatif aux marchés publics
  attribués par une collectivité
---

# Marchés publics

## Version 1.0.1 du 16/05/2018 <a id="version-0-0-0-du-jj-mm-aaaa"></a>

{% hint style="info" %}
Lien permanent vers le [document actuellement publié](http://www.opendatafrance.net/SCDL_Marches_Publics) sur GDrive
{% endhint %}

{% page-ref page="marches-publics.md" %}

## Contexte <a id="contexte"></a>

Au plus tard le 1er octobre 2018, les collectivités locales, doivent offrir sur leur profil d'acheteur, un accès libre, direct et complet aux données essentielles des marchés publics répondant à un besoin dont la valeur est égale ou supérieure à 25 000€ HT. La nature et les modalités de diffusion de ces données essentielles ont été fixées par voie réglementaire.

La spécification SCDL du modèle de données relatif aux marchés publics attribués par une collectivité locale est adossée au format réglementaire pour la publication des données essentielles dans la commande publique, mais elle transpose ce format arborescent \(fichier xml ou json\) dans un format tabulaire \(fichier csv\) pour que toutes les collectivités, en particulier celles qui ne sont pas équipées d'outils adaptés, soient néanmoins en capacité de produire, ouvrir et diffuser leurs données essentielles de marché.

Cette spécification a été élaborée à partir des sources suivantes :

* **Documents de cadrage juridique**

  * [Article 107 du Décret n° 2016-360 du 25 mars 2016 relatif aux marchés publics](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000032295952)
  * [Arrêté du 14 avril 2017 relatif aux données essentielles dans la commande publique](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000034492587)
  * [Arrêté du 14 avril 2017 relatif aux fonctionnalités et exigences minimales des profils d'acheteurs](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000034492557)
  * [Arrêté du 27 juillet 2018 modifiant l'arrêté du 14 avril 2017 relatif aux données essentielles dans la commande publique](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000037282994)

* **Document de cadrage technique**
  * [Format réglementaire pour la publication des données essentielles des marchés publics français sur le dépôt Github de la mission Etalab](https://github.com/etalab/format-commande-publique)​

Si nécessaire, elle sera mise à jour, adaptée et consolidée à partir des mêmes sources.

## Modèle de données <a id="modele-de-donnees"></a>

Ce modèle de données fait partie et respecte les exigences du [Socle Commun des Données Locales](../../recommandations-relatives-aux-jeux-de-donnees.md). Il repose sur les **`27 champs`** suivants correspondant aux colonnes du fichier tabulaire.

{% hint style="warning" %}
**Avertissement !** Dans cette spécification, la transposition du format réglementaire \(passage d'un format arborescent à un format tabulaire\) implique de prêter une attention toute particulière aux éventuelles incidences \(champs à valeurs variables qui nécessitent de démultiplier le nombre de lignes du fichier\) que peuvent susciter la présence, pour un même marché public, de plusieurs acheteurs, de plusieurs titulaires, de plusieurs lots ou encore de plusieurs modifications apportées à ce marché alors que ses données essentielles ont déjà été publiées.
{% endhint %}

#### `MARCHE_ID` <a id="marcheid"></a>

* Titre : Identifiant du marché public
* Description : Exprimé sous la forme d'une chaîne de caractères d'un seul tenant, l'identifiant de marché, composé de trois parties, contient l'année de notification sur 4 caractères, suivie par le numéro d'ordre interne propre à l'acheteur comprenant de 1 à 10 caractères, complété par le numéro d'ordre de la modification sur 2 caractères \('00' si aucune modification, '01' si une première modification intervient, '02' si une deuxième modification intervient, etc\).
* Type : chaîne de caractères
* Exemple : '2014NNNNNNNNNN00' ou '2014NNNNNNNNNN01'
* Valeur : **obligatoire**
* Motif : `^\d{4}.{1,10}\d{2}$`

#### **`MARCHE_UID`**

* Titre : Identifiant unique du marché public
* Description : Exprimé sous la forme d'une chaîne de caractères d'un seul tenant, cet identifiant unique contient [`MARCHE_ID`](marches-publics.md#marcheid-1) préfixé de [`ACHETEURS_ID`](marches-publics.md#acheteursid), c'est-à-dire du [numéro SIRET](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) de l'acheteur.
* Type : chaîne de caractères \(format `uuid`\)
* Exemple : '213502388000192014NNNNNNNNNN00'
* Valeur : **optionnelle**
* Motif : ?

#### `ACHETEURS_ID` <a id="acheteursid"></a>

* Titre : Identifiant de l'acheteur
* Description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) \(SIRET\) de l'acheteur, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
* Type : chaîne de caractères
* Exemple : '21350238800019'
* Valeur : **obligatoire**
* Motif : `^\d{14}$`

#### `ACHETEURS_NOM` <a id="acheteursnom"></a>

* Titre : Nom de l'acheteur
* Description : Nom officiel de la collectivité qui passe le marché. Si le marché est passé par un groupement d'acheteurs, le nom désigne le mandataire du groupement.
* Type : chaîne de caractères
* Exemple : 'Ville de Rennes'
* Valeur : **obligatoire**
* Motif : `^[A-Za-zÀÂÄÇÉÈÊËÎÏÔÖÙÛÜŸàâäçéèêëîïôöùûüÿÆŒæœ -']*$`

#### `NATURE_MARCHE` <a id="naturemarche"></a>

* Titre : Nature du marché
* Description : La nature du marché est désignée en choisissant une valeur parmi une liste pré-établie de valeurs possibles : 'Marché', 'Marché de partenariat', 'Accord-cadre', ou 'Marché subséquent'.
* Type : chaîne de caractères
* Exemple : 'Accord-cadre'
* Valeur : **obligatoire**
* Valeurs autorisées : 'Marché', 'Marché de partenariat', 'Accord-cadre', 'Marché subséquent'

#### `MARCHE_OBJET` <a id="marcheobjet"></a>

* Titre : Objet du marché ou du lot
* Description : Description synthétique de l'objet du marché ou du lot qui ne doit pas excéder 256 caractères.
* Type : chaîne de caractères
* Exemple : 'Entretien des jardins municipaux'
* Valeur : **obligatoire**
* Taille maximale : 256

#### `CPV_CODE` <a id="cpvcode"></a>

* Titre : Code CPV principal
* Description : Le CPV \(Common Procurement Vocabulary\) est un vocabulaire commun qui désigne un [système de classification pour les marchés publics](https://simap.ted.europa.eu/fr/web/simap/cpv) de l'Union Européenne, rendu obligatoire par le [règlement \(CE\) nº 213/2008](https://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=OJ:L:2008:074:0001:0375:FR:PDF). Le vocabulaire principal du CPV repose sur une structure arborescente de codes comptant jusqu'à 9 chiffres \(un code à 8 chiffres complété par un chiffre de contrôle séparés par un tiret du milieu\) auxquels, pour chacun d'entre eux, correspond un intitulé qui décrit le type de fournitures, de travaux ou de services, objet du marché. Même s'il est toléré, il préférable d'omettre le chiffre de contrôle et donc de renseigner un code CPV principal sur 8 chiffres.
* Type : chaîne de caractères
* Exemple : '77313000'
* Valeur : **obligatoire**
* Motif : `^[0-9]{8}(\-[0-9])?$`

#### `PROCEDURE` <a id="procedure"></a>

* Titre : Procédure de passation du marché
* Description : Ce champ permet de renseigner la procédure de passation de marché utilisée par l'acheteur en choisissant une valeur parmi une liste pré-établie de valeurs possibles : 'Procédure adaptée', 'Appel d’offres ouvert', 'Appel d’offres restreint', 'Procédure concurrentielle avec négociation', 'Procédure négociée avec mise en concurrence préalable', 'Marché négocié sans publicité ni mise en concurrence préalable', ou 'Dialogue compétitif'.
* Type : chaîne de caractères
* Exemple : 'Marché négocié sans publicité ni mise en concurrence préalable'
* Valeur : **obligatoire**
* Valeurs autorisées : 'Procédure adaptée', 'Appel d’offres ouvert', 'Appel d’offres restreint', 'Procédure concurrentielle avec négociation', 'Procédure négociée avec mise en concurrence préalable', 'Marché négocié sans publicité ni mise en concurrence préalable', 'Dialogue compétitif'

#### `LIEU_EXEC_CODE` <a id="lieuexeccode"></a>

* Titre : Code du lieu d'exécution
* Description : Le code du lieu d'exécution du marché peut être soit le code postal, soit un des codes référencés par l'INSEE dans le [Code Géographique Officiel](https://www.insee.fr/fr/information/2016807) \(COG\) pour désigner une commune, un canton, un arrondissement, un département, une région, ou un pays. Les codes INSEE sont à privilégier aux dépens du code postal.
* Type : chaîne de caractères
* Exemple : '35238'
* Valeur : **obligatoire**

#### `LIEU_EXEC_TYPE` <a id="lieuexectype"></a>

* Titre : Type de code du lieu d'exécution
* Description : Ce champ permet de renseigner le type de code utilisé pour désigner le lieu d'exécution du marché en choisissant une valeur parmi une liste pré-établie de valeurs possibles : 'Code postal', 'Code commune', 'Code arrondissement', 'Code canton', 'Code département', 'Code région', 'Code pays'. Hormis le code postal géré par le service national de l'adresse de La Poste, tous ces types de code correspondent à des [codes géographiques](https://www.insee.fr/fr/information/2016807) gérés par l'INSEE.
* Type : chaîne de caractères
* Exemple : 'Code commune'
* Valeur : **obligatoire**
* Valeurs autorisées : 'Code postal', 'Code commune', 'Code arrondissement', 'Code canton', 'Code département', 'Code région', 'Code pays'

#### `LIEU_EXEC_NOM` <a id="lieuexecnom"></a>

* Titre : Nom du lieu d'exécution
* Description : Ce nom désigne le lieu d'exécution du marché et respecte le formalisme de la [chaîne de caractères type](http://xml.insee.fr/schema/commun.html#ChaineFrancaisOfficiel_stype) utilisée par l'INSEE pour décrire les caractères autorisés dans les documents officiels en français.
* Type : chaîne de caractères
* Exemple : 'Rennes'
* Valeur : **obligatoire**
* Motif : `^[A-Za-zÀÂÄÇÉÈÊËÎÏÔÖÙÛÜŸàâäçéèêëîïôöùûüÿÆŒæœ \-']*$`

#### `DUREE_MOIS` <a id="dureemois"></a>

* Titre : Durée initiale du marché
* Description : La durée initiale du marché est exprimée en nombre de mois telle qu'elle est définie au moment de la publication des données essentielles. Elle comprend la durée des tranches et reconductions potentielles. Sa valeur ne peut pas être inférieure à '1'. Si la durée ne correspond pas à un nombre exact de mois, elle est arrondie au nombre entier supérieur. Par exemple, la valeur '9' est attendue pour une durée de 9 mois ; la valeur '1' est attendue pour une durée de 2 semaines ; la valeur '2' est attendue pour une durée de 1 mois et 3 semaines. Dans le cas d'une modification de la durée du marché, la valeur de ce champ reste identique et celle du champ [`MODIF_DUREE_MOIS`](marches-publics.md#modifdureemois) est renseignée.
* Type : nombre entier
* Exemple : '24'
* Valeur : **obligatoire**
* MinMax : 1 au minimum et 999 au maximum

#### `NOTIFICATION_DATE` <a id="notificationdate"></a>

* Titre : Date de la notification du marché au\(x\) titulaire\(s\)
* Description : Date à laquelle le marché a été notifié au\(x\) titulaire\(s\) au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : '2014-08-13'
* Valeur : **obligatoire**

#### `PUBLICATION_DATE` <a id="publicationdate"></a>

* Titre : Date de la publication des données essentielles du marché
* Description : Date à laquelle les données essentielles du marché décrit ont été publiées pour la première fois au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601). Cette date ne nécessite donc pas de mise à jour en cas de modification du marché.
* Type : date
* Exemple : '2014-08-19'
* Valeur : **obligatoire**

#### `MONTANT` <a id="montant"></a>

* Titre : Montant forfaitaire ou estimé maximum HT
* Description : Ce montant est exprimé en euros hors-taxe sous la forme d'un nombre décimal dans lequel le séparateur entre la partie entière et la partie décimale du nombre est le point. Dans le cas d'une modification du montant du marché, la valeur de ce champ reste identique et celle du champ [`MODIF_MARCHE_MONTANT`](marches-publics.md#modifmarchemontant) est renseignée.
* Type : nombre décimal
* Exemple : '127000.50'
* Valeur : **obligatoire**

#### `PRIX_FORME` <a id="prixforme"></a>

* Titre : Forme du prix
* Description : Ce champ permet de renseigner la forme du prix utilisée par l'acheteur en choisissant une valeur parmi une liste pré-établie de valeurs possibles. Cette forme est 'Ferme' quand le prix est fixé pour toute la durée marché. Elle est 'Ferme et actualisable' quand le prix peut évoluer périodiquement selon des conditions prévues dans le contrat initial \(par exemple, variation d'indice\). Elle est 'Révisable' quand l'acheteur et le titulaire peuvent s'entendre sur une modification du prix après la signature du marché.
* Type : chaîne de caractères
* Exemple : 'Ferme et actualisable'
* Valeur : **obligatoire**
* Valeurs autorisées : 'Ferme', 'Ferme et actualisable', 'Révisable'

#### `TITULAIRES_ID` <a id="titulairesid"></a>

* Titre : Identifiant du titulaire du marché
* Description : Pour identifier le ou les opérateur\(s\) économique\(s\) titulaire\(s\) du marché, plusieurs types d'identifiants peuvent être utilisés. En fonction du [type d'identifiant utilisé](marches-publics.md#titulairesidtype), ce champ contient la valeur correspondante sous la forme d'une chaine de caractères. S'il existe, il est recommandé de privilégier le [numéro SIRET](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements). Dans le cas d'une modification du titulaire du marché, la valeur de ce champ reste identique et celle du champ [`MODIF_TITULAIRES_ID`](marches-publics.md#modiftitulairesid) est renseignée.
* Type : chaîne de caractères
* Exemple : '21350238800019'
* Valeur : **obligatoire**
* Motif : `^[A-Z0-9]{9,}$`

#### `TITULAIRES_ID_TYPE` <a id="titulairesidtype"></a>

* Titre : Type d'identifiant utilisé pour identifier le titulaire du marché
* Description : Pour identifier le ou les opérateur\(s\) économique\(s\) titulaire\(s\) du marché, plusieurs types d'identifiants peuvent être utilisés. Ce champ permet de renseigner le type d'identifiant parmi une liste pré-établie de valeurs possibles : 'SIRET', 'TVA', 'TAHITI', 'RIDET', 'FRWF', 'IREP', ou 'HORS UE'. S'il existe, il est recommandé de privilégier le [numéro SIRET](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements). Dans le cas d'une modification du titulaire du marché, la valeur de ce champ reste identique et celle du champ [`MODIF_TITULAIRES_ID_TYPE`](marches-publics.md#modiftitulairesidtype) est renseignée.
* Type : chaîne de caractères
* Exemple : 'SIRET'
* Valeur : **obligatoire**
* Valeurs autorisées : 'SIRET', 'TVA', 'TAHITI', 'RIDET', 'FRWF', 'IREP', 'HORS UE'

#### `TITULAIRES_DENOMINATION` <a id="titulairesdenomination"></a>

* Titre : Dénomination sociale du titulaire du marché
* Description : Ce champ permet de renseigner le nom du ou des opérateur\(s\) économique\(s\) titulaire\(s\) du marché sous la forme d'une chaîne de caractères. Dans le cas d'une modification du titulaire du marché, la valeur de ce champ reste identique et celle du champ [`MODIF_TITULAIRES_DENOMINATION`](marches-publics.md#modiftitulairesdenomination) est renseignée.
* Type : chaîne de caractères
* Exemple : 'Garami SARL'
* Valeur : **obligatoire**

#### `MODIF_OBJET` <a id="modifobjet"></a>

* Titre : Objet de la modification
* Description : Description de l'objet d'une modification du marché intervenue après la publication de ses données essentielles ne pouvant excéder 256 caractères.
* Type : chaîne de caractères
* Exemple : 'Modification du titulaire du marché. Nouveau titulaire : Rodriguez SAS'
* Valeur : **optionnelle**
* Taille maximale : 256

#### `MODIF_NOTIFICATION_DATE` <a id="modifsignaturedate"></a>

* Titre : Date de la notification de la modification
* Description : Date à laquelle une modification du marché intervenue après la publication de ses données essentielles est notifiée par l'acheteur. Cette date est au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : '2015-08-13'
* Valeur : **optionnelle**

#### `MODIF_PUBLICATION_DATE` <a id="modifpublicationdate"></a>

* Titre : Date de la republication des données suite à une modification
* Description : Date à laquelle les données essentielles sont republiées suite à une modification. Cette date est au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
* Type : date
* Exemple : '2015-08-19'
* Valeur : **optionnelle**

#### `MODIF_DUREE_MOIS` <a id="modifdureemois"></a>

* Titre : Modification de la durée initiale du marché
* Description : Dans le cas d'une modification de la durée initiale du marché, la nouvelle durée est exprimée en nombre de mois telle qu'elle est définie au moment de la republication des données essentielles. La manière d'exprimer cette nouvelle durée est identique à [celle qui prévaut pour exprimer la durée initiale](marches-publics.md#dureemois).
* Type : nombre entier
* Exemple : '36'
* Valeur : **optionnelle**
* MinMax : 1 au minimum et 999 au maximum

#### `MODIF_MARCHE_MONTANT` <a id="modifmarchemontant"></a>

* Titre : Modification du montant forfaitaire ou estimé maximum HT
* Description : Dans le cas d'une modification du montant du marché, le nouveau montant est renseigné tel qu'il est défini au moment de la republication des données essentielles. La manière d'exprimer ce nouveau montant est identique à [celle qui prévaut pour exprimer le montant initial](marches-publics.md#montant).
* Type : nombre décimal
* Exemple : '147000.50'
* Valeur : **optionnelle**

#### `MODIF_TITULAIRES_ID` <a id="modiftitulairesid"></a>

* Titre : Identifiant d'un nouveau titulaire du marché
* Description : Dans le cas d'une modification de l'opérateur économique titulaire du marché, ce champ contient la valeur, exprimée sous la forme d'une chaîne de caractères, qui correspond au type d'identifiant utilisé pour désigner ce nouveau titulaire. S'il existe, il est recommandé de privilégier le [numéro SIRET](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements). La manière d'exprimer cet identifiant est identique à [celle qui prévaut pour exprimer l'identifiant initial](marches-publics.md#titulairesid).
* Type : chaîne de caractères
* Exemple : '80053452100011'
* Valeur : **optionnelle**

#### `MODIF_TITULAIRES_ID_TYPE` <a id="modiftitulairesidtype"></a>

* Titre : Type d'identifiant utilisé pour identifier un nouveau titulaire du marché
* Description : Dans le cas d'une modification de l'opérateur économique titulaire du marché, ce champ permet de renseigner le type d'identifiant utilisé pour identifier ce nouveau titulaire parmi une liste pré-établie de valeurs possibles : 'SIRET', 'TVA', 'TAHITI', 'RIDET', 'FRWF', 'IREP', ou 'HORS UE'. S'il existe, il est recommandé de privilégier le [numéro SIRET](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements). La manière d'exprimer ce type d'identifiant est identique à [celle qui prévaut pour exprimer le type d'identifiant initial](marches-publics.md#titulairesidtype).
* Type : chaîne de caractères
* Exemple : 'SIRET'
* Valeur : **optionnelle**
* Valeurs autorisées : SIRET, TVA, TAHITI, RIDET, FRWF, IREP, HORS UE

#### `MODIF_TITULAIRES_DENOMINATION` <a id="modiftitulairesdenomination"></a>

* Titre : Dénomination sociale d'un nouveau titulaire du marché
* Description : Dans le cas d'une modification de l'opérateur économique titulaire du marché, ce champ permet de renseigner le nom de ce nouveau titulaire sous la forme d'une chaîne de caractères. La manière d'exprimer cette dénomination est identique à [celle qui prévaut pour exprimer la dénomination initiale](marches-publics.md#titulairesdenomination).
* Type : chaîne de caractères
* Exemple : 'Rodriguez SAS'
* Valeur : **optionnelle**

## Voir aussi <a id="voir-aussi"></a>

La spécification du modèle de données peut être utilement complétée par les documents suivants :

* Exemple de fichier
* [Schéma de validation](https://git.opendatafrance.net/scdl/marches-publics/blob/master/schema.json)​
* [Documentation générée à partir du schéma](https://scdl.opendatafrance.net/docs/schemas/scdl-marches-publics.html)​

Pour poser une question, commenter, faire un retour d’usage ou contribuer à l’amélioration du modèle de données, vous pouvez :

* adresser un message à scdl@opendatafrance.email
* participer au [fil de discussion dédié sur le forum de la mission Etalab](https://forum.etalab.gouv.fr/t/schemas-de-validation-des-donnees-essentielles-des-marches-publics/3141)​
* ouvrir un ticket sur le [dépôt GitLab d’OpenDataFrance](https://git.opendatafrance.net/scdl/marches-publics/issues/new)​ ou sur le [dépôt Github de la mission Etalab](https://github.com/etalab/format-commande-publique/issues/new)

