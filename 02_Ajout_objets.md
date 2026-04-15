## 🎨 Mise en place de la scène {#scène}

### Ajouter un fond (arrière-plan)

1. À droite de l'écran, cherche le panneau **"Objets"**
2. Clique sur **"Ajouter un objet"** (icône `+`)
3. Cherche et sélectionne un fond dans le Magazin de Ressources GDevelop
   - Cherche : **"Blue Space"** 
4. Nomme cet objet : `Background`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/blue_space.png" alt="Fond" width="700"/>

Ensuite, ajoute **Blue Space** sur ta scène et fais lui couvrir toute la scène (800×600)

---

## 🎯 Création des objets principaux

### Créer la raquette (Paddle)

#### Étape A : Ajouter l'objet Paddle

1. Va dans le panneau **"Objets"** à gauche
2. Clique sur **"Ajouter un objet"** (`+`)
3. Sélectionne **Nouvel objet à partir de zéro**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/nouvel_objet_zero.png" alt="Fond" width="300"/>
   
4. Sélectionne **"Sprite"**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/sprite.png" alt="Fond" width="300"/>

5. Nomme-le : **`Paddle`** ⚠️ (nom important, utilisé partout)

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/renommer_objet.png" alt="Fond" width="300"/>

6. Clique sur le bouton **Importer des images**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_importer_images.png" alt="Fond" width="300"/>

   - Va dans le dossier *`Assets`* et choisis une des raquette de ton choix
   - Taille idéale : **64×16 pixels** (largeur × hauteur)
     
7. Ton objet est créé.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objet_cree.png" alt="Fond" width="300"/>

8. Cliquer sur **Appliquer**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_appliquer.png" alt="Fond" width="300"/>

9. Ton objet est bien présent sur la scène.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objet_dans_scene.png" alt="Fond" width="300"/>


---

### 6️⃣ Créer la balle (Ball)

#### Étape A : Ajouter l'objet Ball

1. **Ajouter un objet** → **"Sprite"**
2. Nomme-le : **`Ball`** ⚠️ (nom important)
3. Sélectionne une **image circulaire/sphérique**
   - Cherche : "ball", "sphere", "orb", "bullet"
   - Taille : **16×16 ou 32×32 pixels**

#### Étape B : Ajouter une animation

1. Double-clique sur **`Ball`**
2. Onglet **"Animations"** → **"Ajouter une animation"**
3. Nomme-la : **`Normal`**
4. Ajoute l'image du sprite

#### Étape C : Ajouter un comportement physique

1. Toujours dans les propriétés de **`Ball`**
2. Section **"Comportements"** → **"Ajouter un comportement"**
3. Sélectionne **"Physique 2D"**
4. Configure les paramètres :
   - **Type d'objet** : `Dynamique`
   - **Gravité appliquée** : `Non` (important !)
   - **Peut se mettre en arrêt** : `Oui`
   - **Élasticité (rebond)** : `1` (rebond parfait)
   - **Friction** : `0` (pas de friction)
   - **Densité** : `1`

👉 **Pourquoi ces paramètres ?** Avec élasticité = 1 et friction = 0, la balle se comporte comme un vrai rebond arcade.

---

### 7️⃣ Créer les murs (Wall)

Les murs empêchent la balle de sortir des côtés et du haut.

1. **Ajouter un objet** → **"Tiled Sprite"**
2. Nomme-le : **`Wall`** ⚠️ (nom important)
3. Sélectionne une texture pour les murs
   - Cherche : "wall", "brick", "stone"
4. Ajoute une **animation** (Tiled Sprite en a besoin)
5. Ajoute le comportement **"Physique 2D"** :
   - **Type d'objet** : `Statique` (immobile)

Tu vas placer 3 instances de `Wall` :
- **Wall gauche** : X=0, Y=0, Width=16, Height=600

- **Wall droit** : X=784, Y=0, Width=16, Height=600

- **Wall haut** : X=0, Y=0, Width=800, Height=16

---

### 8️⃣ Créer les briques (Bricks)

**Pour le Level 1, tu crées SEULEMENT 2 types de briques :**

#### Étape A : Créer Red_Brick

1. **Ajouter un objet** → **"Sprite"**
2. Nomme-le : **`Red_Brick`** ⚠️ (nom exact)
3. Sélectionne une **image rectangulaire rouge**
   - Cherche : "brick red", "block red"
   - Taille : **64×32 pixels**
4. Ajoute une animation nommée **`Normal`**
5. Ajoute le comportement **"Physique 2D"** :
   - **Type** : `Statique` (ne se déplace pas)

#### Étape B : Créer Green_Brick

1. **Dupliquer** l'objet `Red_Brick` (clic droit → Dupliquer)
2. Renomme-le : **`Green_Brick`** ⚠️
3. Double-clique et change l'image pour une **version verte**
4. Garde les mêmes paramètres (animation, Physique 2D)

#### ❌ Pas de Yellow_Brick ni Blue_Brick pour le Level 1 !

Ces briques plus complexes arrivent au **Level 2**. Pour Level 1, on reste simple ! 🎯
