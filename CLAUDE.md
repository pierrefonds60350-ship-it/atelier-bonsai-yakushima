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
- **Composition `.zen-feature`** (2026-07-16, suite à la demande cliente d'une mise en page
  « plus créative » pour « Qui suis-je ? ») : layout asymétrique remplaçant le `.split` classique
  pour les deux sections « Qui suis-je ? » (hero d'`a-propos.html` et le teaser d'`index.html`) —
  grand kanji en filigrane (`.zen-feature__kanji`, actuellement 静 shizu/« calme, sérénité », en
  écho au texte de Maria sur sa recherche de sérénité) positionné en absolu derrière le texte,
  photo détourée (fond retiré, `filter: drop-shadow(...)` plutôt qu'un cadre avec bordure) qui
  déborde visuellement de la grille, petite légende verticale `.zen-feature__vertical` en
  `writing-mode: vertical-rl` (masquée sous 860px). Utiliser `.zen-feature__kanji--right` (ou le
  modificateur `.zen-feature--reverse`, qui inverse aussi l'ordre media/texte) quand la photo est
  du côté gauche, pour que le kanji reste derrière la colonne de texte plutôt que sous la photo.
  Opacité du kanji réglée à 0,16 (0,07 testé d'abord, invisible à l'écran — corrigé après
  vérification visuelle). Réservé pour l'instant aux deux sections « Qui suis-je ? » : ne pas
  systématiser ce traitement à toutes les sections `.split` du site, ça perdrait son effet de
  signature si générisé partout.

Palette définie dans `:root` de `assets/css/style.css`, contrastes vérifiés ≥ 4,5:1 pour texte
blanc sur boutons primaire/accent :
- **Encre** (`--color-ink-*`) — texte, fond du footer et du bandeau CTA (seuls fonds sombres).
- **Papier** (`--color-paper-*`) — fonds clairs (proche d'un papier washi), y compris le header
  (fond clair avec filet bas, pas de bandeau sombre comme dans la première version).
- **Mousse / matcha** (`--color-sage-*`) — couleur principale, titres, boutons primaires, liens.
- **Vermillon** (`--color-vermillion-*`) — accent rare (sceau, eyebrow, liseré CTA, focus ring).

## Illustrations et photos — statut (mis à jour 2026-07-16)

Le site a d'abord utilisé des **illustrations SVG en trait fin, dessinées à la main dans le
code** (pas de fichier binaire, pas de dépendance externe) en l'absence de toute photo : un
bonsaï stylisé (silhouette + pot) et un enso (cercle zen incomplet), en `stroke="currentColor"`.
Ce motif SVG reste disponible dans l'historique git si besoin de le réintroduire ailleurs sur le
site (par exemple en complément de photos, pas uniquement en placeholder).

Trois photos ont ensuite été intégrées comme **placeholders temporaires**, à remplacer dès que
la cliente aura ses propres photos (elle l'a confirmé explicitement : « on peut placer ces
photos, qui seront remplacées par Maria ») :
- `assets/images/hero-bonsai-alcove.webp` (hero accueil) : photo de la banque **Pexels**
  (licence gratuite, usage commercial autorisé sans attribution — vérifié avant intégration),
  ne représente pas un arbre réel de Maria. **Recadrée le 2026-07-17** (bounding box du contenu
  non-noir calculé via numpy pour retirer la grande marge noire du fond studio d'origine, 675×900
  → 559×555) à la demande de la cliente (« enlève le rectangle noir autour de la photo »).
  `.hero__photo` en CSS est passé de `max-width:320px` + bordure fine à `max-width:620px` sans
  bordure avec `filter: drop-shadow(...)` sur l'image, pour un vrai visuel de hero plutôt qu'une
  petite vignette encadrée.
- `assets/images/bonsai-cutout.webp` (genévrier Pexels `pexels-j-232682-6392043.jpg`, fond
  détouré avec `rembg`/U2Net, recadré sur le sujet + petite marge, WebP avec canal alpha) :
  utilisé dans les deux compositions `.zen-feature` « Qui suis-je ? » (accueil et à propos).
  L'ancienne version encadrée `a-propos-bonsai-genevrier.webp` (fond studio gris conservé, boîte
  avec bordure) a été supprimée, remplacée par cette version détourée suite à la demande cliente
  de retirer l'arrière-plan pour une mise en page plus créative/japonisante.
- `assets/images/atelier-ligature-taille.webp` (page ateliers, mains en train de ligaturer/
  tailler un pin) : extraite de la livraison photo professionnelle de l'événement « Jardins et
  Nature en Fête 2026 » (dossier `Desktop/JNF2026/.../Photo JNF 2026/`), où Maria intervient
  comme experte bonsaï. Usage confirmé explicitement par la cliente pour ce site, en attendant
  ses propres photos.

**Portrait de Maria (2026-07-17, vraie photo, pas un placeholder)** : `assets/images/
maria-portrait.webp`, détouré en cercle (480×480, canal alpha, fond transparent hors du cercle)
à partir d'un fichier fourni par la cliente (`~/Desktop/IA/Bonsaï/photo Maria.heif`, HEIF converti
en JPEG via `sips`, recadrage visage au carré puis masque circulaire via Pillow, pas besoin de
`rembg` ici — juste un crop + masque, le fond du carré source est conservé jusqu'au bord du
cercle). Affiché en `.author-badge` (56px, filet fin) à côté du nom « Maria Millet », dans les
deux sections « Qui suis-je ? » (accueil et à propos). Contrairement aux 3 photos ci-dessus, **ce
n'est pas un placeholder** : c'est la vraie photo de la cliente, à garder telle quelle.

**Outil de détourure** : `rembg` (modèle U2Net, ~176 Mo téléchargé au premier usage dans
`~/.u2net/`) installé via `pip3 install rembg onnxruntime` — pas encore dans un fichier de
dépendances du projet puisque ce n'est pas un besoin récurrent du build (aucun build step), juste
un outil ponctuel utilisé en local pour cette détourure. Si une nouvelle détourure est nécessaire
plus tard, réinstaller au besoin plutôt que d'ajouter une dépendance permanente au projet.

**Point de vigilance photos en général sur ce projet** : plusieurs photos proposées par la
cliente au fil de la conversation se sont révélées non réutilisables et ont été écartées :
une photo de presse (crédit photographe + journal régional, droit d'auteur tiers) et une photo
de provenance non identifiée (« resize pixel », probablement trouvée en ligne). Toujours
vérifier la provenance (nom de fichier, dossier source, mention explicite de la cliente) avant
d'intégrer une photo fournie en pièce jointe de conversation plutôt qu'en fichier déposé
directement dans le projet.

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

Voir « Illustrations et photos — statut » ci-dessus pour l'état actuel. Le portrait de Maria est
maintenant une vraie photo (voir ci-dessus), plus un placeholder. Toujours à fournir par la
cliente, pour remplacer les 3 placeholders restants :
- Vraies photos de l'atelier / des bonsaïs de Maria (hero de l'accueil, page à propos, page
  ateliers).
- Logo, si la cliente en a un (sinon le site garde le sceau `.hanko` 山 en logo temporaire).

## Déploiement (2026-07-17)

- **Dépôt GitHub** : `pierrefonds60350-ship-it/atelier-bonsai-yakushima` (privé), créé et publié
  par le client lui-même via GitHub Desktop (Add Local Repository → Publish repository), pas par
  moi (création de dépôt = action nécessitant confirmation explicite de l'utilisateur, refusée
  deux fois par le classifieur auto-mode avant que le client la fasse lui-même).
- **Cloudflare Pages** : projet `atelier-bonsai-yakushima`, déployé sur
  `https://atelier-bonsai-yakushima.pages.dev`, dans le même compte Cloudflare que
  drevantjnf.fr (sous-domaine `drevantjnf.workers.dev`).
  **Déployé par glisser-déposer d'un zip (« direct upload »), PAS par connexion Git.** Plusieurs
  tentatives de connecter le dépôt GitHub ont échoué (la fenêtre d'autorisation GitHub
  redirigeait systématiquement vers la page d'info de l'app plutôt que vers un écran
  d'autorisation, y compris en repartant de zéro depuis Paramètres → Build → Référentiel Git →
  Connexion). Non résolu à ce jour.
  **Conséquence pratique importante** : les futures modifications que je fais sur le code ne se
  déploient PAS automatiquement. Il faut à chaque fois régénérer un zip (exclure `.git/`,
  `.claude/`, `.private/`, `.DS_Store` — voir commande utilisée : `zip -r -X site.zip . -x
  ".git/*" ".claude/*" ".private/*" ".DS_Store"`) et le redéposer manuellement dans Cloudflare
  (Workers et Pages → atelier-bonsai-yakushima → bouton "..." ou re-upload direct). Retenter la
  connexion Git une prochaine fois si l'automatisation redevient nécessaire (le client a un
  compte GitHub avec l'app Cloudflare déjà installée et autorisée sur ce dépôt spécifiquement,
  donc l'autorisation en tant que telle n'est pas le problème — c'est un souci de redirection
  côté interface Cloudflare/GitHub à l'usage).
- Pas de nom de domaine personnalisé à ce jour, le client achètera plus tard via Cloudflare
  Registrar une fois le site validé par Maria.

## Prochaines étapes

1. Récupérer les vraies photos/logo restantes auprès de la cliente et remplacer les 3
   placeholders (voir « Illustrations et photos — statut »). Le portrait de Maria est déjà réglé.
2. Créer un compte gratuit sur web3forms.com, générer une clé d'accès, la renseigner dans
   `contact.html` (`<input type="hidden" name="access_key" value="...">`), puis redéployer.
3. Décider des informations pratiques manquantes (tarifs, durée des stages, dates, nombre de
   places par session, individuel/groupe) — actuellement pas affichées faute de donnée.
4. Réessayer de connecter le dépôt Git à Cloudflare Pages pour automatiser le déploiement (voir
   « Déploiement » ci-dessus), ou continuer en zip manuel si ça reste bloqué.
5. Achat du nom de domaine (Cloudflare Registrar) une fois le site validé.
