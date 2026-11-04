# 🧩 Puzzle Studio

Jeu de puzzle interactif **complet et autonome** — un seul fichier `index.html` (HTML + CSS + JavaScript), zéro dépendance, fonctionne hors ligne.

## 🚀 Lancer le jeu

- **Option 1** : ouvrir `index.html` directement dans un navigateur (double-clic).
- **Option 2** : servir le dossier :
  ```bash
  python3 -m http.server 8000
  # puis ouvrir http://localhost:8000
  ```

## ✨ Fonctionnalités

| Fonctionnalité | Détail |
|---|---|
| 📤 **Import d'image** | « Téléimporter une image » : l'image de l'appareil est redimensionnée (max 1600 px) puis découpée dynamiquement selon la grille |
| 🎲 **Images intégrées** | 3 ambiances générées aléatoirement (géométrique, coucher de soleil, vagues) — le jeu marche sans aucun fichier externe |
| 🎚️ **6 niveaux** | Facile 3×3 · Moyen 4×4 · Difficile 5×5 · Expert 6×6 · Maître 12×12 · Légendaire 36×36 (1 296 pièces) |
| 🖱️ **Glisser-déposer** | Pointer Events (souris, tactile, stylet) avec aimantation (*snap*) près du bon emplacement |
| 👆 **Mode clic** | 1ᵉʳ clic = sélection + surlignage de l'emplacement · 2ᵉ clic (pièce ou emplacement) = pose directe |
| 📊 **Statistiques** | Chronomètre, compteur de coups, pièces placées, barre de progression |
| 🏆 **Victoire** | Modale de félicitations + confettis + son |
| 📱 **Responsive** | Mise en page adaptée ordinateur / tablette / mobile, repositionnement automatique à redimensionnement |
| 🔊 **Son** | Effets audio WebAudio, activables/désactivables |

## 🎮 Commandes

- **Glisser** une pièce vers son emplacement → elle s'aimante (l'emplacement pulse en cyan quand on approche).
- **Cliquer** une pièce puis son emplacement (ou cliquer 2 fois la pièce) pour la poser sans glisser.
- 🔀 **Recommencer** : remélanger · 🎲 **Nouvelle image** : autre ambiance · 👁️ : voir l'image complète.

## 🧪 Tests

Deux suites de tests automatisés (jsdom) valident le rendu, le mélange, l'aimantation, le glisser-déposer complet, la victoire et les changements de niveau jusqu'au 36×36 : **47 + 29 assertions, toutes vertes**.
