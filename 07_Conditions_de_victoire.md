## Victoire (Toutes les briques cassées)

**Condition** : Vérifier qu'il reste **0 briques** du groupe `Bricks`

### Au démarrage du jeu

Dans l'espace de gauche sur notre scène, en plus du *score* et des *points de vie*, nous allons ajouter le nombre de *bricks* à détruire, et faire un décompte à chaque fois que nous en touchons une.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/nombre_bricks_visuel.png" alt="Victoire" width="300"/>

Nous allons utiliser une méthode toute prête de gDevelop **SceneInstancesCount()** qui permet de compter le nombre d'instances d'un objet dans la scène (ici le nombre de bricks).

#### En détail

 - Créé une variable de scène **Nombre_bricks** de type *nombre*

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_nombre_bricks.png" alt="Victoire" width="600"/>

 - Quand le jeu démarre, donne-lui la valeur `SceneInstancesCount(Bricks)` ou `Bricks` représente notre groupe d'objets.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/scene__instance.png" alt="Victoire" width="900"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/scene_instance_detail.png" alt="Victoire" width="400"/>

 - Ajoute un objet *texte* et donne lui la valeur permanente de `ToString(SceneInstancesCount(Bricks))` pour afficher en continu dans le jeu le nombre de `bricks` restantes

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/affichage_nombre_bricks.png" alt="Victoire" width="900"/>

### Évènements et actions

1. **Ajouter un événement**
2. Cherche **"Autres conditions"** → **"Variables"** → **"Valeur de la variable"**
3. Variable : `Nombre_bricks`
4. Condition : `=` (égal à)
5. Valeur : `0`

**Action** :

- Supprime l'objet `Ball`
- Joue un son de victoire (optionnel)

**Avant de partir direction le level 2, quelques derniers ajustement**

### Score global

Nous allons créer une variable globale `globalScore`.  
Contrairement aux *variables de scène*, cette variable existe dans l'**intégralité** de toutes les scènes du jeu.  
Nous allons enregistrer nos scores de niveaux au fur et à mesure pour faire un **high score** global.  


Dans les propriétés du jeu (menu hamburger), clique sur **Variables globles** et créer la variable `globalScore`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/creer_vg.png" alt="Victoire" width="400"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/vg_detail.png" alt="Victoire" width="600"/>

Une fois la victoire obtenue, nous allons basculer le score de la scene (`sceneScore`) à `globalScore` pour le sauvegarder.  

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/score_ok.png" alt="Victoire" width="700"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/score_ok_detail.png" alt="Victoire" width="300"/>

### Level 2 

Let's go ! Nous pouvons aller au **level 2** !
  
- Cherche **Autres actions** puis **"Scène"** → **"Changer de scène"**
- Choisir la scène : **"Level2"** (que tu auras créer juste avant)

Voici à quoi pourra ressembler ton bloc complet de victoire :

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bloc_victoire.png" alt="Victoire" width="900"/>

---

## Sauvegarder

<img src="https://sebastien-devos.fr/img/codegaming/atelier-decouverte/19_Sauvegarder.png" alt="Placement des objets" width="200"/>

Clique maintenant sur l'icône en forme de **disquette** en haut à gauche de ton espace de travail *GDevelop* pour sauvegarder ton projet.

---

**Direction le niveau 2**
