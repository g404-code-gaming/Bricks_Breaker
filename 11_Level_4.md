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

### Créer l'objet PowerUp

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

## 🔥 Configurer le Paddle avec Fire {#paddle-fire}

### Ajouter l'animation Fire au Paddle

Le Paddle doit avoir **2 animations** :

1. Double-clique sur l'objet **`Paddle`** (dans la liste des objets)
2. Onglet **"Propriétés"**
3. **Ajouter une animation** → Nomme-la **`Fire`**
4. Sélectionne l'image : **"assets/paddle-fire.png"**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/animation_paddle_fire.png" alt="level4" width="600" />

### Modifier les points du Paddle

Ajoute une variable d'objet au Paddle :

1. Double-clique sur l'objet **`Paddle`**
2. Clique sur *Modifier les points*
3. Ajoute deux nouveaux points, `Fire1` et `Fire2` placés à gauche et droite au `Paddle`, au centre des extrémités

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/points_paddle_fire_base.png" alt="level4" width="800" />

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/ajout_points_bullet.png" alt="level4" width="800" />

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/points_ajoutes.png" alt="level4" width="500" />

### Ajouter le comportement Fire Bullets

1. Toujours dans les propriétés de **`Paddle`**
2. Section **"Comportements"**
3. **Ajouter un comportement**
4. Cherche : **"Fire Bullets"** (comportement officiel gDevelop)
5. Configure le **Firing cooldown** à 1 seconde

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/comportement_fire_bullets.png" alt="level4" width="800" />

---

## ⚙️ Programmer les événements {#events}

### Événement A : Collision PowerUp + Paddle

**Condition** : PowerUp en collision avec Paddle

**Actions** :

**Action A.1** : Changer l'animation du Paddle
- Cherche **"Animation"** → **"Changer l'animation"**
- Objet : `Paddle`
- Animation : `Fire`

**Action A.2** : Démarrer fireTimer
- Cherche **"Variables de l'objet"** → **"Modifier la variable d'objet"**
- Objet : `Paddle`
- Variable : `fireTimer`
- Opération : `=`
- Valeur : `0` (réinitialiser)

**Action A.3** : Activer Fire Bullets
- Cherche **"Fire Bullets"** → **"Activer le tir"**
- Objet : `Paddle`

**Action A.4** : Jouer un son
- Cherche **"Sonore"** → **"Jouer un son"**
- Son : `beep.ogg` (ou `life.ogg`)

**Action A.5** : Détruire le PowerUp
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `PowerUp`

---

### Événement B : Gérer le timer du Paddle

**Condition** : Paddle.Variable(fireTimer) < 10 (le pouvoir est actif)

**Actions** :

**Action B.1** : Incrémenter fireTimer
- Cherche **"Variables de l'objet"** → **"Modifier la variable d'objet"**
- Objet : `Paddle`
- Variable : `fireTimer`
- Opération : `+`
- Valeur : `dt` ou `TimeDelta()` (pour avancer d'une frame)

Ou plus simplement :
- Valeur : `0.016` (= 1 frame à 60 FPS)

---

### Événement C : Fin du pouvoir

**Condition** : Paddle.Variable(fireTimer) >= 10

**Actions** :

**Action C.1** : Revenir à l'animation normale
- Cherche **"Animation"** → **"Changer l'animation"**
- Objet : `Paddle`
- Animation : `""` (vide = animation par défaut)

**Action C.2** : Désactiver Fire Bullets
- Cherche **"Fire Bullets"** → **"Désactiver le tir"**
- Objet : `Paddle`

**Action C.3** : Réinitialiser fireTimer
- Cherche **"Variables de l'objet"** → **"Modifier la variable d'objet"**
- Objet : `Paddle`
- Variable : `fireTimer`
- Opération : `=`
- Valeur : `-1` (ou `11` pour marquer comme terminé)

---

### Événement D : Bullet en collision avec Bricks

**Condition** : Bullet en collision avec groupe `Bricks`

**Actions** :

**Action D.1** : Détruire la brique
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `Red_Brick` (ou selon la collision)

**Action D.2** : Détruire la bullet
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `Bullet`

**Action D.3** : Ajouter des points
- Cherche **"Variables de scène"** → **"Modifier une variable de scène"**
- Variable : `sceneScore`
- Opération : `+`
- Valeur : `3` (les bullets donnent moins que la balle)

**Action D.4** : Mettre à jour l'affichage du score
- Cherche **"Texte"** → **"Modifier le texte"**
- Objet : `The_Score`
- Texte : `ToString(Variable(sceneScore))`

---

### Événement E : PowerUp tombe hors écran

**Condition** : PowerUp.Y > 600

**Actions** :

**Action E.1** : Détruire le PowerUp
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `PowerUp`

👉 Cet événement évite que le PowerUp reste bloqué en bas et affecte les collisions.

---

### Événement F : Collision Grey_brick + Ball (destruction)

**Condition** : Ball en collision avec Grey_brick

**Actions** :

**Action F.1** : Jouer un son
- Cherche **"Sonore"** → **"Jouer un son"**
- Son : `touch-one.ogg`

**Action F.2** : Détruire Grey_brick
- Cherche **"Objet"** → **"Supprimer l'objet"**
- Objet : `Grey_brick`

**Action F.3** : Créer une instance PowerUp
- Cherche **"Objet"** → **"Créer un objet"**
- Objet : `PowerUp`
- X : `Grey_brick.X()`
- Y : `Grey_brick.Y()`

**Action F.4** : Ajouter des points pour la destruction
- Cherche **"Variables de scène"** → **"Modifier une variable de scène"**
- Variable : `sceneScore`
- Opération : `+`
- Valeur : `50` (Grey_brick vaut plus cher)

**Action F.5** : Mettre à jour l'affichage
- Cherche **"Texte"** → **"Modifier le texte"**
- Objet : `The_Score`
- Texte : `ToString(Variable(sceneScore))`

---

## 🧪 Test du niveau {#test}

### Checklist de test :

| Fonctionnalité | À tester |
|---|---|
| **Bullets** | S'affichent quand le Paddle a le PowerUp |
| **Destruction Bricks par Bullets** | Briques disparaissent quand touchées par bullet |
| **Points Bullets** | +3 points par brick détruit par bullet |
| **PowerUp drop** | Lâché quand Grey_brick est cassée |
| **Paddle animation Fire** | Change de sprite quand PowerUp attrapé |
| **FireTimer 10 sec** | Paddle revient normal après 10 secondes |
| **Fin du pouvoir** | Bullets s'arrêtent après 10 sec |
| **Score Grey_brick** | +50 points pour casser la Grey_brick |
| **Victoire** | Passe au niveau suivant quand 0 briques |

---

## 📚 Résumé Level 4

### Nouveaux objets :
- **`Grey_brick`** : Brique grise qui lâche un PowerUp
- **`PowerUp`** : Item qui tombe du Grey_brick
- **`Bullet`** : Projectile tiré par le Paddle

### Nouvelle animation Paddle :
- **`Fire`** : Sprite du Paddle avec des flammes

### Nouvelles variables :
- **`Paddle.fireTimer`** : Compte à rebours du pouvoir (0-10 sec)

### Nouveaux comportements :
- **`Paddle` + Fire Bullets** : Permet de tirer des projectiles

### Points :
- Red_Brick : 5
- Green_Brick : 5
- Blue_Brick : 20 (total)
- Yellow_Brick : 15 (total)
- **Grey_brick : 50** ← Nouveau
- **Bullet hit : 3 points** ← Nouveau

---

Voilà les consignes complètes pour **Level 4** ! 🔥🎮
