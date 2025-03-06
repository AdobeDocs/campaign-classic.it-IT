---
product: campaign
title: Raccolta file
description: Ulteriori informazioni sull'attività del flusso di lavoro dell'agente di raccolta file
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Raccolta file{#file-collector}



L&#39;**Agente di raccolta file** controlla l&#39;arrivo di uno o più file in una directory e attiva la relativa transizione per ogni file ricevuto. Per ogni evento, una variabile **[!UICONTROL filename]** contiene il nome completo del file ricevuto. I file raccolti vengono spostati in un’altra directory a scopo di archiviazione e per assicurarsi che vengano conteggiati una sola volta.

Per impostazione predefinita, l&#39;agente di raccolta file è un&#39;attività persistente che verifica la presenza di file nei momenti specificati dalla pianificazione.

I file devono trovarsi nel server in cui viene eseguito il modulo wfserver responsabile del flusso di lavoro. Se in una singola istanza vengono distribuiti più moduli wfserver, è necessario specificare l&#39;affinità delle attività che utilizzano questi file o l&#39;affinità complessiva del flusso di lavoro.

## Proprietà {#properties}

La prima scheda dell&#39;attività **[!UICONTROL File collector]** consente di selezionare la directory di origine e, se necessario, di filtrare i file raccolti. Le altre schede sono dettagliate in [E-mail in entrata](inbound-emails.md) (**[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** schede).

![](assets/file_collect_edit.png)

1. **Download dei file** in corso

   * **[!UICONTROL Directory]**

     Directory contenente i file da scaricare. Questa directory deve essere creata in precedenza sul server: se non esiste, verrà generato un errore.

   * **[!UICONTROL Filter]**

     Vengono considerati solo i file che corrispondono a questo filtro. Gli altri file nella directory vengono ignorati. Se il filtro è vuoto, vengono presi in considerazione tutti i file nella directory. Esempi di filtro: **&#42;.zip**, **import-&#42;.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

     Se questa opzione è abilitata, l’attività termina dopo la ricezione del primo file. Se nella directory sono presenti più file corrispondenti al filtro, ne verrà preso in considerazione solo uno. Questa opzione garantisce che venga inviato un solo evento. Il file preso in considerazione è il primo dell’elenco in ordine alfabetico.

     Per un&#39;attività non pianificata, se nella directory specificata non viene trovato alcun file corrispondente al filtro e se l&#39;opzione **[!UICONTROL Process file nonexistence]** non è abilitata, verrà generato un errore.

   * **[!UICONTROL Execution schedule]**

     Determina la frequenza del controllo della presenza di file tramite i parametri della scheda **[!UICONTROL Schedule]**.

1. **Gestione errori**

   Sono disponibili le due opzioni seguenti:

   * **[!UICONTROL Process missing file]**

     Questa opzione avvia una transizione speciale ogni volta che nella directory specificata non viene trovato alcun file corrispondente al filtro.

     Se l’attività non è pianificata, questa transizione verrà attivata una sola volta.

   * **[!UICONTROL Process errors]**

     Questa opzione consente di visualizzare una transizione speciale da attivare in caso di errore. In questo caso, il flusso di lavoro non passa allo stato di errore e continua l’esecuzione

     Gli errori presi in considerazione sono errori del file system (file non spostabile, directory non accessibile, ecc.).

     Questa opzione non elabora gli errori relativi alla configurazione dell’attività, ovvero valori non validi.

1. **Cronologia**

   Fai riferimento al passaggio **[!UICONTROL File historization]** qui: [Download web](web-download.md).

Impossibile determinare l&#39;ordine di elaborazione dei file. Per elaborare un set di file in sequenza, utilizzare l&#39;opzione **[!UICONTROL Stop as soon as a file has been processed]** e creare un ciclo continuo. In questo caso, i file verranno elaborati in ordine alfabetico. L&#39;opzione **[!UICONTROL Process file nonexistence]** consente di completare l&#39;iterazione.

![](assets/file_collect_loop.png)

## Parametri di output {#output-parameters}

* nomefile: nome file completo. Questo è il nome del file dopo che è stato spostato nella directory di storicizzazione. Il percorso è quindi diverso, ma il nome è diverso anche se nella directory esiste già un altro file con lo stesso nome. L’estensione viene mantenuta.
