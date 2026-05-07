---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: ht
source-wordcount: '294'
ht-degree: 100%

---

# Ultima versione {#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign Classic v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.4.3 - Build 9394 {#release-7-4-3}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

_16 marzo 2026_

>[!CAUTION]
>
> L’aggiornamento della console client è obbligatorio.

### Miglioramenti di sicurezza {#security-7-4-3}

* Per mantenere sicurezza, stabilità e conformità ottimali, Debian è stato aggiornato alla versione 13 e PostgreSQL alla versione 17.Consulta la [matrice di compatibilità](compatibility-matrix.md).

### Correzioni {#fixes-7-4-3}

* È stato risolto un problema a causa del quale il componente codice a barre consentiva un parametro di altezza non limitato, che poteva comportare una vulnerabilità di sicurezza.(NEO-89984)
* È stato risolto un problema a causa del quale nei campi di enumerazione presenti negli elenchi creati tramite flussi di lavoro mancavano gli attributi dei nomi temporanei, comportando la visualizzazione nell’interfaccia di etichette di enumerazione errate o vuote.(NEO-91158)
* È stato risolto un problema a causa del quale le statistiche di consegna non venivano ricalcolate totalmente per alcune consegne, influendo in particolare sugli indicatori di completamento.(NEO-88106)
* È stato risolto un problema a causa del quale la preparazione della consegna non riusciva generando errori di personalizzazione durante l’utilizzo dei campi targetData nei flussi di lavoro con attività di deduplica.(NEO-87693)
* È stato risolto un problema a causa del quale la concatenazione di campi stringa a carattere singolo con altre stringhe non riusciva in PostgreSQL 15, dovuto ai requisiti di casting dei tipi.(NEO-88028)
* È stato risolto un problema a causa del quale i log di tracciamento per le campagne collaborative per il marketing distribuito non venivano scritti nel database per una mancata corrispondenza tra gli ID di consegna principali e secondari.(NEO-86836)
* È stato risolto un problema a causa del quale i registri di consegna mostravano messaggi come annullati nonostante fossero stati inviati correttamente, interessando in particolare le consegne con pianificazione a scaglioni.(NEO-78933)
* È stato risolto un problema a causa del quale il flusso di lavoro di pulizia del database non eliminava i dati in modo efficiente, il che poteva avere un impatto sulle prestazioni.(NEO-76439)

