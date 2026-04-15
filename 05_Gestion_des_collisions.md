## ⚽ Gestion de la balle et des collisions

Maintenant tu vas programmer les **événements** (conditions + actions).

### Événement d'initialisation (Au démarrage)

#### Événement 1 : "Au lancement de la scène"

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/action_lancement_scene.png" alt="Action" width="500"/>

1. Clique sur l'onglet **"Événements"**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/ajout_evenement.png" alt="Action" width="500"/>

2. **Ajouter un événement** → **"Au lancement de la scène"**

Ajoute les actions suivantes :

**Action 1.1** : Initialiser le score
- **"Ajouter une action"**
- Cherche **"Variables"** → **"Modifier une variable de scène"**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/icone_variables_scene.png" alt="Action" width="100"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_scenescore.png" alt="Action" width="700"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_scenescore_detail.png" alt="Action" width="300"/>

- Variable : `sceneScore`
- Opération : `=`
- Valeur : `0`

**Action 1.2** : Gérer le lancement du jeu

Ici, nous allons créer une variable qui va nous permettre de gérer l'état du jeu (*non démarré*, *en cours*, *en pause*).

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_gamestate.png" alt="Action" width="700"/>

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_gamestate_detail.png" alt="Action" width="300"/>

- **"Ajouter une action"**
- Cherche **"Variables"** → **"Modifier une variable de scène"**

- Variable : `GameState`
- Opération : `=`
- Valeur : `"NotStarted"`

**Action 1.3** : Positionner la raquette au centre-bas

- **"Ajouter une action"**

- Objet : `Paddle`
- Cherche **"Position"**
- X : `464`
- Y : `528`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/position_paddle.png" alt="Action" width="400"/>

**Action 1.4** : Positionner la balle au-dessus du Paddle

---

### Événement 2 : Contrôle du Paddle (Flèche GAUCHE)

1. **Ajouter un événement**
2. Cherche **"Clavier"** → **"Touche pressée"**
3. Sélectionne **"Left"** (flèche gauche)
4. **Ajoute une action** :
   - Cherche **Ajouter une force (angle)**
   - Objet : `Paddle`
   - Angle : `180`
   - Vitesse : `300`
  
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/touche_left.png" alt="Action" width="900"/>


**Action supplémentaire** : Limiter le Paddle à ne pas dépasser le mur gauche


---

### Événement 3 : Contrôle du Paddle (Flèche DROITE)

Même chose que l'événement 2, mais :

1. Touche : **"Right"** (flèche droite)
2. Action : **Ajouter une force (angle)**
   - Angle : `0` (vers la droite)
   - Vitesse : `300`

  
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/touche_right.png" alt="Action" width="900"/>

---

### 1️⃣7️⃣ Événement 4 : Lancer la balle

**Conditions** :
1. La balle est **en arrêt** (immobile)
2. La touche **Up** (flèche haut) est **enfoncée**

  
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/conditions_ball.png" alt="Action" width="400"/>

1. **Ajouter un événement**
2. **Condition 1** : Cherche **"Objet en arrêt"**
   - Objet : `Ball`
3. **Condition 2** : Cherche **"Clavier"** → **"Touche pressée"**
   - Touche : **"Up"** (flèche haut)
4. **Action** :
   - Cherche **"Ajouter une force (angle)"** 
   - Objet : `Ball`
   - Angle : `-45+RandomInRange(-10,10)` (vers le haut ± variation aléatoire)
   - Vitesse : `300`
   - *Permanente*
  
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/random_ball.png" alt="Action" width="800"/>

👉 **RandomInRange** : Ajoute une variation aléatoire (-15 à +15°) pour que chaque lancement soit légèrement différent.

---

### 1️⃣8️⃣ Événement 5 : Rebonds de la balle

**Condition** : La balle entre en **collision** avec les objets du groupe `Rebond`

1. **Ajouter un événement**
2. Cherche **"Collision"** → **"Au contact"** (ou "In collision with")
3. **Premier objet** : `Ball`
4. **Deuxième objet** : Groupe **`Rebond`**
5. **Action** :
   - Cherche **"Physique 2D"** → **"Rebondir"** (ou "Bounce")
   - L'action gère **automatiquement** les rebonds !

👉 **Magie de gDevelop** : La fonction "Rebondir" calcule automatiquement l'angle et la direction du rebond. Pas besoin de physique complexe ! 🎯

---

### 1️⃣9️⃣ Événement 6 : Détruire Red_Brick

**Condition** : La balle touche une brique rouge.

1. **Ajouter un événement**
2. **Collision** → **"Au contact"**
3. `Ball` + `Red_Brick`
4. **Actions** :

   **Action 6.1** : Jouer un son (optionnel)
   - Cherche **"Sonore"** → **"Jouer un son"**
   - Son : Cherche dans les ressources (ex: `touch.ogg`, `pop.ogg`)

   **Action 6.2** : Supprimer la brique
   - Cherche **"Objet"** → **"Supprimer l'objet"**
   - Objet : `Red_Brick`

   **Action 6.3** : Ajouter 5 points
   - Cherche **"Variables"** → **"Modifier une variable de scène"**
   - Variable : `sceneScore`
   - Opération : `+`
   - Valeur : `5`

   **Action 6.4** : Mettre à jour l'affichage du score
   - Cherche **"Texte"** → **"Modifier le texte"**
   - Objet : `The_Score`
   - Texte : `ToString(Variable(sceneScore))`

---

### 2️⃣0️⃣ Événement 7 : Détruire Green_Brick

**Identique à l'Événement 6**, sauf :

1. Collision : `Ball` + `Green_Brick`
2. Objet à supprimer : `Green_Brick`
3. Points à ajouter : `8` (un peu plus que le rouge pour récompenser)
4. Le reste reste identique

---
