
# Space Collector — La collecte des étoiles

J’ai réalisé un petit mini‑jeu web où je contrôle un astronaute dans l’espace pour **collecter un maximum d’étoiles en un temps limité**.

## Le principe du jeu

- Je dirige l’astronaute (👨‍🚀) pour qu’il **attrape des étoiles** (⭐) qui apparaissent aléatoirement sur l’écran.
- À chaque étoile attrapée, **le score augmente** et une nouvelle étoile réapparaît ailleurs.
- Le jeu dure **60 secondes** : quand le temps tombe à 0, la partie se termine et j’affiche le score final.

## Comment jouer

- **Au lancement**, une fenêtre d’instructions s’affiche.
- Je clique sur **“J’ai compris !”** pour démarrer la partie.

### Sur ordinateur

- L’astronaute **suit ma souris** (avec un mouvement fluide, pas instantané).
- Je passe sur les étoiles pour les collecter.

### Sur mobile (à savoir)

J’ai prévu l’idée “l’astronaute suit le doigt” dans le texte d’instructions, mais dans le code actuel, je gère surtout la **souris** (événement `mousemove`). Si je veux un vrai support mobile, je devrai ajouter la gestion des événements tactiles (`touchstart` / `touchmove`).

## Ce que j’ai implémenté techniquement

- **Déplacement fluide** : je récupère la position de la souris, puis je fais “glisser” l’astronaute vers cette position (interpolation) pour éviter un déplacement trop brusque.
- **Collisions** : je compare les rectangles (bounding boxes) de l’astronaute et des étoiles ; si ça se chevauche, je compte une collecte.
- **Timer** : je décrémente le temps chaque seconde ; à 0, j’arrête le jeu et j’affiche un message de fin.

## Structure du dossier

- `space-collector` : la page HTML (éléments du jeu + modale d’instructions)
- `script.js` : toute la logique (déplacement, étoiles, collisions, score, timer, fin de partie)
- `styles.css` : le style (fond spatial, positionnement, HUD score/temps, modale)
- `space.webp` : l’image de fond (espace)

## Remarques / améliorations possibles

- Ajouter un vrai contrôle **tactile** (mobile).
- Éviter le `location.reload()` en fin de partie et plutôt réinitialiser l’état proprement (score, étoiles, timer).