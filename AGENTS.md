# AGENTS.md — JurisMaster

Plateforme éducative juridique française (HTML/CSS/JS statique, aucun build requis).

## Stack technique

- **HTML5** sémantique (pas de framework)
- **Tailwind CSS 3.x** via CDN (`https://cdn.tailwindcss.com`)
- **Vanilla JS ES6+** (pas de bundler, pas de npm)
- **Google Fonts** : Inter (corps) + Playfair Display (titres)
- **localStorage** pour la gamification (`jurismaster.v1`)

Aucune commande d'installation, aucun build. Ouvre directement `index.html` dans un navigateur.

## Structure du projet

```
JurisMaster/
├── index.html                              # Catalogue / page d'accueil
├── ma-progression.html                     # Dashboard gamification
├── intro-droit.html                        # Résumé matière L1 - Introduction au droit
├── droit-constitutionnel.html              # Résumé matière L1 - Droit constitutionnel
├── droit-des-personnes-et-famille.html     # Résumé matière L1 - Personnes & famille
├── obligations.html                        # Résumé matière L2 - Obligations
├── droit-penal-general.html                # Résumé matière L2 - Droit pénal
├── cours/
│   ├── introduction-au-droit/              # 9 leçons HTML
│   ├── droit-constitutionnel/              # 12 leçons HTML
│   ├── droit-des-personnes-et-famille/     # 10 leçons HTML
│   ├── droit-des-obligations/              # 6 leçons HTML
│   └── droit-penal-general/               # 10 leçons HTML
├── Instructions Kimi v2.md                 # Prompt système pour la génération de contenu
├── Plans Leçons - Conformité Juridique.md  # Plans détaillés et sources juridiques
└── _bkp/                                   # Sauvegardes (ne pas modifier)
```

### Nommage des fichiers de leçons

- Kebab-case, ASCII uniquement, pas d'accents : `notion-etat-elements-constitutifs.html`
- Chemin : `cours/<matiere-slug>/<lecon-slug>.html`
- Slugs de matières : `introduction-au-droit`, `droit-constitutionnel`, `droit-des-personnes-et-famille`, `droit-des-obligations`, `droit-penal-general`

## Template d'une leçon

