# Level 4

Dans ce dernier niveau, nous allons ajouté un élément de gameplay qui fut ajouté sur les versions plus récentes de Breakout : les **Power up**.  
Certaines `Bricks` vont te permettre de libérer un boost qui va transformer ton `Paddle` et lui permettre de tirer des projectiles en direction des `Bricks` pour les détruire plus vite !

---

## 🎯 Introduction Level 4

Ce qui change :  
✅ une nouvelle brick : **Grey_brick** qui lâche un **Power_Up**   
✅ quand le `Paddle` attrape le `Power_Up` :  
   - l'animation du `Paddle` change
   - il peut tirer des **Bullets** vers le haut pendant **10 secondes**
   - il tire avec un **cooldown** entre les tirs
   - après 10 secondes, le `Paddle` revient à sa forme normale

---

## 🚀 Créer la scène Level4

Duplique **Level2** pour créer **Level4** :

1. Fais un clic droit sur **Level2** → **Dupliquer**
2. Renomme le layout dupliqué : **Level4** 

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/level_4.png" alt="level2" width="400"/>

---

## 🧱 Ajouter Grey_brick

### Créer l'objet Grey_brick

1. **Ajouter un objet** → **"Sprite"**
2. Nomme-le : **`Grey_brick`** ⚠️
3. Importe l'image : **"assets/Grey_brick.png"**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_importer_images.png" alt="level4" width="400" />

4. Ajoute une animation (par défaut une seule) nommée par défaut `Base`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/grey_brick_detail.png" alt="level4" width="400" />

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/grey_brick.png" alt="level4" width="400" />

### Ajouter Grey_brick au groupe Rebond

Modifie le groupe d'objets :

**Groupe `Rebond`** → Ajoute Grey_brick ICI
- Paddle
- Red_Brick
- Green_Brick
- Blue_Brick
- Yellow_Brick
- Wall
- **Grey_brick** ← NOUVEAU

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/ajouter_grey_brick_rebond.png" alt="level4" width="600" />

### Placer Grey_brick sur la scène

Place 3 ou 4 instances de **Grey_brick** stratégiquement (ex : milieu-bas, pour que le joueur la découvre facilement).

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/exemple_grey_bricks.png" alt="level4" width="600" />

---

## 🎁 Créer le Power_Up

### Créer l'objet Power_Up

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objet_power_up.png" alt="level4" width="800" />

1. **Ajouter un objet** → **"Magasin de ressources"**
2. Cherche l'objet : **`Power_Up`** 
3. Ajoute-le à la scène

### Variables du Power_Up

Le `Power_Up` n'a pas besoin de variables spéciales pour Level 4 - c'est juste une animation qui tombe et qui active l'effet sur collision.

---

## 🔫 Créer les Bullets

### Créer l'objet Bullet

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objet_bullet.png" alt="level4" width="800" />

1. **Ajouter un objet** → **"Magsin de ressources"**
2. Cherche l'objet : **`Bullet`** 
3. Ajoute-le à la scène
4. Doucle-clique dessus et clique sur *Modifier les points*
5. Prends le point **Origin** et place-le aux mêmes coordonnées que le point **Center**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/modifier_points_bullet.png" alt="level4" width="800" />

Cette modification va permettre de placer très précisemment les projectiles lorsque le `Paddle` fera feu. 

---

## 🔥 Configurer le Paddle avec Fire

### Ajouter l'animation Fire au Paddle

Le Paddle doit avoir **2 animations** :

1. Double-clique sur l'objet **`Paddle`** (dans la liste des objets)
2. Onglet **"Propriétés"**
3. **Ajouter une animation** → Nomme-la **`Fire`**
4. Sélectionne l'image : **"assets/paddle-fire.png"**
5. Profites-en pour appeler l'animation de base `Base`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/animation_paddle_fire.png" alt="level4" width="400" />

### Modifier les points du Paddle

Ajoute une variable d'objet au Paddle :

1. Double-clique sur l'objet **`Paddle`**
2. Clique sur *Modifier les points*
3. Ajoute deux nouveaux points, `Fire1` et `Fire2` placés à gauche et droite au `Paddle`, au centre des extrémités

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/points_paddle_fire_base.png" alt="level4" width="800" />

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/ajout_points_bullet.png" alt="level4" width="800" />

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/points_ajoutes.png" alt="level4" width="400" />

### Ajouter le comportement Fire Bullets

