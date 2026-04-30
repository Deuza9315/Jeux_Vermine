# Documentation Technique

## Architecture

Le projet VERMINE est un jeu monolithique HTML/CSS/JS sans dépendances externes.

### Structure

```
vermine.html (230 Ko)
├── HTML5 Structure
├── CSS3 (Styling + Animations)
├── JavaScript (Gameplay)
├── Web Audio API (Sound)
└── Assets (Base64 embedded)
```

## Technologies

### HTML5
- Structure sémantique
- Canvas API (non utilisée, rendu DOM)
- localStorage pour la persistence

### CSS3
- Grid + Flexbox pour le layout
- Animations keyframes pour les sprites
- box-shadow pour le pixel art (chauve-souris)
- Dégradés radiaux pour les effets

### JavaScript Vanilla
- Boucle de jeu (requestAnimationFrame)
- Détection de collisions (AABB - Axis-Aligned Bounding Box)
- Gestion d'état simple
- Event listeners pour les contrôles

### Web Audio API
- Générateurs d'oscillateurs (sine, square, sawtooth)
- Enveloppe d'amplitude
- Bruit blanc (buffers aléatoires)
- Zéro fichier audio externe

## Logique de Jeu

### Game Loop
```
1. Capture input (clavier)
2. Update positions
3. Check collisions
4. Update UI
5. Render
```

### Système de Collision
- AABB simple (rectangles)
- Check chaque ennemi vs joueur chaque frame
- Hitbox customisée par ennemi type

### Spawn System
- Spawn d'ennemis toutes les 0.5-2 secondes
- Vitesse et fréquence augmentent avec le score
- Bonus spawn toutes les 6-12 secondes
- Positions aléatoires aux bords de l'écran

### Scoring
- 1 point par 10 ms de survie
- `score = Math.floor(timeSurvived / 10)`
- Top 5 sauvegardé en localStorage

## Optimisations

- DOM minimal (16 éléments max en même temps)
- RAF throttling (60fps max)
- Pas d'alloc/dealloc en boucle (object pools)
- CSS transforms pour les animations (GPU)
- Événements délégués

## Limitations et Compromis

### Pas de Canvas
- Plus simple avec DOM
- Animation CSS native
- Meilleure accessibilité

### Monofichier
- Embeds tout en Base64
- Zéro requête HTTP
- Partage facile
- Payload unique (230 Ko)

### localStorage
- Persistance locale uniquement
- Pas de cloud sync
- Limite 5-10 Mo par domaine

## Performances

- FPS constant 60
- Memory usage < 50 Mo
- CPU usage < 5% idle
- Compatible tous navigateurs modernes

## Fichiers Assets Embarqués

- Sprites PNG/GIF encodés en Base64
- Aucune requête externe
- Temps de chargement < 100ms

## Debugging

Ouvre console (F12) et utilise:
- `window.gameState` pour l'état actuel
- `window.DEBUG = true` pour les logs additionnels
