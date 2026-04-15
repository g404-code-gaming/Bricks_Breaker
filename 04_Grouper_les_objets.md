### Créer les groupes d'objets

Les groupes permettent de programmer les collisions une seule fois au lieu de 4 fois !

#### Groupe 1 : `Bricks` (toutes les briques cassables)

1. En bas à droite, cherche l'onglet **"Groupes d'objets"** (ou **"Object groups"**)
2. Clique sur **"Ajouter un groupe"**
3. Nomme-le : **`Bricks`** ⚠️ (nom exact)
4. Ajoute ces objets au groupe :
   - ✅ `Red_Brick`
   - ✅ `Green_Brick`

#### Groupe 2 : `Rebond` (objets avec lesquels la balle rebondit)

1. **Ajouter un groupe**
2. Nomme-le : **`Rebond`** ⚠️ (nom exact)
3. Ajoute :
   - ✅ `Paddle` (la raquette)
   - ✅ `Red_Brick`
   - ✅ `Green_Brick`
   - ✅ `Wall` (les murs)

👉 **Logique** : Le groupe `Bricks` pour détruire et scorer, le groupe `Rebond` pour gérer les rebonds de la balle.

<img src="https://sebastien-devos.fr/img/codegaming/bricksbreaker/groupe_objets.png" alt="Fond" width="400"/>
