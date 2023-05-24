---
product: campaign
title: Informazioni sugli strumenti di reporting di Adobe Campaign
description: Analizza il successo delle campagne in report integrati o personalizzati
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 19%

---

# Introduzione alla generazione di rapporti {#about-adobe-campaign-reporting-tools}



Oltre a [rapporti incorporati](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign consente di generare rapporti in vari contesti e per soddisfare esigenze diverse. I principi relativi alle modalità di utilizzo e di implementazione sono descritti nel presente documento.

Adobe Campaign non è uno strumento di reporting specializzato: i rapporti creati in Adobe Campaign consentono principalmente di visualizzare i dati aggregati. I rapporti di Adobe Campaign, dedicati all’analisi e alla rappresentazione dei dati, non sono progettati per le esportazioni di database.

Per esportare dati dal database di Adobe Campaign, devi creare un flusso di lavoro e utilizzare un’attività di esportazione dati. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/about-action-activities.md).

Adobe Campaign fornisce diversi strumenti di reporting:

1. **Rapporti incorporati**: Adobe Campaign offre una serie di rapporti su consegne, campagne, attività della piattaforma, funzionalità opzionali e così via. Questi rapporti sono disponibili attraverso le varie funzionalità a cui si riferiscono. Possono essere adattati alle tue esigenze specifiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-campaign-built-in-reports.md).

1. **Analisi dei dati descrittivi**: Adobe Campaign fornisce uno strumento visivo per la produzione di statistiche sui dati nel database. Puoi creare rapporti di analisi descrittivi utilizzando una procedura guidata dedicata e adattarne il contenuto e il layout in base alle tue esigenze.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-descriptive-analysis.md).

1. **Rapporti personalizzati**: Adobe Campaign consente di creare rapporti sui dati nel database. Una volta create, queste sono rese accessibili nei contesti appropriati.

   A seconda della complessità delle query, dei calcoli e dei volumi, i dati analizzati in questi rapporti possono essere raccolti tramite una query e preaggregati in un elenco (flusso di lavoro di tipo &quot;gestione dati&quot;) o in un cubo (utilizzando Marketing Analytics). Verrà visualizzata sotto forma di tabella pivot o di elenco di gruppi.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Rapporti di analisi**: Marketing Analytics consente l’esplorazione intuitiva dei dati.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Per semplificare la visualizzazione e la manipolazione, nonché per un&#39;esportazione efficiente, i report non devono contenere più di 1.000 righe.
