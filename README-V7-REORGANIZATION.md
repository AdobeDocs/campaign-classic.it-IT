---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# Kit di riorganizzazione della documentazione di 📚 v7

**2 richiede pour analyzer et réorganizer la doc v7 → v8**

---

## 📁 Fichiers

### 🔍 richieste (istruzioni)

| Fichier | Descrizione | Output |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analizza corrispondenza % avec cartella détaillée d&#39;UN | `[folder]-detailed-analysis.md` |

---

## Utilizzo di 🚀

### 1️⃣ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère**:
- 📊 riepilogo esecutivo (stats globales)
- 📁 Analizzare le cartelle des 21
- 🎯 Matrice de prioritization
- ✅ azioni
- ⚠️ rischi
- 📈 metriche

**Taille** : ~50-60 pagine Markdown

---

### 2️⃣ Analizzare la cartella Détaillée d&#39;un

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère**:
- 📊 statistiche della cartella
- 📋 Tableau détaillé organisé comme Experience League
- 🔗 cliquable di linee (v7 + Experience League)
- 📈 Jusqu&#39;à 3 matchs v8 par fichier avec %
- 📄 file di riepilogo par file
- 🎯 Piano di riorganizzazione
- ✅ Caselle di controllo versano tracciamento

**Taille** : ~30-40 pagine Markdown

---

## 📊 Esempio d&#39;Output

### Prompt 1 (panoramica)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Prompt 2 (cartella dettagliata)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯 consigliato flusso di lavoro

### Semaine 1 : Vue d&#39;ensemble
1. Exécuter **Prompt 1** → Obtenir `v7-reorganization-overview.md`
2. L’identificatore definisce le priorità delle cartelle
3. Consulenza utenti finali

### Semaine 2-4 : Analizzare détaillée
1. Priorità cartella di spostamento:
   - Esperto **Prompt 2**
   - Obtenir `[folder]-detailed-analysis.md`
   - Valider les décisions
   - Azioni del campo Inizio

### Semaine 5+: Esecuzione
1. Supprimer les fichiers identifiés (DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Manichino Migrer le contenu (MOVE)
4. Recensore les cas ambigus (RECENSIONE)

---

## 💡 suggerimenti

### Versare i prompt
- ✅ copia/coller l&#39;intégralité du prompt
- ✅ Nuovo formato modificatore pas
- ✅ seulement delle schede chemin du folder (Prompt 2)

### Pour les output
- Output di 📝 in Markdown (pas HTML)
- 🔗 tipi di client automatici
- ✅ Caselle di controllo versano tracciamento
- 📊 Statistiche et pourcentages
- 🎨 Emojis e icônes

### Pour l&#39;analyse
- 🎯 Cartelle gros par les di Commencer (consegna, flusso di lavoro)
- ⚡ Prioriser les quick wins (95-100% di corrispondenza)
- 🔍 Manuale del revisore les cas ambigus (corrispondenza &lt;70%)
- ✅ Valider avec SME avant soppressione massiccia

---

## ⚠️ importante

### Avant de supprimer
1. ✅ Vérifier l&#39;équivalent v8
2. ✅ Vérifier qu&#39;il n&#39;y a pas de contenu specifico per v7
3. ✅ Metri à jour `redirects.csv`
4. ✅ Valider avec un expert (pour les premiers)

### Pour les fichiers v7-only
1. ✅ Ajouter un badge au début du fichier
2. ✅ Expliquer pourquoi c&#39;est v7-only
3. ✅ Limitazioni di Lien vers les v8

---

## Supporto 🆘

**Domande**?
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Trop di produzione lungo → Demander un résumé
- Besoin d&#39;aide → Ping l&#39;équipe doc

---

**Dernière mise à jour** : 13/01/2026

