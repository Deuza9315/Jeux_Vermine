# FAQ - Questions Fréquemment Posées

## Gameplay

### Q: Comment augmenter mon score rapidement?
**R:** Chaque seconde de survie = 10 points. Utilise les bonus (surtout Ralenti) pour rester en vie plus longtemps. Évite les coins - reste au centre.

### Q: Quel est le meilleur bonus?
**R:** Ça dépend de la situation:
- **+Vie** si tu as 1-2 vies
- **~Ralenti** si tu es encerclé
- **O Bouclier** en dernier recours
- **\* Bombe** quand c'est le chaos

### Q: Les ennemis passent parfois par-dessus?
**R:** Non, les collisions sont strictes AABB. Tu as peut-être l'invincibilité active (1 sec après un coup).

### Q: Je peux pause le jeu?
**R:** Non, pas encore. C'est sur la roadmap!

## Technique

### Q: Ça fonctionne hors-ligne?
**R:** OUI! Télécharge vermine.html et ouvre-le localement. Zéro serveur requis.

### Q: Quel navigateur pour jouer?
**R:** Chrome, Firefox, Edge, Safari (versions récentes). Pas de support IE.

### Q: Le jeu peut être hôté où?
**R:** Partout! Server statique, GitHub Pages, Dropbox, ton PC... C'est un seul fichier HTML.

### Q: Pourquoi pas de dépendances?
**R:** Simplicité maximale. Un fichier = facile à partager, maintenir, exécuter.

## Données

### Q: Où sont sauvegardés mes scores?
**R:** Dans le localStorage de ton navigateur. Local uniquement.

### Q: Si je vide le cache?
**R:** Tes scores disparaissent. Prochaines updates vont prévoir export/import.

### Q: Comment voir mon pseudo?
**R:** Il s'affiche dans le classement si tu es top 5.

## Performance

### Q: Pourquoi ça lag parfois?
**R:** Généralement: onglets trop nombreux, extension browser lourde, ou CPU saturé. Ferme les onglets inutiles.

### Q: Ça bouffe combien de batterie?
**R:** ~3% sur 1h de jeu continu. Raisonnable pour un jeu.

### Q: CPU/RAM utilisés?
**R:** < 5% CPU idle, ~50 MB RAM. Très léger.

## Idées et Support

### Q: Comment suggérer une feature?
**R:** Ouvre une issue GitHub ou contacte via email. Les idées sont bienvenues!

### Q: Puis-je moddifier le jeu?
**R:** Bien sûr! C'est sous licence MIT. Fork, modifie, améliore!

### Q: Ça va sortir sur mobile?
**R:** Mode tactile sur la roadmap. Pas encore implémenté.

### Q: Peut-on faire un multijoueur?
**R:** Bonne idée mais complexe pour ce format. À voir en future version.

## Bugs Connus

- Très rare: parfois un ennemi spawn en même position que le joueur (invincibilité active)
- Sur mobile: la barre d'adresse peut scroller (espace limité)

---

**Plus de questions?** Ouvre une [issue GitHub](https://github.com/Deuza9315/Jeux_Vermine/issues)!
