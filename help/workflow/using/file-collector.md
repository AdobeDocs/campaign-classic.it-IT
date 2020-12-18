---
solution: Campaign Classic
product: campaign
title: Raccolta file
description: Ulteriori informazioni sull'attività del flusso di lavoro del raccoglitore file
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Raccolta file{#file-collector}

Il **File Collector** controlla l&#39;arrivo di uno o più file in una directory e ne attiva la transizione per ogni file ricevuto. Per ogni evento, una variabile **[!UICONTROL filename]** contiene il nome completo del file ricevuto. I file raccolti vengono spostati in un&#39;altra directory a scopo di archiviazione e per essere certi che vengano conteggiati una sola volta.

Per impostazione predefinita, il raccoglitore file è un&#39;attività persistente che verifica la presenza di file nei momenti specificati dalla pianificazione.

I file devono trovarsi sul server in cui viene eseguito il modulo wfserver responsabile del flusso di lavoro. Se più moduli wfserver vengono distribuiti su un&#39;unica istanza, è necessario specificare l&#39;affinità delle attività che utilizzano tali file o l&#39;affinità complessiva del flusso di lavoro.

## Properties {#properties}

La prima scheda dell&#39;attività **[!UICONTROL File collector]** consente di selezionare la directory di origine e, se necessario, di filtrare i file raccolti. Le altre schede sono dettagliate nelle schede [Inbound Emails](../../workflow/using/inbound-emails.md) (**[!UICONTROL Schedule]** e **[!UICONTROL Expiry]**).

![](assets/file_collect_edit.png)

1. **Download dei file**

   * **[!UICONTROL Directory]**

      Directory contenente i file da scaricare. Questa directory deve essere creata in anticipo sul server: se non esiste, verrà generato un errore.

   * **[!UICONTROL Filter]**

      Vengono presi in considerazione solo i file che corrispondono a questo filtro. Gli altri file della directory vengono ignorati. Se il filtro è vuoto, vengono presi in considerazione tutti i file presenti nella directory. Esempi di filtri: ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      Se questa opzione è attivata, l&#39;attività termina dopo la ricezione del primo file. Se nella directory sono presenti più file corrispondenti al filtro, ne verrà preso in considerazione solo uno. Questa opzione garantisce che venga inviato un solo evento. Il file preso in considerazione è il primo nell&#39;elenco in ordine alfabetico.

      Per un&#39;attività non pianificata, se nella directory specificata non viene trovato alcun file corrispondente al filtro e se l&#39;opzione **[!UICONTROL Process file nonexistence]** non è abilitata, verrà generato un errore.

   * **[!UICONTROL Execution schedule]**

      Determina la frequenza del controllo della presenza del file tramite i parametri della scheda **[!UICONTROL Schedule]**.

1. **Gestione degli errori**

   Sono disponibili le due opzioni seguenti:

   * **[!UICONTROL Process file nonexistence]**

      Questa opzione avvia una transizione speciale ogni volta che nella directory specificata non viene trovato alcun file corrispondente al filtro.

      Se l&#39;attività non è pianificata, questa transizione verrà attivata una sola volta.

   * **[!UICONTROL Processing errors]**

      Questa opzione consente di visualizzare una transizione speciale da attivare in caso di generazione di un errore. In questo caso, il flusso di lavoro non cambia in stato di errore e continua l&#39;esecuzione

      Gli errori presi in considerazione sono errori del file system (file non può essere spostato, directory non è stato accessibile, ecc.).

      Questa opzione non elabora gli errori relativi alla configurazione dell&#39;attività, ovvero i valori non validi.

1. **Storizzazione**

   Fare riferimento al passaggio **[!UICONTROL File historization]** qui: [Download Web](../../workflow/using/web-download.md).

Impossibile determinare l&#39;ordine di elaborazione del file. Per elaborare un set di file in sequenza, utilizzate l&#39;opzione **[!UICONTROL Stop as soon as a file has been processed]** e create un ciclo. In questo caso, i file verranno elaborati in ordine alfabetico. L&#39;opzione **[!UICONTROL Process file nonexistence]** consente di terminare l&#39;iterazione.

![](assets/file_collect_loop.png)

## Parametri di output {#output-parameters}

* nomefile: Nome file completo. Questo è il nome del file dopo che è stato spostato nella directory di cronologia. Il percorso è quindi diverso, ma il nome è diverso se nella directory esiste già un altro file con lo stesso nome. L&#39;estensione viene mantenuta.
