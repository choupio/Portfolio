# Portfolio Cloud et réseaux — dossier de projet

Oct 17, 2026 · @Ginkaku

## Contexte et références

Ce dossier retrace la conception d'un portfolio pour un étudiant en informatique, parcours cloud et réseaux, codé avec l'aide d'un assistant puis déployé en ligne. L'objectif est un site original, qui montre le métier dans sa forme même et pas seulement dans son contenu.

Références fournies au départ :

| Référence | Statut |
| --- | --- |
| [Figma, exemples de portfolios](https://www.figma.com/fr-fr/resource-library/exemples-sites-portfolio/) | Non consultée, accès automatisé bloqué |
| [Canva, modèles de portfolio](https://www.canva.com/fr_fr/presentations/modeles/portfolio/) | Consultée |
| [Portfoliobox, modèles](https://www.portfoliobox.com/fr/templates) | Consultée |
| [Pinterest, idées de portfolio](https://fr.pinterest.com/ideas/portfolio-exemple/944268390318/) | Non ouverte |
| [Guide du portfolio, académie d'Aix-Marseille (PDF)](https://www.pedagogie.ac-aix-marseille.fr/upload/docs/application/pdf/2017-01/guide_portfolio.pdf) | Non ouvert |

Les deux références consultées visent surtout des photographes et des designers, avec beaucoup de beige, de noir et blanc et de minimalisme. Elles ne disent rien d'un profil cloud et réseaux : elles servent d'inspiration pour la mise en page et la typographie, pas de modèle à copier.

## Concepts proposés et choix

Le choix retenu est un hybride : une accroche en pleine page (le paquet qui remonte les couches OSI), puis des études de cas au style plan d'ingénieur. Un recruteur passe environ 30 secondes sur une page, il faut donc une accroche forte puis du fond.

| Concept | Idée | Remarque |
| --- | --- | --- |
| 1. Paquet OSI | Au scroll, un paquet remonte les 7 couches. Chaque couche retire un en-tête et le texte devient lisible. | Le plus original. Retenu pour l'accroche. |
| 2. NOC / dashboard | Un tableau de bord type Grafana ou page de status. Chaque projet est un service avec un statut et des métriques. | Possibilité d'un vrai indicateur d'uptime du site. |
| 3. Carte topologique | Un schéma réseau animé dont les nœuds sont les projets, compétences et certifs. | Spectaculaire, à bien soigner sur mobile. |
| 4. Terminal | Un faux shell avec des commandes comme `whoami` ou `ls projects/`. | Un peu vu. Prévoir un mode interface classique. |
| 5. Blueprint | Fond de plan technique, chaque projet présenté comme un schéma d'architecture. | Le plus sobre, met le contenu en avant. Retenu pour les études de cas. |

Les concepts 2, 3 et 4 sont écartés pour l'instant.

## Identité visuelle et brief maître

Le site s'inspire d'un plan d'ingénieur : fond bleu cyanotype, traits clairs, orange et aqua repris des gaines de fibre optique. Un seul effet fort, l'accroche, le reste reste calme. Le brief ci-dessous est à copier dans un fichier `BRIEF.md` à la racine du projet (ou `CLAUDE.md`, `.cursorrules` selon l'outil).

```markdown
# Portfolio de [PRÉNOM NOM] — étudiant en informatique, parcours cloud et réseaux

## Objectif
Portfolio pour recruteurs (stages, alternance) et jury de l'école. Un visiteur doit comprendre en 30 secondes qui je suis, et pouvoir creuser 3 à 4 projets en profondeur. Langue : français d'abord, structure prête pour l'anglais.

## Stack
Astro (TypeScript strict), Tailwind, MDX, content collection "projets", GSAP + ScrollTrigger pour l'accroche uniquement, SVG inline pour les schémas. Polices auto-hébergées via Fontsource. Site 100 % statique.

## Identité visuelle : plan d'ingénieur
Couleurs (variables CSS) :
- Cyanotype #123A73 : fond principal
- Calque #EEF3F9 : texte et traits sur fond bleu, fond des sections claires
- Quadrillage #3F6DB5 : grille et traits secondaires
- Orange fibre #FF6B1A : le paquet, le chemin de donnée, les boutons
- Aqua OM3 #45D9D2 : état validé, donnée lisible
- Encre #0A2147 : texte sur fond clair ET texte sur fond orange
Règle de contraste : l'orange ne sert jamais de couleur de texte courant (sous 4,5:1 sur le bleu), uniquement pour les graphiques, les gros titres et les boutons.

Typographie :
- Titres : Archivo, axe de largeur étendu, graisse 700, casse normale
- Texte : Source Serif 4, 18 px minimum, interligne 1,65, lignes de 70 caractères max
- Code et configs : IBM Plex Mono, uniquement pour du vrai code

Structure visuelle : fond de quadrillage fin sur les sections bleues. Les sections "à propos" et "contact" sont sur fond Calque pour créer du rythme.

## Accroche : le paquet qui remonte les couches
Section épinglée, pilotée par le scroll, sur environ 3 hauteurs d'écran. Le paquet arrive en bits bruts et remonte de la couche 1 à la couche 7. À chaque couche, un segment d'en-tête sort du paquet et le texte brouillé devient plus lisible.
- Couche 1, physique : bruit de bits. Légende : "Signal reçu."
- Couche 2, liaison : trame Ethernet, en-tête retiré. "Trame reçue."
- Couche 3, réseau : paquet IP. "Paquet routé jusqu'ici."
- Couche 4, transport : segment TCP. "Connexion établie."
- Couche 5, session : "Session ouverte."
- Couche 6, présentation : le texte se déchiffre. "Données décodées."
- Couche 7, application : texte entièrement lisible : nom, titre, une phrase, boutons "Voir les projets" et "Télécharger le CV (PDF)".
À gauche, la pile des 7 couches sert de navigation et de progression. Les numéros de couche sont les seuls numéros du site, parce que c'est une vraie séquence. Un lien "Passer l'animation" est toujours visible. Avec prefers-reduced-motion, afficher directement l'état final avec la pile en schéma statique.

## Études de cas
Une page par projet (3 à 4). Chaque page commence par un cartouche de plan (projet, rôle, période, stack, lien GitHub), puis : contexte et problème, schéma d'architecture en SVG avec le chemin principal en orange, choix techniques, difficultés rencontrées, résultat. Les extraits de config sont réels, courts et commentés.

## Autres pages
À propos, homelab, certifications (obtenues ou en cours, clairement distinguées), veille technologique, contact. Sobres, sans animation.

## Règles de mouvement
Une seule animation autonome : l'accroche. Ailleurs, le mouvement répond uniquement à une action de l'utilisateur. Pas d'apparition en fondu sur chaque section, pas d'effet de survol sur chaque carte.

## Interdits
Dégradés décoratifs, cartes arrondies identiques en série, fond noir avec accent vert fluo, fond crème avec terracotta, étiquettes en majuscules au-dessus des titres, numérotation hors couches OSI, flèches "→" ajoutées partout.

## Textes
Phrases courtes, verbes simples, casse normale. Les boutons disent ce qui se passe ("Télécharger le CV (PDF)", "Voir l'architecture"). Pas de "passionné par", pas de formules creuses.

## Qualité minimale
Responsive dès 360 px, focus clavier visible, contrastes AA, images en WebP avec alt, titres hiérarchisés, balises Open Graph, Lighthouse supérieur à 90 partout.
```

À la mise en œuvre, Tailwind et MDX ne sont pas installés dès l'étape 1 : le CSS est écrit à la main, MDX viendra avec les pages de projets (voir le journal en fin de dossier).

## Plan de travail et prompts

Le chantier tient en 7 étapes, avec un commit après chaque étape réussie.

- [ ] 1\. Fondations : projet Astro, couleurs et polices, layout de base
- [ ] 2\. Premier déploiement : dépôt GitHub branché sur Cloudflare Pages ou Vercel
- [ ] 3\. Accroche OSI avec GSAP ScrollTrigger
- [ ] 4\. Gabarit d'étude de cas : cartouche de plan et schéma SVG
- [ ] 5\. Pages restantes : à propos, homelab, certifications, veille, contact
- [ ] 6\. Finitions : accessibilité, performance, mobile, Open Graph
- [ ] 7\. Infrastructure as code : S3, CloudFront, ACM, Route 53 avec Terraform et GitHub Actions

Prompts à confier à l'assistant. L'étape 1 a finalement été faite à la main (voir la section « Structure du projet et code »), la variante ci-dessous reste utilisable si le projet existe déjà.

**Étape 1, variante projet déjà créé**

```text
Lis BRIEF.md. Le projet Astro existe déjà et tourne en local. Ajoute Tailwind et MDX, crée la content collection "projets", installe en auto-hébergement les polices Archivo, Source Serif 4 et IBM Plex Mono, et définis les couleurs et l'échelle typographique en variables CSS. Si l'axe de largeur d'Archivo n'est pas disponible, propose une alternative avant de continuer. Crée le layout de base (en-tête, pied de page) et une page d'accueil vide. Ne fais rien d'autre et liste ce que tu as modifié.
```

**Étape 3, l'accroche**

```text
Construis l'accroche décrite dans BRIEF.md avec GSAP ScrollTrigger. Commence par la version statique des 7 couches, puis ajoute l'animation. Gère prefers-reduced-motion, le lien "Passer l'animation" et la version mobile. Montre-moi le résultat avant d'aller plus loin.
```

**Étape 4, gabarit d'étude de cas**

```text
Crée le gabarit de page projet : cartouche de plan, zone de schéma SVG, sections de texte. Fais-en un composant Astro réutilisable alimenté par le frontmatter MDX. Crée un projet factice pour tester.
```

**Étape 6, finitions**

```text
Audite le site : accessibilité clavier et lecteur d'écran, contrastes, performance, mobile 360 px, balises Open Graph. Corrige tout ce qui fait passer un score Lighthouse sous 90 et liste ce que tu as changé.
```

Les étapes 2, 5 et 7 se font sans prompt dédié : l'étape 2 consiste à brancher le dépôt GitHub sur l'hébergeur, l'étape 5 reprend le style sobre du reste du site, l'étape 7 est décrite ci-dessous.

**Déploiement.** Deux voies sont prévues. La voie simple et gratuite : Cloudflare Pages, Vercel ou Netlify, avec un nom de domaine à soi. La voie qui valorise le parcours : S3 + CloudFront + ACM + Route 53 (ou Azure Static Web Apps), décrits en Terraform, avec un pipeline GitHub Actions qui déploie à chaque push, des en-têtes de sécurité, HTTPS/HSTS et une sonde d'uptime. Le déploiement devient alors lui-même une étude de cas. Le coût attendu est très faible hors nom de domaine, à vérifier sur la tarification des fournisseurs.

**Conseils de vibe coding**

1. Rédiger d'abord un brief de design : palette, 2 polices maximum, principes d'animation, ton.
2. Construire section par section, jamais tout d'un coup.
3. Exiger dès le départ le responsive, `prefers-reduced-motion` et un bon score Lighthouse.
4. Faire un commit à chaque étape réussie.
5. Après l'étape 3, tester le site sur téléphone avant de continuer.

## Mise en place de l'environnement

Il faut Node.js, Git, VS Code et un compte GitHub. Les commandes sont données pour Windows, elles sont identiques sous macOS et Linux une fois les outils installés. Les projets se placent hors d'un dossier synchronisé par OneDrive, car `node_modules` est volumineux et la synchronisation cause des bugs.

**Node.js.** Astro demande Node.js 22.22.0 ou plus récent, en version paire : les versions impaires comme la v23 ne sont pas supportées. Installer la version LTS depuis nodejs.org, puis vérifier :

```bash
node -v
npm -v
```

**Git.** Installer depuis git-scm.com avec les options par défaut, puis configurer l'identité :

```bash
git config --global user.name "Ton Nom"
git config --global user.email "ton@email.fr"
git config --global init.defaultBranch main
```

**VS Code.** Installer depuis code.visualstudio.com et cocher l'option qui ajoute `code` au PATH.

**Extensions** (panneau Extensions : `Ctrl+Shift+X`)

| Extension | Identifiant | Usage |
| --- | --- | --- |
| Astro | `astro-build.astro-vscode` | Extension officielle recommandée par Astro |
| Prettier | `esbenp.prettier-vscode` | Formatage |
| MDX | `unifiedjs.vscode-mdx` | Pages d'études de cas, plus tard |
| Tailwind CSS IntelliSense | `bradlc.vscode-tailwindcss` | Utile seulement si Tailwind est ajouté |
| Claude Code | `anthropic.claude-code` | Assistant dans VS Code |

**Assistant Claude Code.** Il faut VS Code 1.98.0 ou plus récent. Installer l'extension depuis la vue Extensions en cherchant « Claude Code », puis se connecter avec un compte Anthropic ou une clé API. Si l'extension n'apparaît pas, redémarrer VS Code ou lancer « Developer: Reload Window » depuis la palette de commandes (`Ctrl+Shift+P`). L'extension embarque la CLI, mais lancer `claude` dans le terminal intégré demande d'installer la CLI séparément. Les conditions d'accès changent : les vérifier sur le site d'Anthropic.

**Routine de travail**

1. Garder un terminal avec `npm run dev` ouvert et le site à côté, sur http://localhost:4321.
2. Donner une seule petite tâche à la fois.
3. Relire les modifications avant de les accepter, puis tester dans le navigateur.
4. Faire un commit quand ça marche (Source Control, `Ctrl+Shift+G`).
5. Pour annuler les modifications non commitées des fichiers existants : `git restore .` (les nouveaux fichiers restent).

Pour tester sur téléphone, sur le même Wi-Fi : `npm run dev -- --host`, puis ouvrir l'adresse réseau affichée.

**Problèmes fréquents**

| Symptôme | Solution |
| --- | --- |
| `node` n'est pas reconnu | Fermer et rouvrir VS Code après l'installation de Node |
| PowerShell : exécution de scripts désactivée | `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, ou passer le terminal VS Code sur Command Prompt ou Git Bash |
| `code .` ne marche pas | Palette de commandes : « Shell Command: Install 'code' command in PATH » (surtout macOS) |
| Le port 4321 est déjà pris | Astro en propose un autre, lire l'adresse affichée dans le terminal |

## Structure du projet et code

La base du site est un projet Astro installé à la main dans le dépôt cloné, avec du CSS simple. Chaque fichier ci-dessous se crée tel quel : clic droit dans l'explorateur de VS Code, « New File », puis le chemin complet (les dossiers se créent tout seuls).

```text
portfolio/
├── public/                  fichiers servis tels quels (CV en PDF, images)
├── src/
│   ├── components/
│   │   └── Hero.astro       l'accroche
│   ├── layouts/
│   │   └── Base.astro       le cadre commun à toutes les pages
│   ├── pages/
│   │   └── index.astro      une page = un fichier = une URL
│   └── styles/
│       └── global.css       couleurs, polices, styles de base
├── .gitignore
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

**Installation.** Dans le dépôt cloné (le dossier s'appelle ici `portfolio`) :

```bash
cd portfolio
code .
npm init --yes
npm install astro
npm install @fontsource-variable/archivo @fontsource-variable/source-serif-4 @fontsource/ibm-plex-mono
```

Astro s'installe en local, jamais avec `-g`. Archivo existe en version variable avec un axe de largeur, réglé en CSS avec `font-variation-settings`. Ensuite, remplacer le bloc `scripts` de `package.json` par :

```json
"scripts": {
  "dev": "astro dev",
  "build": "astro build",
  "preview": "astro preview"
},
```

**astro.config.mjs**

```js
import { defineConfig } from 'astro/config';

export default defineConfig({});
```

**tsconfig.json**

```json
{
  "extends": "astro/tsconfigs/strict"
}
```

**.gitignore** (vérifier qu'il contient bien `node_modules/` avant le premier commit)

```text
.astro/
.env
dist/
node_modules/
```

**src/styles/global.css**

```css
:root {
  --cyanotype: #123a73;
  --calque: #eef3f9;
  --quadrillage: #3f6db5;
  --orange: #ff6b1a;
  --aqua: #45d9d2;
  --encre: #0a2147;

  --police-titre: 'Archivo Variable', system-ui, sans-serif;
  --police-texte: 'Source Serif 4 Variable', Georgia, serif;
  --police-code: 'IBM Plex Mono', ui-monospace, monospace;

  --marge: clamp(1rem, 5vw, 4rem);
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
  background-color: var(--cyanotype);
  background-image:
    linear-gradient(color-mix(in srgb, var(--quadrillage) 35%, transparent) 1px, transparent 1px),
    linear-gradient(90deg, color-mix(in srgb, var(--quadrillage) 35%, transparent) 1px, transparent 1px);
  background-size: 48px 48px;
  color: var(--calque);
  font-family: var(--police-texte);
  font-size: 1.125rem;
  line-height: 1.65;
}

h1,
h2,
h3 {
  margin: 0;
  font-family: var(--police-titre);
  font-weight: 700;
  font-variation-settings: 'wdth' 125, 'wght' 700;
  line-height: 1.05;
}

p {
  max-width: 70ch;
  margin: 0;
}

a {
  color: inherit;
}

:focus-visible {
  outline: 3px solid var(--aqua);
  outline-offset: 3px;
}

.bouton {
  display: inline-block;
  padding: 0.75rem 1.25rem;
  border: 2px solid var(--orange);
  background: var(--orange);
  color: var(--encre);
  font-family: var(--police-titre);
  font-variation-settings: 'wdth' 110, 'wght' 700;
  text-decoration: none;
}

.bouton.secondaire {
  background: transparent;
  border-color: var(--calque);
  color: var(--calque);
}

.clair {
  background: var(--calque);
  color: var(--encre);
}
```

**src/layouts/Base.astro** : le cadre commun (polices, styles globaux, en-tête, zone de contenu)

```astro
---
import '@fontsource-variable/archivo/wdth.css';
import '@fontsource-variable/source-serif-4';
import '@fontsource/ibm-plex-mono/400.css';
import '../styles/global.css';

interface Props {
  titre: string;
  description?: string;
}

const {
  titre,
  description = 'Portfolio de Prénom Nom, étudiant en informatique, parcours cloud et réseaux.',
} = Astro.props;
---

<!doctype html>
<html lang="fr">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="description" content={description} />
    <title>{titre}</title>
  </head>
  <body>
    <header class="entete">
      <a class="nom" href="/">Prénom Nom</a>
      <nav aria-label="Navigation principale">
        <a href="/#projets">Projets</a>
        <a href="/#contact">Contact</a>
      </nav>
    </header>
    <main>
      <slot />
    </main>
  </body>
</html>

<style>
  .entete {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    padding: 1.25rem var(--marge);
    font-family: var(--police-titre);
  }
  .entete a {
    text-decoration: none;
  }
  .entete a:hover {
    text-decoration: underline;
  }
  .nom {
    font-variation-settings: 'wdth' 125, 'wght' 700;
  }
  nav {
    display: flex;
    gap: 1.5rem;
  }
</style>
```

**src/components/Hero.astro** : l'accroche, version statique (l'animation viendra à l'étape 3)

```astro
---
const couches = [
  { numero: 7, nom: 'Application' },
  { numero: 6, nom: 'Présentation' },
  { numero: 5, nom: 'Session' },
  { numero: 4, nom: 'Transport' },
  { numero: 3, nom: 'Réseau' },
  { numero: 2, nom: 'Liaison' },
  { numero: 1, nom: 'Physique' },
];
---

<section class="hero" aria-labelledby="titre-hero">
  <ol class="pile" aria-label="Les sept couches du modèle OSI">
    {
      couches.map((couche) => (
        <li class:list={['couche', { actif: couche.numero === 7 }]}>
          <span class="numero">{couche.numero}</span>
          <span>{couche.nom}</span>
        </li>
      ))
    }
  </ol>

  <div class="message">
    <h1 id="titre-hero">Prénom Nom</h1>
    <p class="accroche">
      Étudiant en informatique, parcours cloud et réseaux. À adapter : ce que tu
      cherches (stage, alternance) et ce que tu sais faire.
    </p>
    <p class="actions">
      <a class="bouton" href="#projets">Voir les projets</a>
      <a class="bouton secondaire" href="/cv.pdf">Télécharger le CV (PDF)</a>
    </p>
  </div>
</section>

<style>
  .hero {
    display: grid;
    grid-template-columns: minmax(11rem, 15rem) 1fr;
    gap: 3rem;
    align-items: center;
    min-height: 80svh;
    padding: 3rem var(--marge) 5rem;
  }
  .pile {
    display: grid;
    gap: 0.5rem;
    margin: 0;
    padding: 0;
    list-style: none;
  }
  .couche {
    display: flex;
    gap: 1rem;
    align-items: baseline;
    padding: 0.6rem 0.9rem;
    border: 1px solid var(--quadrillage);
    font-family: var(--police-titre);
    color: color-mix(in srgb, var(--calque) 70%, transparent);
  }
  .couche.actif {
    border-color: var(--orange);
    background: color-mix(in srgb, var(--orange) 14%, transparent);
    color: var(--calque);
  }
  .numero {
    width: 1.5ch;
    color: var(--aqua);
    font-variation-settings: 'wdth' 125, 'wght' 700;
  }
  h1 {
    font-size: clamp(2.75rem, 8vw, 6rem);
  }
  .accroche {
    margin-top: 1.5rem;
    font-size: 1.35rem;
  }
  .actions {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    margin-top: 2rem;
  }
  @media (max-width: 720px) {
    .hero {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    .message {
      order: -1;
    }
  }
</style>
```

**src/pages/index.astro** : la page d'accueil

```astro
---
import Base from '../layouts/Base.astro';
import Hero from '../components/Hero.astro';
---

<Base titre="Prénom Nom, cloud et réseaux">
  <Hero />

  <section id="projets" class="section">
    <h2>Projets</h2>
    <p>Les études de cas arriveront ici.</p>
  </section>

  <section id="contact" class="section clair">
    <h2>Contact</h2>
    <p>Ton adresse e-mail et tes liens GitHub et LinkedIn.</p>
  </section>
</Base>

<style>
  .section {
    padding: 5rem var(--marge);
  }
</style>
```

**Lancer et sauvegarder**

```bash
npm run dev
```

Ouvrir http://localhost:4321. Le résultat attendu : un fond bleu quadrillé, le nom en grand avec les deux boutons, la pile des 7 couches à gauche avec la couche 7 en orange, puis une section « Projets » sur fond bleu et une section « Contact » sur fond clair. Le bouton CV pointe vers un 404 tant que le fichier n'est pas placé dans `public/cv.pdf`. Quand tout fonctionne :

```bash
git add .
git commit -m "Structure Astro et page d'accueil"
git push
```

Remplacer partout « Prénom Nom » par le vrai nom.

## Journal, prochaines étapes et sources

Toutes les décisions ci-dessous datent du 17 octobre 2026, de la plus récente à la plus ancienne.

| Date | Décision | Raison |
| --- | --- | --- |
| 17 oct. 2026 | Mise en œuvre manuelle d'Astro, CSS simple, sans Tailwind ni MDX à l'étape 1 | Fonctionne dans un dépôt déjà cloné et montre chaque fichier. MDX viendra avec les pages de projets. |
| 17 oct. 2026 | Travail dans VS Code, avec l'extension Claude Code en option | Le brief et les prompts marchent avec n'importe quel assistant. |
| 17 oct. 2026 | Hybride retenu : accroche OSI puis études de cas style blueprint | Accroche forte, puis du fond, pour un recruteur qui passe environ 30 secondes sur la page. |
| 17 oct. 2026 | Références analysées : Canva et Portfoliobox consultés, Figma bloqué, Pinterest et PDF non ouverts | Références orientées créatifs, utilisées seulement pour la mise en page et la typographie. |

**Prochaines étapes**

- [ ] Remplacer « Prénom Nom », rédiger l'accroche, placer le CV dans `public/cv.pdf`
- [ ] Lancer l'étape 1 en local, puis commit et push
- [ ] Brancher le dépôt sur un hébergeur (étape 2)
- [ ] Lister les 3 ou 4 projets à mettre en avant
- [ ] Écrire l'animation OSI au scroll (étape 3)
- [ ] Créer le gabarit des pages de projet avec MDX (étape 4)

**Sources**

- [Astro, installation et prérequis](https://docs.astro.build/en/install-and-setup/)
- [Claude Code dans VS Code](https://code.claude.com/docs/en/vs-code)
- [Fontsource, Archivo variable](https://fontsource.org/fonts/archivo/install)
- [Fontsource, polices variables et axes](https://fontsource.org/docs/getting-started/variable)
