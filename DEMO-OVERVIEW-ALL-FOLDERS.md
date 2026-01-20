---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 23%

---
# Riorganizzazione della documentazione di 📊 v7 - Panoramica

**Generato**: 13/01/2026\
**Cartelle totali**: 21\
**File totali**: ~1.500

&#x200B;---

## Riepilogo esecutivo di 📈

| Metrica | Conteggio | Percentuale |
|--------|-------|------------|
| 📄 **File totali** | 1.500 | 100% |
| ✅ **MANTIENI (specifico per v7)** | 400 | 27% |
| 🗑️ **DELETE (in v8)** | 800 | 53% |
| ➡️ **SPOSTA (in v8)** | 200 | 13% |
| 🔍 **REVISIONE (non chiara)** | 100 | 7% |

**🎯Riduzione Stimata**: 60-75% (1.500 → 400-600 file)

&#x200B;---

## Analisi cartella 📁 per priorità

### 🟢 Priorità 1: KEEP 100% - Funzionalità solo v7

| Cartella | File | Motivo | Stato v8 | Azione |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | Configurazione on-premise/ibrida | Solo cloud in v8 | ✅ MANTIENI TUTTO + badge |
| 📂 `/mrm/` | 5 | Gestione delle risorse marketing | NOT in FFDA | ✅ MANTIENI TUTTO + badge |
| 📂 `/surveys/` | 8 | Sondaggi online | NOT in FFDA | ✅ MANTIENI TUTTO + badge |
| 📂 `/distributed/` | 7 | Marketing distribuito | NOT in FFDA | ✅ MANTIENI TUTTO + badge |
| 📂 `/response/` | 5 | Gestione risposte | Stato non chiaro | 🔍 VERIFICA E MANTIENI |
| 📂 `/migration/` | 8 | Migrazione v6.1 → v7 | specifico per v7 | ✅ MANTIENI TUTTO |
| **TOTALE** | **108** | **7%** | - | **Distintivo come solo v7** |

&#x200B;---

### 🔴 Priorità 2: 60-70% DELETE - Alta duplicazione

| Cartella | Totale | KEEP | DELETE | SPOSTA | RECENSIONE | Note |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16%) | 67 (60%) | 8 (7%) | 18 (17%) | E-mail/SMS/Push in v8 |
| 📂 `/workflow/` | 121 | 24 (20%) | 60 (50%) | 12 (10%) | 25 (20%) | Attività comuni nella versione v8 |
| 📂 `/reporting/` | 32 | 3 (10%) | 22 (70%) | 2 (6%) | 5 (14%) | Rapporti riprogettati in v8 |
| 📂 `/platform/` | 61 | 12 (20%) | 34 (55%) | 5 (8%) | 10 (17%) | Funzioni comuni nella versione v8 |
| 📂 `/campaign/` | 11 | 2 (18%) | 7 (64%) | 1 (9%) | 1 (9%) | Gestione delle campagne nella versione v8 |
| **TOTALE** | **336** | **59** | **190** | **28** | **59** | **Potenziale di riduzione elevato** |

&#x200B;---

### 🟡 Priorità 3: 30-50% MISTO - Analisi dettagliata richiesta

| Cartella | Totale | MANTIENI % | DELETE % | Note |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65% | 22% | Configurazioni schema/DB (principalmente v7) |
| 📂 `/production/` | 43 | 65% | 23% | Gestione dei server (principalmente v7) |
| 📂 `/integrations/` | 37 | 40% | 40% | Verifica la disponibilità del connettore |
| 📂 `/interaction/` | 39 | 51% | 31% | Motore di offerta (verifica v8) |
| 📂 `/web/` | 26 | 92% | 8% | App web > Pagine di destinazione v8 |
| 📂 `/message-center/` | 16 | 60% | 30% | Messaggistica transazionale |
| **TOTALE** | **230** | **~55%** | **~25%** | **Richiede la revisione cartella per cartella** |

&#x200B;---

## 🎯 risultati positivi rapidi - Settimana 1

### Eliminazioni con affidabilità elevata (corrispondenza 95-100% v8)

