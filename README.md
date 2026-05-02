# 🦇 VERMINE

Survis aux bestioles dans une ruelle pourrie de banlieue.

Un mini-jeu d'esquive en HTML/CSS/JS pur avec des sprites pixel art animés.

## 🎮 Comment Jouer

1. **Téléchargez** le fichier `vermine.html`
2. **Double-cliquez** pour l'ouvrir dans votre navigateur
3. **Entrez votre pseudo** (8 caractères max)
4. **Cliquez sur JOUER** et survivez !

### Contrôles

| Touches | Action |
|---------|--------|
| ↑ ↓ ← → | Se déplacer |
| Z Q S D | Se déplacer (alternative AZERTY) |
| Entrée  | Rejouer (sur écran Game Over) |

### Objectif

Survivre le plus longtemps possible. **Score = temps survécu × 10**

## ⚡ Système de Bonus

Des éléments apparaissent aléatoirement à l'écran toutes les 6-12 secondes :

| Icône | Bonus | Effet | Durée |
|-------|-------|-------|-------|
| 🟥   | +Vie  | Restaure une vie | Permanent |
| 🟦   | ~Ralenti | Tous les ennemis ralentis | 5 secondes |
| 🔵   | O Bouclier | Invincibilité | 3 secondes |
| 🟧   | * Bombe | Efface tous les ennemis | Instantané |

## 👹 Bestiaire

Trois ennemis viennent te traquer dans la ruelle :

### 🦇 Chauve-souris
Sprite CSS pur réalisé avec box-shadow formant un pixel art sur 7 frames d'animation.

### 🐍 Serpent à Sonnette
Sprite généré sur PixelLab.ai et animé sur Piskel. La tête se balance et le corps respire.

### 🕷️ Araignée
Feuille de sprite 16 images générées sur PixelLab.ai, converties en GIF transparent.

## 🎨 Le Décor

Une ambiance ruelle de banlieue immersive :

- **Mur de briques texturées** avec dégradés CSS
- **Couches de saleté** avec radial-gradients
- **Sol sombre et taché**
- **Deux poubelles** avec ordures qui dépassent
- **3 graffitis SVG** : chauve-souris, serpent et araignée taggés
- **Éclaboussures de spray** (rouge sang, noir)

## 🔊 Système Sonore

Tous les effets sonores sont générés **à la volée via la Web Audio API** :

| Événement | Effet |
|-----------|-------|
| Mort | Oscillateur dents de scie descendant |
| Coup | Onde carrée courte |
| Power-up | Square wave montante |
| Bouclier | Sine montante |
| Ralentissement | Sine descendante |
| Bombe | Bruit blanc exponentiel |

## 🏆 Leaderboard

Top 5 des meilleurs scores sauvegardés dans le localStorage.
Ton score apparaît surligné en jaune s'il rentre dans le classement.

## 🛠️ Stack Technique

- **HTML5** — structure
- **CSS3** — décor, animations, sprites
- **JavaScript vanilla** — gameplay, collisions AABB
- **Web Audio API** — sons générés
- **localStorage** — sauvegarde scores
- **SVG inline** — graffitis

✅ **Zéro dépendances**
✅ **Un seul fichier** (~230 Ko)
✅ **Jouable hors ligne**
✅ **Compatible tous navigateurs**

## ✨ Fonctionnalités

- ✅ 3 ennemis avec animations distinctes
- ✅ Difficulté progressive
- ✅ 4 types de bonus
- ✅ Système de vies + invincibilité temporaire
- ✅ Pseudo joueur sauvegardé
- ✅ Leaderboard top 5
- ✅ Sons générés en temps réel
- ✅ Décor immersif avec graffitis SVG
- ✅ Hitboxes enrichies
- ✅ Compatible AZERTY et QWERTY

## 📋 Roadmap Futur

- 📱 Mode mobile avec contrôles tactiles
- 🎯 Modes de difficulté (Facile/Normal/Hardcore)
- 👾 Nouveaux ennemis (rat, scorpion, cafard)
- 🔉 Ambiance sonore de ruelle
- ✨ Particules visuelles
- 💥 Animations de mort améliorées
- 🏅 Boss tous les 1000 points

---

**Besoin d'aide ?** Ouvrez simplement `vermine.html` dans votre navigateur. Pas d'installation requise ! 🎮
