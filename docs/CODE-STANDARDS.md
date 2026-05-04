# Code Standards & Guidelines

## Philosophie

```
Keep It Simple, Stupid (KISS)
- Vanilla JavaScript
- Pas de frameworks
- Pas de dépendances externes
- Code lisible et transparent
```

## JavaScript Standards

### Naming Conventions

```javascript
// Variables & functions: camelCase
let playerPosition = { x: 0, y: 0 };
function calculateScore() { }

// Constants: UPPER_SNAKE_CASE
const MAX_LIVES = 5;
const GAME_WIDTH = 800;

// Classes: PascalCase
class Enemy { }
class GameState { }

// Private variables: underscore prefix
let _internalState = { };
function _helperFunction() { }
```

### Code Style

```javascript
// ✅ GOOD: Clear and concise
function updatePlayerPosition(dx, dy) {
  player.x += dx;
  player.y += dy;
  clampToScreen();
}

// ❌ BAD: Unclear
function update(a, b) {
  p.x += a;
  p.y += b;
  c();
}
```

### Comments

```javascript
// ✅ GOOD: Comment WHY not WHAT
// Respawn at opposite edge to create teleport effect
if (player.x > GAME_WIDTH) {
  player.x = 0;
}

// ❌ BAD: Comment obvious code
let x = 0; // set x to 0

// ❌ BAD: Outdated comments
// TODO: Fix collision (done in v0.8)
```

### Structure

```javascript
// File structure:
1. Constants & configs
2. Game state initialization
3. Helper functions
4. Game loop (update + render)
5. Event listeners
6. Exports (if any)
```

### Best Practices

```javascript
// ✅ Use const by default
const SPEED = 5;

// ✅ Use let for mutable state
let playerX = 0;

// ❌ Avoid var (function scope confusion)
var oldStyle = true;

// ✅ Destructuring
const { x, y } = position;

// ✅ Template literals
const msg = `Score: ${score}`;

// ✅ Arrow functions for callbacks
events.forEach(e => handle(e));

// ✅ Guard clauses
if (lives <= 0) return gameOver();

// ❌ Avoid nested callbacks
// Use promises or async/await instead
```

## CSS Standards

### Organization

```css
/* 1. Reset & Defaults */
* { margin: 0; padding: 0; }

/* 2. Layout & Structure */
#game-container { }
#game-area { }

/* 3. Typography */
body { font-family: ... }

/* 4. Colors & Backgrounds */
.enemy { background: #f00; }

/* 5. Animations */
@keyframes sprite { }

/* 6. Media Queries */
@media (max-width: 600px) { }
```

### Naming

```css
/* BEM-like naming for clarity */
.game-container { }
.game-container__area { }
.enemy { }
.enemy--active { }

/* CSS Variables for reusability */
:root {
  --game-width: 800px;
  --primary-color: #ffff00;
}
```

### Values

```css
/* ✅ Use CSS variables */
width: var(--game-width);

/* ✅ Use shorthand */
margin: 0 auto; /* not margin-left + margin-right */

/* ✅ Use meaningful values */
color: var(--player-color);

/* ❌ Avoid magic numbers */
width: 800px; /* should be var(--game-width) */
```

## HTML Standards

### Structure

```html
<!-- Semantic HTML5 -->
<header>Navigation</header>
<main>
  <section id="game-container">
    <div id="game-area">Content</div>
  </section>
</main>
<footer>Credits</footer>
```

### ARIA & Accessibility

```html
<!-- ✅ GOOD: Semantic + ARIA -->
<button aria-label="Start game">PLAY</button>
<div role="status" aria-live="polite">Lives: 3</div>

<!-- ❌ BAD: No semantic meaning -->
<div class="button" onclick="startGame()">PLAY</div>
```

## Performance Practices

### ✅ Do This
- Use `requestAnimationFrame` for animations
- Cache DOM queries
- Batch DOM updates
- Use CSS animations for smooth 60 FPS
- Minimize repaints and reflows

### ❌ Don't Do This
- Allocate memory in game loop
- Query DOM frequently in loops
- Use inline styles
- Animate via JavaScript if CSS can handle it
- Create massive objects each frame

## Testing Standards

### Manual Testing Checklist

```markdown
- [ ] Game starts without errors
- [ ] Keyboard controls work (arrows + AZERTY)
- [ ] Enemies spawn correctly
- [ ] Collisions detect properly
- [ ] Score increments each second
- [ ] Bonus activates correctly
- [ ] Game-over triggers on 0 lives
- [ ] Leaderboard saves/displays
- [ ] Audio plays (all 6 sounds)
- [ ] Works on Chrome/Firefox/Safari/Edge
- [ ] Works offline
- [ ] FPS stays 60 (check DevTools)
```

## Documentation Standards

### Comment Blocks

```javascript
/**
 * Calculate distance between two points
 * @param {number} x1 - First X coordinate
 * @param {number} y1 - First Y coordinate
 * @param {number} x2 - Second X coordinate
 * @param {number} y2 - Second Y coordinate
 * @returns {number} Distance between points
 */
function getDistance(x1, y1, x2, y2) {
  return Math.sqrt((x2-x1)**2 + (y2-y1)**2);
}
```

## Git Commit Standards

### Format

```
<type>: <subject>

<body (optional)>
```

### Types
- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation
- `style:` Formatting/style
- `refactor:` Code restructure
- `test:` Tests
- `chore:` Maintenance

### Examples
```
✅ feat: ajouter système de bonus
✅ fix: corriger collision AABB
✅ docs: ajouter guide de gameplay
❌ WIP: stuff
❌ Updated code
```

## File Organization

```
vermine/
├── vermine.html          # Main game file
├── chauve-souris.html    # Prototype/reference
├── README.md             # Main documentation
├── LICENSE               # MIT license
├── CONTRIBUTING.md       # Contribution guide
├── package.json          # Meta info
└── docs/
    ├── GAMEPLAY.md       # How to play
    ├── TECHNICAL.md      # Architecture
    ├── ASSETS.md         # Sprite guide
    ├── FAQ.md            # FAQ
    ├── FEATURES.md       # Feature list
    ├── OPTIMIZATION.md   # Performance tips
    └── TROUBLESHOOTING.md # Debug guide
```

## Browser Compatibility

### Supported
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ Opera 76+

### Not Supported
- ❌ IE11 (outdated)
- ❌ Older mobile browsers

### Testing
Use BrowserStack or local VMs to test compatibility.

## Security Considerations

```javascript
// ✅ Safe: No user input executed
let score = localStorage.getItem('score');

// ❌ Unsafe: eval() never!
eval(userInput); // NEVER

// ✅ Safe: HTML escaped
textContent = userName; // not innerHTML

// ❌ Unsafe: Inject unescaped HTML
innerHTML = userInput; // BAD
```

---

**Follow these standards to keep the code maintainable and performant!** 🚀