| Cartella | File da eliminare | Impatto | Impegno |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 file | 🔥🔥🔥 alta | 2 giorni |
| 📂 `/workflow/` | 60 file | 🔥🔥🔥 alta | 2 giorni |
| 📂 `/reporting/` | 22 file | 🔥🔥 Medium | 1 giorno |
| 📂 `/platform/` | 34 file | 🔥🔥 Medium | 1 giorno |
| 📂 `/campaign/` | 7 file | 🔥 bassa | 0,5 giorno |
| **TOTALE** | **190 file** | **riduzione del 53%** | **6,5 giorni** |

**Esempi**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (flusso di lavoro) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

&#x200B;---

## Dettaglio cartella di 📋

### Consegna 📂 (`/help/delivery/using/`) - 111 file

| Categoria | File | KEEP | DELETE | SPOSTA | RECENSIONE | Note |
|----------|-------|------|--------|------|--------|-------|
| Introduzione | 8 | 0 | 7 | 0 | 1 | Nozioni di base nella versione 8 |
| E-mail | 18 | 0 | 16 | 0 | 2 | Completamente in v8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-sourcing = KEEP |
| Push | 9 | 0 | 8 | 0 | 1 | Completamente in v8 |
| Direct mailing | 4 | 0 | 4 | 0 | 0 | In v8 |
| Personalizzazione | 8 | 1 | 6 | 0 | 1 | Coupon = KEEP |
| Modelli | 6 | 0 | 6 | 0 | 0 | In v8 |
| Test A/B | 11 | 0 | 10 | 0 | 1 | In v8 |
| Monitoraggio | 14 | 0 | 12 | 1 | 1 | Principalmente in v8 |
| Risoluzione dei problemi | 9 | 2 | 4 | 2 | 1 | Mantieni suggerimenti on-premise |
| Recapito messaggi | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Avanzate | 9 | 11 | 5 | 5 | 8 | Misto |
| **TOTALE** | **111** | **18** | **67** | **8** | **18** | È possibile eliminare **60%** |

**Deve Mantenere**:
- ✅ `personalized-coupons.md` - NON in FFDA v8
- ✅ `sms-set-up-mid.md` - Mid-sourcing (on-premise)
- ✅ `spamassassin.md` - Filtro posta indesiderata locale

**Esempi di eliminazione rapida**:
- 🗑️ `about-email-channel.md` → 95% in `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95% in `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90% in `campaign-web/v8/msg/send-sms`

&#x200B;---

### Flusso di lavoro 📂 (`/help/workflow/using/`) - 121 file

| Categoria | File | KEEP | DELETE | SPOSTA | RECENSIONE | Note |
|----------|-------|------|--------|------|--------|-------|
| Introduzione | 12 | 2 | 9 | 0 | 1 | Nozioni di base nella versione 8 |
| Targeting | 18 | 3 | 12 | 1 | 2 | Query/suddivisione in v8 |
| Controllo del flusso | 15 | 2 | 10 | 1 | 2 | Comune nella versione v8 |
| Attività azione | 24 | 4 | 16 | 2 | 2 | Più nella versione v8 |
| Attività evento | 8 | 1 | 6 | 0 | 1 | In v8 |
| Attività MRM | 5 | 5 | 0 | 0 | 0 | NOT in FFDA |
| Tecnico | 16 | 4 | 8 | 2 | 2 | Misto |
| Avanzate | 12 | 3 | 4 | 3 | 2 | Pattern utili |
| Casi d’uso | 11 | 0 | 5 | 3 | 3 | Esempi validi |
| **TOTALE** | **121** | **24** | **60** | **12** | **25** | È possibile eliminare **50%** |

**Deve Mantenere**:
- ✅ Tutte le attività MRM (5 file) - NON in FFDA v8
- ✅ configurazioni on-premise
- ✅ Flussi di lavoro tecnici avanzati

**Esempi di eliminazione rapida**:
- 🗑️ `query.md` → 95% in `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95% in `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95% in `campaign/v8/automation/workflow/enrichment`

&#x200B;---

### Installazione di 📂 (`/help/installation/using/`) - 75 file

