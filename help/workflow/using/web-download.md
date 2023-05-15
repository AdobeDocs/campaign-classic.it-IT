---
product: campaign
title: Download web
description: Ulteriori informazioni sull'attività del flusso di lavoro per il download del web
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# Download web{#web-download}



La **Download Web** l’attività avvia il download di un file su un URL esplicito, un account esterno o un’istanza di Adobe Campaign. Viene utilizzato il protocollo HTTP. Questo può essere un download di GET o POST.

## Properties {#properties}

1. **Selezione del file Web**

   Per specificare il file da scaricare, puoi immettere l’URL del file, utilizzare l’account HTTP esterno in cui è memorizzato il file o caricare il file tramite un’istanza Adobe Campaign. I parametri disponibili sono descritti di seguito:

   * Per immettere direttamente l’URL del file da scaricare, seleziona la **[!UICONTROL Explicit URL]** e specifica l’URL nel campo appropriato. Questo URL può essere costruito con dati variabili.

      ![](assets/download_web_edit.png)

   * Per utilizzare un **[!UICONTROL External account]**, seleziona l’account dall’elenco a discesa e specifica il file da scaricare.

      Gli account esterni sono configurati dal **[!UICONTROL Administration > Platform > External accounts]** nodo della struttura Adobe Campaign. I parametri dell’account possono essere modificati tramite la **[!UICONTROL Edit link]** icona.

      ![](assets/download_web_edit_external.png)

   * Per scaricare il file dall’istanza di Adobe Campaign, seleziona la **[!UICONTROL Adobe Campaign Instance]** opzione .

      ![](assets/download_web_edit_instance.png)

1. **Storico dei file**

   La **[!UICONTROL File historization settings...]** link consente di specificare la directory di archiviazione dei file e la frequenza di eliminazione di questa directory.

   ![](assets/download_web_edit_hist.png)

   Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Use a default storage directory]**: il file viene sempre spostato prima di essere elaborato. Se questa opzione è selezionata, il file viene spostato nella directory di archiviazione predefinita (il **vars** della cartella di installazione di Adobe Campaign). Per specificare una directory di archiviazione, deselezionare la casella e immettere il relativo percorso nel **[!UICONTROL Storage directory]** field
   * **[!UICONTROL Number of files]**: immettere il numero massimo di file da conservare nella directory di archiviazione.
   * **[!UICONTROL Maximum size (in Mb)]**: immettere la capacità massima della directory di archiviazione (in megabyte).

   Ogni file viene conservato per 24 ore prima di essere sottoposto alle regole di eliminazione definite. L’eliminazione avviene immediatamente prima dell’inizio dell’attività e non prende quindi in considerazione il file del flusso di lavoro in corso.

   I file vengono eliminati in funzione della loro età (dal più vecchio al più recente). I file meno recenti vengono eliminati finché non vengono verificate entrambe le regole di eliminazione. Pertanto, se viene definito un limite di 100 file, ciò significa che la directory di archiviazione conterrà sempre i 100 file più recenti prima dell’inizio del flusso di lavoro, nonché quelli in fase di elaborazione nel flusso di lavoro in corso.

   Se non desideri più impostare un limite per il **[!UICONTROL Number of files]** e **[!UICONTROL Maximum size (in Mb)]** , immetti 0 come valore.

1. **Parametri avanzati**

   La **[!UICONTROL Advanced parameters...]** link ti consente di specificare le opzioni aggiuntive mostrate di seguito:

   ![](assets/download_web_edit_advanced.png)

   La **[!UICONTROL Process errors]** è descritta in [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Parametri di output {#output-parameters}

* nome file: Nome completo del file scaricato.
