---
product: campaign
title: Raccolta file
description: Ulteriori informazioni sull’attività del flusso di lavoro di raccolta file
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Raccolta file{#file-collector}

Il **File Collector** controlla l&#39;arrivo di uno o più file in una directory e attiva la relativa transizione per ogni file ricevuto. Per ogni evento, una variabile **[!UICONTROL filename]** contiene il nome completo del file ricevuto. I file raccolti vengono spostati in un&#39;altra directory a scopo di archiviazione e per assicurarsi che vengano conteggiati una sola volta.

Per impostazione predefinita, il raccoglitore di file è un&#39;attività persistente che verifica la presenza di file nei momenti specificati dalla pianificazione.

I file devono trovarsi sul server in cui viene eseguito il modulo wfserver responsabile di questo flusso di lavoro. Se più moduli wfserver sono distribuiti su una singola istanza, è necessario specificare l’affinità delle attività che utilizzano questi file o l’affinità complessiva del flusso di lavoro.

## Properties {#properties}

La prima scheda dell’attività **[!UICONTROL File collector]** ti consente di selezionare la directory di origine e, se necessario, di filtrare i file raccolti. Le altre schede sono dettagliate nelle schede [E-mail in entrata](../../workflow/using/inbound-emails.md) (**[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** ).

![](assets/file_collect_edit.png)

1. **Download dei file**

   * **[!UICONTROL Directory]**

      Directory contenente i file da scaricare. Questa directory deve essere creata in precedenza sul server: se non esiste, verrà generato un errore.

   * **[!UICONTROL Filter]**

      Vengono presi in considerazione solo i file che corrispondono a questo filtro. Gli altri file nella directory vengono ignorati. Se il filtro è vuoto, vengono presi in considerazione tutti i file presenti nella directory. Esempi di filtro: ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      Se questa opzione è abilitata, l’attività termina dopo la ricezione del primo file. Se nella directory sono presenti più file corrispondenti al filtro, ne verrà preso in considerazione solo uno. Questa opzione garantisce che venga inviato un solo evento. Il file preso in considerazione è il primo dell&#39;elenco in ordine alfabetico.

      Per un’attività non pianificata, se nella directory specificata non viene trovato alcun file corrispondente al filtro e se l’opzione **[!UICONTROL Process file nonexistence]** non è abilitata, viene generato un errore.

   * **[!UICONTROL Execution schedule]**

      Determina la frequenza del controllo della presenza del file tramite i parametri della scheda **[!UICONTROL Schedule]** .

1. **Gestione degli errori**

   Sono disponibili le due opzioni seguenti:

   * **[!UICONTROL Process file nonexistence]**

      Questa opzione avvia una transizione speciale ogni volta che nessun file corrispondente al filtro viene trovato nella directory specificata.

      Se l’attività non è pianificata, questa transizione verrà attivata una sola volta.

   * **[!UICONTROL Processing errors]**

      Questa opzione fa apparire una transizione speciale, da attivare se viene generato un errore. In questo caso, il flusso di lavoro non cambia in stato di errore e continua l’esecuzione

      Gli errori presi in considerazione sono errori del file system (file non spostato, directory non accessibile, ecc.).

      Questa opzione non elabora gli errori relativi alla configurazione dell’attività, ovvero i valori non validi.

1. **Storizzazione**

   Fai riferimento al passaggio **[!UICONTROL File historization]** qui: [Download Web](../../workflow/using/web-download.md).

Impossibile determinare l&#39;ordine di elaborazione dei file. Per elaborare un set di file in sequenza, utilizza l&#39;opzione **[!UICONTROL Stop as soon as a file has been processed]** e crea un ciclo. In questo caso, i file verranno elaborati in ordine alfabetico. L’opzione **[!UICONTROL Process file nonexistence]** ti consente di terminare l’iterazione.

![](assets/file_collect_loop.png)

## Parametri di output {#output-parameters}

* nome file: Nome file completo. Questo è il nome file dopo essere stato spostato nella directory di storizzazione. Il percorso è quindi diverso, ma anche il nome è diverso se nella directory esiste già un altro file con lo stesso nome. L&#39;estensione viene mantenuta.
