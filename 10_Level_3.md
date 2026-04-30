
# Level 3 — Consignes de création

## 1. Duplique le Level 2

Crée le `Level3` à partir du `Level2` afin de conserver :

- le gameplay
- les collisions
- le système de score
- les comportements des briques
- les événements existants

Le Level 3 est une évolution directe du niveau précédent.  
Clique donc sur les trois petits points en face de la scène `Level2` et clique sur **Dupliquer**. 

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/trois_niveaux.png" alt="level2" width="400"/>

---

## 2. Modifie le layout des bricks

Change la disposition des briques sur la scène pour varier le niveau.

Objectif :

- proposer une nouvelle lecture du terrain
- éviter une simple répétition du Level 2

---

### Important

Ne mets pas trop de briques complexes ou résistantes dans dans ce niveau car :

- les briques descendent progressivement vers le joueur
- le joueur doit avoir le temps de nettoyer le terrain

Le niveau doit rester tendu, dynamique mais toujours faisable.

---

### Recommandation de level design

Privilégie :

- des lignes simples
- quelques trous dans la formation
- des patterns lisibles
- peu de briques multi-hit

---

## 3. Créer un chrono de scène

Dans le bloc de code de départ `Au lancement du niveau`, ajoute une nouvelle action : **Démarrer (ou réinitialiser) un chronomètre de scène**.  
Appelle le `BrickDropTimer`.  

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/lancer_chrono.png" alt="level2" width="600"/>

---

## 4. Faire descendre les bricks

Toutes les 10 secondes, tu vas déplacer le groupe de `Bricks` de 20px en direction du joueur.

#### Condition
 - Chronomètre `BrickDropTimer` >= 10 secondes

#### Actions

 - Changer la position Y de `Bricks` : ajouter 20px
 - Réinitialiser le chronomètre `BrickDropTimer`

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/10_secondes.png" alt="level2" width="900"/>

---

## 5. Nouvelle condition de défaite

Si les `Bricks` sont trop basses et que le joueur n'a pas réussi à tout détruire, alors nous allons ajouter une nouvelle condition de défaite !  
Pour cela, surveille la position Y de ton groupe `Bricks` !

#### Condition

  - Si la position Y de `Bricks` >= 500 *(par exemple, la coordonnée peut être différente)*

#### Actions

  - Change l'animation de `Life1`, `Life2`, `Life3` à `Empty` pour bien signifier que la partie est perdue
  - Supprime le `Paddle`
  - Supprime la `Ball`
  - Joue un son de mort *si tu en as un*
  - Change le texte de **Main_Text** à `Game Over` *si tu l'as créé à l'étape 8*
  - Relance le niveau !

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/code_bricks_basses.png" alt="level2" width="900"/>

---

## 6. Fin du niveau

Quand toutes les briques sont détruites, n'oublie pas :

 - d'arrêter le chronomètre de scène
 - de gérer le score comme d'habitude (comme tu as dupliqué le level 2, cela devrait déjà être bon)
 - d'aller au dernier niveau, le `level 4`

### Important

Le timer doit être stoppé avant :

 - la transition
 - le message de victoire
 - le changement de scène

Sinon les briques pourraient encore bouger pendant la fin du niveau.

### Progression

Le Level 3 doit créer une pression progressive :

 - plus le temps passe
 - plus les briques se rapprochent du joueur

Si tu vois que le niveau 3 est trop simple, ajoute quelques `Bricks` !  
Ou fais descendre tes `Bricks` plus vite !
