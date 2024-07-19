---
product: campaign
title: Download web
description: Ulteriori informazioni sull’attività del flusso di lavoro Download web
feature: Workflows
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: a0c0c7d13704b0155004e578d6739852ceb43c81
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 1%

---

# Download web{#web-download}



L&#39;attività **Download Web** avvia il download di un file su un URL esplicito, un account esterno o un&#39;istanza di Adobe Campaign. Viene utilizzato il protocollo HTTP. Può trattarsi di un download GET o POST.

## Properties {#properties}

1. **Selezione del file Web**

   Per specificare il file da scaricare, puoi immettere l’URL del file, utilizzare l’account HTTP esterno in cui è memorizzato il file oppure caricare il file tramite un’istanza di Adobe Campaign. I parametri disponibili sono descritti di seguito:

   * Per immettere direttamente l&#39;URL del file da scaricare, selezionare l&#39;opzione **[!UICONTROL Explicit URL]** e specificare l&#39;URL nel campo appropriato. Questo URL può essere costruito con dati variabili.

     ![](assets/download_web_edit.png)

   * Per utilizzare un **[!UICONTROL External account]**, selezionare l&#39;account dall&#39;elenco a discesa e specificare il file da scaricare.

     Gli account esterni sono configurati dal nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura Adobe Campaign. I parametri dell&#39;account possono essere modificati tramite l&#39;icona **[!UICONTROL Edit link]**.

     ![](assets/download_web_edit_external.png)

   * Per scaricare il file dall&#39;istanza di Adobe Campaign, selezionare l&#39;opzione **[!UICONTROL Adobe Campaign Instance]**.

     ![](assets/download_web_edit_instance.png)

1. **Storicizzazione file**

   Il collegamento **[!UICONTROL File historization settings...]** consente di specificare la directory di archiviazione dei file e la frequenza di eliminazione della directory.

   ![](assets/download_web_edit_hist.png)

   Sono disponibili le seguenti opzioni:

   * **[!UICONTROL Use a default storage directory]**: il file viene sempre spostato prima di essere elaborato. Se questa opzione è selezionata, il file viene spostato nella directory di archiviazione predefinita (la directory **vars** della cartella di installazione di Adobe Campaign). Per specificare una directory di archiviazione, deselezionare la casella e immetterne il percorso nel campo **[!UICONTROL Storage directory]**
   * **[!UICONTROL Number of files]**: immettere il numero massimo di file da mantenere nella directory di archiviazione.
   * **[!UICONTROL Maximum size (in Mb)]**: immettere la capacità massima della directory di archiviazione (in MB).

   Ogni file viene conservato per 24 ore prima di essere sottoposto alle regole di rimozione definite. L’eliminazione avviene subito prima dell’inizio dell’attività e pertanto non tiene conto del file del flusso di lavoro in corso.

   I file vengono eliminati in funzione della loro età (dal meno recente al più recente). I file meno recenti vengono eliminati finché non vengono verificate entrambe le regole di eliminazione. Pertanto, se è definito un limite di 100 file, significa che la directory di archiviazione conterrà sempre i 100 file più recenti prima dell’inizio del flusso di lavoro, nonché quelli in fase di elaborazione nel flusso di lavoro in corso.

   Se non si desidera più impostare un limite per le opzioni **[!UICONTROL Number of files]** e **[!UICONTROL Maximum size (in Mb)]**, immettere 0 come valore.

1. **Parametri avanzati**

   Il collegamento **[!UICONTROL Advanced parameters...]** consente di specificare le opzioni aggiuntive riportate di seguito:

   * **[!UICONTROL Follow redirections]**: il reindirizzamento dei file consente di utilizzare gli override per indirizzare l&#39;input o l&#39;output di dati a un dispositivo di tipo diverso.
   * **[!UICONTROL Add the HTTP headers to the file]**: in alcuni casi, potrebbe essere utile aggiungere altre intestazioni HTTP a un file. Nella maggior parte dei casi, queste intestazioni verranno utilizzate per fornire informazioni aggiuntive a scopo di risoluzione dei problemi, per [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/docs/Web/HTTP/CORS) o per impostare direttive di caching specifiche.
   * **[!UICONTROL Ignore the HTTP return code]**: i codici di ritorno HTTP, noti anche come codici di stato HTTP, indicano il risultato di una richiesta HTTP.

   ![](assets/download_web_edit_advanced.png)

   L&#39;opzione **[!UICONTROL Process errors]** è descritta in [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Parametri di output {#output-parameters}

* nome file: nome completo del file scaricato.
