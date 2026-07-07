# MERIDIAN — Design System v1

**House of Meridian · houseofmeridian.fr · Refonte luxe Shopify (thème Horizon)**
Document de référence pour tous les livrables (pages HTML, sections Liquid). Toute décision visuelle s'y conforme.

---

## 1. Principes directeurs

1. **La retenue.** Une seule idée par section. L'espace vide est un matériau, pas un manque. Si un élément ou un effet peut être retiré sans perte, il est retiré.
2. **La lenteur.** Rien ne surgit : tout se révèle. Entrées longues et douces, orbites quasi imperceptibles, jamais de rebond ni d'élasticité.
3. **L'or en filigrane.** L'or champagne ne couvre jamais : il souligne. Filets 1 px, lettres espacées, lueurs. Jamais d'aplat massif ; l'or plein est réservé au bouton primaire (un seul par écran).
4. **La nuit céleste.** Fond noir profond, anneaux orbitaux dorés, points lumineux. C'est la signature de la maison : chaque page porte sa propre constellation, discrète et unique.
5. **Le contenu d'abord.** `prefers-reduced-motion` neutralise toute animation (contenu visible immédiatement), contrastes AA, focus visibles or, HTML sémantique. Le luxe n'excuse aucune barrière.

---

## 2. Tokens

> Convention : préfixe `--mrd-`. **Isolation stricte** : les tokens sont déclarés sur la racine scopée de chaque livrable (`#mrd-home`, `.mrd-section`…), jamais sur `:root` ni `body`.

### 2.1 Couleurs

| Token | Valeur | Usage |
|---|---|---|
| `--mrd-noir` | `#0B0B0D` | Fond principal |
| `--mrd-surface` | `#101013` | Surfaces, cartes, bandeaux |
| `--mrd-surface-2` | `#16161B` | Surface survolée / élevée |
| `--mrd-creme` | `#F2EDE4` | Texte principal (contraste ≈ 16:1 sur noir) |
| `--mrd-gris` | `#9B968C` | Texte secondaire (contraste ≈ 6,7:1 — AA) |
| `--mrd-or` | `#C8A35F` | Accents : eyebrows, prix, icônes, filets |
| `--mrd-or-clair` | `#E7CF94` | Haut du dégradé or, éclats |
| `--mrd-or-sombre` | `#9C7B3E` | Bas du dégradé or, états pressés |
| `--mrd-grad-or` | `linear-gradient(135deg,#E7CF94 0%,#C8A35F 45%,#9C7B3E 100%)` | Texte dégradé (`background-clip:text`), filets précieux |
| `--mrd-ligne-or` | `rgba(200,163,95,.28)` | Filets et bordures or (hairlines) |
| `--mrd-ligne` | `rgba(242,237,228,.08)` | Séparateurs neutres |
| `--mrd-voile` | `rgba(11,11,13,.55)` | Voile sur images (lisibilité texte) |

**Règles d'usage.** L'or en texte uniquement ≥ 12 px / graisse ≥ 400 (contraste ≈ 8:1 — AA). Jamais deux boutons or pleins visibles simultanément. Surface dorée totale < 5 % d'un écran.

### 2.2 Typographie

| Rôle | Fonte | Style |
|---|---|---|
| Display (h1) | Cormorant Garamond 500 | `clamp(2.6rem, 6vw, 4.75rem)` · line-height 1.05 · letter-spacing .01em |
| Titre de section (h2) | Cormorant Garamond 500 | `clamp(2rem, 4vw, 3.25rem)` · line-height 1.12 |
| Sous-titre (h3) | Cormorant Garamond 500 | `clamp(1.35rem, 2.2vw, 1.75rem)` |
| Eyebrow (sur-titre) | Inter 500 | 11–12 px · uppercase · letter-spacing .35em · or champagne |
| Corps | Inter 300/400 | 16–17 px · line-height 1.7 · crème ou gris chaud · mesure ≤ 68 caractères |
| Prix | Cormorant Garamond 500 | 1.25–1.6rem · or · `font-variant-numeric: lining-nums` |
| Bouton / lien | Inter 500 | 12 px · uppercase · letter-spacing .3em |

Chargement : `Cormorant+Garamond:wght@500;600` + `Inter:wght@300;400;500`, `display=swap` (déjà chargées par le layout — ne recharger que dans les pages HTML autonomes).

### 2.3 Espacement

Base 8 px, progression ample (le vide respire) :

`--mrd-s1: .5rem` · `--mrd-s2: 1rem` · `--mrd-s3: 1.5rem` · `--mrd-s4: 2.5rem` · `--mrd-s5: 4rem` · `--mrd-s6: 6.5rem` · `--mrd-s7: 10rem`

- Padding vertical de section : `clamp(6rem, 14vh, 10rem)`
- Conteneur : `max-width: 1320px` · texte courant : `max-width: 720px`
- Gouttières : `clamp(1.25rem, 5vw, 4rem)`

### 2.4 Rayons

Le rectangulaire est un code maison. `--mrd-r0: 0` (boutons, images, cartes) · `--mrd-r1: 2px` (toléré sur swatches et champs). Jamais de pilule, jamais d'arrondi > 2 px.

### 2.5 Ombres & lueurs

Sur fond noir, pas d'ombre grise : on travaille en **lueurs** et **filets**.

| Token | Valeur | Usage |
|---|---|---|
| `--mrd-lueur` | `0 0 60px rgba(200,163,95,.08)` | Halo doux derrière objets clés |
| `--mrd-lueur-hover` | `0 0 40px rgba(200,163,95,.14)` | Cartes et boutons survolés |
| `--mrd-focus` | `0 0 0 2px #0B0B0D, 0 0 0 4px #C8A35F` | Focus clavier (toujours visible) |

