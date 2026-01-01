# Memory Game - Vue.js

> Jeu Memory développé avec Vue.js 3 (Composition API) dans le cadre d'un projet B2-DEV à l'EFREI

## Description du projet

Application web permettant de jouer au jeu Memory classique où le joueur doit retrouver des paires de cartes identiques en les retournant deux par deux.

### Principe du jeu
1. Les cartes sont disposées face cachée en forme de grille
2. À chaque tour, le joueur retourne 2 cartes
3. Si elles sont identiques, elles restent visibles
4. Sinon, elles se retournent à nouveau
5. Le jeu continue jusqu'à ce que toutes les paires soient découvertes
6. Le joueur peut enregistrer son score avec son pseudo

---

## Fonctionnalités

### Fonctionnalités obligatoires
- Jeu entièrement fonctionnel avec possibilité de faire plusieurs parties
- Choix du niveau de difficulté : 4x4, 5x5 ou 6x6
- Disposition aléatoire des cartes à chaque nouvelle partie
- Menu principal avec options de jeu
- Enregistrement du pseudo en fin de partie
- Affichage de l'historique des parties (pseudo, difficulté, temps, nombre d'essais)
- Tri de l'historique des parties
- Modification du pseudo après la partie
- Suppression d'une partie ou reset complet de l'historique
- Interface ergonomique et agréable

### Fonctionnalités bonus (optionnel)
- Design personnalisé et soigné
- Thème de cartes personnalisé
- Animations et effets visuels
- Système de score avancé
- *(Ajoutez ici vos propres fonctionnalités)*

---

## Technologies utilisées

- **Vue.js 3** (Composition API)
- **Vue Router** (Navigation entre les pages)
- **CSS3** (Styling et animations)
- **LocalStorage** (Sauvegarde des parties)

---

## Installation

### Prérequis
- Node.js (version 16 ou supérieure)
- npm ou yarn

### Étapes d'installation

1. **Cloner le repository**
```bash
git clone https://github.com/VOTRE-USERNAME/memory_game.git
cd memory_game
```

2. **Installer les dépendances**
```bash
npm install
# ou
yarn install
```

3. **Lancer le serveur de développement**
```bash
npm run dev
# ou
yarn dev
```

4. **Ouvrir l'application dans le navigateur**
```
http://localhost:5173
```

---

## Utilisation

### Démarrer une partie
1. Depuis le menu principal, cliquer sur "Nouvelle Partie"
2. Choisir le niveau de difficulté (4x4, 5x5 ou 6x6)
3. Cliquer sur deux cartes pour les retourner
4. Mémoriser leur position et trouver les paires
5. Continuer jusqu'à découvrir toutes les cartes

### Consulter l'historique
1. Depuis le menu principal, cliquer sur "Historique"
2. Voir toutes les parties jouées avec :
   - Pseudo du joueur
   - Niveau de difficulté
   - Temps écoulé
   - Nombre d'essais
3. Trier la liste selon vos préférences
4. Modifier un pseudo ou supprimer une partie

---

## Structure du projet

```
memory_game/
├── public/              # Fichiers statiques
├── src/
│   ├── assets/         # Images, icônes, etc.
│   ├── components/     # Composants Vue réutilisables
│   │   ├── Card.vue
│   │   ├── GameBoard.vue
│   │   ├── ScoreBoard.vue
│   │   ├── DifficultySelector.vue
│   │   └── HistoryList.vue
│   ├── views/          # Pages de l'application
│   │   ├── Home.vue
│   │   ├── Game.vue
│   │   └── History.vue
│   ├── router/         # Configuration du routeur
│   │   └── index.js
│   ├── stores/         # Gestion d'état (si nécessaire)
│   ├── App.vue         # Composant racine
│   └── main.js         # Point d'entrée
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

---

## Guide de développement

### Étapes de réalisation recommandées

#### Phase 1 : Setup et structure de base
- [ ] Initialiser le projet Vue.js avec Vite
- [ ] Configurer Vue Router
- [ ] Créer la structure de dossiers
- [ ] Créer les composants de base (vides)

#### Phase 2 : Logique du jeu
- [ ] Créer le composant Card (carte retournable)
- [ ] Implémenter la logique de retournement des cartes
- [ ] Gérer la détection des paires
- [ ] Créer la grille de jeu avec différentes tailles
- [ ] Implémenter la disposition aléatoire des cartes

#### Phase 3 : Interface utilisateur
- [ ] Créer le menu principal
- [ ] Créer le sélecteur de difficulté
- [ ] Afficher le timer et le compteur d'essais
- [ ] Créer le formulaire de saisie du pseudo
- [ ] Styliser l'ensemble de l'application

#### Phase 4 : Gestion des données
- [ ] Implémenter le LocalStorage pour sauvegarder les parties
- [ ] Créer la page d'historique
- [ ] Ajouter le tri de l'historique
- [ ] Permettre la modification des pseudos
- [ ] Implémenter la suppression des parties

#### Phase 5 : Finitions
- [ ] Tester l'application (mode "zéro bug")
- [ ] Optimiser les performances
- [ ] Ajouter des commentaires au code
- [ ] Vérifier la qualité du code
- [ ] Ajouter des animations (bonus)
