## Victoire (Toutes les briques cassées)

**Condition** : Vérifier qu'il reste **0 briques** du groupe `Bricks`

### Au démarrage du jeu

Dans l'espace de gauche sur notre scène, en plus du *score* et des *points de vie*, nous allons ajouter le nombre de *bricks* à détruire, et faire un décompte à chaque fois que nous en touchons une.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/nombre_bricks_visuel.png" alt="Victoire" width="400"/>

Nous allons utiliser une méthode toute prête de gDevelop **SceneInstancesCount()** qui permet de compter le nombre d'instances d'un objet dans la scène (ici le nombre de bricks).

#### En détail

 - Créé une variable de scène **Nombre_bricks** de type *nombre*

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_nombre_bricks.png" alt="Victoire" width="600"/>

 - Quand le jeu démarre, donne-lui la valeur `SceneInstancesCount(Bricks)` ou `Bricks` représente notre groupe d'objets.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/scene__instance.png" alt="Victoire" width="900"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/scene_instance_detail.png" alt="Victoire" width="400"/>

 - Ajoute un objet *texte* et donne lui la valeur permanente de `ToString(SceneInstancesCount(Bricks))` pour afficher en continu dans le jeu le nombre de `bricks` restantes

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/affichage_nombre_bricks.png" alt="Victoire" width="900"/>

### Évènement

1. **Ajouter un événement**
2. Cherche **"Comparaison"** → **"Nombre d'instances"**
3. Groupe : `Bricks`
4. Condition : `=` (égal)
5. Valeur : `0`

**Action** :

- Cherche **"Scène"** → **"Changer de scène"** (ou "Go to scene")

- Scène : **"Victory"** (tu la créeras plus tard)

### Score global


### Level 2 