| Categoria | File | Azione | Note |
|----------|-------|--------|-------|
| Installazione del server | 18 | MANTIENI ✅ | Solo on-premise |
| Impostazione database | 12 | MANTIENI ✅ | Solo on-premise |
| Configurazione | 15 | MANTIENI ✅ | nlserver, ecc. |
| Rete | 8 | MANTIENI ✅ | Aree di protezione |
| Integrazione | 10 | MANTIENI ✅ | LDAP, ecc. |
| Risoluzione dei problemi | 8 | MANTIENI ✅ | Issues on-premise |
| Documentazione generica | 4 | 🗑️ DELETE | Nella guida introduttiva della versione 8 |
| **TOTALE** | **75** | **71 KEEP / 4 DELETE** | **95% specifico per v7** |

**Motivo**: v8 è solo cloud; tutti i documenti di configurazione on-premise sono specifici per v7.

&#x200B;---

### 📂 Web (`/help/web/using/`) - 26 file

| Categoria | File | KEEP | DELETE | Note |
|----------|-------|------|--------|-------|
| App web | 14 | 14 | 0 | Funzioni avanzate non disponibili in v8 |
| Moduli web | 8 | 8 | 0 | Più di pagine di destinazione v8 |
| Pagine di destinazione | 2 | 0 | 2 | Pagine di base nella versione 8 |
| Editor HTML | 2 | 2 | 0 | Diverso da v8 |
| **TOTALE** | **26** | **24** | **2** | **92% specifico per v7** |

**Motivo**: v7 dispone di un framework completo per le applicazioni Web, v8 di pagine di destinazione semplificate.

&#x200B;---

## Piano d&#39;azione ✅

### Settimana 1: Eliminazioni ad alto impatto- [ ] `/delivery/`: elimina 67 file (e-mail, SMS, nozioni di base push)- [ ] `/workflow/`: eliminare 60 file (attività comuni)- [ ] `/reporting/`: eliminare 22 file (report standard)- [ ] `/platform/`: Elimina 34 file (caratteristiche comuni)- [ ] `/campaign/`: elimina 7 file (gestione campagne)- **Totale**: 190 file eliminati (riduzione del 13%)

### Settimana 2: badge specifico per v7- [ ] `/installation/`: badge 71 file come &quot;solo v7 on-premise&quot;- [ ] `/mrm/`: file badge 5 come &quot;Non disponibile in v8 FFDA&quot;- [ ] `/surveys/`: badge 8 file come &quot;Non disponibile in v8 FFDA&quot;- [ ] `/distributed/`: file Badge 7 come &quot;Non disponibile in v8 FFDA&quot;- [ ] `/web/`: badge 24 file come &quot;applicazioni Web v7&quot;- **Totale**: 115 file con badge

### Settimana 3: migrazione dei contenuti- [ ] Suggerimenti per la risoluzione dei problemi relativi alla migrazione da `/delivery/` a v8- [ ] Migrazione delle best practice del flusso di lavoro a v8- [ ] Migrazione dei pattern avanzati da `/platform/` a v8- **Totale**: 40 file migrati ed eliminati

### Settimana 4: Revisione manuale- [ ] Rivedi `/configuration/` contenuto misto- [ ] Verifica disponibilità connettore `/integrations/`- [ ] Rivedi la copertura del motore di offerta `/interaction/`- [ ] Rivedi lo stato della funzionalità `/response/`- **Totale**: 50 file esaminati e decisi

&#x200B;---

## 📊 risultati previsti

| Fase | File interessati | % cumulativa |
|-------|----------------|--------------|
| Settimana 1: eliminazioni | 190 | 13% |
| Settimana 2: Distintivo | 115 | 20% |
| Settimana 3: migrazione | 40 | 23% |
| Settimana 4: recensione | 50 | 26% |
| **TOTALE** | **395** | **26% elaborato** |

**Rimanenti**: ~1.100 file da elaborare nelle fasi successive

**Obiettivo finale**: 1.500 → 400-600 file (riduzione del 60-73%)

&#x200B;---

## 🎯 metriche di successo

| Metrica | Target | Stato |
|--------|--------|--------|
| File eliminati | 800+ (53%) | ⏳ in sospeso |
| File con badge | OLTRE 200 (13%) | ⏳ in sospeso |
| File migrati | OLTRE 200 (13%) | ⏳ in sospeso |
| Collegamenti interrotti | 0 | ⏳ in sospeso |
| Approvazione delle parti interessate | ✅ | ⏳ in sospeso |

&#x200B;---

**Ultimo aggiornamento**: 13/01/2026\
**Revisione successiva**: dopo l&#39;esecuzione della prima settimana

