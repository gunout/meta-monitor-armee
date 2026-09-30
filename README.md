# 🇫🇷 Meta Monitor Armée

> **Dashboard d'analyse et d'expertise des 199 jeux de données ouverts du Ministère des Armées français** — publié par [data.gouv.fr](https://www.data.gouv.fr/organizations/ministere-des-armees).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/gunout/meta-monitor-armee/releases)
[![DSFR](https://img.shields.io/badge/design-DSFR%201.11.2-000091.svg)](https://www.systeme-de-design.gouv.fr/)
[![HTML](https://img.shields.io/badge/HTML-5-E34F26.svg?logo=html5&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/HTML)
[![CSS](https://img.shields.io/badge/CSS-3-1572B6.svg?logo=css3&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E.svg?logo=javascript&logoColor=black)](https://developer.mozilla.org/fr/docs/Web/JavaScript)
[![Chart.js](https://img.shields.io/badge/Chart.js-4.4.0-FF6384.svg?logo=chartdotjs&logoColor=white)](https://www.chartjs.org/)
[![SheetJS](https://img.shields.io/badge/SheetJS-0.18.5-217346.svg?logo=microsoftexcel&logoColor=white)](https://sheetjs.com/)
[![jsPDF](https://img.shields.io/badge/jsPDF-2.5.1-FF0000.svg)](https://github.com/parallax/jsPDF)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![Made in France](https://img.shields.io/badge/Made%20in-France-000091.svg)](https://www.gouvernement.fr/)

---

## 📖 Table des matières

- [Présentation](#-présentation)
- [Fonctionnalités](#-fonctionnalités)
- [Démo & captures](#-démo--captures)
- [Démarrage rapide](#-démarrage-rapide)
- [Architecture](#-architecture)
- [Configuration](#-configuration)
- [Utilisation](#-utilisation)
- [Expertiseur de données](#-expertiseur-de-données)
- [Détection PII](#-détection-pii)
- [Surveillance automatique](#-surveillance-automatique)
- [Export & rapports](#-export--rapports)
- [Stack technique](#-stack-technique)
- [Contribuer](#-contribuer)
- [Licence](#-licence)
- [Remerciements](#-remerciements)

---

## 🎯 Présentation

**Meta Monitor Armée** est un dashboard statique, 100% client-side, qui permet d'explorer, d'analyser et d'expertiser les **199 jeux de données ouverts** publiés par le **Ministère des Armées** sur la plateforme [data.gouv.fr](https://www.data.gouv.fr/organizations/ministere-des-armees).

L'application agrège automatiquement les métadonnées, catégorise les jeux par thématique, analyse en profondeur chaque ressource attachée (CSV, JSON, XLSX), détecte les anomalies, génère des graphiques et produit des rapports d'expertise exportables.

### 🎯 Objectifs

- **Transparence** : rendre visible et compréhensible la production de données ouvertes du Ministère des Armées
- **Qualité** : mesurer la conformité de chaque jeu aux standards data.gouv.fr
- **Découvrabilité** : faciliter la recherche et l'accès aux données
- **Audit** : identifier les jeux obsolètes, incomplets ou contenant des données sensibles

### ✨ Points clés

- 🚀 **Aucun backend** — tout tourne dans le navigateur
- 🎨 **Design DSFR** — conforme au Système de Design de l'État
- 🔬 **Expertise complète** — analyse statistique de chaque ressource
- 📊 **Graphiques dynamiques** — 5 visualisations générées automatiquement
- 🔒 **Détection PII** — emails, téléphones, IBAN, SIRET, etc.
- 🚨 **Surveillance** — alertes automatiques sur 199 jeux
- 📄 **Export PDF** — rapports d'expertise professionnels

---

## 🚀 Fonctionnalités

### 📋 Exploration des données

- **199 jeux** organisés en **10 catégories thématiques** (Effectifs & RH, Budget, Équipements, Reconversion, etc.)
- **Classification automatique** par mots-clés (titre + description + tags)
- **Recherche full-text** instantanée
- **Tri** : popularité, récence, titre, nombre de ressources
- **Pagination** configurable (10 / 25 / 50 résultats par page)
- **Filtres** : catégorie, popularité, mise à jour récente

### 🔬 Expertiseur de données

Pour chaque ressource attachée à un jeu (CSV, JSON, XLSX) :

- ✅ **Détection du format réel** (magic bytes + extension)
- ✅ **Statistiques globales** : taille, lignes, colonnes, séparateur
- ✅ **Types par colonne** : string, number, date, boolean, empty
- ✅ **Statistiques avancées** : min, max, moyenne, médiane, Q1, Q3, IQR, écart-type
- ✅ **Détection de doublons** (comparaison ligne à ligne)
- ✅ **Valeurs aberrantes** (méthode IQR : Q1-1.5×IQR, Q3+1.5×IQR)
- ✅ **Corrélations de Pearson** (|r| > 0.5) entre colonnes numériques
- ✅ **Insights automatiques** : taux de remplissage, colonnes vides, cardinalité
- ✅ **Aperçu tabulaire** des 10 premières lignes

### 📊 Graphiques générés automatiquement

- 📊 **Répartition des types** (doughnut)
- 💧 **Taux de remplissage par colonne** (bar)
- 🔢 **Cardinalité des colonnes** (bar horizontal)
- 📉 **Distribution numérique** (Min / Q1 / Médiane / Q3 / Max)
- 🏷️ **Top catégories** (pie)

### 📐 Score de conformité data.gouv.fr

Chaque jeu reçoit une **note sur 100** basée sur 7 critères :

| Critère | Poids | Vérification |
|---|---|---|
| **Titre** | 20 pts | Présent et ≥ 10 caractères |
| **Description** | 25 pts | Présente et ≥ 100 caractères (ou 30 car. pour score partiel) |
| **Organisation** | 10 pts | Renseignée |
| **URL** | 5 pts | HTTPS valide |
| **Tags** | 15 pts | ≥ 3 tags (ou 1 tag pour score partiel) |
| **Fraîcheur** | 15 pts | MAJ < 1 an (ou < 5 ans pour score partiel) |
| **Ressources** | 10 pts | Au moins 1 ressource attachée |

### 🔒 Détection PII

Scan automatique pour identifier les données personnelles :

| Type | Sévérité | Regex |
|---|---|---|
| **Email** | 🚨 Critique | RFC 5322 simplifié |
| **Téléphone FR** | 🚨 Critique | +33 / 0X XX XX XX XX |
| **IBAN** | 🚨 Critique | Format européen |
| **NIR (sécu)** | 🚨 Critique | 15 chiffres |
| **SIRET** | ⚠️ Warning | 14 chiffres |
| **SIREN** | ⚠️ Warning | 9 chiffres |
| **Code postal FR** | ⚠️ Warning | 5 chiffres |
| **Date de naissance** | ⚠️ Warning | JJ/MM/AAAA ou AAAA-MM-JJ |
| **IP adresse** | ⚠️ Warning | IPv4 |
| **URL** | ⚠️ Warning | http(s):// |

### 🚨 Surveillance automatique

Analyse des 199 jeux et détection des alertes :

- ⏳ **Données anciennes** (> 5 ans = warning, > 10 ans = critique)
- 📝 **Description absente ou trop courte** (< 50 caractères)
- 🏷️ **Aucun tag** (découvrabilité réduite)
- 📎 **Aucune ressource** attachée
- 🔗 **URL absente ou non sécurisée**

### 📄 Export & rapports

- **PDF structuré** par jeu (métadonnées + analyses)
- **CSV enrichi** avec scores et comptages
- **JSON complet** avec rapports d'analyse
- **Rapport texte** pour audit

---

## 🖼️ Démo & captures

> 📸 *Ajoutez ici vos captures d'écran : `docs/screenshot-dashboard.png`, `docs/screenshot-expertise.png`, etc.*

```
┌─────────────────────────────────────────────────────────────┐
│  🇫🇷 Meta Monitor Armée       199 jeux · 296 ressources      │
├───────────┬─────────────────────────────────┬───────────────┤
│ Catégories│  Résultats / Expertise / PII    │  Intelligence │
│           │                                 │               │
│ 👥 RH (49)│  📋 Répartition des effectifs   │  📊 Score     │
│ 💰 Bud (24)│  📎 2 ressources CSV            │  🚨 Alertes   │
│ ⚔️ Équ (28)│  📐 Score : 85/100              │  🕐 Historique│
│ 💼 Reco(28)│  👁️ Aperçu  [Expertiser]        │               │
└───────────┴─────────────────────────────────┴───────────────┘
```

---

## 🚀 Démarrage rapide

### Prérequis

- Un **navigateur moderne** (Chrome 90+, Firefox 88+, Safari 14+)
- **Python 3** (pour servir les fichiers en local — recommandé)
- Le fichier **`army.json`** (fourni dans le repo)

### Installation

```bash
# 1. Cloner le dépôt
git clone https://github.com/gunout/meta-monitor-armee.git
cd meta-monitor-armee

# 2. Servir les fichiers en local (obligatoire — fetch() bloque en file://)
python3 -m http.server 8000

# 3. Ouvrir dans le navigateur
open http://localhost:8000/meta-monitor-armee.html
```

### Alternative : Node.js

```bash
npx serve -p 8000
```

### Alternative : VS Code Live Server

Clic droit sur `meta-monitor-armee.html` → **Open with Live Server**.

> ⚠️ **Important** : le protocole `file://` bloque `fetch()` pour des raisons de sécurité CORS. Vous **devez** servir les fichiers via un serveur HTTP local.

---

## 🏗️ Architecture

```
meta-monitor-armee/
├── 📄 meta-monitor-armee.html    # Application complète (HTML + CSS + JS inline)
├── 📊 army.json                  # Dataset : 199 jeux du Ministère des Armées
├── 📄 README.md                  # Ce fichier
├── 📄 LICENSE                    # MIT
├── 📁 docs/                      # Captures d'écran, documentation
│   ├── screenshot-dashboard.png
│   ├── screenshot-expertise.png
│   └── screenshot-pii.png
├── 📁 scripts/                   # Scripts utilitaires
│   ├── fetch.py                  # Téléchargement du dataset via l'API data.gouv.fr
│   └── enrich.py                 # Enrichissement avec les ressources
└── 📁 examples/                  # Exemples de rapports générés
    ├── rapport_exemple.pdf
    └── rapport_exemple.txt
```

### Flux de données

```
data.gouv.fr API v1
        │
        │ GET /api/1/datasets/?organization=534fff92a3a7292c64a77f94
        ▼
   army.json  ──────►  meta-monitor-armee.html
   (199 jeux)          │
                       ├──► Classification thématique
                       ├──► Expertise des ressources
                       ├──► Détection PII
                       ├──► Surveillance
                       └──► Graphiques & rapports
```

---

## ⚙️ Configuration

### Fichier `army.json`

Structure attendue :

```json
{
  "query": "",
  "total": 199,
  "errors": null,
  "results": [
    {
      "id": "53699ef2a3a729239d205feb",
      "titre": "Répartition des effectifs militaires par catégorie et armée en 2024",
      "organisation": "Ministère des Armées",
      "url": "https://www.data.gouv.fr/datasets/...",
      "tags": "armee, categorie, effectif, militaire",
      "last_update": "2025-10-03T12:56:31.583000+00:00",
      "popularity": 35330,
      "description": "champ : effectifs en ETPT sous PMEA...",
      "resources": [
        {
          "id": "36eeeef4-165f-480a-b248-895fb403de2b",
          "title": "Fichier CSV",
          "format": "csv",
          "url": "https://www.data.gouv.fr/storage/f/..."
        }
      ]
    }
  ]
}
```

### Régénérer `army.json`

```python
# scripts/fetch.py
import json, time, urllib.request, urllib.parse

ORG_ID = "534fff92a3a7292c64a77f94"  # Ministère des Armées
OUT = "army.json"
PAGE_SIZE = 100
BASE = "https://www.data.gouv.fr/api/1/datasets/"

def fetch_page(page):
    params = urllib.parse.urlencode({
        "organization": ORG_ID,
        "page_size": PAGE_SIZE,
        "page": page,
    })
    url = f"{BASE}?{params}"
    req = urllib.request.Request(url, headers={"User-Agent": "MetaMonitor/1.0"})
    with urllib.request.urlopen(req, timeout=30) as r:
        return json.loads(r.read().decode("utf-8"))

def main():
    all_results, page, total = [], 1, None
    while True:
        print(f"→ Page {page}...")
        data = fetch_page(page)
        if total is None:
            total = data.get("total", 0)
            print(f"  Total : {total}")
        items = data.get("data", [])
        if not items: break
        all_results.extend(items)
        print(f"  +{len(items)} (cumul : {len(all_results)}/{total})")
        if len(all_results) >= total or len(items) < PAGE_SIZE: break
        page += 1
        time.sleep(0.3)
    payload = {"query": "", "total": len(all_results), "errors": None, "results": all_results}
    with open(OUT, "w", encoding="utf-8") as f:
        json.dump(payload, f, ensure_ascii=False, indent=2)
    print(f"\n✅ {len(all_results)} jeux dans {OUT}")

if __name__ == "__main__":
    main()
```

### Ajouter une catégorie thématique

Éditez le tableau `CATEGORIES` dans `meta-monitor-armee.html` :

```javascript
const CATEGORIES = [
  {
    id: 'ma-nouvelle-cat',
    nom: 'Ma Nouvelle Catégorie',
    icon: '🎯',
    keywords: ['mot1', 'mot2', 'mot3']
  },
  // ...
];
```

### Modifier les seuils de surveillance

```javascript
// Dans runSurveillance()
if (age > 3650) alerts.push({ severity: 'critical', ... });  // > 10 ans
else if (age > 1825) alerts.push({ severity: 'warning', ... });  // > 5 ans
```

---

## 📖 Utilisation

### 🔍 Rechercher un jeu

1. Tapez un mot-clé dans la barre de recherche centrale
2. Filtrez par catégorie via la sidebar gauche
3. Triez par popularité, récence ou nombre de ressources

### 🔬 Expertiser une ressource

1. Cliquez sur un jeu dans la liste
2. L'onglet **🔬 Expertise** s'active automatiquement
3. Sur chaque ressource, cliquez **🔬 Expertiser**
4. L'analyse complète s'affiche en quelques secondes :
   - Statistiques par colonne
   - Détections (doublons, aberrations, corrélations, PII)
   - Graphiques automatiques
   - Aperçu des données

### 🚨 Lancer la surveillance

- Cliquez sur l'onglet **🚨 Surveillance** dans le haut
- Ou bouton **Lancer la surveillance** dans le panneau droit
- Liste complète des alertes classées par sévérité

### 🔒 Scanner les PII

1. Expertisez au moins une ressource contenant des données
2. Cliquez sur l'onglet **🔒 PII**
3. Liste consolidée des données personnelles détectées

### 📄 Exporter un rapport

- Ouvrez un jeu
- Cliquez sur **📄 Export PDF**
- Le rapport est généré et téléchargé automatiquement

---

## 🔬 Expertiseur de données

### Capacités par format

| Analyse | CSV | JSON | XLSX |
|---|---|---|---|
| Détection format réel | ✅ | ✅ | ✅ |
| Taille fichier | ✅ | ✅ | ✅ |
| Nombre de lignes | ✅ | ✅ | ✅ |
| Nombre de colonnes | ✅ | ✅ | ✅ |
| Séparateur | ✅ | — | — |
| Types par colonne | ✅ | ✅ | ✅ |
| Statistiques (min/max/moy) | ✅ | ✅ | ✅ |
| Quartiles (Q1/Q3/IQR) | ✅ | ✅ | ✅ |
| Doublons | ✅ | ✅ | ✅ |
| Aberrations (IQR) | ✅ | ✅ | ✅ |
| Corrélations Pearson | ✅ | ✅ | ✅ |
| Détection PII | ✅ | ✅ | ✅ |
| Graphiques | ✅ | ✅ | ✅ |
| Aperçu | ✅ | ✅ | ✅ |

### Formule IQR pour les aberrations

```
Q1 = 25e percentile
Q3 = 75e percentile
IQR = Q3 - Q1
Borne inférieure = Q1 - 1.5 × IQR
Borne supérieure = Q3 + 1.5 × IQR
```

Toute valeur en dehors de ces bornes est signalée comme aberrante.

### Corrélation de Pearson

```
r = Σ((xi - x̄)(yi - ȳ)) / √(Σ(xi - x̄)² × Σ(yi - ȳ)²)
```

Les corrélations `|r| > 0.5` sont affichées.

---

## 🔒 Détection PII

### Motifs détectés

| Motif | Sévérité | Exemple |
|---|---|---|
| Email | 🚨 Critique | `jean.dupont@example.fr` |
| Téléphone FR | 🚨 Critique | `06 12 34 56 78` |
| IBAN | 🚨 Critique | `FR76 3000 6000 0112 3456 7890 189` |
| NIR | 🚨 Critique | `1 85 03 75 123 456 78` |
| SIRET | ⚠️ Warning | `123 456 789 00012` |
| SIREN | ⚠️ Warning | `123 456 789` |
| Code postal | ⚠️ Warning | `75001` |
| Date naissance | ⚠️ Warning | `15/03/1985` |
| Adresse IP | ⚠️ Warning | `192.168.1.1` |
| URL | ⚠️ Warning | `https://example.fr` |

### Conformité RGPD

Cet outil vous aide à **identifier** d'éventuelles données personnelles dans les jeux ouverts, mais **ne se substitue pas** à un audit RGPD complet. Les résultats sont indicatifs.

---

## 🚨 Surveillance automatique

### Règles de surveillance

| Alerte | Seuil | Sévérité |
|---|---|---|
| Données très anciennes | > 10 ans | 🚨 Critique |
| Données anciennes | > 5 ans | ⚠️ Warning |
| Description absente | 0 caractère | 🚨 Critique |
| Description trop courte | < 50 caractères | ⚠️ Warning |
| Aucun tag | 0 tag | ⚠️ Warning |
| Aucune ressource | 0 ressource | ⚠️ Warning |
| URL absente | Champ vide | 🚨 Critique |
| URL non HTTPS | http:// | 🚨 Critique |

### Rapport de surveillance

La vue Surveillance liste les alertes avec :
- Titre du jeu concerné
- Sévérité (critique / warning)
- Raison précise
- Lien direct vers le jeu

---

## 📄 Export & rapports

### Export PDF

Généré via **jsPDF** + **jspdf-autotable**. Contenu :

- En-tête République Française
- Métadonnées du jeu (titre, organisation, ID, MAJ, popularité, score)
- Description complète
- Liste des tags
- Liste des ressources (jusqu'à 20)
- Rapports d'analyse en cache
- Pied de page avec pagination

### Export CSV

Colonnes : `id, titre, organisation, tags, last_update, popularity, score, grade, issues_count, forts_count`.

### Export JSON

Contient l'intégralité des analyses en cache, structurées pour intégration dans une CI/CD.

---

## 🛠️ Stack technique

| Composant | Version | Rôle |
|---|---|---|
| **DSFR** | 1.11.2 | Design System de l'État |
| **Chart.js** | 4.4.0 | Graphiques interactifs |
| **SheetJS** | 0.18.5 | Lecture des fichiers XLSX |
| **jsPDF** | 2.5.1 | Génération PDF |
| **jspdf-autotable** | 3.8.1 | Tableaux dans les PDF |
| **Vanilla JS** | — | Aucun framework (léger et rapide) |

### Compatibilité

| Navigateur | Version min |
|---|---|
| Chrome | 90+ |
| Firefox | 88+ |
| Safari | 14+ |
| Edge | 90+ |

---

## 🤝 Contribuer

Les contributions sont **les bienvenues** ! Voici comment procéder.

### Signaler un bug

Ouvrez une [issue](https://github.com/gunout/meta-monitor-armee/issues) avec :

- Description du problème
- Étapes de reproduction
- Comportement attendu vs observé
- Captures d'écran si possible
- Version du navigateur

### Proposer une fonctionnalité

1. Fork le projet
2. Créez une branche : `git checkout -b feature/ma-fonctionnalite`
3. Committez : `git commit -m "feat: ajout de ma fonctionnalité"`
4. Pushez : `git push origin feature/ma-fonctionnalite`
5. Ouvrez une Pull Request

### Convention de commits

Ce projet suit la spécification [Conventional Commits](https://www.conventionalcommits.org/) :

```
feat:     nouvelle fonctionnalité
fix:      correction de bug
docs:     documentation
style:    formatage (pas de changement de code)
refactor: refactoring
test:     ajout de tests
chore:    tâches de maintenance
```

### Idées d'amélioration

- [ ] Analyse de séries temporelles (évolution des jeux dans le temps)
- [ ] Comparaison inter-ministères
- [ ] Intégration d'un backend FastAPI pour l'API data.gouv.fr
- [ ] Export Excel multi-feuilles
- [ ] Mode hors-ligne (PWA)
- [ ] Notifications push sur nouvelles publications
- [ ] Support d'autres formats (Parquet, XML, GeoJSON)

---

## 📜 Licence

Ce projet est sous licence **MIT** — voir le fichier [LICENSE](LICENSE) pour plus de détails.

```
MIT License

Copyright (c) 2026 gunout

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🙏 Remerciements

- **[Ministère des Armées](https://www.defense.gouv.fr/)** — producteur des données ouvertes
- **[data.gouv.fr](https://www.data.gouv.fr/)** — plateforme d'open data de l'État
- **[Etalab](https://www.etalab.gouv.fr/)** — pilotage de la politique open data
- **[DSFR](https://www.systeme-de-design.gouv.fr/)** — Système de Design de l'État
- **[Chart.js](https://www.chartjs.org/)**, **[SheetJS](https://sheetjs.com/)**, **[jsPDF](https://github.com/parallax/jsPDF)** — bibliothèques open source

---

## 📊 Statistiques du projet

![GitHub last commit](https://img.shields.io/github/last-commit/gunout/meta-monitor-armee)
![GitHub commit activity](https://img.shields.io/github/commit-activity/m/gunout/meta-monitor-armee)
![GitHub issues](https://img.shields.io/github/issues/gunout/meta-monitor-armee)
![GitHub stars](https://img.shields.io/github/stars/gunout/meta-monitor-armee)
![GitHub forks](https://img.shields.io/github/forks/gunout/meta-monitor-armee)

---

<div align="center">

**🇫🇷 Liberté · Égalité · Fraternité**

Fait avec ❤️ pour la transparence de la donnée publique

[⬆ Retour en haut](#-meta-monitor-armée)

</div>

---

<div align="center">

### 🇫🇷 Gunout · 2026

![Made in France](https://img.shields.io/badge/Made_in-France-002395?style=flat-square&labelColor=FFFFFF&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAgNjAwIj48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjYwMCIgZmlsbD0iIzAwMjM5NSIvPjxyZWN0IHdpZHRoPSI5MDAiIGhlaWdodD0iNDAwIiB5PSIxMDAiIGZpbGw9IiNmZmYiLz48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjIwMCIgeT0iNDAwIiBmaWxsPSIjZWQyOTM5Ii8+PC9zdmc+)
![GitHub](https://img.shields.io/badge/GitHub-gunout-181717?style=flat-square&logo=github&logoColor=white)
![Year](https://img.shields.io/badge/2026-ED2939?style=flat-square&labelColor=FFFFFF)

<sub>© 2026 <strong>Gunout</strong> — Tous droits réservés.</sub>

</div>
