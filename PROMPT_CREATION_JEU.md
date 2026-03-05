# Process de création d'un jeu — Guide et prompt Claude Code

## Vue d'ensemble

Chaque jeu est un fichier HTML autonome (pas de framework, CSS/JS inline).
La source de vérité est `notions.csv`. Une ligne CSV = un jeu à produire.

---

## Étape 1 — Choisir une notion à réaliser

Ouvrir `notions.csv` et chercher une ligne avec `Statut = à faire`.

**Structure du CSV :**
```
Niveau;Matiere;Notion;Type_jeu;Fichier_html;Statut
3e, 4e, 5e, 6e;Allemand;La negation dans la phrase (nicht / kein);lacunes;allemand/negation-nicht-kein.html;fait
6e;Francais;L'accord sujet-verbe;lacunes;francais/l-accord-sujet-verbe.html;à faire
```

Colonnes :
- **Niveau** — niveaux scolaires concernés (séparés par `, `)
- **Matiere** — matière exacte (voir valeurs dans le CSV)
- **Notion** — titre exact du jeu (utilisé tel quel dans le `<h1>`)
- **Type_jeu** — slug du type parmi les 25 définis dans `GAME_TYPES.md`
- **Fichier_html** — chemin relatif depuis la racine du projet (`dossier/slug.html`)
- **Statut** — `fait` ou `à faire`

---

## Étape 2 — Conventions de nommage

### Slug de fichier

Le slug est généré depuis le champ **Notion** :
1. Supprimer les accents (NFD + strip Mn)
2. Mettre en minuscules
3. Remplacer toute séquence de caractères non alphanumériques par `-`
4. Supprimer les `-` en début et fin

Exemples :
| Notion | Slug → Fichier_html |
|--------|---------------------|
| L'accord sujet-verbe | `francais/l-accord-sujet-verbe.html` |
| La négation dans la phrase (nicht / kein) | `allemand/la-negation-dans-la-phrase-nicht-kein.html` |
| Les fractions : addition et soustraction | `mathematiques/les-fractions-addition-et-soustraction.html` |

### Dossiers par matière

| Matière (CSV) | Dossier |
|---------------|---------|
| Allemand | `allemand/` |
| Anglais | `anglais/` |
| Espagnol | `espagnol/` |
| Francais | `francais/` |
| Mathematiques | `mathematiques/` |
| Mathematiques expertes | `mathematiques-expertes/` |
| Specialite Mathematiques | `mathematiques-specialite/` |
| Histoire-Geographie | `histoire-geo/` |
| EMC | `emc/` |
| SVT | `svt/` |
| Specialite SVT | `svt-specialite/` |
| Physique-Chimie | `physique-chimie/` |
| Sciences et technologie | `sciences/` |
| Enseignement scientifique | `ens-scientifique/` |
| Philosophie | `philosophie/` |
| SES | `ses/` |
| Specialite SES | `ses-specialite/` |
| SNT | `snt/` |
| Specialite NSI | `nsi/` |
| Specialite SI | `si/` |
| Specialite HGGSP | `hggsp/` |
| Specialite HLP | `hlp/` |
| Questionner le monde | `questionner-le-monde/` |

---

## Étape 3 — Structure HTML obligatoire

Chaque fichier jeu doit respecter ce squelette :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="niveau" content="VALEUR_NIVEAU">
  <meta name="matiere" content="VALEUR_MATIERE">
  <meta name="type" content="SLUG_TYPE_JEU">
  <title>NOTION_EXACTE — Minijeux</title>
  <style>
    /* CSS inline, pas de fichier externe */
  </style>
</head>
<body>
  <header>
    <a href="../index.html">← Accueil</a>
    <h1>NOTION_EXACTE</h1>
    <p class="subtitle">MATIERE — NIVEAU</p>
  </header>
  <main>
    <!-- Contenu du jeu -->
  </main>
  <script>
    // JS inline, pas de fichier externe
  </script>
