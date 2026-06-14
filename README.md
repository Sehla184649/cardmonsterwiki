# Card Monsters Wiki

Encyclopédie offline et boîte à outils pour **Card Monsters** : cartes, passifs, deck builder, comparateur et application desktop Windows avec mises à jour automatiques.

[![Release](https://img.shields.io/github/v/release/Sehla184649/cardmonsterwiki?label=version)](https://github.com/Sehla184649/cardmonsterwiki/releases/latest)
[![License: ISC](https://img.shields.io/badge/license-ISC-blue.svg)](LICENSE)

---

## Téléchargement

**Windows (recommandé)** — installez la dernière release :

👉 **[Télécharger sur GitHub Releases](https://github.com/Sehla184649/cardmonsterwiki/releases/latest)**

Fichier : `Card-Monsters-Wiki-Setup-x.x.x.exe`

Page de présentation : [`docs/index.html`](docs/index.html) (GitHub Pages ou ouverture locale).

---

## Fonctionnalités

| Module | Description |
|--------|-------------|
| **Bibliothèque** | Recherche, filtres (faction, mana, rareté, type), fiches détaillées avec passifs |
| **Grimoire des passifs** | Encyclopédie paginée, filtres par tier (S → D), recherche |
| **Deck Forge Pro** | Construction de deck (8 monstres / 8 sorts-équipements), conseils, stats, export/import |
| **Comparateur** | Comparez plusieurs cartes côte à côte |
| **Card Maker** | Créez une carte custom et exportez-la en PNG |
| **Actualités** | Fil d’annonces depuis `news.json` |
| **Auto-update** | Mises à jour détectées depuis GitHub Releases (version Electron) |

Données embarquées : `card.json`, `passives.json`, images et audio — **fonctionne sans connexion** une fois installé.

---

## Captures d’écran

> Ajoutez `docs/screenshot.png` pour illustrer la page de téléchargement.

---

## Installation développeur

### Prérequis

- [Node.js](https://nodejs.org/) 18+
- Windows (cible principale du build)

### Lancer en local (Electron)

```powershell
cd "C:\Users\u4662\Documents\CARD MONSTER WIKI"
npm install
npm start
```

### Lancer en navigateur (sans Electron)

Serveur local léger :

```powershell
npm run dev
```

Puis ouvrez `http://localhost:3000` (ou le port affiché) et naviguez vers `INDEX.html`.

---

## Build & publication

### Build Windows (.exe)

```powershell
npm run build
```

Sortie : dossier `dist/`  
(`Card Monsters Wiki Setup 1.0.0.exe`, `latest.yml`, `.blockmap`)

### Publier une release GitHub

1. **Commit + push** du code sur `main`
2. **Tag** sur le bon commit : `git tag -a v1.0.0 -m "Release v1.0.0"` puis `git push origin v1.0.0`
3. Token GitHub dans `.env` (voir `.env.example`) :

   ```
   GH_TOKEN=ghp_votre_token
   ```

4. Publication :

   ```powershell
   .\publish.ps1
   ```

   ou :

   ```powershell
   $env:GH_TOKEN = "ghp_votre_token"
   npm run build:publish
   ```

**Upload manuel** : en cas de souci avec `electron-builder`, uploadez sur la release GitHub les 3 fichiers de `dist/` :

- `Card-Monsters-Wiki-Setup-x.x.x.exe`
- `Card-Monsters-Wiki-Setup-x.x.x.exe.blockmap`
- `latest.yml`

---

## Structure du projet

```
├── INDEX.html          # Hub principal (wiki, passifs, maker, news)
├── deckbuilder.html    # Deck Forge Pro
├── ADMIN.html          # Panel admin (gestion cartes / passifs)
├── gametest.html       # Prototype de test de combat
├── card-utils.js       # Rendu cartes, passifs, fit titres
├── card-styles.css     # Styles partagés
├── card.json           # Base de cartes
├── passives.json       # Base de passifs
├── main.js             # Process Electron + auto-updater
├── updater.js          # UI mises à jour
├── docs/               # Page de téléchargement
└── images/             # Assets cartes & cadres
```

Scripts Python (`scrape_*.py`, `merge_*.py`, etc.) : outils de maintenance de la base de données, hors app joueur.

---

## Versions

| Fichier | Rôle |
|---------|------|
| `package.json` | Version npm / electron-builder |
| `version.json` | Fallback navigateur |
| `updater.js` | Constante `APP_VERSION` |

Pour une release **x.y.z**, mettez à jour ces trois fichiers avant de builder.

---

## Crédits

- **Auteur** : [Sehla184649](https://github.com/Sehla184649)
- **Jeu** : Card Monsters — ce wiki est un projet communautaire, non officiel.

© 2026 Sehla184649
