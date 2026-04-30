# Guide des Assets

## Sprites des Ennemis

### 🦇 Chauve-souris
- **Format**: CSS pure (box-shadow)
- **Technique**: 7 frames d'animation pixelisée
- **Inspiré par**: @thecodetutor sur CodePen
- **Taille**: ~50px × 40px
- **Couleur**: Gris/noir
- **Vitesse d'animation**: 100ms par frame

### 🐍 Serpent à Sonnette
- **Format**: Sprite PNG animé
- **Source**: PixelLab.ai
- **Éditeur**: Piskel
- **Frames**: 8 images
- **Taille**: ~60px × 60px
- **Couleurs**: Marron, rouge, jaune (sonnette)
- **Animation**: Tête qui balance (4Hz)

### 🕷️ Araignée Venimeuse
- **Format**: Sprite sheet PNG + GIF animé
- **Source**: PixelLab.ai
- **Frames**: 16 images
- **Taille**: ~50px × 50px
- **Couleurs**: Noir, rouge yeux
- **Effet**: Poussière sous les pattes (IA)

## Décor

### Mur de Briques
- Texture CSS avec dégradés linéaires
- Ombre pour la 3D
- Variation de couleur #8B4513 à #654321

### Saleté et Poussière
- Radial-gradients avec blur
- Opacité variable
- Positions aléatoires

### Graffitis SVG
- Chauve-souris: Path animé
- Serpent: Ondulant
- Araignée: Avec filaments

### Poubelles
- DIV + CSS
- Ordures qui dépassent (texte emoji)
- Ombres pour la perspective

### Sol
- Dégradé horizontal
- Taches CSS blur
- Couleur base: #1a1a1a

## Sons (Web Audio API)

### Mort
- Oscillateur dents de scie
- Fréquence: 200Hz → 50Hz en 0.5s
- Durée: 0.5 secondes

### Coup
- Onde carrée courte
- Fréquence: 400Hz
- Durée: 0.1 secondes
- Volume décroissant

### Power-up
- Square wave montante
- 300Hz → 600Hz en 0.3s
- Arpège 4 notes

### Bouclier
- Sine wave
- 600Hz → 800Hz
- Durée: 0.4s

### Ralenti
- Sine wave descendante
- 800Hz → 400Hz
- Durée: 0.5s

### Bombe
- Bruit blanc
- Enveloppe exponentielle
- Durée: 0.6s

## Palettes de Couleurs

### Joueur
- Primaire: #FFFF00 (jaune pur)
- Invincibilité: #FF00FF (magenta clignotant)

### Bonus
- Vie: #FF0000 (rouge)
- Ralenti: #0000FF (bleu)
- Bouclier: #00FFFF (cyan)
- Bombe: #FF8800 (orange)

### Ambiance
- Fond: #0d0d0d (noir profond)
- Mur: #8B4513 (brique)
- Accent: #CC0000 (rouge sang)

## Formats et Encodages

Tous les assets sont **Base64 encodés** dans le HTML pour:
- Zéro requête externe
- Partage facile (un seul fichier)
- Jouable hors-ligne

### GIF encodés
- Transparent background
- Dimensions: 16×16 à 64×64px
- 8-16 frames max pour performance

### PNG
- RGB ou RGBA
- Compression: 9 (max)
- Dimensions: sprites < 128px

## Intégration

Tous les assets sont intégrés via:
```javascript
// Images
document.getElementById('sprite').src = 'data:image/png;base64,...';

// Sons
audioContext.decodeAudioData(arrayBuffer);
```

## Optimisations

- Images compressées au maximum
- Couleurs limitées (8-16 max par sprite)
- Animations CSS plutôt que JS
- Sprites uniques pour éviter duplication
