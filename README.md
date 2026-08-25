# Introduction à TypeScript par l'exemple

Le cours **Introduction à TypeScript par l'exemple** est
la mise à jour 2026 du cours ECMAScript 6 originellement écrit par Serge Tahé
en octobre 2019. Le cours complet (texte, explications, sorties d'exécution
commentées) est publié sur [stahe.github.io/typescript-sept-2026](https://stahe.github.io/typescript-sept-2026).

**Ce cours et ses codes ont été entièrement écrits par l'IA Claude d'Anthropic.**

## Prérequis

- **[Node.js](https://nodejs.org) 26 ou plus récent** — nécessaire pour que
  les chapitres `ecmascript-2026/` et `temporal/` s'exécutent correctement
  (voir plus bas) ; les autres chapitres fonctionnent dès Node 18-22.
- **npm** (fourni avec Node.js).

Chaque script se lance de la même façon, avec **[tsx](https://github.com/privatenumber/tsx)** :
aucune compilation préalable n'est nécessaire, `tsx` transpile et exécute le
fichier `.ts` à la volée.

Pour seulement vérifier les types de tout le projet, sans rien exécuter :

```bash
npm run check
```

## Organisation du projet

Un dossier par chapitre du cours :

| Dossier | Chapitre |
|---|---|
| `bases/` | Les bases de TypeScript |
| `tableaux/` | Les tableaux |
| `objets/` | Les objets littéraux |
| `strings/` | Les chaînes de caractères |
| `regexp/` | Expressions régulières |
| `fonctions/` | Les fonctions |
| `exceptions/` | Les erreurs et exceptions |
| `modules/` | Les modules |
| `async/` | Programmation événementielle et fonctions asynchrones |
| `http/` | Les fonctions HTTP de TypeScript (fetch, axios) |
| `classes/` | Les classes |
| `client impots/` | Clients HTTP du service de calcul de l'impôt (3 versions : console en couches, puis navigateur avec webpack) |
| `nouveautes/` | Nouveautés ECMAScript 2020-2024 |
| `ecmascript-2026/` | Nouveautés ECMAScript 2026 |
| `temporal/` | `Temporal`, le remplaçant moderne de `Date` |

Chaque dossier contient son propre `README.md`, résumé condensé du contenu
pédagogique correspondant du cours complet.

## ⚠️ Chapitres nécessitant Node 26

Les dossiers `ecmascript-2026/` et `temporal/` illustrent des nouveautés très
récentes du langage, pas toutes disponibles sur toutes les versions de
Node.js — certaines fonctionnalités d'ECMAScript 2026 elles-mêmes ne sont pas
encore implémentées par tous les moteurs JavaScript malgré leur adoption
officielle par TC39 (voir `ecmascript-2026/README.md` pour le détail). Les
scripts concernés vérifient eux-mêmes, avec `typeof`, la disponibilité de
chaque fonctionnalité avant de l'utiliser, et affichent un message clair
sinon plutôt que de planter.

## Cas particulier : `client impots/client http 3`

Ce sous-dossier est un mini-projet **webpack** autonome (son propre
`package.json` et son propre `tsconfig.json`), destiné à tourner dans un
navigateur plutôt qu'avec node — voir son propre `README.md`.

## Comment le code a été typé

Le cours original enseignait volontairement des comportements dynamiques
propres à JavaScript (une variable qui change de type, un tableau qui mélange
plusieurs types, un objet auquel on ajoute des propriétés après coup...).
Pour rester fidèle à ces démonstrations tout en produisant du TypeScript
authentique :

- **types précis** (`string`, `number`, interfaces dédiées...) partout où la
  donnée a réellement une forme fixe — la majorité des cas ;
- **`any` explicite**, commenté, lorsque le script démontre justement la
  flexibilité dynamique de JavaScript — un choix assumé, différent d'un `any`
  implicite (que `tsconfig.json` interdit via `strict: true`) ;
- **`@ts-expect-error`**, commenté, lorsque le script démontre volontairement
  une erreur : TypeScript la détecte dès la compilation, là où JavaScript ne
  la révélait qu'à l'exécution.

## Configuration du projet

- **`tsconfig.json`** : mode `strict` activé, résolution `NodeNext` (les
  imports relatifs gardent l'extension `.js`, qui pointe en réalité vers le
  fichier source `.ts` correspondant — convention moderne node + ESM +
  TypeScript). Contient `"types": ["node"]`, nécessaire depuis TypeScript 6.0
  pour que les globales de node (`console`, `process`...) restent reconnues.
- **`.eslintrc.cjs`** : parser `@typescript-eslint`, pour analyser
  correctement la syntaxe TypeScript (types, interfaces, champs privés
  `#x`...).

## Auteur

IA Claude d'Anthropic [[https://claude.com/fr](https://claude.com/fr)], Serge Tahé — [stahe.github.io](https://stahe.github.io)
