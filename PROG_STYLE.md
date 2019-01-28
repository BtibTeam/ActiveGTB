# Charte de la station de base

# Nom de la station
Suite un pseudo format SemVersion
`active{Mode}{Language}V{MajorNiagaraVersion}_{Minor}_{Patch}`

*Exemple: activeStandAloneFrV47_1_0*

* Ajout d'une fonctionalité : on incrémente le minor et on repasse le patch à 0
* Correction d'une fonctionalité sans ajout : on incrémente le Patch

# Organisation de la partie config
Config doit rester propre.
Un seul dossier Accueil qui contient les fonctions générales de la station (plus ou moins le contenu du menu de navigation de gauche)

* **Config**
    * **Services**
    * **Drivers**
    * **Apps**
    * **Station Info Source**
    * **Accueil**
        * **Alarmes**
        * **Navigation Géographique**
        * **...**

# Organisation de la partie fichiers
Le nom des répertoires doit suivre la charte suivante : 
* Peut être au pluriel
* Toujours écrit en minuscule
* Utilisation de `_` si deux mots
* Pas de caractères spéciaux

Voici les dossiers par défaut :
* **activedb** : ne rien mettre dans ce dossier qui est utilisé par les différents composants btib
* **images** : répertoire contenant tous les images organisées en sous-dossiers
    * **arriere_plans** : pour toutes les images utilisées en arrière plan (photos de bâtiments, fonds d'écran etc.)
    * **icones** : contient toutes les icônes utilisées dans la station. Privilégier les icônes du répertoire de thème (plus simple pour les mises à jour). Si une image vous semble récurrente et intéressante à intégrer, vous pouvez utiliser la partie "issues" pour le signaler. 
    * **logos** : contient les logos utilisés (à séparer du reste pour plus de lisibilité)
    * **plans** : contient les plans d'étage et autres synoptiques
* **imports** : contient les fichiers d'imports de données (les historiques par exemple pour la démo)
* **nav** : contient les fichiers nav de la station
* **px** : doit contenir une seule .px `accueil.px`. Voici l'organisation de quelques dossiers par défaut : 
    * **deploy** : pour les templates
    * **fonctions** : organisation en sous-dossier des différentes fonctions générales de la station. Exemple : *tout ce qui concerne la map doit se trouver dans un sous-dossier ici*. A bien dissocier du dossier sources qui contient tout ce qui concernent les vues par rapport aux équipements, points etc.
    * **geo/metier** etc. shortname des apects créés dans la station qui contiendront les vues associées à chaque aspect. Exemple : *toutes les vues de la navigation géographique dans le répertoire geo*
    * **menu** : vues utilisées en tant que menu. Exemples : `gauche.px`, `haut.px`
    * **sources** : toutes les vues relatives aux équipements/dossiers de points etc. à organiser en sous-dossier selon l'usage. A bien dissocier des fonctions.
* **ressources** : tout ce qui est utilisé comme ressources (nom anglais gardé)
    * **bog** : tous les .bog. A organiser par sous-dossiers si besoin.
    * **macro** : implémenté automatiquement lors de la création de macros.
    * **px** : à organiser en sous-dossier avec deux principaux
        * **items** : tous les petits éléments. Voir la charte associée au nommage des items.
        * **masques** : tous les masques de la station. Voir la charte associée au nommage des masques.
* **webservice** : généré automatiquement par la personalisation du css du login

Lorsque vous avez un fichier '.px' include créer un dossier 'includes' à la racine du dossier où se trouve votre fichier '.px'
* **dossier_de_px** : votre dossier avec le fichier '.px' et le dossier 'includes'
	* **px.px** : votre fichier '.px'
	* **includes** : votre dossier contenant vos includes
		* **include.px** : votre fichier include
	

Le nom des fichiers doit suivre la charte suivante
* Utilisation du camelCase pour le nom du fichier
* Pas de caractères spéciaux

# Organisation du modèle
* Les Aspects doivent être nommés en minuscule. Leur displayName doit commencer par une majuscule.
* Le ShortName d'un Aspect doit contenir les 3 premières lettres du nom de l'aspect en minuscule. Exemple `geo` pour *geographie*
* Les définitions doivent être nommées en minuscule et en **un seul mot**. Exemple : *salleDeReunion* Leur displayName doit commencer par une majusculeet peut contenir des espaces.
* Les définitions dans le Wiresheet de l'Aspect doivent être organisées par niveau, le niveau 1 étant situé en haut.
* Les NodeTags et NodeRelations doivent être nommées en minuscule et en un seul mot et doivent être précédée du shortName du dictionaire associé `b:`, `n:`, `hs:` etc.

# Organisation des sélections
Les sélections sont organisées dans 5 dossiers : 
* **Modèle**
* **Source**
* **Historiques**
* **Alarmes**
* **Général**
Les sélections sont préférentiellement précédées du mot `Tous les` si la sélection portent sur tous les éléments d'une même catégorie. Exemple : *Tous les bâtiments*

# Organisation des ressources
Toutes les ressources générales doivent être contenues dans le dossier General. Son nom ne doit pas être changé.
Les ressources par défaut ne doivent pas être traduites : 
* Color
* GraphType
* Y Aggregation  
Les ressources du dossier Masques Px doivent suivre le format `Masque {Element}`. Exemple : *Masque Bâtiment*  
Les ressources du dossier Items Px doivent suivre le format `Items xxx pour yyy`. Exemple : *Items Nature pour Vues CTA*

# Organisation des stratégies
Il doit y avoir un dossier de stratégie : 
* Pour chaque Aspect : déploiement des éléments à décomposer par définition si possible 
* Pour les sources : déploiement d'équipements, de points
* Pour les fonctions : ce qui est général dans la station : synthèses, rapports etc.
* Pour les Historiques : traitement + export
* Pour les alarmes : traitement + export
* Pour les macros que l'on nomme *Utilitaires*
Lorsque les stratégies créent des éléments dans la station, il est recommandé par convention de les précéder du mot clé `Déploiement`. Exemple : *Déploiement des bâtiments*

Chaque statégie doit contenir en haut à gauche un commentaire sur fond noir expliquant le but global de la stratégie. On doit comprendre quel est le rôle de la stratégie.
En dessous doivent être présent le LogExt et le trigger. Il est vivement recommandé d'utilier des commentaires sur fond gris détaillant une partie de la stratégie.
Les blocks de stratégies doivent être nommés de manière lisible pour exploquer brièvement le rôle du bloc. **Le nom par défaut ne doit pas être conservé.**
Les liens et relations doivent être matérialisés dans le nom du bloc par une flèche ->. Exemple : *nvoSpaceTemp -> nviSpaceTemp*  
![](https://i.ibb.co/2PgHdkS/Format-Strategie.png)  
Les artifacts doivent être nommés en camelCase. S'il y a potentiellement plusieurs valeurs dans un artifact (un tableau), ajouter un s à la fin. Exemple : *`infoSource` si un seul ou `infoSources` si plusieurs*  
Toujours commencer un SFormat par le mot clé `origin` ou un artifact. Exemple : *`{origin.%displayName%}` et non pas `{%displayName%}` même si cela fonctionne*

# Organisation des PxProperties
Les PxProperties doivent être nommées en camelCase.
Deux types de couleurs existent : 
* Background Color : elles sont suffixées par `BgColor`. Exemple : *gaucheBgColor* 
* Foreground Color : elles sont sufficées par `FgColor`. Exemple : *hautFgColor*
S'il y a un besoin de nuances de couleurs, créer deux couleurs Shade (plus foncée) et Tint (plus claire) à ajouter au prefix de la couleur principale. Exemple : *gaucheBgColorShade*.
Utiliser un maximum de PxProperties dans les vues.