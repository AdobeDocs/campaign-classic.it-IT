---
product: campaign
title: Avvio di un flusso di lavoro
description: Scopri come avviare un flusso di lavoro e scoprire la barra delle azioni dei flussi di lavoro e fai clic con il pulsante destro del mouse sul menu
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---

# Avvio di un flusso di lavoro {#starting-a-workflow}

Un flusso di lavoro viene sempre avviato manualmente. Quando viene avviato, può tuttavia rimanere inattivo a seconda delle informazioni specificate tramite un programmatore (consulta [Scheduler](../../workflow/using/scheduler.md)) o la pianificazione delle attività.

Azioni relative all’esecuzione del flusso di lavoro di targeting (avvio, arresto, pausa, ecc.) sono processi **asincroni**: l&#39;ordine viene registrato e avrà effetto non appena il server sarà disponibile ad applicarlo.

La barra degli strumenti ti consente di avviare e tenere traccia dell’esecuzione del flusso di lavoro.

Di seguito è riportato un elenco dettagliato delle opzioni disponibili nel menu **[!UICONTROL Actions]** e nel menu di scelta rapida.

>[!IMPORTANT]
>
>Tieni presente che quando un operatore esegue un’azione su un flusso di lavoro (avvio, arresto, pausa, ecc.), l’azione non viene eseguita immediatamente, ma inserita in una coda per essere elaborata dal modulo [flusso di lavoro](../../workflow/using/architecture.md).

## Barra delle azioni {#actions-toolbar}

I pulsanti della barra degli strumenti sono descritti in questa sezione [sezione](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Il pulsante **[!UICONTROL Actions]** ti consente di accedere a opzioni di esecuzione aggiuntive per intervenire sui flussi di lavoro selezionati. Puoi inoltre utilizzare il menu **[!UICONTROL File > Actions]** oppure fare clic con il pulsante destro del mouse su un flusso di lavoro e selezionare **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Questa azione ti consente di avviare l’esecuzione di un flusso di lavoro: un flusso di lavoro che è **Finished**, **In corso di modifica** o **Paused** cambia lo stato in **Started**. Il motore del flusso di lavoro gestisce quindi l’esecuzione di questo flusso di lavoro. Se il flusso di lavoro è stato messo in pausa, viene ripreso, altrimenti il flusso di lavoro viene avviato dall’inizio e le attività iniziali vengono attivate.

   L&#39;avvio è un processo asincrono: La richiesta viene salvata ed elaborata il prima possibile da un server del flusso di lavoro.

* **[!UICONTROL Pause]**

   Questa azione imposta lo stato del flusso di lavoro su **Sospeso**. Nessuna attività viene attivata finché il flusso di lavoro non viene ripreso; tuttavia, le operazioni in corso non vengono messe in pausa.

* **[!UICONTROL Stop]**

   Questa azione interrompe l&#39;esecuzione di un flusso di lavoro. Lo stato dell&#39;istanza è impostato su **Finished**. Le operazioni in corso vengono interrotte, se possibile. Le importazioni e le query SQL vengono annullate immediatamente.

   L&#39;arresto è un processo asincrono. La richiesta viene registrata, quindi il server del flusso di lavoro o i server annullano le operazioni in corso. L’arresto di un’istanza di flusso di lavoro può richiedere del tempo, specialmente se il flusso di lavoro è in esecuzione su più server, ciascuno dei quali deve assumere il controllo per annullare le attività in corso.

* **[!UICONTROL Restart]**

   Questa azione si interrompe e quindi riavvia il flusso di lavoro. Nella maggior parte dei casi, è possibile riavviare più velocemente. È inoltre utile automatizzare il riavvio quando l&#39;arresto richiede un certo tempo: questo perché il comando &#39;Stop&#39; non è disponibile quando il flusso di lavoro viene arrestato.

   Le azioni **[!UICONTROL Start / Pause / Stop / Restart]** sono disponibili anche tramite le icone di esecuzione nella barra degli strumenti. Per ulteriori informazioni, consulta questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   Questa azione ti consente di eliminare la cronologia del flusso di lavoro. Per ulteriori informazioni, consulta [Rimozione dei registri](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   Questa opzione consente di avviare il flusso di lavoro in modalità di simulazione anziché in modalità reale. Ciò significa che quando si attiva questa modalità, vengono eseguite solo le attività che non hanno alcun impatto sul database o sul file system (ad esempio **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, ecc.). Attività che hanno un impatto (ad es. **[!UICONTROL Export]**, **[!UICONTROL Import]**, ecc.) e quelli successivi (nello stesso ramo) non vengono eseguiti.

* **[!UICONTROL Execute pending tasks now]**

   Questa azione consente di avviare tutte le attività in sospeso il prima possibile. Per avviare un’attività specifica, fai clic con il pulsante destro del mouse sulla relativa attività e seleziona **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   Questa opzione modifica lo stato del flusso di lavoro in **[!UICONTROL Finished]**. Questa azione deve essere utilizzata come ultima risorsa solo se il normale processo di arresto non riesce dopo diversi minuti. Utilizza l’arresto incondizionato solo se sei sicuro che non siano presenti processi di flusso di lavoro effettivi in corso.

   >[!CAUTION]
   >
   >Questa opzione è riservata agli utenti esperti.

* **[!UICONTROL Save as template]**

   Questa azione crea un nuovo modello di flusso di lavoro basato sul flusso di lavoro selezionato. È necessario specificare la cartella in cui verrà salvato (nel campo **[!UICONTROL Folder]** ).

   Le opzioni **[!UICONTROL Mass update of selected lines]** e **[!UICONTROL Merge selected lines]** sono opzioni generiche della piattaforma disponibili in tutti i menu **[!UICONTROL Actions]**. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/updating-data.md).

## Menu di scelta rapida {#right-click-menu}

Quando selezioni una o più attività del flusso di lavoro, puoi fare clic con il pulsante destro del mouse per intervenire sulla selezione.

![](assets/contextual_menu.png)

Nel menu di scelta rapida sono disponibili le seguenti opzioni:

**[!UICONTROL Open]**: questa opzione ti consente di accedere alle proprietà dell’attività.

**[!UICONTROL Display logs:]** questa opzione ti consente di visualizzare il registro di esecuzione dell’attività per l’attività selezionata. Fare riferimento a [Visualizzazione dei registri](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** questa azione consente di iniziare le attività in sospeso il prima possibile.

**[!UICONTROL Workflow restart from a task:]** questa opzione ti consente di riavviare il flusso di lavoro utilizzando i risultati memorizzati in precedenza per questa attività.

**[!UICONTROL Cut/Copy/Paste/Delete:]** queste opzioni consentono di tagliare, copiare, incollare ed eliminare le attività.

**[!UICONTROL Copy as bitmap:]** questa opzione ti consente di scattare una schermata di tutte le attività.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** queste opzioni sono disponibili anche nella  **[!UICONTROL Advanced]** scheda delle proprietà dell’attività. Sono descritti in [Execution](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** consente di salvare o annullare le modifiche apportate a un flusso di lavoro.

>[!NOTE]
>
>È possibile selezionare un gruppo di attività e applicarvi uno di questi comandi.

Il menu di scelta rapida è inoltre descritto in questa sezione [sezione](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
