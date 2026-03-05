# Types de jeux — Référentiel

Ce fichier définit les 25 types de jeux utilisés dans le projet.
Chaque jeu produit doit utiliser **exactement** un des slugs ci-dessous dans :
- la colonne `Type_jeu` du fichier `notions.csv`
- l'attribut `data-type` de la carte dans `index.html`
- la `<meta name="type">` du fichier HTML du jeu

---

## Les 25 types

| # | Slug | Nom affiché | Emoji | Description courte |
|---|------|-------------|-------|--------------------|
| 1 | `quiz` | Quiz (QCM) | ❓ | 4 propositions, une seule bonne réponse. Format universel. |
| 2 | `vrai-faux` | Vrai ou Faux | ✅ | Affirmer ou infirmer une proposition. Rapide, idéal pour les règles et définitions. |
| 3 | `lacunes` | Texte à trous | ✏️ | Compléter des blancs dans une phrase ou un texte. Adapté aux règles de grammaire et syntaxe. |
| 4 | `conjugaison` | Conjugaison | 🔤 | Compléter une table de conjugaison ou saisir la forme verbale correcte. |
| 5 | `association` | Associer | 🔗 | Relier par des traits un terme à sa définition / traduction / image. |
| 6 | `memory` | Memory | 🃏 | Retourner des cartes pour trouver des paires (FR↔langue, terme↔définition…). |
| 7 | `tri` | Trier / Classer | 🔀 | Glisser-déposer des éléments dans des catégories. |
| 8 | `puzzle` | Puzzle / Remettre en ordre | 🧩 | Remettre des mots, phrases ou étapes dans le bon ordre. |
| 9 | `classement` | Ordonner | ↕️ | Placer des éléments du plus petit au plus grand, du plus ancien au plus récent… |
| 10 | `carte` | Carte interactive | 🗺️ | Localiser des éléments (pays, villes, batailles…) sur une carte cliquable. |
| 11 | `chronologie` | Frise chronologique | 📅 | Placer des événements dans l'ordre sur une ligne du temps. |
| 12 | `schema` | Légender un schéma | 🔬 | Placer des étiquettes sur les parties d'un schéma (corps humain, atome, circuit…). |
| 13 | `mots-croises` | Mots croisés | 📝 | Trouver des mots à partir de définitions dans une grille. |
| 14 | `mots-meles` | Mots mêlés | 🔍 | Retrouver des mots cachés dans une grille de lettres. |
| 15 | `flashcard` | Flashcards | 📖 | Cartes recto/verso à retourner pour mémoriser notions, définitions, vocabulaire. |
| 16 | `construction` | Construire | 🏗️ | Assembler des blocs (mots, fragments) pour former une phrase, une formule ou une règle correcte. |
| 17 | `identification` | Identifier sur image | 🖱️ | Cliquer sur des zones d'une illustration pour les nommer ou les associer. |
| 18 | `devinette` | Devinette | 🕵️ | Trouver un mot ou un concept à partir d'indices progressifs. |
| 19 | `pendu` | Pendu | 🪢 | Trouver un mot lettre par lettre avant d'épuiser les tentatives. |
| 20 | `correspondance` | Correspondance | ↔️ | Faire glisser des définitions / exemples vers le terme ou la case qui correspond. |
| 21 | `calcul` | Calcul mental | 🔢 | Résoudre des opérations (addition, soustraction, multiplication, division, fractions…). |
| 22 | `completion` | Compléter une série | 🔁 | Trouver le terme manquant dans une suite, une règle ou une formule. |
| 23 | `dictee` | Dictée interactive | 🎙️ | Écrire un mot ou une phrase d'après une consigne textuelle ou audio. |
| 24 | `qcm-image` | QCM illustré | 🖼️ | QCM avec support visuel : graphique, image, carte, schéma fourni comme contexte. |
| 25 | `simulation` | Simulation interactive | ⚗️ | Expérience ou situation simulée à manipuler (circuit électrique, équilibre de bilan…). |

---

## Règles d'attribution

### Par type de notion

| Catégorie de notion | Types recommandés (dans l'ordre) |
|---|---|
| Règle de grammaire / syntaxe | `lacunes` → `quiz` → `vrai-faux` |
| Conjugaison / formes verbales | `conjugaison` → `lacunes` |
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

---

## Correspondance data-type → filtre index.html

Tous les slugs ci-dessus sont utilisables comme valeur de `data-type` sur les cartes.
Le filtre "Type" de `index.html` n'affiche que les types les plus fréquents :
`quiz`, `lacunes`, `conjugaison`, `memory`, `tri`, `puzzle`, `classement`, `carte`, `chronologie`, `schema`, `association`, `vrai-faux`, `calcul`, `mots-croises`, `flashcard`.

Les types moins fréquents (`mots-meles`, `construction`, `identification`, `devinette`, `pendu`, `correspondance`, `completion`, `dictee`, `qcm-image`, `simulation`) sont filtrables via la recherche future.
