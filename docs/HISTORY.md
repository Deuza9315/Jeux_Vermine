# Historique du Projet VERMINE

## Genèse

VERMINE est né d'une envie simple: créer un jeu jouable immédiatement, sans installation, dans un navigateur, sans serveur.

## Phase 1: Concept (Avril 2026)

- **Inspiration**: Jeux arcade classiques (Pac-Man, Galaga)
- **Décision 1**: HTML/CSS/JS vanilla (zéro dépendances)
- **Décision 2**: Un seul fichier HTML (partage facile)
- **Décision 3**: Thème "ruelle de banlieue" pour l'ambiance

### Première Itération
- Simple carré jaune vs ennemis
- Murs de briques CSS
- Collisions AABB basiques

## Phase 2: Ennemis (Avril 27-30, 2026)

### Chauve-souris
- Technique: CSS pure avec box-shadow
- Challenge: Animer 50+ éléments simultanement
- Solution: 7 frames sur une grille 10×10

### Serpent à Sonnette
- Source: PixelLab.ai
- Édition: Piskel
- Caractère: Mouvement ondulant

### Araignée
- 16 sprites générés par IA
- Conversion PNG → GIF en Python
- Effet: Poussière sous les pattes

## Phase 3: Mécaniques (Mai 1-3, 2026)

### Bonus System
- +Vie (simple, utile)
- Ralenti (gameplay changer)
- Bouclier (tactique)
- Bombe (climax moment)

### Audio API
- Web Audio API pour zéro fichier externe
- 6 sons générés en temps réel
- Enveloppes d'amplitude

### Leaderboard
- localStorage pour persistence
- Top 5 avec surlignage du joueur
- Pseudo sauvegardé

## Phase 4: Polish & Documentation (Mai 4-5, 2026)

- README complet
- Guides techniques et gameplay
- FAQ et troubleshooting
- Architecture documentée

## Points Clés de Développement

### Choix Technologiques
1. **Pas de Canvas**: DOM + CSS = Plus simple, animations natives
2. **Monofichier**: Base64 encoding, zéro HTTP requests
3. **Vanilla JS**: Zéro overhead, code transparent
4. **Web Audio**: Générative, paramétrable, efficace

### Optimisations
- requestAnimationFrame pour 60 FPS
- Pas d'allocation dynamique en boucle
- CSS transforms (GPU accélérées)
- Minimal DOM repaint

### Design Decisions
- Carrés simples: hitboxes évidentes
- Pixel art: compatibilité esthétique
- Couleurs primaires: lisibilité maxima
- Sons rétro: ambiance arcade

## Statistiques

- **Temps de développement**: ~5 jours
- **Taille fichier**: ~230 Ko
- **Lignes de code**: ~1300 lines HTML
- **Zéro dépendances**: ✅
- **Cross-browser**: ✅
- **Performance**: 60 FPS stable

## Moments Mémorables

1. **CSS Box-Shadow Sprite**: "C'est possible?!" → "Oh wow!"
2. **Web Audio Synthesis**: Premier son généré en temps réel
3. **localStorage Leaderboard**: Persistance locale = 🎉
4. **Décor SVG**: Graffitis qui font l'ambiance

## Inspiration et Crédit

- **Box-shadow technique**: @thecodetutor (CodePen)
- **Sprites IA**: PixelLab.ai
- **Animation sprites**: Piskel
- **Pixel art style**: Tradition arcade 8-bit

## Futur

La roadmap inclut:
- Mode mobile tactile
- Difficultés progressives
- Nouveaux ennemis
- Ambiance sonore
- Particules dynamiques
- Boss fights

Mais le core loop du jeu? C'est déjà bon. 🎮

---

**Made with ❤️ in 2026**
