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
| 🎲 **11 images intégrées** | Ambiances **générées aléatoirement par canvas** (géométrique, coucher de soleil, vagues, forêt, océan, nuit étoilée, montagnes, aurore boréale, désert, abstrait, ville) + couleurs renouvelées à chaque génération — le jeu marche sans aucun fichier externe |
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

## ⚡ Performance

Optimisations clés (le 36×36 = 1 296 pièces doit rester fluide) :

- **Image déclarée une seule fois** via la variable CSS `--puzzle-img` héritée — jamais dupliquée dans le style des 1 296 pièces (≈117 Mo → ≈250 Ko, gain ×470 sur la mémoire et le recalcul de style).
- **Repositionnement léger** : un redimensionnement ne recrée plus les ~4 000 nœuds du DOM (les éléments existants sont simplement repositionnés) ; calcul des réserves sans rétroaction → pas de cascade ResizeObserver.
- **Grilles denses (≥ 100 pièces)** : classe `.dense` supprime les ombres portées par pièce (peinture divisée), contour léger à la place.
- Images importées réduites à 1024 px sur les grosses grilles (12×12+).

## 🧪 Tests

Deux suites de tests automatisés (jsdom) valident le rendu, le mélange, l'aimantation, le glisser-déposer complet, la victoire, les changements de niveau jusqu'au 36×36, **les optimisations mémoire/perf** et **les 11 ambiances de la galerie procédurale** : **57 + 28 assertions, toutes vertes (85/85)**.
