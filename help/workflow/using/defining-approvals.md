---
product: campaign
title: Definire le approvazioni
description: Le approvazioni consentono agli operatori di prendere decisioni relative a un flusso di lavoro o di confermarne l’esecuzione
feature: Approvals
hide: true
hidefromtoc: true
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---

# Definire le approvazioni {#defining-approvals}



Le approvazioni consentono agli operatori di prendere decisioni relative a un flusso di lavoro o di confermarne l’esecuzione.

Un messaggio viene inviato a un gruppo di operatori e il flusso di lavoro attende una risposta prima di riprendere. Il flusso di lavoro non viene interrotto e possono essere eseguite altre operazioni. Ad esempio, possono essere presenti più approvazioni simultanee in sospeso.

Un’approvazione può contenere più opzioni che l’operatore può scegliere. Tuttavia, è possibile limitare il numero di scelte a una per inviare un&#39;attività da eseguire a un operatore, ad esempio l&#39;esecuzione del targeting. L&#39;operatore può quindi rispondere una volta che l&#39;operazione viene eseguita (il processo riprende). L’esempio seguente illustra questi tipi di approvazioni:

![](assets/validation-1.png)

Nelle operazioni, tutte le fasi che richiedono l’approvazione si basano sullo stesso principio.

![](assets/validation-1-in-op.png)

Esempi di approvazione sono disponibili in [questa sezione](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Un operatore può rispondere in uno dei due modi seguenti: tramite la convalida tramite la pagina web collegata nel messaggio e-mail o tramite la console.

>[!NOTE]
>
>Una volta salvata, la risposta non può essere modificata.

## Approvazioni per e-mail {#sending-emails}

È possibile ricevere un messaggio di approvazione contenente un collegamento a una pagina web tramite il quale è possibile rispondere. Affinché l’operatore di destinazione riceva un’e-mail di approvazione, l’indirizzo e-mail dell’operatore deve essere completo. In caso contrario, l’operatore deve utilizzare la console per rispondere

La gestione degli operatori è descritta in questa [sezione](../../platform/using/access-management.md).

Le e-mail di approvazione vengono inviate in modo continuo. Il modello di consegna predefinito è **[!UICONTROL notifyAssignee]**: è salvato nella cartella **[!UICONTROL Administration > Campaign management > Technical delivery templates]**. Questo scenario può essere personalizzato e si consiglia inoltre di crearne una copia e di modificare i modelli per ogni attività.

Le consegne create tramite questo modello vengono archiviate nella cartella **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**.

## Approvazioni tramite la console {#approval-via-the-console}

Nelle operazioni, gli elementi da approvare vengono visualizzati nel dashboard della campagna.

Per i flussi di lavoro tecnici, è possibile accedere alle attività che l&#39;utente può approvare dalla struttura ad albero nella cartella **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]**.

![](assets/validation-node.png)

## Gruppi {#groups}

Un’approvazione viene assegnata a un gruppo di operatori, a un singolo operatore o a un insieme di operatori selezionati tramite una condizione di filtro.

1. Per una forma di approvazione più semplice, l’attività viene completata non appena un operatore risponde. Qualsiasi altro operatore che tenti di rispondere riceverà una notifica di qualcuno che l&#39;ha già fatto.
1. Per più approvazioni, fare riferimento a [Approvazioni multiple](#multiple-approval).

I gruppi di operatori per le approvazioni devono essere designati come ruoli o funzioni anziché come individui con nome. Ad esempio, un gruppo &quot;Budget campagna&quot; è preferibile a &quot;Gruppo di Harry&quot;. È consigliabile avere almeno due persone in un gruppo che possano approvare un&#39;attività. In questo modo, se uno è assente, l&#39;altro può rispondere.

## Scadenze {#expirations}

Le scadenze sono transizioni specifiche utilizzate in diversi tipi di attività e in particolare nelle approvazioni. Puoi utilizzare una scadenza per attivare un’azione dopo un determinato periodo di tempo senza risposta. Può essere utilizzato anche, ad esempio, per seguire il flusso di lavoro e assegnare un’approvazione a un gruppo diverso.

La seconda scheda nelle proprietà di approvazione dell’attività ti consente di definire una o più scadenze. In effetti, puoi definire più tipi di scadenza.

![](assets/expiration.png)

Per aggiungere una nuova scadenza, fare clic su **[!UICONTROL Add]**. A ciascuna delle scadenze create viene aggiunta una transizione. Puoi eseguire le seguenti azioni:

* modificare direttamente i parametri tipici facendo clic su una cella dell&#39;elenco (o premendo F2),
* oppure modificare l&#39;espressione facendo clic sul pulsante **[!UICONTROL Detail...]**.

>[!NOTE]
>
>Non è necessario specificare un ordine per le scadenze in quanto vengono elaborate in ordine cronologico.

L&#39;opzione **[!UICONTROL Do not terminate the task]** lascia l&#39;approvazione attiva quando il ritardo viene superato. Questa modalità consente di gestire i promemoria lasciando attiva l’approvazione: gli operatori possono ancora rispondere. Questa opzione è disabilitata per impostazione predefinita, il che significa che l’attività è considerata completata alla scadenza e che gli operatori potrebbero non rispondere più.

Puoi creare quattro tipi di scadenza:

* **Ritardo dopo l&#39;inizio dell&#39;attività**: la scadenza viene calcolata aggiungendo un periodo di tempo specificato alla data di attivazione dell&#39;approvazione.
* **Ritardo dopo una data specificata**: la scadenza viene calcolata aggiungendo un periodo di tempo a una data specificata.
* **Ritardo prima di una data specificata**: la scadenza viene calcolata sottraendo un periodo di tempo da una data specificata.
* **Scadenza calcolata dallo script**: la scadenza viene calcolata utilizzando JavaScript.

  L&#39;esempio seguente calcola una scadenza 24 ore prima della data di inizio di una consegna (identificata da **vars.deliveryId**):

  ```
  var delivery = nms.delivery.get(vars.deliveryId)
  var expiration = delivery.scheduling.contactDate
  var oneDay = 1000*60*60*24
  expiration.setTime(expiration.getTime() - oneDay)
  return expiration
  ```

## Approvazione multipla {#multiple-approval}

L’approvazione multipla è un meccanismo che consente a tutti gli operatori di approvazione di rispondere. Viene attivata una transizione per ogni risposta.

L’approvazione multipla è utile per i meccanismi di voto o di sondaggio. Puoi contare le risposte ed elaborarne i risultati dopo un determinato periodo aggiungendo una scadenza.

## Diritti richiesti {#required-rights}

Per poter rispondere a una richiesta di approvazione, gli operatori di un gruppo devono disporre almeno dei seguenti diritti:

* Autorizzazioni di scrittura per il flusso di lavoro.
* Autorizzazioni di lettura e scrittura per la cartella contenente le attività da approvare.

Il gruppo &quot;Esecuzione del flusso di lavoro&quot; dispone di questi diritti. Un operatore aggiunto a questo gruppo dispone dei diritti per rispondere a una richiesta di approvazione.
