---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 PROMPT DEMO - Analisi della documentazione da v7 a v8

**Copia e incolla l&#39;intero prompt in Cursor/ChatGPT per analizzare qualsiasi cartella v7**

&#x200B;---

## 📋 IL PROMPT (COPIA DA QUI) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## 🎯 ISTRUZIONI DEMO

### Passaggio 1: visualizzare la richiesta1. Apri il file (`DEMO-PROMPT-STANDALONE.md`)2. Scorri fino alla sezione &quot;IL PROMPT&quot;3. Dire: *&quot;Questo è il nostro prompt di analisi automatizzata&quot;*

### Passaggio 2: copia la richiesta1. Seleziona tutto, da &quot;# Analisi della documentazione di Campaign v7&quot; alla fine2. Copia negli Appunti3. Dire: *&quot;Copia l&#39;intero prompt...&quot;*

### Passaggio 3: Incollare ed eseguire1. Apri cursore2. Incolla il prompt3. Dì: *&quot;...e incollalo nel cursore&quot;*4. Premi Invio

### Passaggio 4: mostrare i risultati1. Attendere la generazione (~30-60 secondi)2. Scorri nel rapporto generato3. Evidenzia sezioni chiave:   - 📊 statistiche di riepilogo   - 📋 tabella file per file   - ✅ deve mantenere la sezione   - 🗑️ risultati positivi rapidi   - 🎯 piano di esecuzione

### Passaggio 5: Momento di insuccesso1. Mostra l’anteprima markdown2. Osserva:   - *&quot;111 file analizzati automaticamente&quot;*   - *&quot;Eliminazione sicura di 67 file (riduzione del 60%)&quot;*   - *&quot;File specifici di v7 identificati&quot;*   - *&quot;Completare il piano di esecuzione con le tempistiche&quot;*

&#x200B;---

## 💡 SUGGERIMENTI DEMO

### Rendi interattivo&#x200B;**Chiedi al pubblico**: *&quot;Quale cartella analizzare?&quot;*- consegna ✅ (111 file - notevole)- flusso di lavoro ✅ (121 file, anche più grandi)- web ✅ (26 file - demo rapida)- generazione rapporti ✅ (32 file - fast)

### Personalizza al volo&#x200B;**Mostra flessibilità**: cambia il percorso della cartella nel prompt:

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Evidenzia caratteristiche principali1. **Automazione**: *&quot;Nessun lavoro manuale richiesto&quot;*2. **Precisione**: *&quot;Utilizza la documentazione v8 per il confronto&quot;*3. **Actionable**: *&quot;Piano pronto per l&#39;esecuzione con caselle di controllo&quot;*4. **Smart**: *&quot;Identifica automaticamente le funzionalità specifiche di v7&quot;*

### Confronto dei tempi&#x200B;**Prima**: *&quot;Analisi manuale = 2-3 giorni per cartella&quot;*\**Dopo**: *&quot;Analisi automatizzata = 30 secondi per cartella&quot;*

**ROI**: *&quot;21 cartelle × 2 giorni = 42 giorni → 15 minuti&quot;*

&#x200B;---

## 📊 ANTEPRIMA DI OUTPUT PREVISTA

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## SCRIPT DEMO 🎬

**Apertura**:
> &quot;Oggi vi mostrerò come abbiamo automatizzato la riorganizzazione della documentazione v7 utilizzando l’intelligenza artificiale. Questo richiedeva settimane, ora ci vogliono minuti.&quot;

**Problema**:
> &quot;Disponiamo di oltre 1.500 file di documentazione v7. Molti sono duplicati in v8. Dobbiamo identificare cosa mantenere, eliminare o migrare.&quot;

**Soluzione**:
> &quot;Abbiamo creato uno smart prompt che analizza qualsiasi cartella e genera consigli actionable.&quot;

**Demo**:
> &quot;Lasciate che vi mostri. Analizzerò la cartella &quot;delivery&quot; con 111 file...&quot;
> 
> [Copia richiesta, Incolla, Esegui]
> 
> &quot;...e in 30 secondi, otteniamo un&#39;analisi completa.&quot;

**Risultati**:
> &quot;Guardate qui:
> - 67 file da eliminare (riduzione del 60%)
> - 18 file specifici per v7 identificati
> - 8 file da migrare
> - Completa il piano di esecuzione di 3 settimane
> 
> Tutti automatizzati. Tutto accurato&quot;.

**Chiudi**:
> &quot;Questo stesso processo funziona per tutte le 21 cartelle. Quello che prima richiedeva 6 settimane ora richiede 15 minuti.&quot;

&#x200B;---

## 🚀 PRONTO PER LA DEMO.

**Solo**:
1. Apri il file
2. Copia il prompt
3. Incolla nel cursore
4. Mostra la magia ✨

**Tempo demo totale**: 3-5 minuti\
**Fattore Wow**: 🔥🔥🔥

