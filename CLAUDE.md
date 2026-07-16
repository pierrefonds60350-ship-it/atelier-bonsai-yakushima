# L'Atelier du Bonsaï Yakushima — site vitrine statique

Site vitrine pour **l'Atelier du Bonsaï Yakushima**, animé par Maria Millet à
**Ainay-le-Vieil (Cher)**. Ateliers découverte et stages de perfectionnement autour de l'art
du bonsaï (formation à l'Académie Bonsaï auprès de Senseï Yudji Akanuma).

Projet **indépendant** du site Jardins & Nature en Fête (`drevant-natureenfete`) : dossier de
travail, dépôt Git et déploiement Cloudflare Pages séparés.

## Stack

- HTML5 / CSS3 / JS vanilla. Aucune dépendance npm, aucun build step.
- Polices système (pas de requête externe) : `Georgia, 'Iowan Old Style', serif` pour les
  titres (h1–h4), `-apple-system, 'Segoe UI', Roboto, sans-serif` pour le corps de texte.
  À remplacer par des polices auto-hébergées si une identité typographique plus marquée est
  souhaitée plus tard.
- Hébergement cible : Cloudflare Pages. Pas de nom de domaine à ce jour (2026-07-16) — le
  client achètera un nom de domaine chez Cloudflare Registrar une fois le site prêt ; en
  attendant, déploiement sur le sous-domaine gratuit `*.pages.dev`.
- Formulaire de contact : structure Web3Forms prête dans `contact.html`
  (`https://api.web3forms.com/submit`), **clé d'accès à renseigner par le client** (compte
  gratuit sur web3forms.com — je ne peux pas créer ce compte à sa place).

## Structure de fichiers

```
/
├── CLAUDE.md
├── .gitignore
├── index.html            ← accueil
├── ateliers.html          ← détail des stages + thèmes abordés
├── a-propos.html          ← bio de Maria Millet
├── contact.html           ← email / téléphone + formulaire Web3Forms
├── robots.txt
├── sitemap.xml
└── assets/
    ├── css/style.css      ← tokens + base + composants (fichier unique)
    ├── js/main.js         ← burger menu mobile
    └── images/            ← vide pour l'instant, voir "Visuels à fournir"
```

## Direction artistique — épurée, zen, japonisante (2026-07-16)

À la demande de la cliente (« LE SITE DOIT ETRE EPURÉ ZEN A LA JAPONAISE »), le design a été
repensé dans cet esprit après une première version plus « artisanale/chaleureuse ». Principes
à respecter pour toute nouvelle page ou section :
- **Beaucoup de blanc/vide** : espacements de section généreux (`--space-2xl: 100px`), pas de
  surcharge visuelle, un seul point d'attention par section.
- **Pas d'ombres, pas de dégradés** : composants à plat, séparés par des filets fins
  (`--color-line`, 1px) plutôt que des `box-shadow`. `.theme-grid` utilise un filet de grille
  1px plutôt que des cartes ombrées.
- **Rouge vermillon utilisé avec parcimonie** (`--color-vermillion-*`) : comme un sceau
  (« hanko ») japonais, jamais en aplat large sauf le bandeau CTA (`.cta-banner`, fond encre +
  liseré vermillon en haut, pas de bloc vermillon plein comme avant).
- **Motif `.ornament`** (trait fin + petit cercle) en haut des sections/hero pour un rythme
  calme, esprit zen.
- **Le sceau `.hanko`** : carré vermillon avec le kanji 山 (yama, « montagne », clin d'œil à
  Yakushima) à côté du nom du site dans le logo, tient lieu de logo temporaire tant que la
  cliente n'en a pas fourni.

Palette définie dans `:root` de `assets/css/style.css`, contrastes vérifiés ≥ 4,5:1 pour texte
blanc sur boutons primaire/accent :
- **Encre** (`--color-ink-*`) — texte, fond du footer et du bandeau CTA (seuls fonds sombres).
- **Papier** (`--color-paper-*`) — fonds clairs (proche d'un papier washi), y compris le header
  (fond clair avec filet bas, pas de bandeau sombre comme dans la première version).
- **Mousse / matcha** (`--color-sage-*`) — couleur principale, titres, boutons primaires, liens.
- **Vermillon** (`--color-vermillion-*`) — accent rare (sceau, eyebrow, liseré CTA, focus ring).

## Illustrations en attendant les photos réelles

Aucune photo/logo n'a encore été fournie par la cliente (« PAS ENCORE DE LOGO NI DE PHOTO »).
Plutôt que d'utiliser de fausses photos de banque (problème de droits + décalage avec le
« vrai » atelier), les emplacements `.split__media` utilisent des **illustrations SVG en trait
fin, dessinées à la main dans le code** (pas de fichier binaire, pas de dépendance externe) :
un bonsaï stylisé (silhouette + pot) et un enso (cercle zen incomplet), tous deux en
`stroke="currentColor"` pour hériter de la couleur du composant. Elles sont dupliquées telles
quelles dans `index.html` et `a-propos.html`. **À remplacer par de vraies photos dès
réception**, mais le style trait-fin peut être conservé comme identité graphique même après
(par exemple en complément des photos, pas uniquement en placeholder).

## Contenu — sources et statut

Tout le texte ci-dessous a été fourni directement par la cliente (Maria Millet) par message,
repris tel quel (légère relecture orthographique/typographique autorisée, pas de réécriture
éditoriale) :
- Texte de présentation de l'atelier (page d'accueil).
- Liste des thèmes abordés en stage (formes et styles, outils/matériel/substrats, taille et
  pinçage, ligature et pliage, fertilisation/arrosage/traitements, rempotage et taille des
  racines, définition d'un projet pour l'arbre, calendrier d'entretien, poteries, exposition en
  Tokonoma, conseils d'entretien à domicile).
- Texte « À propos » (bio complète de Maria Millet).
- Coordonnées de contact : email `Maria.millet18@gmail.com`, téléphone `07 62 35 80 57`.

## Visuels à fournir par la cliente

`assets/images/` est vide pour l'instant. En attendant les vraies photos, le site utilise des
fonds dégradés CSS (tons vert mousse / terre cuite) à la place de photos, sans fausse image
de banque. **À remplacer dès réception** :
- Photo(s) de l'atelier / des bonsaïs de Maria (hero de l'accueil).
- Photo de Maria (page à propos).
- Logo, si la cliente en a un (sinon le site utilise un simple lettrage « Yakushima »).

## Prochaines étapes

1. Récupérer les photos/logo auprès de la cliente et les intégrer (remplacer les fonds
   dégradés CSS par de vraies images, compressées avant intégration).
2. Créer un compte gratuit sur web3forms.com, générer une clé d'accès, la renseigner dans
   `contact.html` (`<input type="hidden" name="access_key" value="...">`).
3. Décider des informations pratiques manquantes (tarifs, durée des stages, dates, nombre de
   places par session, individuel/groupe) — actuellement pas affichées faute de donnée.
4. Créer le dépôt GitHub et le projet Cloudflare Pages (déploiement sur `*.pages.dev` dans un
   premier temps).
5. Achat du nom de domaine (Cloudflare Registrar) une fois le site validé, puis rattachement au
   projet Cloudflare Pages.
