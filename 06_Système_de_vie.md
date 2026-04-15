## Perte d'une vie

### Créer la variable de vie

- Sur l'objet **Paddle**, ajoute une variable `Life` et la définir à *3* points

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_life.png" alt="Life" width="400"/>

### Créer visuellement la barre de vie

- Dans le Magasin de ressources, ajoute l'objet **Life**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objet_life.png" alt="Life" width="400"/>

- Renomme le *Life1* puis duplique le **deux fois** pour obtenir *Life2* et *Life3*

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objets_life_scene.png" alt="Life" width="400"/>

- Place les trois objets sur la scène dans ton cadre de gauche (aide-toi de la *grille* pour les aligner)

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/life_scene_visuel.png" alt="Life" width="400"/>

- Dans ton code, au **lancement de la scène**, place l'animation des objets *Life1*, *Life2*, *Life3* à **Full**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/lancement_life.png" alt="Life" width="400"/>

### Gérer la variable de vie

**Condition** : La balle sort du bas de l'écran (Y > 560)

1. **Ajouter un événement**
2. Cherche **"Position Y"**
3. Objet : `Ball`
4. Propriété : `Position Y` (position verticale)
5. Condition : `>` (plus grand que)
6. Valeur : `560` (sous la raquette)

**Actions** :

**Action 8.1** : Réduire une vie

- Cherche **"Variables"** → **"Modifier une variable de scène"**

- Variable : `playerLives`

- Opération : `-`

- Valeur : `1`

**Action 8.2** : Supprimer un sprite de vie

C'est plus complexe. Tu vas utiliser un **sous-événement** pour choisir quel `Life` supprimer.

- **Ajouter un sous-événement** → **"Comparaison"**
  - `playerLives` `=` `2`
  - **Action** : Supprimer `Life3`

- **Ajouter un sous-événement** → **"Comparaison"**
  - `playerLives` `=` `1`
  - **Action** : Supprimer `Life2`

- **Ajouter un sous-événement** → **"Comparaison"**
  - `playerLives` `=` `0`
  - **Action** : Aller vers la scène **"GameOver"** (tu la créeras plus tard)

**Action 8.3** : Replacer la balle

- Cherche **"Position"**

- Objet : `Ball`

- X : `400`

- Y : `480`

**Action 8.4** : Immobiliser la balle

- Cherche **"Physique 2D"** → **"Arrêter l'objet"**
- Objet : `Ball`

**Action 8.5** : Repositionner le Paddle au centre
- Cherche **"Position"**

- Objet : `Paddle`

- X : `400`

- Y : `540`
