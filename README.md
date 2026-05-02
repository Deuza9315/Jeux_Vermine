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
