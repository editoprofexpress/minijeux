# Types de jeux — Référentiel

Ce fichier définit les 27 types de jeux utilisés dans le projet.
Chaque jeu produit doit utiliser **exactement** un des slugs ci-dessous dans :
- la colonne `Type_jeu` du fichier `notions.csv`
- l'attribut `data-type` de la carte dans `index.html`
- la `<meta name="type">` du fichier HTML du jeu

---

## Les 27 types

| # | Slug | Nom affiché | Emoji | Description courte | Fichier exemple |
|---|------|-------------|-------|--------------------|--------------------|
| 1 | `quiz` | Quiz (QCM) | ❓ | 4 propositions, une seule bonne réponse. Format universel. | `allemand/negation-nicht-kein.html` |
| 2 | `vrai-faux` | Vrai ou Faux | ✅ | Affirmer ou infirmer une proposition. Rapide, idéal pour les règles et définitions. | `emc/respecter-autrui.html` |
| 3 | `trous` | Texte à trous | ✏️ | Compléter des blancs dans une phrase ou un texte. Adapté aux règles de grammaire et syntaxe. | `anglais/le-present-continu-be-v-ing-actions-en-cours.html` |
| 4 | `conjugaison` | Conjugaison | 🔤 | Compléter une table de conjugaison ou saisir la forme verbale correcte. | `anglais/be-au-preterit-was-were.html` |
| 5 | `association` | Associer | 🔗 | Relier par des traits un terme à sa définition / traduction / image. | `anglais/les-connecteurs-logiques-essentiels.html` |
| 6 | `memory` | Memory | 🃏 | Retourner des cartes pour trouver des paires (FR↔langue, terme↔définition…). | `allemand/memoire-des-mots.html` |
| 7 | `tri` | Trier / Classer | 🔀 | Glisser-déposer des éléments dans des catégories. | `anglais/verbes-reguliers-irreguliers.html` |
| 8 | `puzzle` | Puzzle / Remettre en ordre | 🧩 | Remettre des mots, phrases ou étapes dans le bon ordre. | `francais/puzzle-de-phrases.html` |
| 9 | `classement` | Ordonner | ↕️ | Placer des éléments du plus petit au plus grand, du plus ancien au plus récent… | `mathematiques/ordonner-les-fractions.html` |
| 10 | `carte` | Carte interactive | 🗺️ | Localiser des éléments (pays, villes, batailles…) sur une carte cliquable. | `histoire-geo/europe-carte-interactive.html` |
| 11 | `chronologie` | Frise chronologique | 📅 | Placer des événements dans l'ordre sur une ligne du temps. | `histoire-geo/la-revolution-francaise-les-grandes-etapes.html` |
| 12 | `schema` | Légender un schéma | 🔬 | Placer des étiquettes sur les parties d'un schéma (corps humain, atome, circuit…). | `svt/le-systeme-digestif.html` |
| 13 | `mots-croises` | Mots croisés | 📝 | Trouver des mots à partir de définitions dans une grille. | `francais/les-figures-de-style.html` |
| 14 | `mots-meles` | Mots mêlés | 🔍 | Retrouver des mots cachés dans une grille de lettres. | `espagnol/la-famille.html` |
| 15 | `flashcard` | Flashcards | 📖 | Cartes recto/verso à retourner pour mémoriser notions, définitions, vocabulaire. | `anglais/decrire-une-personne-physique-et-caractere.html` |
| 16 | `construction` | Construire | 🏗️ | Assembler des blocs (mots, fragments) pour former une phrase, une formule ou une règle correcte. | `allemand/la-phrase-interrogative.html` |
| 17 | `identification` | Identifier sur image | 🖱️ | Cliquer sur des zones d'une illustration pour les nommer ou les associer. | `svt/la-cellule-observation-au-microscope.html` |
| 18 | `devinette` | Devinette | 🕵️ | Trouver un mot ou un concept à partir d'indices progressifs. | `mathematiques/les-figures-geometriques.html` |
| 19 | `pendu` | Pendu | 🪢 | Trouver un mot lettre par lettre avant d'épuiser les tentatives. | `anglais/vocabulaire-du-corps-humain.html` |
| 20 | `correspondance` | Correspondance | ↔️ | Faire glisser des définitions / exemples vers le terme ou la case qui correspond. | `histoire-geo/les-grandes-civilisations-de-l-antiquite.html` |
| 21 | `calcul` | Calcul mental | 🔢 | Résoudre des opérations (addition, soustraction, multiplication, division, fractions…). | `mathematiques/la-multiplication-tables-et-calcul-mental.html` |
| 22 | `completion` | Compléter une série | 🔁 | Trouver le terme manquant dans une suite, une règle ou une formule. | `mathematiques/les-suites-numeriques-et-les-patterns.html` |
| 23 | `dictee` | Dictée interactive | 🎙️ | Écrire un mot ou une phrase d'après une consigne textuelle ou audio. | `francais/les-homophones-grammaticaux.html` |
| 24 | `qcm-image` | QCM illustré | 🖼️ | QCM avec support visuel : graphique, image, carte, schéma fourni comme contexte. | `physique-chimie/les-etats-de-la-matiere.html` |
| 25 | `simulation` | Simulation interactive | ⚗️ | Expérience ou situation simulée à manipuler (circuit électrique, équilibre de bilan…). | `physique-chimie/le-circuit-electrique-simple.html` |
| 26 | `code-secret` | Code secret | 🔐 | Série de 4 mini-défis enchaînés (mécaniques variées), chacun révèle un chiffre d'un code final à déverrouiller. Idéal pour les révisions de chapitre. | `histoire-geo/la-seconde-guerre-mondiale-code-secret.html` |
| 27 | `dialogue` | Dialogue interactif | 💬 | Simulation d'une conversation : le joueur choisit parmi 3 répliques. Seule la formulation correcte fait progresser l'échange. Idéal pour les langues vivantes. | `anglais/se-presenter-dialogue-interactif.html` |

---

## Règles d'attribution

### Par type de notion

| Catégorie de notion | Types recommandés (dans l'ordre) |
|---|---|
| Règle de grammaire / syntaxe | `trous` → `quiz` → `vrai-faux` |
| Conjugaison / formes verbales | `conjugaison` → `trous` |
| Vocabulaire thématique | `memory` → `association` → `mots-meles` |
| Thème culturel / civilisation | `quiz` → `flashcard` |
| Compétence orale / écrite | `quiz` → `construction` |
| Œuvre littéraire | `quiz` → `vrai-faux` |
| Événement historique | `quiz` → `chronologie` |
| Repère géographique | `carte` → `quiz` |
| Calcul / opération | `calcul` → `completion` |
| Comparaison / ordre | `classement` → `calcul` |
| Géométrie / figures | `quiz` → `schema` |
| Probabilités / statistiques | `quiz` → `qcm-image` |
| Classification scientifique | `tri` → `association` |
| Anatomie / schéma | `schema` → `identification` |
| Concept scientifique | `quiz` → `vrai-faux` |
| Notion de philosophie / SES | `flashcard` → `quiz` |
| Valeur citoyenne (EMC) | `vrai-faux` → `quiz` → `tri` |
| Informatique / algo | `quiz` → `puzzle` |
| Révision de chapitre (toutes matières) | `code-secret` → `quiz` |
| Expression orale simulée (LV) | `dialogue` → `trous` → `conjugaison` |

---

## Correspondance data-type → filtre index.html

Tous les slugs ci-dessus sont utilisables comme valeur de `data-type` sur les cartes.
Le filtre "Type" de `index.html` affiche les 27 types (tous ont un bouton de filtre).
