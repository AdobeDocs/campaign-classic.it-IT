---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2:
  - id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: a9e48513ed4ceb2650d0eeff18563a010a148c80
workflow-type: tm+mt
source-wordcount: 498
ht-degree: 81%

---

# Ultima versione {#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign Classic v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.4.3 {#release-7-4-3}

### Build 9397 {#build-9397}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

_30 giugno 2026_

#### Miglioramenti di sicurezza {#security-7-4-3-9397}

Questa build include correzioni di sicurezza. Si tratta della build General Availability consigliata che sostituisce le precedenti build di Campaign Classic v7.

#### Altre modifiche {#changes-7-4-3-9397}

Per impostazione predefinita, webForm.jsp ora ignora i parametri `ctx` forniti dal client. Questo è controllato dal parametro `disableCtxInWebForm` che è impostato su &quot;true&quot; per impostazione predefinita.

Se le richieste webForm attualmente trasmettono un parametro `ctx` in, è possibile riabilitare temporaneamente questo comportamento aggiungendo quanto segue &lt;web> elemento della configurazione-&lt;instance>file .xml. Pianifica la graduale eliminazione di questo utilizzo.

```
<web>
  ...
  <jsp disableCtxInWebForm="false" />
  ...
</web>
```

### Build 9396 {#build-9396}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_9 giugno 2026_

Questa build include correzioni di sicurezza.

### Build 9394 {#build-9394}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

>[!CAUTION]
>
> L’aggiornamento della console client è obbligatorio.

_31 marzo 2026_

#### Miglioramenti di sicurezza {#security-7-4-3}

* Per mantenere sicurezza, stabilità e conformità ottimali, Debian è stato aggiornato alla versione 13 e PostgreSQL alla versione 17. Consulta la [matrice di compatibilità](compatibility-matrix.md).

#### Correzioni {#fixes-7-4-3}

>[!NOTE]
>
> Le correzioni elencate di seguito sono state implementate progressivamente nelle build 7.4.3 successive. Passa al [menu](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) **[!UICONTROL Help > About...]** per verificare di disporre della build più recente, 9394@28aaec9. Per ulteriori informazioni, contatta il rappresentante Adobe.

* È stato risolto un problema a causa del quale il componente codice a barre consentiva un parametro di altezza non limitato, che poteva comportare una vulnerabilità di sicurezza. (NEO-89984)
* È stato risolto un problema a causa del quale nei campi di enumerazione presenti negli elenchi creati tramite flussi di lavoro mancavano gli attributi dei nomi temporanei, comportando la visualizzazione nell’interfaccia di etichette di enumerazione errate o vuote. (NEO-91158)
* È stato risolto un problema a causa del quale la preparazione della consegna non riusciva generando errori di personalizzazione durante l’utilizzo dei campi targetData nei flussi di lavoro con attività di deduplica. (NEO-87693)
* È stato risolto un problema a causa del quale la concatenazione di campi stringa a carattere singolo con altre stringhe non riusciva in PostgreSQL 15, dovuto ai requisiti di casting dei tipi. (NEO-88028)
* È stato risolto un problema a causa del quale i log di tracciamento per le campagne collaborative per il marketing distribuito non venivano scritti nel database per una mancata corrispondenza tra gli ID di consegna principali e secondari. (NEO-86836)
* È stato risolto un problema a causa del quale i registri di consegna mostravano messaggi come annullati nonostante fossero stati inviati correttamente, interessando in particolare le consegne con pianificazione a scaglioni. (NEO-78933)
* È stato risolto un problema a causa del quale il flusso di lavoro di pulizia del database non eliminava i dati in modo efficiente, il che poteva avere un impatto sulle prestazioni. (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* È stato risolto un problema a causa del quale le statistiche di consegna non venivano ricalcolate totalmente per alcune consegne, influendo in particolare sugli indicatori di completamento. (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* È stato risolto un problema che poteva causare l’arresto anomalo della console client all’apertura di determinati flussi di lavoro che facevano riferimento a uno schema di targeting a monte mancante. (NEO-28727)
* È stato risolto un problema che impediva l’identificazione della versione della console client dopo un avvio non riuscito, perché il file di versione non era presente nel pacchetto di installazione. (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

