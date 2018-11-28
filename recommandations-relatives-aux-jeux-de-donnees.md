# Recommandations relatives aux jeux de données

## Recommandations pour le formatage des fichiers

Pour toutes les spécifications SCDL, le format de fichier retenu pour la publication des données est le [CSV](https://fr.wikipedia.org/wiki/Comma-separated_values) \(Comma Separated Values, valeurs séparées par des virgules\).

Les fichiers doivent, sauf exception et autant que possible, respecter les règles de formatage suivantes :

* l’encodage des caractères est [UTF-8](https://fr.wikipedia.org/wiki/UTF-8),
* le séparateur des colonnes est la virgule,
* le séparateur des nombres décimaux est le point,
* le séparateur de valeurs multiples dans un champ est le point-virgule,
* si un champ contient une virgule, il doit être entouré de guillemets doubles,
* chaque ligne doit avoir le même nombre de champs,
* le type MIME ou Content-Type est text/csv.

## Recommandations pour le nommage des fichiers

Les fichiers doivent, sauf exception et autant que possible, respecter les règles de nommage suivantes :

**AAAAMMJJ\_idProducteur**_**\_**_**nom-du-fichier.extension**

* **AAAAMMJJ** : Date de création du fichier
* **idProducteur** : Numéro [SIREN](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_entreprises) sur 9 chiffres pour identifier le producteur
* **nom-du-fichier** Chaîne de caractères dont les termes, en minuscules non accentuées, sont séparés par un tiret du milieu
* **.extension** : Si les [règles de formatage](./#recommandations-pour-le-formatage-des-fichiers) sont respectées, l'extension est .csv

Les 3 éléments constitutifs de la chaîne principale avant l'extension sont assemblés en un seul tenant et séparés par un tiret du bas.

Exemple : '20180314\_213502388\_prenoms-nouveaux-nes-rennes-2017.csv'

## Recommandations pour la mise en conformité

Pour garantir la conformité des jeux de données publiés par rapport aux spécifications SCDL, il est demandé aux producteurs de s'assurer que la structure, les champs et les contenus attendus sont effectivement respectés.

De fait, les fichiers tabulaires doivent, autant que possible, contenir :

* **Toutes les colonnes**, y compris celles dont les cellules ne sont pas renseignées, dans le bon ordre, et avec des en-têtes correctement nommées sur la première ligne
* **Autant de lignes que nécessaire** comprenant des cellules dont les valeurs peuvent être **obligatoires** \(elles doivent être impérativement renseignées\) ou **optionnelles** \(elles sont seulement recommandées ou soumises à condition de disponibilité / pertinence\)

## Recommandations pour la découvrabilité

Pour faciliter la détection des jeux de données qui s'appuient sur les spécifications SCDL, ils doivent, autant que possible, être marqués avec des tags prédéfinis au moment où ils sont déposés sur une plateforme open data \(renseignement de la métadonnée 'tags' du catalogue\).

Les régles d'étiquetage des jeux de données sont les suivantes :

* Un premier tag 'SCDL' doit être indifféremment ajouté à tous les jeux de données concernés
* Un ou plusieurs autre\(s\) tag\(s\) spécifique\(s\) doi\(ven\)t être ajouté\(s\) en fonction du jeu de données

