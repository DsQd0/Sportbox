# Sportbox

Appli de musculation à la maison (poids du corps + barre de traction) : une bibliothèque de 24 exercices en Push/Pull/Legs, un tirage automatique de la semaine (4 séances), l'échauffement et les étirements pour chaque séance, un minuteur de repos entre les séries, le suivi des charges/répétitions par exercice, et un carnet de poids corporel.

C'est une PWA (Progressive Web App) en HTML/CSS/JS pur, sans build ni dépendances — un simple site statique installable sur téléphone, sur le même principe que [Cookbox](https://github.com/DsQd0/Cookbox).

Direction artistique identique à Cookbox/Loverbox (façon Letterboxd) : fond quasi noir (#14171b), cartes ardoise (#1b1f27), vert (#30cb75) comme accent principal, orange pour Push, ambre pour Pull, vert pour Legs, texte en Inter sans-serif bold.

## Installer sur son téléphone

1. Active GitHub Pages pour ce dépôt (une seule fois) :
   - Repo GitHub → **Settings** → **Pages**
   - Source : **Deploy from a branch**
   - Branche : choisis la branche qui contient ce code (ex. `claude/sports-app-questions-co6x8m`, ou `main` une fois la PR mergée) — dossier `/ (root)`
   - **Save**, puis attends ~1 minute. L'URL apparaît en haut de la page (du type `https://<ton-user>.github.io/Sportbox/`).
2. Ouvre cette URL sur ton téléphone.
3. Installe l'appli :
   - **iPhone (Safari)** : bouton Partager → *Sur l'écran d'accueil*.
   - **Android (Chrome)** : menu ⋮ → *Installer l'application* (ou bannière automatique).

L'icône Sportbox apparaît alors sur l'écran d'accueil, en plein écran, sans barre d'adresse.

## Développement local

Aucune installation nécessaire, c'est du HTML/CSS/JS statique :

```bash
python3 -m http.server 8000
# puis ouvrir http://localhost:8000
```

## Structure

- `index.html` — l'application (une seule page)
- `manifest.json` — métadonnées PWA (nom, icônes, couleurs)
- `sw.js` — service worker (cache l'appli pour un usage hors-ligne)
- `icons/` — icônes de l'appli (192, 512, apple-touch-icon, et la source `icon.svg`)

## Principe de la semaine

Chaque semaine, l'appli tire automatiquement 4 séances parmi la bibliothèque : Push, Pull, Legs, et une 4ᵉ séance qui tourne (Push, Pull ou Legs selon la semaine) pour équilibrer le volume sur plusieurs semaines. Dans chaque catégorie, 5 exercices sont tirés au sort parmi les 8 disponibles. Le bouton « Nouveau tirage » relance tout, et « Changer » ne relance que la séance concernée.

Chaque séance contient un échauffement, les exercices (avec minuteur de repos et champs pour noter les répétitions et la charge ajoutée), et des étirements adaptés à la zone travaillée.

## Données

Les cases cochées, le tirage de la semaine, les performances notées par exercice et les pesées sont sauvegardés dans le `localStorage` du navigateur — propre à chaque appareil, rien n'est envoyé sur un serveur.
