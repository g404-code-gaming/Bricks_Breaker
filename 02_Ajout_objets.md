## 🎨 Mise en place de la scène

### Ajouter un arrière-plan

1. À droite de l'écran, cherche le panneau **"Objets"**
2. Clique sur **"Ajouter un objet"** (icône `+`)
3. Cherche et sélectionne un fond dans le Magazin de Ressources GDevelop
   - Cherche : **"Blue Space"** 
4. Nomme cet objet : `Background`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/blue_space.png" alt="Fond" width="600"/>

Ensuite, ajoute **Blue Space** sur ta scène et fais lui couvrir toute la scène (800×600)

---

## 🎯 Création des objets principaux

### Étape A : Ajouter l'objet Paddle

1. Va dans le panneau **"Objets"** à gauche
2. Clique sur **"Ajouter un objet"** (`+`)
3. Sélectionne **Nouvel objet à partir de zéro**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/nouvel_objet_zero.png" alt="Fond" width="300"/>
   
4. Sélectionne **"Sprite"**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/sprite.png" alt="Fond" width="300"/>

5. Nomme-le : **`Paddle`** ⚠️ (nom important, utilisé partout)

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/paddle_objet.png" alt="Fond" width="300"/>

6. Clique sur le bouton **Importer des images**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_importer_images.png" alt="Fond" width="300"/>

   - Va dans le dossier *`Assets`* et choisis une des raquette de ton choix
   - Taille idéale : **64×16 pixels** (largeur × hauteur)
     
7. Ton objet est créé.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/paddle_en_place.png" alt="Fond" width="300"/>

8. Clique sur **Appliquer**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bouton_appliquer.png" alt="Fond" width="300"/>

9. Ton objet est bien présent sur la scène.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/paddle_nom.png" alt="Fond" width="300"/>


⚠️ **Nous allons répéter l'opération pour la `Ball`et les `Bricks`**

### Étape B : Ajouter l'objet Ball

1. **Ajouter un objet** → **"Sprite"**
2. Nomme-le : **`Ball`**
3. Sélectionne l'objet :
   - Va dans le dossier *`Assets`* et choisis la `Ball`
   - Taille idéale : **8×8 pixels** (largeur × hauteur)
4. Ajoute-lui un comporterment : **Rebond** (ou **Bounce** en anglais) et clique sur **Appliquer**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/ball.png" alt="Fond" width="300"/>  

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/bounce.png" alt="Fond" width="600"/>  

### Étape C : Créer Red_Brick

1. **Ajouter un objet** → **"Sprite"**
2. Nomme-le : **`Red_Brick`**
3. Sélectionne l'objet :
   - Va dans le dossier *`Assets`* et choisis `Red_brick`
   - Taille : **32×16 pixels**
4. **Appliquer**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/red_brick.png" alt="Fond" width="300"/>  

### Étape D : Créer Green_Brick

1. **Ajouter un objet** → **"Sprite"**
2. Nomme-le : **`Green_Brick`**
3. Sélectionne l'objet :
   - Va dans le dossier *`Assets`* et choisis `Green_brick`
   - Taille : **32×16 pixels**
4. **Appliquer**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/green_brick.png" alt="Fond" width="300"/>  

**Pour le Level 1, tu crées SEULEMENT 2 types de briques :**

#### ❌ Pas de Yellow_Brick ni Blue_Brick pour le Level 1 !

Ces briques plus complexes arrivent au **Level 2**. Pour Level 1, on reste simple ! 🎯

### Étape E : Ajouter les murs

Les murs empêchent la balle de sortir des côtés et du haut.

1. **Ajouter un objet** → Magazin de Ressources
2. Cherche la série d'objets `Dungeon` ou tape *`Wall`* dans la barre de recherche
3. Sélectionne plusieurs murs de manière à construre un espace fermé **carré** qui te servira de scène.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/serie_dungeon.png" alt="Fond" width="600"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/wall_corner.png" alt="Fond" width="600"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/wall_side_mid_right.png" alt="Fond" width="600"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/wall_corner_top_right.png" alt="Fond" width="600"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/wall_top_mid.png" alt="Fond" width="600"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/wall_side_mid_left.png" alt="Fond" width="600"/>


Le but sera d'obtenir ce genre de résultat : 

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/mur.png" alt="Fond" width="600"/>

