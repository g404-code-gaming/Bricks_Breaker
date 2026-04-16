# 🎮 Bricks Breaker - Consignes Level 2

## 🎨 Préparation de Level2

### Créer la scène Level2

1. Fais un clic sur **"Propriétés"** en haut à gauche (menu hamburger) de gDevelop
2. Dans `Scènes`, clique sur les trois petits points en face de **level1** et clique sur **Dupliquer**
3. Nomme-la nouvelle scène : **`Level2`**
4. Comme tu as dupliqué le level1, tout est déjà en place pour les objets et une grande partie du code !

### Initialiser le score global

Au démarrage de Level2, récupère le score du Level1 et affiche-le.

**Événement "Au démarrage de la scène"** :

**Action** : Initialiser sceneScore avec globalScore au lancement de la scène

- Cherche **"Variables"** → **"Modifier une variable de scène"**

- Variable : `sceneScore`
- Opération : `=`
- Valeur : `globalScore`
- Affiche-le dans l'objet texte `The_Score`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/egalite_score.png" alt="level2" width="700"/>

---

## 🧱 Créer les briques complexes

### Créer Blue_Brick (3 animations, 1 variable)

#### Étape A : Ajouter l'objet

1. **Ajouter un objet** → **À partir de zéro** → **"Sprite"**
2. Nomme-le : **`Blue_Brick`** 
3. Importe l'image `Blue_brick_full.png`
4. Renomme l'animation `Full`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_importer_images.png" alt="level2" width="300"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/full.png" alt="level2" width="300"/>

#### Étape B : Ajouter les animations

1. Clique sur **"Ajouter une animation"**
2. Importe l'image `Blue_brick_damaged.png`
3. Renomme l'animation `Damaged`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_animation.png" alt="level2" width="300"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/damaged.png" alt="level2" width="300"/>

5. Clique sur **"Ajouter une animation"**
6. Importe l'image `Red_brick.png`
7. Renomme l'animation `End`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/end.png" alt="level2" width="300"/>

8. Ta brique a désormais trois états :

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/trois_etats.png" alt="level2" width="300"/>

#### Étape C : Ajouter la variable d'objet à Blue_Brick

1. Onglet **"Variables de l'objet"**
2. **Ajouter une variable** :
   - **Nom** : **`isDamaged`**
   - **Type** : `Booléen`
   - **Valeur initiale** : `false`

👉 **Note** : Cette variable booléenne suit si la brique a été frappée. `false` = intacte, `true` = endommagée au moins une fois.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/ajouter_variable.png" alt="level2" width="300"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/isDamaged.png" alt="level2" width="700"/>

---

### Créer Yellow_Brick (2 animations, 1 variable)

Procède de la même façon pour la `Yellow_Brick`.  
La seule différence est qu'elle n'a que deux animations au lieu de trois : `Full` et `Damaged` 

1. **Ajouter un objet** → **À partir de zéro** → **"Sprite"**
2. Nomme-le : **`Yellow_Brick`** 
3. Importe l'image `Yellow_brick_full.png`
4. Renomme l'animation `Full`
5. Ajoute une animation
6. Importe l'image `Yellow_brick_damaged.png`
7. Renomme l'animation `Damaged`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/yellow_brick.png" alt="level2" width="300"/>

De la même façon également, ajoute-lui la variable `isDamaged`

1. Onglet **"Variables de l'objet"**
2. **Ajouter une variable** :
   - **Nom** : **`isDamaged`**
   - **Type** : `Booléen`
   - **Valeur initiale** : `false`
     
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/isDamaged.png" alt="level2" width="700"/>

---

### Placer les briques sur Level2

Place tes `Bricks` sur ton niveau.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/placement_level2.png" alt="level2" width="700"/>

---

### Mettre à jour les groupes d'objets

Maintenant que nous avons créé deux nouveaux types de `Bricks`, il faut les inclure dans nos groupes d'objets **`Bricks`** et **`Rebond`** que la balle puisse rebondir dessus. 

**Groupe `Bricks`** (ajoute les briques complexes) :

- ✅ `Red_Brick`
- ✅ `Green_Brick`
- ✅ `Blue_Brick` **← NOUVEAU**
- ✅ `Yellow_Brick` **← NOUVEAU**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/groupe_bricks.png" alt="level2" width="300"/>

**Groupe `Rebond`** (ajoute les briques complexes) :

- ✅ `Paddle`
- ✅ `Red_Brick`
- ✅ `Green_Brick`
- ✅ `Blue_Brick` **← NOUVEAU**
- ✅ `Yellow_Brick` **← NOUVEAU**
- ✅ `Wall`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/groupe_rebond.png" alt="level2" width="300"/>

---

## Programmer les collisions

### Collision avec Blue_Brick

**Événement** : Balle en collision avec Blue_Brick

Tu vas devoir gérer les différentes états de `Blue_Brick` pour switcher d'une **animation** à une autre suvant si la balle à toucher une fois, deux fois ou trois fois `Blue_Brick`.

 - Si `Ball` touche une première fois `Blue_Brick`
 - Que l'animation de `Blue_Brick` est à `Full`
 - Que la variable `isDamaged`de `Blue_Brick` est à `false`

Alors tu peux changer **l'animation** de `Blue_Brick` à `Damaged` et mettre ta **variable** `isDamaged` à `true`.  
Et bien entendu gérer le `sceneScore` !

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/conditions_blue_brick.png" alt="level2" width="700"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/actions_blue_brick_1.png" alt="level2" width="700"/>

 - Si `Ball` touche une seconde fois `Blue_Brick`
 - Que l'animation de `Blue_Brick` est à `Damaged`
 - Que la variable `isDamaged`de `Blue_Brick` est à `vrai`

Alors tu peux changer **l'animation** de `Blue_Brick` à `End` et gérer la collision suivante de manière classique : `Blue_Brick` est supprimée.  

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/conditions_bb_damaged.png" alt="level2" width="700"/>

### Collision avec Yellow_Brick

Le schéma va être le même avec `Yellow_Brick` sauf qu'il n'y a que deux étapes. Encore plus simple !

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/conditions_yb.png" alt="level2" width="700"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/actions_yb_1" alt="level2" width="700"/>


## Victoire

Les conditions de victoire sont les mêmes que le niveau 1 : casser toutes les `Bricks` ! 

La seule différence va être dans ta gestion du score.  
À la fin du niveau 2, il va te falloir addtionner le score du `level1` et le score de `level2`.  

Ta variable *`globalScore`* doit récupérer sa valeur de base et y ajouter la valeur fiale de *`sceneScore`*.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/gestion_score_globaux" alt="level2" width="700"/>


## 🎉 Level 2 Terminé !

Tu as maintenant :

- ✅ Score global récupéré du Level 1
- ✅ Briques complexes avec variables booléennes `isDamaged`
- ✅ Animations d'endommagement (Full → Damaged → End pour Blue)
- ✅ Système de points variables
- ✅ Gestion correcte des collisions multiples

**Prochaine étape** : le Level 3 avec un timer et descente des briques ! ⏱️👽
