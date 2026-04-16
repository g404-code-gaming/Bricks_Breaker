# 🎮 Bricks Breaker - Consignes Level 2

## 🎨 Préparation de Level2

### Créer la scène Level2

1. Fais un clic sur **"Propriétés"** en haut à gauche (menu hamburger) de gDevelop
2. Dans `Scènes`, clique sur les trois petits points en face de **level1** et clique sur **Dupliquer**
3. Nomme-la nouvelle scène : **`Level2`** ⚠️
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

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/egalite_score.png" alt="Placement" width="700"/>

---

## 🧱 Créer les briques complexes

### Créer Blue_Brick (3 animations, 1 variable)

#### Étape A : Ajouter l'objet

1. **Ajouter un objet** → **À partir de zéro** → **"Sprite"**
2. Nomme-le : **`Blue_Brick`** 
3. Importe l'image `Blue_brick_full.png`
4. Renomme l'animation `Full`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_importer`_images.png" alt="Placement" width="300"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/full.png" alt="Placement" width="300"/>

#### Étape B : Ajouter les animations

1. Clique sur **"Ajouter une animation"**
2. Importe l'image `Blue_brick_damaged.png`
3. Renomme l'animation `Damaged`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_animation.png" alt="Placement" width="300"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/damaged.png" alt="Placement" width="300"/>

5. Clique sur **"Ajouter une animation"**
6. Importe l'image `Red_brick.png`
7. Renomme l'animation `End`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/end.png" alt="Placement" width="300"/>

8. Ta brique a désormais trois états :

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/trois_etats.png" alt="Placement" width="300"/>

#### Étape C : Ajouter la variable d'objet

1. Onglet **"Variables de l'objet"**
2. **Ajouter une variable** :
   - **Nom** : **`isDamaged`** ⚠️ (booléen, PAS un nombre !)
   - **Type** : `Booléen`
   - **Valeur initiale** : `false`

👉 **Note** : Cette variable booléenne suit si la brique a été frappée. `false` = intacte, `true` = endommagée au moins une fois.

---

### 4️⃣ Créer Yellow_Brick (2 animations, 1 variable)

#### Étape A : Dupliquer Blue_Brick

1. Clic droit sur **`Blue_Brick`** → **Dupliquer**
2. Renomme-le : **`Yellow_Brick`** ⚠️

#### Étape B : Modifier les animations

1. Double-clique sur **`Yellow_Brick`**
2. Onglet **"Animations"**

**Garde** : Animation **`Full`**

- Renomme-la : **`Full`** (garder le nom)

- Change l'image : **`Yellow_brick.png`**

**Garde** : Animation **`Damaged`**

- Nomme-la : **`Damaged`** (garder le nom)

- Change l'image : **`Yellow_brick_damaged.png`**

**Supprime** : Animation **`End`** (Yellow n'a que 2 états)

#### Étape C : Variable d'objet

Garde la même : **`isDamaged`** (booléen, `false`)

---

### 5️⃣ Placer les briques sur Level2

Structure du Level2 (basée sur le JSON) :



👉 Utilise le JSON comme référence pour les positions exactes (X et Y).

---

### 6️⃣ Mettre à jour les groupes d'objets

**Groupe `Bricks`** (ajoute les briques complexes) :

- ✅ `Red_Brick`

- ✅ `Green_Brick`

- ✅ `Blue_Brick` **← NOUVEAU**

- ✅ `Yellow_Brick` **← NOUVEAU**

**Groupe `Rebond`** (ajoute les briques complexes) :

- ✅ `Paddle`

- ✅ `Red_Brick`

- ✅ `Green_Brick`

- ✅ `Blue_Brick` **← NOUVEAU**

- ✅ `Yellow_Brick` **← NOUVEAU**

- ✅ `Wall`

---

## ⚽ Programmer les collisions {#collisions}

### 7️⃣ Collision avec Blue_Brick

**Événement** : Balle en collision avec Blue_Brick

1. **Ajouter un événement**
2. Condition : **"Collision"** → **"Au contact"**
   - `Ball` + `Blue_Brick`

3. **Actions** :

**Action A** : Jouer un son

- **"Sonore"** → **"Jouer un son"**

- Son : `touch-one.ogg`

**Action B** : Checker l'état de isDamaged et agir
