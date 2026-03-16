---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 66387e2e008051901fe3385f571d7fe798829100
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# Ultima versione {#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign Classic v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.4.3 - Build 9392 {#release-7-4-3}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

_martedì 16 marzo 2026_

>[!CAUTION]
>
> L’aggiornamento della console client è obbligatorio.

### Miglioramenti di sicurezza {#security-7-4-3}

* Per mantenere la sicurezza, la stabilità e la conformità ottimali, Debian è stato aggiornato alla versione 13 e PostgreSQL alla versione 17. Consulta la [matrice di compatibilità](compatibility-matrix.md).

### Correzioni {#fixes-7-4-3}

* È stato risolto un problema a causa del quale il componente codice a barre consentiva un parametro di altezza non limitato, che poteva causare una vulnerabilità di sicurezza. (NEO-89984)
* È stato risolto un problema che causava la mancanza di attributi di nome temporanei nei campi di enumerazione negli elenchi creati tramite flussi di lavoro, causando la visualizzazione di etichette di enumerazione errate o vuote nell’interfaccia. (NEO-91158)
* È stato risolto un problema a causa del quale le statistiche di consegna non venivano ricalcolate completamente per alcune consegne, influenzando in particolare gli indicatori di successo. (NEO-88106)
* È stato risolto un problema a causa del quale la preparazione della consegna non riusciva a causa di errori di personalizzazione durante l’utilizzo dei campi targetData nei flussi di lavoro con attività di deduplicazione. (NEO-87693)
* È stato risolto un problema che impediva la concatenazione di campi stringa a carattere singolo con altre stringhe in PostgreSQL 15 a causa di requisiti di cast del tipo. (NEO-88028)
* È stato risolto un problema che impediva la scrittura nel database dei registri di tracciamento per le campagne collaborative in Distributed Marketing a causa di una mancata corrispondenza tra gli ID di consegna principali e secondari. (NEO-86836)
* È stato risolto un problema a causa del quale i registri di consegna mostravano che i messaggi venivano annullati anche se venivano inviati correttamente, in particolare per quanto riguarda le consegne con pianificazione ondata. (NEO-78933)
* È stato risolto un problema che impediva l’eliminazione efficiente dei dati da parte del flusso di lavoro di pulizia del database, con possibile impatto sulle prestazioni. (NEO-76439)

