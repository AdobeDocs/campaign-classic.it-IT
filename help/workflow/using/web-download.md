---
solution: Campaign Classic
product: campaign
title: Download web
description: Ulteriori informazioni sull'attività del flusso di lavoro di download Web
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---


# Download web{#web-download}

L&#39;attività **Download Web** avvia il download di un file su un URL esplicito, un account esterno o un&#39;istanza Adobe Campaign . Viene utilizzato il protocollo HTTP. Può trattarsi di un download di GET o POST.

## Properties {#properties}

1. **Selezione del file Web**

   Per specificare il file da scaricare, potete immettere l&#39;URL del file, utilizzare l&#39;account HTTP esterno in cui è memorizzato il file oppure caricare il file tramite un&#39;istanza Adobe Campaign . I parametri disponibili sono descritti di seguito:

   * Per immettere direttamente l&#39;URL del file da scaricare, selezionate l&#39;opzione **[!UICONTROL Explicit URL]** e specificate l&#39;URL nel campo appropriato. Questo URL può essere costruito con dati variabili.

      ![](assets/download_web_edit.png)

   * Per utilizzare un **[!UICONTROL External account]**, selezionate l&#39;account dall&#39;elenco a discesa e specificate il file da scaricare.

      Gli account esterni sono configurati dal nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura di Adobe Campaign . I parametri dell&#39;account possono essere modificati tramite l&#39;icona **[!UICONTROL Edit link]**.

      ![](assets/download_web_edit_external.png)

   * Per scaricare il file dall&#39;istanza di Adobe Campaign , selezionare l&#39;opzione **[!UICONTROL Adobe Campaign Instance]**.

      ![](assets/download_web_edit_instance.png)

1. **Storizzazione dei file**

   Il collegamento **[!UICONTROL File historization settings...]** consente di specificare la directory di memorizzazione dei file e la frequenza di eliminazione di questa directory.

   ![](assets/download_web_edit_hist.png)

   Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Use a default storage directory]**: il file viene sempre spostato prima di essere elaborato. Se questa opzione è selezionata, il file viene spostato nella directory di memorizzazione predefinita (la directory **vars** della cartella di installazione  Adobe Campaign). Per specificare una directory di memorizzazione, deselezionare la casella e immettere il percorso nel campo **[!UICONTROL Storage directory]**
   * **[!UICONTROL Number of files]**: immettere il numero massimo di file da conservare nella directory di memorizzazione.
   * **[!UICONTROL Maximum size (in Mb)]**: immettete la capacità massima della directory di memorizzazione (in megabyte).

   Ogni file viene conservato per 24 ore prima di essere sottoposto alle regole di eliminazione definite. La rimozione avviene appena prima dell&#39;inizio dell&#39;attività e non tiene conto del file del flusso di lavoro in corso.

   I file vengono eliminati in funzione della loro età (dal più vecchio al più recente). I file meno recenti vengono eliminati finché non vengono verificate entrambe le regole di eliminazione. Di conseguenza, se viene definito un limite di 100 file, la directory di memorizzazione conterrà sempre i 100 file più recenti prima dell’inizio del flusso di lavoro, nonché quelli in fase di elaborazione nel flusso di lavoro in corso.

   Se non si desidera più impostare un limite per le opzioni **[!UICONTROL Number of files]** e **[!UICONTROL Maximum size (in Mb)]**, immettere 0 come valore.

1. **Parametri avanzati**

   Il collegamento **[!UICONTROL Advanced parameters...]** consente di specificare le opzioni aggiuntive indicate di seguito:

   ![](assets/download_web_edit_advanced.png)

   L&#39;opzione **[!UICONTROL Process errors]** è dettagliata in [Errori di elaborazione](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Parametri di output {#output-parameters}

* nomefile: Nome completo del file scaricato.
