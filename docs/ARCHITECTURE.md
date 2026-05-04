# Architecture et Design du Jeu

## Vue d'Ensemble

VERMINE est une application monolithique HTML/CSS/JavaScript vanilla.

```
vermine.html (230 KB)
├── HTML Structure
│   ├── #game-container (viewport principal)
│   ├── #game-area (zone de jeu)
│   ├── UI elements (score, lives, leaderboard)
│   └── Hidden assets (graffitis SVG)
│
├── CSS Styling & Animation
│   ├── Décor (murs, poubelles, graffitis)
│   ├── Sprites enemies (chauve-souris, serpent, araignée)
│   ├── Animations keyframes
│   └── Responsive layout
│
└── JavaScript Game Logic
    ├── Game state management
    ├── Input handling
    ├── Update loop
    ├── Collision detection
    ├── Audio synthesis
    └── UI rendering
```

## État du Jeu (Game State)

```javascript
gameState = {
  // Joueur
  player: {
    x: number,        // Position X
    y: number,        // Position Y
    width: 20,        // Hitbox width
    height: 20,       // Hitbox height
    invincible: false, // Protection temporaire?
    invincibleTime: 0  // Timer
  },

  // Progression
  lives: number,      // Vies actuelles (1-5)
  score: number,      // Score = temps × 10
  timeStarted: timestamp,

  // Ennemis
  enemies: [
    {
      type: 'bat'|'snake'|'spider',
      x: number,
      y: number,
      vx: number,  // Vélocité X
      vy: number,  // Vélocité Y
      width: number,
      height: number,
      animationFrame: number
    }
    // ... plus d'ennemis
  ],

  // Bonus
  bonuses: [
    {
      type: '+life'|'slowdown'|'shield'|'bomb',
      x: number,
      y: number,
      width: 30,
      height: 30
    }
    // ... plus de bonus
  ],

  // Activations actuelles
  activeBonus: {
    shield: false,      // Bouclier activé?
    shieldTime: 0,      // Durée restante
    slowdown: false,    // Ralenti activé?
    slowdownTime: 0     // Durée restante
  },

  // UI
  gameOver: false,
  paused: false,
  pseudo: 'Joueur'
};
```

## Boucle de Jeu (Game Loop)

```
┌─────────────────────────────────────┐
│  requestAnimationFrame(gameLoop)    │
├─────────────────────────────────────┤
│ 1. Capture Input                    │
│    - Lire keysPressed               │
│    - Appliquer mouvement joueur     │
│                                     │
│ 2. Update Logic                     │
│    - Mise à jour ennemis            │
│    - Spawn new ennemis (aléatoire)  │
│    - Mise à jour bonus              │
│    - Spawn new bonus (aléatoire)    │
│                                     │
│ 3. Collision Detection              │
│    - Joueur vs ennemis              │
│    - Joueur vs bonus                │
│    - Appliquer dégâts/effets        │
│                                     │
│ 4. Update UI                        │
│    - Score (temps × 10)             │
│    - Lives display                  │
│    - Active bonus timers            │
│                                     │
│ 5. Render                           │
│    - Positionner éléments DOM       │
│    - Animations CSS (auto)          │
│    - Update active effects          │
│                                     │
│ 6. Check Win/Lose                   │
│    - Si lives === 0 → gameOver()    │
│    - Si timeout → continuer         │
│                                     │
│ 7. Next Frame                       │
│    - requestAnimationFrame(gameLoop)│
└─────────────────────────────────────┘
```

## Système de Collision

### AABB (Axis-Aligned Bounding Box)

```javascript
function isColliding(a, b) {
  return a.x < b.x + b.width &&
         a.x + a.width > b.x &&
         a.y < b.y + b.height &&
         a.y + a.height > b.y;
}

// Complexité: O(1) par collision check
// Total: O(n) pour n ennemis
```

### Hitboxes Spécifiques

```javascript
// Chauve-souris: hitbox réduite (5px padding)
const batHitbox = {
  x: bat.x + 5,
  y: bat.y + 5,
  width: bat.width - 10,
  height: bat.height - 10
};

// Serpent: hitbox allongée (tête surtout)
const snakeHitbox = {
  x: snake.x,
  y: snake.y + snake.height / 2,  // Tête seulement
  width: snake.width,
  height: snake.height / 2
};

// Araignée: hitbox standard
const spiderHitbox = spider;
```

## Spawn System

### Ennemis

```javascript
// Probabilité spawn: augmente avec le score
const spawnChance = 0.5 + (score / 5000);

// Position: toujours aux bords (random)
const spawnEdge = Math.floor(Math.random() * 4);
//  0 = top, 1 = right, 2 = bottom, 3 = left

// Vitesse: augmente avec le temps
const baseSpeed = 2;
const speedMultiplier = 1 + (timeSurvived / 60000);
```

