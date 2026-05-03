# Guide de Troubleshooting

## ❌ Le jeu ne démarre pas

### "Fichier introuvable"
- Assure-toi que `vermine.html` est bien téléchargé
- Pas de typo dans le nom du fichier
- Essai: Double-clic sur le fichier

### "Erreur de sécurité / CORS"
- Ce message s'affiche si tu ouvres le fichier via file:// depuis une extension
- **Solution**: Utilise un serveur local
  ```bash
  python3 -m http.server 8000
  # Puis ouvre http://localhost:8000/vermine.html
  ```

### "Page blanche"
- JavaScript peut être désactivé
  - Vérifier: Chrome → Settings → Site Settings → JavaScript
  - Activer JavaScript

## 🐢 Le jeu rame / lagge

### Si le jeu saccade (FPS faible)

1. **Ferme les autres onglets**
   - Le jeu partage les ressources CPU
   - Une 20aine d'onglets ouverts = lag garanti

2. **Désactive les extensions lourdes**
   - Adblockers (Ublock, Adblock Plus)
   - Gestionnaires de mots de passe
   - VPN/Proxy extensions

3. **Vérifie ton système**
   - Utilise un gestionnaire de tâches
   - Regarde si CPU est à 100%
   - Libère de la RAM si possible

4. **Essai un autre navigateur**
   - Chrome vs Firefox vs Safari vs Edge
   - Parfois c'est optimisé différemment

### Lag progressif (ça ralentit progressivement)

**Cause**: Memory leak (peu probable)
- Redémarre la page (Ctrl+R)
- Si ça revient = signal un bug

## 🔇 Pas de son

### Pas de son du tout

1. **Vérif le volume système**
   - Pas de muet sur le navigateur
   - Volume système normal

2. **Vérif les permissions audio**
   - Certains navigateurs demandent permission audio
   - Accepte quand asked

3. **Web Audio API pas supportée**
   - Vieux navigateur (IE11?)
   - Essai récent version de Chrome/Firefox

### Son cassé (distorsionné, bizarre)

- C'est la synthèse Web Audio en live
- Parfois génère du bruit blanc
- Normal pour ce type de génération
- Pas c'est pas un bug

## 🎮 Problèmes de Gameplay

### Le joueur bouge pas

1. Assure-toi que la fenêtre est focused
2. Essai les flèches (↑↓←→)
3. Essai AZERTY (Z Q S D)
4. Redémarre le jeu (Entrée après game-over)

### Les ennemis passent à travers le joueur

**C'est normal si**:
- Tu as invincibilité active (clignotement magenta)
- Les collisions fonctionnent correctement

**Si c'est sans invincibilité**:
- Redémarre le jeu
- Signal un bug si ça persiste

### Score pas sauvegardé après refresh

**Par design**:
- localStorage est local par navigateur
- Changer de navigateur = nouveau leaderboard
- Vider cache = données perdues

**Pour éviter**:
- Prends screenshot de ton score
- Partage ton pseudo au lieu de ton nombre exact

### Pseudo s'efface après refresh

- C'est sauvegardé en localStorage
- Si tu vides le cache → pseudo parti
- À part ça, ça devrait persister

## 🌐 Problèmes Navigateur Spécifiques

### Firefox
- ✅ Compatible
- Possible: lag si "Reduced Motion" activé (settings → accessibilité)

### Chrome
- ✅ Parfait support
- Hardware acceleration: Settings → Advanced → GPU acceleration (activé)

### Safari
- ✅ Compatible
- Peut-être: Web Audio API première utilisation demande permission

### Edge
- ✅ Fonctionne
- Basé Chromium = même perf que Chrome

### Mobile Browsers
- ⚠️ Contrôles clavier pas disponibles
- Feature tactile sur roadmap

## 📱 Problèmes Mobile

### Écran trop petit
- Jeu optimisé 800×500px minimum
- Sur petit téléphone: zoom sur le navigateur (pinch)

### Tactile: aucun contrôle
- Pas encore supporté (roadmap pour mai)
- Attends la prochaine version

## 🔐 Problèmes de Sécurité / Virus

### "Le navigateur a bloqué ce fichier"
- Certains navigateurs bloquent les téléchargements "suspects"
- C'est juste parce que c'est un petit jeu inconnu
- **C'est complètement sûr** (code opensource)

### "Attention: site malveillant"
- Erreur fausse positive (rare)
- GitHub Pages héberge code safe
- Pas de risk

## 📊 Comment Reporter un Bug

Si le troubleshooting n'aide pas:

1. Ouvre une **Issue GitHub**
   - URL: https://github.com/Deuza9315/Jeux_Vermine/issues

2. Fournis ces infos:
   ```
   - Navigateur + version (Chrome 120, Firefox 121, etc)
   - OS (Windows 11, macOS 14, Ubuntu 22.04)
   - Étapes pour reproduire
   - Comportement attendu vs réel
   - Screenshot si possible
   ```

3. Titre clair:
   - ✅ "Jeu lagge après 30 secondes"
   - ❌ "Pourquoi ça lag???"

## Console Debugging

Pour les pros qui veulent plus d'infos:

```javascript
// Ouvre F12 → Console

// Voir l'état du jeu
window.gameState

// Voir les meilleurs scores
localStorage.getItem('scores')

// Voir les contrôles detectés
window.keysPressed

// Debug mode (plus de logs)
window.DEBUG = true;
// Relance la page
```

---

**Toujours pas d'aide?** [@Deuza](https://github.com/Deuza9315) est là pour toi! 🎮
