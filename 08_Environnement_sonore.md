# Environnement sonore et Main Text

### Un peu d'histoire

Dans les jeux d’arcade des années 1970 comme Breakout, l’environnement sonore est extrêmement minimaliste : il se limite généralement à quelques bruitages simples (rebond, collision, score), sans musique de fond. Cette austérité s’explique par les contraintes techniques des machines, qui ne disposaient souvent que d’un seul canal audio très basique.  

Le son a alors une fonction purement utilitaire : donner un retour immédiat au joueur plutôt que créer une ambiance immersive.
À cette époque, l’identité sonore du jeu repose donc davantage sur le rythme des actions et la répétition des effets que sur une composition musicale.

### Ajouter des bruitages

Dans le dossier `sounds`, tu trouveras des exemples de sons utilisables pour ton jeu.  

Mais tu es libre :

- de créer tes sons directement sur gDevelop avec **jfxr**
- d'aller chercher d'autres sons sur des bibliothèques de sons libres. Fais une recherche *8 bits sound library* sur le web, tu trouveras ton bonheur !

Tu vas pouvoir placer des sons à des moments clés du **gameplay** de ton jeu : rebond de la `Ball`, `Brick` touchée ou brisée, perte d'une vie, `game over`,  etc...


# Main_Text

`Main_Text` est un objet de type **Text** dans GDevelop.

Il est placé au centre de l’écran et sert à afficher les messages importants du jeu au joueur.

## Rôle principal

L’objet change de valeur selon l’état du jeu :

- `"Up to Play"` → au début de la partie
- `"You Win"` / `"Well Done"` → quand le joueur gagne
- `"Game Over"` → quand le joueur perd
- `""` (texte vide) → pendant le gameplay

## Fonctionnement

Le texte est modifié dynamiquement avec des actions du type :

```text
Modifier le texte de Main_Text
```
<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/well_done" alt="Connexion" width="500"/>

Selon certaines conditions :

  - début de partie
  - victoire
  - défaite
  - attente avant relance

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/game_over_png" alt="Connexion" width="500"/>

## Visibilité pendant le jeu

`Main_Text` doit :

 - être visible lors des étapes importantes
 - être caché pendant le gameplay normal

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/cacher_main_text_png" alt="Connexion" width="800"/>