### Bonus

```javascript
// Spawn toutes les 6-12 secondes
const spawnInterval = 6000 + Math.random() * 6000;

// Type aléatoire avec poids
const weights = {
  '+life': 0.25,
  'slowdown': 0.35,
  'shield': 0.25,
  'bomb': 0.15
};

// Position: aléatoire n'importe où
const x = Math.random() * GAME_WIDTH;
const y = Math.random() * GAME_HEIGHT;
```

## Système d'Invincibilité

```javascript
// Après un coup:
function takeDamage() {
  lives--;
  player.invincible = true;
  player.invincibleTime = 1000; // ms

  // Clignotement visuel (CSS)
  player.element.classList.add('invincible');
}

// Chaque frame:
if (player.invincible) {
  player.invincibleTime -= deltaTime;
  if (player.invincibleTime <= 0) {
    player.invincible = false;
    player.element.classList.remove('invincible');
  }
}

// Collision:
if (isColliding(player, enemy) && !player.invincible) {
  takeDamage();
}
```

## Système d'Audio

### Web Audio API

```javascript
// Contexte audio (une seule instance)
const audioContext = new (window.AudioContext || 
                          window.webkitAudioContext)();

// Création d'un son: paire oscillateur + gain
function playSound(frequency, duration, type) {
  const osc = audioContext.createOscillator();
  const gain = audioContext.createGain();

  osc.type = type; // 'sine', 'square', 'sawtooth'
  osc.frequency.setValueAtTime(frequency, audioContext.currentTime);

  gain.gain.setValueAtTime(0.3, audioContext.currentTime);
  gain.gain.exponentialRampToValueAtTime(
    0.01,
    audioContext.currentTime + duration
  );

  osc.connect(gain);
  gain.connect(audioContext.destination);

  osc.start();
  osc.stop(audioContext.currentTime + duration);
}

// Exemples:
playSound(200, 0.5, 'sawtooth');    // mort
playSound(400, 0.1, 'square');      // coup
playSound(600, 0.3, 'sine');        // bonus
```

## localStorage Persistence

```javascript
// Structure
localStorage.scores = JSON.stringify([
  { pseudo: 'Alice', score: 5000 },
  { pseudo: 'Bob', score: 4500 },
  // ... top 5
]);

localStorage.lastPseudo = 'Alice';

// Sauvegarde
function saveScore(pseudo, score) {
  let scores = JSON.parse(localStorage.scores || '[]');
  scores.push({ pseudo, score });
  scores.sort((a, b) => b.score - a.score);
  localStorage.scores = JSON.stringify(scores.slice(0, 5));
  localStorage.lastPseudo = pseudo;
}

// Chargement
function loadScores() {
  return JSON.parse(localStorage.scores || '[]');
}
```

## Animation System

### CSS Keyframes (Préféré)

```css
/* Sprites: les animations CSS gèrent tout */
@keyframes bat-animation {
  0% { background-position: 0 0; }
  14.28% { background-position: -50px 0; }
  28.56% { background-position: -100px 0; }
  /* ... etc, 7 frames */
}

.enemy.bat {
  animation: bat-animation 200ms steps(7) infinite;
}
```

### JavaScript Animation (si besoin)

```javascript
// Rarement utilisé (CSS > JS pour perf)
function animateEnemy(enemy) {
  enemy.animationFrame++;
  if (enemy.animationFrame >= 8) {
    enemy.animationFrame = 0;
  }
  // Met à jour background-position
}
```

## Performance Optimizations

### 1. Minimal DOM Operations
- Cache les sélecteurs
- Batch les updates
- Utilise classes pour les changements d'état

### 2. GPU Acceleration
- CSS transforms (translate3d)
- CSS animations
- Évite les repaints

### 3. Memory Management
- Pools d'objets (pas d'allocation par frame)
- Réutilise les ennemis/bonus
- Pas de closures dans la boucle

### 4. requestAnimationFrame
- Sync avec écran 60 Hz
- Pas de setTimeout
- Batterie optimisée

## Diagramme de Flux Principal

```
Game Start
    ↓
Display Title Screen
    ↓
Get Player Pseudo
    ↓
Initialize Game State
    ↓
┌─────────────────────────┐
│  Game Loop (RAF)        │
│  ├─ Input handling      │
│  ├─ Update state        │
│  ├─ Collision check     │
│  ├─ Render              │
│  └─ Check end condition │
└─────────────────────────┘
    ↓ (lives === 0)
Game Over Screen
    ↓
Display Leaderboard
    ↓
Save Score to localStorage
    ↓
Offer Replay
```

---

**Architecture simple = code maintenable = jeu fun!** 🎮