Chaque fichier de leçon respecte cette structure exacte (voir `cours/introduction-au-droit/la-regle-de-droit.html` comme référence canonique) :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{TITRE LEÇON} - {MATIÈRE}</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; line-height: 1.8; }
        h1, h2, h3 { font-family: 'Playfair Display', serif; }
        .prose h2 { font-size: 2rem; font-weight: 700; margin-top: 3rem; margin-bottom: 1.5rem; color: #1e3a8a; border-bottom: 2px solid #e2e8f0; padding-bottom: 0.5rem; }
        .prose h3 { font-size: 1.5rem; font-weight: 600; margin-top: 2rem; margin-bottom: 1rem; color: #1e40af; }
        .prose p { margin-bottom: 1.5rem; color: #334155; text-align: justify; }
        .sidebar-link.active { color: #1d4ed8; font-weight: 600; border-left: 3px solid #1d4ed8; }
        .focus-box { background-color: #f8fafc; border-left: 4px solid #3b82f6; padding: 1.5rem; border-radius: 0.5rem; margin: 2rem 0; }
        .citation { font-style: italic; color: #475569; border-left: 2px solid #cbd5e1; padding-left: 1.5rem; margin: 2rem 0; }
    </style>
</head>
<body class="bg-white">

    <!-- BARRE DE NAVIGATION SUPÉRIEURE -->
    <nav class="sticky top-0 z-50 bg-white border-b border-slate-200 px-6 py-3 flex justify-between items-center">
        <a href="../../index.html" class="text-xl font-bold tracking-tight">JURIS<span class="text-blue-700">MASTER</span></a>
        <!-- barre de progression -->
    </nav>

    <div class="max-w-7xl mx-auto flex flex-col md:flex-row">

        <!-- BARRE LATÉRALE (liens vers toutes les leçons de la matière) -->
        <aside class="w-full md:w-80 border-r border-slate-100 p-8 h-screen sticky top-14 overflow-y-auto bg-slate-50/50">
            <!-- liste de toutes les leçons ; leçon active avec class="sidebar-link active" -->
        </aside>

        <!-- CONTENU PRINCIPAL -->
        <main class="flex-1 py-16 px-6 md:px-20 max-w-5xl">
            <article class="prose prose-slate lg:prose-lg mx-auto text-left">
                <!-- fil d'Ariane, h1, exorde, h2/h3, focus-box, citation, quiz, toolbox -->
            </article>
        </main>
    </div>

    <!-- GAMIFICATION JS -->
    <script>
        const JM = {
            get() { try { return JSON.parse(localStorage.getItem('jurismaster.v1')) || {}; } catch { return {}; } },
            set(s) { localStorage.setItem('jurismaster.v1', JSON.stringify(s)); },
            addXP(n) { const s = this.get(); s.xp = (s.xp || 0) + n; this.set(s); },
            completeLesson(slug, xp = 50) {
                const s = this.get();
                if (!s.lessonsCompleted) s.lessonsCompleted = [];
                if (!s.lessonsCompleted.includes(slug)) { s.lessonsCompleted.push(slug); this.addXP(xp); }
                this.set(s);
            },
            touchStreak() {
                const s = this.get(); const today = new Date().toDateString();
                if (s.lastVisit !== today) { s.streak = (s.streak || 0) + 1; s.lastVisit = today; this.set(s); }
            }
        };
        JM.touchStreak();
    </script>
</body>
</html>
```

### Éléments obligatoires dans chaque leçon

| Élément | Règle |
|---|---|
| `<html lang="fr">` | Toujours |
| Navigation sticky | Logo lié à `../../index.html` |
| Sidebar | Tous les liens de la matière ; leçon courante avec `class="sidebar-link active"` |
| `<h1>` | Titre de la leçon, police Playfair Display |
| Exorde | ≥ 200 mots, citation d'introduction en italique |
| Partie I & II | ≥ 600 mots chacune, avec `<h2>` et `<h3>` |
| `.focus-box` | Au moins une par leçon (définition clé ou point doctrinal) |
| `.citation` | Au moins une référence jurisprudentielle ou doctrinale |
| Quiz | 3 à 5 questions QCM avec feedback adaptatif |
| Disclaimer légal | Pied de leçon : contenu pédagogique, non un conseil juridique |
| `JM.completeLesson(slug)` | Appelé à la complétion du quiz |

### Sources juridiques

- Toujours citer les articles de loi avec leur numéro exact (ex : `art. 1240 C. civ.`)
- Jurisprudence : numéro de pourvoi + date + juridiction (ex : `Cass. civ. 1re, 13 janv. 1998, n° 96-12.253`)
- Toute affirmation non vérifiable : `<!-- SOURCE À VÉRIFIER -->`
- Sources de référence : Légifrance, Dalloz, LexisNexis, doctrine académique

## API gamification (localStorage)

Clé de stockage : `jurismaster.v1` (objet JSON)

```js
{
  xp: 0,                          // Points d'expérience cumulés
  streak: 0,                      // Jours consécutifs de visite
  lastVisit: "Mon Apr 25 2026",   // Dernière visite (Date.toDateString())
  lessonsCompleted: [],           // Slugs des leçons terminées
  badges: [],                     // Badges obtenus
  quizScores: {}                  // { slug: { attempts, best } }
}
```

Fonctions disponibles dans chaque leçon : `JM.get()`, `JM.set(s)`, `JM.addXP(n)`, `JM.completeLesson(slug, xp=50)`, `JM.touchStreak()`.

## Conventions de code

- **Pas de framework JS, pas de npm, pas de build** — tout doit fonctionner en ouvrant le fichier HTML directement
- **Tailwind via CDN uniquement** — ne pas télécharger ni compiler Tailwind localement
- **Palette couleurs** : primaire `blue-700`, texte `slate-900` (clair) / `slate-100` (sombre), fond `slate-50` (clair) / `slate-950` (sombre)
- **Typographie** : Inter pour le corps, Playfair Display pour les titres — uniquement via Google Fonts CDN
- **Accessibilité** : WCAG AA minimum (contraste 4.5:1), HTML sémantique (`<article>`, `<section>`, `<aside>`, `<nav>`)
- **Longueur leçon** : 1 500 à 2 500 mots de contenu textuel
- **Langue** : français uniquement (contenu et attributs HTML comme `lang="fr"`)

## Ce qu'il ne faut PAS faire

- Ne pas introduire de backend, de serveur, de base de données ou de dépendances npm
- Ne pas remplacer Tailwind CDN par un fichier compilé localement
- Ne pas modifier `_bkp/` (archive)
- Ne pas créer de nouvelles matières sans mettre à jour `index.html` et ajouter la page résumé correspondante
- Ne pas omettre le disclaimer légal dans une leçon
- Ne pas publier de contenu juridique sans source vérifiable

## Workflow de développement

1. Lire `Plans Leçons - Conformité Juridique.md` pour les plans et sources de chaque leçon
2. Lire `Instructions Kimi v2.md` pour les normes de rédaction et le QA checklist
3. Créer la leçon HTML en suivant le template ci-dessus
4. Mettre à jour la sidebar de toutes les autres leçons de la même matière pour inclure le nouveau lien
5. Mettre à jour la page résumé de la matière (`intro-droit.html`, etc.) si nécessaire
6. Tester en ouvrant directement dans un navigateur (aucun serveur requis)

## Tests

Pas de suite de tests automatisés. Validation manuelle :

- Ouvrir la leçon dans un navigateur et vérifier la mise en page
- Vérifier que le quiz s'exécute et sauvegarde dans localStorage
- Vérifier les liens de la sidebar (pas de 404)
- Vérifier le contraste couleur (outil DevTools accessibilité)
- Vérifier que toutes les sources citées sont vérifiables
