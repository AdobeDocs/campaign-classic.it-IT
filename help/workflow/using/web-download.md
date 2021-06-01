---
product: campaign
title: Download web
description: Ulteriori informazioni sull'attività del flusso di lavoro per il download del web
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# Download web{#web-download}

L&#39;attività **Download Web** avvia il download di un file su un URL esplicito, un account esterno o un&#39;istanza Adobe Campaign. Viene utilizzato il protocollo HTTP. Questo può essere un download di GET o POST.

## Properties {#properties}

1. **Selezione del file Web**

   Per specificare il file da scaricare, puoi immettere l’URL del file, utilizzare l’account HTTP esterno in cui è memorizzato il file o caricare il file tramite un’istanza Adobe Campaign. I parametri disponibili sono descritti di seguito:

   * Per immettere direttamente l’URL del file da scaricare, seleziona l’opzione **[!UICONTROL Explicit URL]** e specifica l’URL nel campo appropriato. Questo URL può essere costruito con dati variabili.

      ![](assets/download_web_edit.png)

   * Per utilizzare un **[!UICONTROL External account]**, seleziona l’account dall’elenco a discesa e specifica il file da scaricare.

      Gli account esterni sono configurati dal nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura di Adobe Campaign. I parametri dell’account possono essere modificati tramite l’icona **[!UICONTROL Edit link]** .

      ![](assets/download_web_edit_external.png)

   * Per scaricare il file dall’istanza di Adobe Campaign, seleziona l’opzione **[!UICONTROL Adobe Campaign Instance]** .

      ![](assets/download_web_edit_instance.png)

1. **Storico dei file**

   Il collegamento **[!UICONTROL File historization settings...]** consente di specificare la directory di archiviazione dei file e la frequenza di eliminazione di questa directory.

   ![](assets/download_web_edit_hist.png)

   Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Use a default storage directory]**: il file viene sempre spostato prima di essere elaborato. Se questa opzione è selezionata, il file viene spostato nella directory di archiviazione predefinita (la directory **vars** della cartella di installazione di Adobe Campaign). Per specificare una directory di archiviazione, deselezionare la casella e immettere il relativo percorso nel campo **[!UICONTROL Storage directory]**
   * **[!UICONTROL Number of files]**: immettere il numero massimo di file da conservare nella directory di archiviazione.
   * **[!UICONTROL Maximum size (in Mb)]**: immettere la capacità massima della directory di archiviazione (in megabyte).

   Ogni file viene conservato per 24 ore prima di essere sottoposto alle regole di eliminazione definite. L’eliminazione avviene immediatamente prima dell’inizio dell’attività e non prende quindi in considerazione il file del flusso di lavoro in corso.

   I file vengono eliminati in funzione della loro età (dal più vecchio al più recente). I file meno recenti vengono eliminati finché non vengono verificate entrambe le regole di eliminazione. Pertanto, se viene definito un limite di 100 file, ciò significa che la directory di archiviazione conterrà sempre i 100 file più recenti prima dell’inizio del flusso di lavoro, nonché quelli in fase di elaborazione nel flusso di lavoro in corso.

   Se non si desidera più impostare un limite per le opzioni **[!UICONTROL Number of files]** e **[!UICONTROL Maximum size (in Mb)]**, immettere 0 come valore.

1. **Parametri avanzati**

   Il collegamento **[!UICONTROL Advanced parameters...]** ti consente di specificare le opzioni aggiuntive mostrate di seguito:

   ![](assets/download_web_edit_advanced.png)

   L&#39;opzione **[!UICONTROL Process errors]** è descritta in [Errori di elaborazione](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parametri di output {#output-parameters}

* nome file: Nome completo del file scaricato.
