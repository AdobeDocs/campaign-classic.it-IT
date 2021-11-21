---
product: campaign
title: Definizione delle approvazioni
description: Le approvazioni consentono agli operatori di prendere decisioni relative a un flusso di lavoro o di confermarne l’esecuzione
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 4%

---

# Definizione delle approvazioni {#defining-approvals}

![](../../assets/common.svg)

Le approvazioni consentono agli operatori di prendere decisioni relative a un flusso di lavoro o di confermarne l’esecuzione.

Viene inviato un messaggio a un gruppo di operatori e il flusso di lavoro attende una risposta prima di riprendere. Il flusso di lavoro non viene interrotto e possono essere eseguite altre operazioni. Ad esempio, possono essere presenti più approvazioni simultanee in sospeso.

Un&#39;approvazione può contenere più opzioni per l&#39;operatore da scegliere. Tuttavia, è possibile limitare il numero di scelte a uno al fine di inviare un’attività da eseguire a un operatore, ad esempio l’esecuzione del targeting. L’operatore può quindi rispondere una volta eseguita l’attività (il processo riprende). L&#39;esempio seguente illustra questi tipi di approvazioni:

![](assets/validation-1.png)

Nelle operazioni, tutte le fasi che richiedono l&#39;approvazione si basano sullo stesso principio.

![](assets/validation-1-in-op.png)

Gli esempi di approvazione si trovano in questo [sezione](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Un operatore può rispondere in uno dei due modi seguenti: convalida tramite la pagina web collegata nel messaggio e-mail o tramite la console.

>[!NOTE]
>
>Una volta salvata la risposta, la risposta potrebbe non essere modificata.

## Invio di e-mail {#sending-emails}

È possibile ricevere un messaggio di approvazione contenente un collegamento a una pagina web tramite il quale è possibile rispondere. Affinché l’operatore di destinazione riceva un messaggio e-mail di approvazione, l’indirizzo e-mail dell’operatore deve essere completo. In caso contrario, l’operatore deve utilizzare la console per rispondere

La gestione degli operatori è descritta in questo [sezione](../../platform/using/access-management.md).

Le e-mail di approvazione vengono inviate continuamente. Il modello di consegna predefinito è **[!UICONTROL notifyAssignee]**: Viene salvato nella **[!UICONTROL Administration > Campaign management > Technical delivery templates]** cartella. Questo scenario può essere personalizzato ed è consigliabile creare una copia e modificare i modelli per ogni attività.

Le consegne create tramite questo modello sono memorizzate nella **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** cartella.

## Approvazione tramite la console {#approval-via-the-console}

Nelle operazioni, gli elementi da approvare vengono visualizzati sul dashboard della campagna.

Per i flussi di lavoro tecnici, è possibile accedere alle attività che l’utente può approvare dalla struttura ad albero nel **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** cartella.

![](assets/validation-node.png)

## Gruppi {#groups}

Un’approvazione viene assegnata a un gruppo di operatori, a un singolo operatore o a un insieme di operatori selezionati tramite una condizione di filtro.

1. Per la forma di approvazione più semplice, l&#39;attività viene completata non appena l&#39;operatore risponde. Qualsiasi altro operatore che cerchi di rispondere verrà informato che qualcuno lo ha già fatto.
1. Per più approvazioni, fai riferimento a [Approvazione multipla](#multiple-approval).

I gruppi di operatori per le approvazioni devono essere designati come ruoli o funzioni anziché come persone nominate. Ad esempio, un gruppo &quot;Budget campagna&quot; è preferibile al gruppo &quot;Harry&#39;s&quot;. Consigliamo di avere almeno due persone in un gruppo in grado di approvare un’attività. In questo modo, se uno è assente, l&#39;altro può rispondere.

## Scadenza {#expirations}

Le scadenze sono transizioni specifiche utilizzate in diversi tipi di attività e in particolare nelle approvazioni. Puoi utilizzare una scadenza per attivare un&#39;azione dopo un dato tempo senza risposta. Può anche essere utilizzato, ad esempio, per proseguire il flusso di lavoro e assegnare un’approvazione a un gruppo diverso.

La seconda scheda nelle proprietà di approvazione dell’attività ti consente di definire una o più scadenze. In realtà, puoi definire più tipi di scadenza.

![](assets/expiration.png)

Per aggiungere una nuova scadenza, fai clic su **[!UICONTROL Add]**. A ciascuna delle scadenze create viene aggiunta una transizione. Puoi:

* modificare i parametri tipici direttamente facendo clic su una cella dell&#39;elenco (o premendo F2),
* o modifica l’espressione facendo clic sul pulsante **[!UICONTROL Detail...]** pulsante .

>[!NOTE]
>
>Non è necessario specificare un ordine per le scadenze in ordine cronologico.

La **[!UICONTROL Do not terminate the task]** lascia attiva l&#39;approvazione quando il ritardo viene eseguito. Questa modalità consente di gestire i promemoria lasciando attiva l&#39;approvazione: gli operatori possono ancora rispondere. Questa opzione è disabilitata per impostazione predefinita, il che significa che l’attività è considerata terminata alla scadenza e che gli operatori potrebbero non rispondere più.

È possibile creare quattro tipi di scadenza:

* **Ritardo dopo l&#39;avvio dell&#39;attività**: La scadenza viene calcolata aggiungendo un periodo di tempo specificato alla data in cui l’approvazione viene attivata.
* **Ritardo dopo una data specificata**: La scadenza viene calcolata aggiungendo un periodo di tempo a una data specificata.
* **Ritardo prima di una data specificata**: La scadenza viene calcolata sottraendo un periodo di tempo da una data specificata.
* **Scadenza calcolata dallo script**: La scadenza viene calcolata utilizzando JavaScript.

   L’esempio seguente calcola una scadenza 24 ore prima della data di inizio di una consegna (identificata da **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## Approvazione multipla {#multiple-approval}

L’approvazione multipla è un meccanismo che consente a tutti gli operatori di approvazione di rispondere. Per ogni risposta viene attivata una transizione.

L&#39;approvazione multipla è utile per i meccanismi di voto o di indagine. Puoi contare le risposte ed elaborarne il risultato dopo un determinato periodo aggiungendo una scadenza.

## Diritti richiesti {#required-rights}

Gli operatori di un gruppo devono avere almeno i seguenti diritti per poter rispondere a una richiesta di approvazione:

* Autorizzazioni di scrittura per il flusso di lavoro.
* Autorizzazioni di lettura e scrittura per la cartella contenente le attività da approvare.

Il gruppo &quot;Esecuzione flusso di lavoro&quot; dispone di questi diritti. Un operatore aggiunto a questo gruppo ha i diritti per rispondere a una richiesta di approvazione.