</body>
</html>
```

**Règles :**
- `<h1>` = valeur exacte de la colonne **Notion** du CSV (copier-coller)
- `<meta name="niveau">` = valeur de la colonne **Niveau** (ex : `6e` ou `3e, 4e, 5e, 6e`)
- `<meta name="matiere">` = valeur de la colonne **Matiere**
- `<meta name="type">` = slug du type (colonne **Type_jeu**, voir `GAME_TYPES.md`)
- Pas de dépendances externes (pas de CDN, pas de fichiers JS/CSS séparés)

---

## Étape 4 — Valeurs data-* pour la carte index.html

Après avoir créé le fichier jeu, ajouter une carte dans `index.html`.

### Valeurs `data-level`

Convertir la colonne **Niveau** en valeurs space-separated :

| Niveau CSV | data-level |
|------------|------------|
| CP | `cp` |
| CE1, CE2 | `ce1-ce2` |
| CM1, CM2 | `cm1-cm2` |
| 6e | `6e` |
| 5e | `5e` |
| 4e | `4e` |
| 3e | `3e` |
| Seconde | `seconde` |
| Premiere | `premiere` |
| Terminale | `terminale` |
| Lycee | `lycee` |

Plusieurs niveaux : `data-level="3e 4e 5e 6e"` (espace-séparé, pas de virgule).

### Valeurs `data-subject`

| Matière CSV | data-subject |
|-------------|-------------|
| Allemand | `allemand` |
| Anglais | `anglais` |
| Espagnol | `espagnol` |
| Francais | `francais` |
| Mathematiques | `mathematiques` |
| Histoire-Geographie | `histoire-geo` |
| EMC | `emc` |
| SVT | `svt` |
| Physique-Chimie | `physique-chimie` |
| Sciences et technologie | `sciences` |
| Philosophie | `philosophie` |
| SES | `ses` |
| SNT | `snt` |
| Specialite NSI | `nsi` |
| Specialite SI | `si` |
| Specialite HGGSP | `hggsp` |
| Specialite HLP | `hlp` |
| Enseignement scientifique | `ens-scientifique` |
| Questionner le monde | `questionner-le-monde` |

### Template carte index.html

```html
<div class="game-card"
     data-subject="DATA_SUBJECT"
     data-level="DATA_LEVEL"
     data-type="TYPE_JEU_SLUG">
  <a href="FICHIER_HTML">
    <div class="card-header subject-MATIERE_SLUG">
      <span class="subject-badge">MATIERE_AFFICHEE</span>
      <span class="level-badge">NIVEAU_AFFICHE</span>
    </div>
    <div class="card-body">
      <h3>NOTION_EXACTE</h3>
      <span class="type-badge">EMOJI TYPE_AFFICHE</span>
    </div>
  </a>
</div>
```

---

## Étape 5 — Mettre à jour notions.csv

Après avoir créé et testé le jeu, passer la ligne dans le CSV de `à faire` à `fait` :

```
6e;Francais;L'accord sujet-verbe;lacunes;francais/l-accord-sujet-verbe.html;fait
```

---

## Étape 6 — Commit et push

```bash
git add FICHIER_HTML index.html notions.csv
git commit -m "feat: ajouter jeu NOTION (TYPE_JEU, MATIERE, NIVEAU)"
git push -u origin claude/NOM_BRANCHE
```

---

## Prompt à copier-coller dans Claude Code

> Adapter les parties en MAJUSCULES avant d'envoyer.

---

```
Tu travailles dans le projet minijeux (répertoire git courant).

Crée un jeu éducatif autonome pour la notion suivante, extraite de notions.csv :

- Notion : NOTION_EXACTE
- Matière : MATIERE
- Niveau : NIVEAU
- Type de jeu : TYPE_JEU (voir GAME_TYPES.md pour la définition exacte)
- Fichier à créer : FICHIER_HTML

Contraintes techniques :
1. Fichier HTML autonome, CSS et JS inline, aucune dépendance externe.
2. Le <h1> doit être exactement : "NOTION_EXACTE"
3. Les <meta> obligatoires : niveau="NIVEAU", matiere="MATIERE", type="TYPE_JEU"
4. Design cohérent avec les jeux existants (voir un fichier existant pour le style).
5. Le jeu doit être fonctionnel et pédagogiquement pertinent pour le niveau indiqué.
6. Créer le dossier si nécessaire.

Ensuite :
- Ajouter une carte dans index.html (data-subject="DATA_SUBJECT", data-level="DATA_LEVEL", data-type="TYPE_JEU")
- Passer la ligne dans notions.csv de "à faire" à "fait"
- Committer : git add FICHIER_HTML index.html notions.csv && git commit -m "feat: ajouter jeu NOTION_EXACTE (TYPE_JEU)"

Commence par lire un jeu existant du même type ou d'un type proche pour t'inspirer du style.
```

---

## Référence rapide — Types de jeux

Voir `GAME_TYPES.md` pour la liste complète des 25 types avec emojis et descriptions.

Types les plus courants :

| Slug | Nom | Usage typique |
|------|-----|---------------|
| `quiz` | Quiz (QCM) | Règles, culture générale, sciences |
| `lacunes` | Texte à trous | Grammaire, conjugaison, formules |
| `vrai-faux` | Vrai ou Faux | Définitions, règles, affirmations |
| `memory` | Memory | Vocabulaire (FR↔langue étrangère) |
| `association` | Associer | Terme ↔ définition |
| `tri` | Trier / Classer | Catégorisation, classification |
| `puzzle` | Remettre en ordre | Phrases, étapes, chronologie courte |
| `flashcard` | Flashcards | Notions, vocabulaire recto/verso |
| `calcul` | Calcul mental | Maths : opérations, fractions |
| `chronologie` | Frise chronologique | Événements historiques |
| `carte` | Carte interactive | Géographie, repères spatiaux |
| `schema` | Légender un schéma | SVT, physique, anatomie |
| `conjugaison` | Conjugaison | Formes verbales, tableaux |
