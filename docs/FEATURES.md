# Liste Complète des Fonctionnalités

## ✅ Fonctionnalités Implémentées (v1.0)

### Gameplay Core
- ✅ Boucle de jeu avec requestAnimationFrame (60 FPS)
- ✅ Contrôles clavier (AZERTY + QWERTY)
- ✅ Carré jaune joueur contrôlable
- ✅ Limites d'écran (pas de dépassement)

### Ennemis
- ✅ Chauve-souris (CSS sprite 7 frames)
- ✅ Serpent à sonnette (GIF 8 frames)
- ✅ Araignée venimeuse (GIF 16 frames)
- ✅ Spawn aléatoire tous les 0.5-2s
- ✅ Difficulté progressive (vitesse augmente)
- ✅ Fréquence spawn augmente avec score

### Collisions
- ✅ AABB collision detection
- ✅ Hitboxes spécifiques par ennemi type
- ✅ Système de vies (3-5 vies)
- ✅ Invincibilité temporaire (1s après coup)
- ✅ Invincibilité clignotement (feedback visuel)

### Bonus System
- ✅ +Vie (restaure 1 vie, max 5)
- ✅ ~Ralenti (tous les ennemis -50% vitesse, 5s)
- ✅ O Bouclier (invincibilité totale, 3s)
- ✅ \* Bombe (efface tous ennemis, instantané)
- ✅ Spawn aléatoire 6-12s
- ✅ Collection au contact
- ✅ Affichage sur écran

### Scoring & Leaderboard
- ✅ Score = temps survécu × 10
- ✅ Score affiché en temps réel
- ✅ Top 5 leaderboard
- ✅ localStorage persistence
- ✅ Surlignage du score actuel du joueur
- ✅ Pseudo joueur (max 8 chars)
- ✅ Pseudo sauvegardé

### Interface Utilisateur
- ✅ Écran d'accueil
- ✅ Input pseudo
- ✅ Bouton JOUER
- ✅ Affichage lives en temps réel
- ✅ Affichage score en temps réel
- ✅ Game-over screen
- ✅ Leaderboard affichage
- ✅ Bouton Rejouer

### Décor & Ambiance
- ✅ Mur de briques CSS dégradé
- ✅ Textures mur (pattern relief)
- ✅ Sol sombre taché
- ✅ Poubelles avec ordures
- ✅ 3 graffitis SVG (chauve-souris, serpent, araignée)
- ✅ Éclaboussures de spray (CSS)
- ✅ Palette cohérente (arcade)

### Audio
- ✅ Son mort (sawtooth oscillator)
- ✅ Son coup (square wave)
- ✅ Son power-up (square wave montante)
- ✅ Son bouclier (sine montante)
- ✅ Son ralenti (sine descendante)
- ✅ Son bombe (bruit blanc)
- ✅ Synthèse Web Audio API
- ✅ Zéro fichier externe

### Compatibilité
- ✅ Chrome (Windows, Mac, Linux)
- ✅ Firefox (tous OS)
- ✅ Safari (Mac, iOS)
- ✅ Edge (tous OS)
- ✅ Opera (tous OS)
- ✅ Pas IE support (ancien)

### Code Quality
- ✅ Vanilla JavaScript (zéro dépendances)
- ✅ HTML5 sémantique
- ✅ CSS3 modern
- ✅ Monofichier (230 Ko)
- ✅ Assets Base64 embarqués
- ✅ Jouable offline
- ✅ Pas de console errors

---

## 📋 Fonctionnalités Planifiées (Roadmap)

### v1.1 - Mobile Support
- 📱 Contrôles tactiles (swipe/tap)
- 📱 Responsive design mobile
- 📱 Vibration feedback (haptics)
- 📱 Orientation portrait + landscape

### v1.2 - Gameplay Extensions
- 🎯 Modes de difficulté (Easy/Normal/Hard)
- ⏱️ Time-based challenges
- 🏆 Achievement system
- 🌟 Star ratings pour les runs

### v1.3 - Nouveaux Ennemis
- 🐀 Rat (rapide, imprévisible)
- 🦂 Scorpion (lent mais dangereux)
- 🪳 Cafard (essaim)
- 👁️ Créature mutante (boss?)

### v1.4 - Audio & Ambiance
- 🔊 Ambiance sonore boucle (ruelle)
- 🎵 Musique menu
- 🎵 Musique gameplay (adaptive)
- 📢 Voice over (annoncements)

### v1.5 - Particules & Effects
- ✨ Particules collision
- 💥 Explosion bombe
- 👻 Fantômes ennemis morts
- 🌪️ Effets ralenti visuel

### v1.6 - Boss & Progression
- 👹 Boss fight tous les 1000 pts
- 📊 Progression milestones
- 🏅 Badges spéciaux
- 🎖️ Record personal tracking

### v2.0 - Multiplayer (Future)
- 🎮 Local 2-player
- 🌐 Online leaderboard
- 🎯 Competitive modes
- 👥 Profiles utilisateur

### v2.1 - Customization
- 🎨 Skins joueur
- 🎨 Thèmes visuels
- 🎮 Keybindings custom
- ⚙️ Settings menu

---

## 🔧 Features Techniques

### Optimizations
- ✅ 60 FPS stable
- ✅ GPU accelerated CSS
- ✅ requestAnimationFrame sync
- ✅ Memory optimized
- ✅ No allocation loops
- ✅ Minimal DOM operations

### Accessibility
- ✅ ARIA labels
- ✅ High contrast colors
- ✅ Keyboard navigation
- ✅ Focus indicators
- ✅ Screen reader support (partial)

### Monitoring (Future)
- 📊 FPS counter
- 📊 Memory profiling
- 📊 Performance metrics
- 📊 Analytics hooks

---

## 🐛 Known Issues & Limitations

### Current Limitations
- ⚠️ Pas de mobile tactile (pour v1.1)
- ⚠️ Pas de sound mute (coming)
- ⚠️ Pas de fullscreen mode
- ⚠️ Pas d'export scores
- ⚠️ localStorage uniquement (pas cloud)

### Rare Bugs
- 🐛 Très rare: spawn collision avec joueur
- 🐛 Mobile: address bar scrolling interfère
- 🐛 Safari: rare audio delay au démarrage

### Won't Fix
- ❌ IE11 support (obsolète)
- ❌ Mobile tactile v1.0 (roadmap v1.1)
- ❌ Cloud save (scope trop large)
- ❌ Mod support (game jam context)

---

**Merci d'avoir lu la feature list! 🎮**

La roadmap peut changer en fonction des retours utilisateurs.
Tes suggestions? [Ouvre une issue!](https://github.com/Deuza9315/Jeux_Vermine/issues)
