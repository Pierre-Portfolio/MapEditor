# MapEditor

> ⚠️ **POC (Proof of Concept)** — Ce projet est une preuve de concept pour un futur outil d'édition de cartes interactives. Il n'est pas destiné à la production en l'état.

## Présentation

MapEditor est un éditeur de **cartes interactives** dans le navigateur. Il permet de charger un plan (image de fond) puis d'y placer des **zones cliquables** — rectangles, cercles ou polygones — chacune pouvant pointer vers une URL. L'objectif est de produire facilement une « image map » interactive, exportable au format JSON.

Le rendu graphique repose sur la bibliothèque [Konva.js](https://konvajs.org/).

## Fonctionnalités

- **Plan de fond** avec **zoom** à la molette et **déplacement** (drag) du plan.
- **Ajout de zones** depuis le menu :
  - Rectangle (vert)
  - Cercle (bleu)
  - Polygone (dessiné point par point : clic pour poser chaque sommet, double-clic ou clic sur le 1er point pour fermer la forme)
- **Mode édition** activable/désactivable :
  - actif → on peut déplacer, redimensionner et pivoter les zones ;
  - inactif → les zones sont figées (mode consultation).
- **Panneau Détails** : affiche les coordonnées, la couleur et l'URL de la zone sélectionnée, avec des boutons **Éditer** (re-modifier un polygone) et **Supprimer**.
- **Zones cliquables** : un **double-clic** sur une zone ouvre l'URL associée dans un nouvel onglet.
- **Export JSON** : sauvegarde l'état complet de la carte dans un fichier `stage.json`.

## Utilisation

Aucune installation ni build nécessaire. Ouvrez simplement le fichier `index.html` dans un navigateur web moderne.

```bash
# Exemple : ouvrir directement le fichier
open index.html        # macOS
xdg-open index.html    # Linux
```

> ℹ️ Une connexion internet est requise : la bibliothèque Konva, le plan de fond et les icônes du menu sont chargés depuis des URL externes (CDN).

## Pile technique

- **HTML / CSS / JavaScript** (vanilla, sans framework)
- **[Konva.js](https://konvajs.org/)** (chargé via CDN) pour le rendu sur canvas et la gestion des interactions

## Structure du projet

```
MapEditor/
├── index.html   # Page autonome regroupant le HTML, le CSS et le JS
└── README.md
```

## Origine

Ce POC a d'abord été prototypé sur JSFiddle, puis regroupé dans une page HTML unique :

- https://jsfiddle.net/46x891Lo/10/

## Limitations connues

- Toutes les ressources (plan, icônes, librairie) sont chargées depuis des URL externes ; le projet ne fonctionne pas hors-ligne en l'état.
- Le plan de fond et l'URL des zones sont codés en dur dans `index.html`.
- L'export JSON est possible, mais il n'existe pas encore de fonction d'import/rechargement.

## Pistes d'évolution

- Héberger les ressources en local pour un fonctionnement hors-ligne.
- Permettre de choisir/charger son propre plan de fond.
- Rendre l'URL de chaque zone éditable depuis le panneau Détails.
- Ajouter l'import d'un fichier JSON pour recharger une carte sauvegardée.
