## Perte d'une vie

### Créer la variable de vie

- Sur l'objet **Paddle**, ajoute une variable `Life` et la définir à *3* points

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/variable_life.png" alt="Life" width="800"/>

### Créer visuellement la barre de vie

- Dans le Magasin de ressources, ajoute l'objet **Life**

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/objet_life.png" alt="Life" width="600"/>

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

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/position_ball_y.png" alt="Life" width="400"/>

**Actions** :

**Action 8.1** : Modifier la variable `GameState`à `"Wait"`. Cela va mettre le jeu en suspens.

**Action 8.2** : Supprimer une vie

- Cherche **"Variables"** → **"Modifier une variable de scène"**

- Variable : `Life`

- Opération : `-` (Soustraire)

- Valeur : `1`

**Action 8.3** : Supprimer (*Éteindre*) un sprite de vie

Tu vas utiliser un **sous-événement** pour choisir quel `Life` supprimer.

- **Ajouter un sous-événement** → **"Comparaison"**
  - **Condition** : `Life` `=` `2`
  - **Action** : Changer l'**animation** `Life3` et la passer à *Empty*
 
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/life2_visuel.png" alt="Life" width="400"/>

- **Ajouter un sous-événement** → **"Comparaison"**
  - **Condition** : `Life` `=` `1`
  - **Action** : Changer l'**animation** `Life2` et la passer à *Empty*

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/life1_visuel.png" alt="Life" width="400"/>

- **Ajouter un sous-événement** → **"Comparaison"**
  - **Condition** : `Life` `=` `0`
  - **Actions** :
      - Changer l'**animation** `Life1` et la passer à *Empty*
      - Supprimer les objets `Paddle` et `Ball`
      - Attendre `1s`
      - Relancer la scène
   
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/game_over.png" alt="Life" width="400"/>
