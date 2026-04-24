# ⚖️ Manuel de Développement Autonome - JurisMaster (Version ULTIMATE)

Ce document est le guide de référence absolu pour transformer JurisMaster en une plateforme de classe mondiale (Inspiré par **Harvard Law**, **Quimbee**, **Dalloz** et **Duolingo**).

---

## 🚀 1. Ta Mission : Intelligence Pédagogique Totale

Tu es le garant de la réussite de l'étudiant. Tu dois concevoir un site **profond**, **accessible** et **addictif**.

---

## 📚 2. Standards Académiques "Premium"

### A. La Règle des 1500+ Mots
Pour garantir la densité, chaque leçon doit suivre cette structure quantitative :
- **Exorde (Intro) :** 200 mots (Étymologie, contexte historique, enjeux contemporains).
- **Partie I :** 600 mots (Théories, fondements, Loi).
- **Partie II :** 600 mots (Jurisprudence, pratique, limites).
- **Appareil Critique :** 100 mots (Controverses doctrinales et Bibliographie).

### B. Composants Visuels Avancés (Tailwind)
Ne te contente pas de texte. Crée des composants visuels riches :
- **[ENCADRÉ DOCTRINAL] :** Bordure gauche dorée (`border-amber-400`), fond crème. Pour les citations de grands auteurs.
- **[CASE STUDY CARD] :** Fond blanc, ombre portée douce, icône de balance. Pour l'analyse d'arrêts.
- **[LEXIQUE SIDEBAR] :** Dans le texte, utilise des `<abbr>` stylisés ou des notes de bas de page pour les termes latins.
- **[FLOWCHART] :** Utilise des grilles CSS pour modéliser visuellement les procédures juridiques.

### C. Typographie & Accessibilité
- **"Sentence case" ABSOLU :** Une seule majuscule en début de titre. (Ex: *La force obligatoire du contrat*).
- **Sémantique :** Utilise `article`, `section`, `aside`, `nav` pour un SEO et une accessibilité parfaits.

---

## 🎮 3. Moteur de Gamification "JurisQuest 2.0"

Le système de progression doit être le fil conducteur du site :
- **Streak System :** Affiche une icône de feu si l'utilisateur revient 2 jours de suite (géré via `Date` dans LocalStorage).
- **Points de Prestige :** Les points s'appellent des "Sceaux de Justice".
- **Feedback Adaptatif :** "Excellent, tu maîtrises la distinction entre obligation de moyen et de résultat !" ou "Attention, tu confonds nullité et résolution."

---

## 🗺️ 4. Feuille de Route de Développement (Format Sentence case)

Développe les modules dans cet ordre strict, en visant une exhaustivité totale :

### A. Droit constitutionnel (L1) - Le socle
*   L'État et ses attributs
*   La souveraineté et ses modes d'exercice
*   La Constitution : norme suprême
*   La séparation des pouvoirs : théorie et pratique
*   Le régime parlementaire et ses variantes
*   Le régime présidentiel américain
*   L'histoire constitutionnelle française
*   Le président de la République sous la Ve
*   Le Gouvernement et le Parlement : les rapports de force
*   Le Conseil constitutionnel et la protection des droits

### B. Droit des personnes et de la famille (L1)
*   La personnalité juridique : naissance et fin
*   L'identification de la personne (Nom, domicile, état civil)
*   Les incapacités et les majeurs protégés
*   Le mariage et ses conditions de validité
*   Le divorce et la désunion
*   Le PACS et le concubinage
*   La filiation et l'adoption
*   L'autorité parentale

### C. Droit pénal général (L2)
*   Les principes fondamentaux du droit pénal
*   La classification des infractions
*   L'élément légal et l'interprétation de la loi
*   L'élément matériel : action, omission et tentative
*   L'élément moral : intention, imprudence et faute
*   L'irresponsabilité pénale
*   La peine : fonctions et régimes

---

## 🛠️ 5. Ton Workflow de travail Autonome

Pour chaque page générée, tu dois **OBLIGATOIREMENT** fournir :
1.  **Le code HTML/JS complet.**
2.  **Un module de Quiz JurisQuest intégré.**
3.  **Une barre de "Citations à retenir"** (en bas de page, prête à être copiée pour les révisions).
4.  **Une option "Mode Sombre"** gérée par une classe `.dark` sur le `body`.

**Commençons. Réécris `ma-progression.html` pour en faire une page "Premium" avec un compteur de Streak (flamme), un graphique de progression (SVG simple) et une section de badges "Prestige".**