Élévation d'une carte : fond `--mrd-surface` + bordure `--mrd-ligne` ; au survol : bordure `--mrd-ligne-or` + `--mrd-lueur-hover`. Pas de translation verticale brutale.

### 2.6 Motion

| Token | Valeur | Usage |
|---|---|---|
| `--mrd-ease-out` | `cubic-bezier(.22,1,.36,1)` | Entrées, reveals |
| `--mrd-ease-inout` | `cubic-bezier(.65,0,.35,1)` | Changements d'état |
| `--mrd-t-micro` | `300ms` | Hover, soulignés, boutons |
| `--mrd-t-reveal` | `900ms` | Révélations au scroll |
| `--mrd-t-lent` | `1600ms` | Fondus de héros, crossfades |
| Ken burns | `18s` linéaire, scale 1 → 1.06 | Visuel hero uniquement |
| Orbites | `60–140s` linéaire, rotation continue | Anneaux célestes |
| Stagger | `90–120ms` par élément | Grilles, listes |

**Règles.** `transform` et `opacity` uniquement. Parallaxe ≤ 3 % desktop, désactivé < 750 px. `IntersectionObserver` avec `unobserve` après révélation. Composer avec « MERIDIAN Motion » existant (`.mrd-reveal` → `.mrd-in`, Lenis déjà chargé — ne pas recharger). `prefers-reduced-motion: reduce` : toutes durées à 0, orbites figées, contenu affiché.

### 2.7 Signature céleste

- Anneaux orbitaux : ellipses SVG, trait or 1 px, opacité .18–.35, rotations lentes contraires.
- Points lumineux : disques 1–2 px, crème 20–60 %, scintillement ≥ 8 s (opacity seule).
- Halo : `radial-gradient` or à 6–10 % derrière l'objet central.
- Une constellation par page (accueil, tissus, professionnels…) : même langage, dessin distinct.
- Toujours `aria-hidden="true"`, jamais porteur d'information, `pointer-events:none`.

### 2.8 Champs de formulaire

`input`, `textarea`, `select` — module broderie, prise de rendez-vous professionnels, contact.

| Propriété | Valeur |
|---|---|
| Fond | `--mrd-surface` (`#101013`) |
| Bordure | `1px solid var(--mrd-ligne)` |
| Texte | `--mrd-creme` · Inter 400 · 16 px (évite le zoom iOS) |
| Placeholder | `--mrd-gris` — une indication, jamais un substitut de label |
| Focus | bordure `--mrd-or` + `box-shadow: var(--mrd-focus)` |
| Hauteur | ≥ 48 px (`textarea` : min 120 px) |
| Rayon | `--mrd-r1` (2 px) maximum |

**Règles.** Label toujours visible au-dessus du champ (Inter 500, 12 px, uppercase, letter-spacing .2em, gris chaud). Message d'erreur sous le champ concerné, jamais uniquement en tête de formulaire. `select` : `appearance:none` + chevron SVG or (trait 1.5 px). Champs obligatoires signalés.

---

## 3. Composants

**Fondations**
1. Bouton primaire — or plein, texte noir, uppercase .3em, hauteur ≥ 48 px, hover : dégradé or + lueur
2. Bouton secondaire — contour or 1 px, texte or, hover : fond or 8 %
3. Lien fileté — souligné or animé (scaleX), pour navigations douces
4. En-tête de section — eyebrow or + h2 serif + filet or 1 px (40 px)
5. Filet séparateur — 1 px, dégradé or vers transparent
6. Icônes — filaires SVG inline, trait 1.5 px, or, 24–28 px (jamais d'emoji)
7. Champ de formulaire — input/textarea/select selon § 2.8 : fond surface, filet neutre, focus or, ≥ 48 px, rayon 2 px

**Commerce**
8. Bandeau réassurance — 4 piliers (fabrication à la commande · gants blancs · garantie · échantillons), icône + libellé
9. Carte produit — image 4:5, nom serif, prix or, hover : zoom image 1.03 + bordure or
10. Bloc ensemble — composition 3+2+1, prix ensemble vs pièces, économie en or
11. Module broderie — visuel + champ de personnalisation, mention « +250 € par pièce »
12. Galerie produit immersive — visuel principal + vignettes, fondu croisé
13. Sélecteur de configuration — tissus, coloris, pieds ; libellés visibles, cibles ≥ 44 px
14. Barre d'achat sticky — nom, prix, CTA ; discrète, apparition au scroll

**Éditorial**
15. Hero cinématique — plein écran, ken burns ou emblème orbital, accroche serif
16. Compteurs discrets — chiffres serif, incrément lent à l'entrée
17. Section savoir-faire — image parallaxe + texte court
18. Bloc décorateurs — invitation sobre vers l'espace professionnels
19. Final CTA — pleine largeur, constellation, un seul bouton
20. Grille tissus — swatches par gamme, zoom au survol, CTA échantillons
21. Emblème orbital MERIDIAN — SVG signature, parallaxe souris ≤ 3 %

---

## 4. Garde-fous qualité (rappel par livrable)

- Performance : `loading="lazy"` hors hero, dimensions d'images déclarées (zéro layout shift), listeners `{passive:true}`, `requestAnimationFrame`, JS minimal.
- Mobile-first : typographies `clamp()`, cibles ≥ 44 px, parallaxe coupé < 750 px, aucun débordement horizontal.
- Accessibilité : AA partout, focus or visibles, `alt` descriptifs, hiérarchie h1→h3 stricte, `aria-hidden` sur le décor.
- Éditorial : français de maison — sobre, précis, sensoriel. Jamais de superlatif criard, jamais de jargon.
- Isolation : tout CSS/JS scopé `#mrd-…` / `.mrd-…`. Interdiction de toucher `body`, `main` ou aux sélecteurs du thème.