1. Toujours dans les propriétés de **`Paddle`**
2. Section **"Comportements"**
3. **Ajouter un comportement**
4. Cherche : **"Fire Bullets"** (comportement officiel gDevelop)
5. Configure le **Firing cooldown** à 1 seconde

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/comportement_fire_bullets.png" alt="level4" width="900" />

---

## ⚙️ Programmer les événements 

### Événement A : Collision entre `Grey_brick` + `Ball`

**Condition** : Ball en collision avec Grey_brick

**Actions** :

**Action A.1** : Détruire Grey_brick
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `Grey_brick`

**Action A.2** : Créer une instance Power_Up
- Cherche **"Créer un objet"**
- Objet : `Power_Up`
- X : `Grey_brick.CenterX()`
- Y : `Grey_brick.CenterY()`

**Action A.3** : Envoyer Power_Up vers le joueur
- **Appliquer une force** permanente 
- Objet : `Power_Up`
- Axe X : 0
- Axe Y : 100

**Action A.4** : Ajouter des points pour la destruction
- Cherche **"Variables de scène"** → **"Modifier une variable de scène"**
- Variable : `sceneScore`
- Opération : `+`
- Valeur : `25` (Grey_brick vaut plus cher)

**Action A.5** : Mettre à jour l'affichage
- Cherche **"Texte"** → **"Modifier le texte"**
- Objet : `The_Score`
- Texte : `ToString(Variable(sceneScore))`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/collision_ball_grey_brick.png" alt="level4" width="900" />

### Événement B : Collision PowerUp + Paddle

**Condition** : PowerUp en collision avec Paddle

**Actions** :

**Action B.1** : Détruire le Power_Up
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `Power_Up`

**Action B.2** : Changer l'animation du Paddle
- Cherche **"Animation"** → **"Changer l'animation"**
- Objet : `Paddle`
- Animation : `Fire`

**Action B.3** : Démarrer un chronomètre d'objet
- Cherche **Démarrer le chronomètre d'un objet**
- Objet : `Paddle`
- Variable : `Fire`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/collision_power_paddle.png" alt="level4" width="900" />

---

### Événement C : `Paddle` peut tirer

**Conditions** : 
 - l'animation de `Paddle` est sur *Fire*
 - la touche `Space` est appuyée

**Actions** : Tirer depuis `Fire1`
- Cherche **Tirer des balles vers un angle** 
- Objet balle : `Bullet`
- Position X : `Paddle.PointX("Fire1")`
- Position Y : ``Paddle.Point`Y("Fire1")`
- Angle : 270 (vers le haut)
- Vitesse : 150

**Fais la même chose pour `Fire2`**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/paddle_fire.png" alt="level4" width="900" />

---

### Événement D : Fin du pouvoir

**Condition** : le chronomètre *Fire* de `Paddle` >= 10

**Action** : Revenir à l'animation normale
- Cherche **"Animation"** → **"Changer l'animation"**
- Objet : `Paddle`
- Animation : `Base`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/retour_normal_paddle.png" alt="level4" width="900" />

`Paddle` revenant à sa forme initiale, il ne peut plus tier, puis le tir était actif que lorsque son animation était sur *Fire*

---

### Événement E : Bullet en collision avec les `Bricks`

Pour les collisions entre `Bullet` et les différentes `Bricks` (*red*, *yellow*, *green*, *blue*), tu peux reprendre à peu de chose prêt le code des collisions de `Ball` avec les différentes `Bricks`

La différence :
 - Pense à supprimer `Bullet` à la collision !

Par exemple : 

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/collision_bullet_bricks.png" alt="level4" width="900" />


---

### Événement F : Power_Up tombe hors écran

**Condition** : La position Y de `Power_Up` > 600

**Actions** :

**Action F.1** : Détruire le Power_Up
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `Power_Up`

---

## 🧪 Test du niveau

### Checklist de test :

| Fonctionnalité | À tester |
|---|---|
| **Bullets** | S'affichent quand le Paddle a le PowerUp |
| **Destruction Bricks par Bullets** | Briques disparaissent quand touchées par bullet |
| **PowerUp drop** | Lâché quand Grey_brick est cassée |
| **Paddle animation Fire** | Change de sprite quand PowerUp attrapé |
| **FireTimer 10 sec** | Paddle revient normal après 10 secondes |
| **Fin du pouvoir** | Bullets s'arrêtent après 10 sec |
| **Score Grey_brick** | +25 points pour casser la Grey_brick |

---
