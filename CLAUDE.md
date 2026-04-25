# CLAUDE.md — JurisMaster

Guidelines comportementales pour réduire les erreurs courantes des LLMs. Adapté des observations d'Andrej Karpathy.

**Compromis :** ces règles privilégient la prudence sur la vitesse. Pour les tâches triviales, utilise ton jugement.

---

## 1. Réfléchis avant de coder

**Ne suppose pas. N'occulte pas ta confusion. Expose les compromis.**

Avant d'implémenter :
- Énonce tes hypothèses explicitement. Si incertain, demande.
- Si plusieurs interprétations existent, présente-les — ne choisis pas en silence.
- Si une approche plus simple existe, dis-le.
- Si quelque chose n'est pas clair, arrête-toi. Nomme ce qui est confus. Demande.

## 2. Simplicité d'abord

**Minimum de code qui résout le problème. Rien de spéculatif.**

- Pas de fonctionnalités au-delà de ce qui a été demandé.
- Pas d'abstractions pour du code à usage unique.
- Pas de "flexibilité" ou "configurabilité" non demandée.
- Pas de gestion d'erreurs pour des scénarios impossibles.
- Si tu écris 200 lignes alors que 50 suffisent, réécris.

**Pour ce projet en particulier :** JurisMaster est intentionnellement un site statique sans build, sans npm, sans backend. Ne pas introduire de complexité qui briserait ce principe.

## 3. Changements chirurgicaux

**Ne touche que ce que tu dois. Ne nettoie que ton propre désordre.**

Quand tu modifies du code existant :
- Ne "améliore" pas le code adjacent, les commentaires ou le formatage.
- Ne refactorise pas ce qui n'est pas cassé.
- Respecte le style existant, même si tu ferais autrement.
- Si tu remarques du code mort sans rapport, mentionne-le — ne le supprime pas.

Quand tes changements créent des orphelins :
- Supprime les imports/variables/fonctions que TES changements ont rendus inutiles.
- Ne supprime pas le code mort préexistant sauf si demandé.

Le test : chaque ligne modifiée doit se tracer directement à la demande de l'utilisateur.

## 4. Exécution orientée objectif

**Définis les critères de succès. Boucle jusqu'à vérification.**

Transforme les tâches en objectifs vérifiables :
- "Ajoute une leçon" → "La leçon suit le template canonique, la sidebar est mise à jour, le quiz fonctionne"
- "Corrige le bug" → "Définis le comportement attendu, vérifie manuellement dans un navigateur"
- "Améliore le design" → "Les critères WCAG AA sont respectés avant et après"

Pour les tâches multi-étapes, énonce un plan bref :
```
1. [Étape] → vérification : [contrôle]
2. [Étape] → vérification : [contrôle]
```

---

## Contexte projet

Voir `AGENTS.md` pour la documentation complète du projet (structure, template leçon, API gamification, conventions, contraintes).

Résumé rapide :
- Stack : HTML5 + Tailwind CDN + Vanilla JS — **aucun build, aucun npm**
- Leçons : `cours/<matiere>/<slug>.html` — respecter le template de `la-regle-de-droit.html`
- Gamification : localStorage clé `jurismaster.v1`, API `JM.*` intégrée dans chaque leçon
- Langue : français uniquement
