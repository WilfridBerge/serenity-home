# Design

<!-- impeccable:design-schema 1 -->

## Platform

web

## Origin

Système hérité du logo fourni par le client (`assets/logo/`, réalisé hors de ce projet). Marque incomplète étendue à un site complet — pas un monde visuel inventé depuis zéro. Voir `PRODUCT.md` pour la vérité produit.

## Palette

Valeurs mesurées directement par analyse de pixels sur le logo (pas devinées) :

- `--ink` `#16302d` — texte principal, quasi-noir à dominante pétrole
- `--ink-soft` `#4d5f5a` — texte secondaire
- `--petrol` `#1f5b66` — accent primaire (CTA, liens actifs)
- `--petrol-deep` `#123138` — titres, fond de la section témoignages
- `--gold` `#9d7639` — accent secondaire (eyebrows, bordures d'icônes)
- `--gold-light` `#c9a24c` — accent doré sur fond sombre (témoignages)
- `--ivory` `#f7f2e4` — fond principal
- `--ivory-panel` `#efe7d2` / `--ivory-panel-2` `#e8dfc6` — fonds de panneaux
- `--line` `#ddd0ac` — séparateurs, bordures

Un seul monde visuel (clair) committed — pas de thème sombre, cohérent avec le fond ivoire du logo fourni.

## Typographie

- **Affichage** (titres, wordmark, labels tracés) : `Jost` — sans-serif géométrique, en écho aux capitales espacées du wordmark du logo. Fichier local `img/fonts/jost.woff2`.
- **Texte courant** : `Karla` — grotesque humaniste sobre, pour le corps de texte et l'interface. `img/fonts/karla-400.woff2` (+ italique pour citations/notes).
- Eyebrows et labels en capitales, `letter-spacing` large (0.18–0.22em).

## Composition

- **Motif orbital** : les 5 piliers disposés en cercle autour du nom de la marque, dans l'ordre du logo (Habitat, Énergie, Argent, Nourriture, Eau, sens horaire depuis le haut). Utilisé dans le hero ; se replie en rangée de puces horizontales sous 640px.
- **Une page à défilement** (one-page), sections séparées par une bordure fine (`--line`), pas de cartes/ombres génériques.
- **Piliers** : disposition alterne texte/média gauche-droite, image principale pleine largeur + 2-3 images secondaires en grille, icône ligne fine en tête de section.
- **Pilier Argent** : traité sans photo (choix produit assumé), mais avec la même icône, la même hiérarchie typographique et un fond dédié — jamais présenté comme un manque.
- **Témoignages** : fond `--petrol-deep`, cartes de citation à bordure translucide, attribution en capitales dorées.

## Iconographie

Pictogrammes en trait fin (`stroke-width: 1.6`, `stroke-linecap/linejoin: round`, `fill: none`), un par pilier : maison (Habitat), vague (Eau), soleil + éclair (Énergie), pousse/feuille (Nourriture), pièce stylisée (Argent). Dessinés en SVG inline pour rester nets à toute taille — jamais de captures ou d'images bitmap pour les icônes.

## Média

- Uniquement du contenu réel fourni par le client (`assets/evidence/`), jamais de stock. Copies web-optimisées dans `img/` (JPEG ~1600-1800px, qualité 78-82).
- Orientation EXIF non fiable sur les photos sources (pas de tag Orientation) — chaque photo a été vérifiée visuellement et pivotée manuellement si besoin avant intégration.
- Vidéo : transcodage HEVC → H.264 MP4 + poster, `preload="none"` pour ne pas charger la vidéo tant qu'elle n'est pas lancée.

## Mouvement

Apparition douce au scroll (`opacity`/`translateY`, 0.7s) via `IntersectionObserver`. Protégé par double garde : n'agit que si `html.js-anim` (posé en synchrone dans le `<head>`) et `html.can-animate` (absent si `prefers-reduced-motion: reduce`) sont présents — sans JS, tout le contenu reste visible par défaut (pas de dépendance bloquante au script).

## Ce qui reste à trancher

- Nom/zone géographique volontairement absents du site (choix produit, voir `PRODUCT.md`).
- Pas de tarifs affichés.
- Logo à réutiliser tel quel si mis à jour par le client — ne pas le redessiner depuis ce projet.
