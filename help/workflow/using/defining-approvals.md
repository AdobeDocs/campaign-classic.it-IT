---
title: Definizione delle approvazioni
description: Le approvazioni consentono agli operatori di prendere decisioni su un flusso di lavoro o di confermarne l'esecuzione continua.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---


# Definizione delle approvazioni {#defining-approvals}

Le approvazioni consentono agli operatori di prendere decisioni su un flusso di lavoro o di confermarne l&#39;esecuzione continua.

Un messaggio viene inviato a un gruppo di operatori e il flusso di lavoro attende una risposta prima della ripresa. Il flusso di lavoro non viene interrotto e altre operazioni possono essere eseguite. Ad esempio, potrebbero essere presenti più approvazioni simultanee in sospeso.

Un&#39;approvazione può contenere più opzioni che l&#39;operatore può scegliere. Tuttavia, è possibile limitare il numero di scelte a uno per inviare un&#39;attività da eseguire a un operatore, ad esempio per eseguire il targeting. L&#39;operatore può quindi rispondere una volta eseguita l&#39;attività (il processo riprende). L&#39;esempio seguente illustra questi tipi di approvazione:

![](assets/validation-1.png)

Nelle operazioni, tutte le fasi che richiedono l&#39;approvazione si basano sullo stesso principio.

![](assets/validation-1-in-op.png)

Gli esempi di approvazione sono disponibili in questa [sezione](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Un operatore può rispondere in uno dei due modi seguenti: convalida mediante la pagina Web collegata nel messaggio e-mail o tramite la console.

>[!NOTE]
>
>Una volta salvata la risposta, la risposta potrebbe non essere modificata.

## Invio di e-mail {#sending-emails}

È possibile ricevere un messaggio di approvazione contenente un collegamento a una pagina Web tramite la quale è possibile rispondere. Affinché l&#39;operatore di destinazione riceva un&#39;e-mail di approvazione, l&#39;indirizzo e-mail dell&#39;operatore deve essere completo. In caso contrario, l&#39;operatore deve utilizzare la console per rispondere

La gestione degli operatori è descritta in questa [sezione](../../platform/using/access-management.md).

Le e-mail di approvazione vengono inviate in modo continuo. Il modello di consegna predefinito è **[!UICONTROL notifyAssignee]**: Viene salvata nella **[!UICONTROL Administration > Campaign management > Technical delivery templates]** cartella. Questo scenario può essere personalizzato ed è anche consigliato di creare una copia e modificare i modelli per ogni attività.

Le consegne create tramite questo modello vengono memorizzate nella **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** cartella.

## Approvazione tramite console {#approval-via-the-console}

Nelle operazioni, gli elementi da approvare vengono visualizzati nel dashboard della campagna.

Per i flussi di lavoro tecnici, è possibile accedere alle attività che l&#39;utente può approvare dalla struttura ad albero della **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** cartella.

![](assets/validation-node.png)

## Gruppi {#groups}

Un&#39;approvazione è assegnata a un gruppo di operatori, un singolo operatore o un insieme di operatori selezionati tramite una condizione di filtraggio.

1. Per la forma di approvazione più semplice, l&#39;attività è terminata non appena l&#39;operatore risponde. Tutti gli altri operatori che cercano di rispondere riceveranno una notifica che qualcuno l&#39;ha già fatto.
1. Per approvazioni multiple, fare riferimento a [Approvazione](#multiple-approval)multipla.

I gruppi di operatori per le approvazioni devono essere designati come ruoli o funzioni anziché come individui denominati. Ad esempio, un gruppo &quot;Budget campagna&quot; è preferibile a &quot;Gruppo Harry&quot;. Consigliamo di avere almeno due persone in un gruppo che possano approvare un compito. In questo modo, se uno è assente, l&#39;altro può rispondere.

## Scadenza {#expirations}

Le scadenze sono transizioni specifiche utilizzate in diversi tipi di attività, in particolare nelle approvazioni. Una scadenza può essere utilizzata per attivare un’azione dopo un determinato lasso di tempo in assenza di una risposta o per proseguire il flusso di lavoro (e assegnare un’approvazione a un altro gruppo, ad esempio).

La seconda scheda nelle proprietà di approvazione dell&#39;attività consente di definire una o più scadenze. In realtà, potete definire più tipi di scadenza.

![](assets/expiration.png)

Per aggiungere una nuova scadenza, fate clic su **[!UICONTROL Add]**. A ciascuna scadenza creata viene aggiunta una transizione. È possibile:

* modificare i parametri tipici direttamente facendo clic su una cella nell&#39;elenco (o premendo F2),
* oppure modificare l&#39;espressione facendo clic sul **[!UICONTROL Detail...]** pulsante.

>[!NOTE]
>
>Non è necessario specificare un ordine per le scadenze in quanto elaborate in ordine cronologico.

L&#39; **[!UICONTROL Do not terminate the task]** opzione lascia attiva l&#39;approvazione quando il ritardo viene superato. Questa modalità consente di gestire i promemoria lasciando attiva l’approvazione: gli operatori possono ancora rispondere. Questa opzione è disabilitata per impostazione predefinita, pertanto l&#39;attività viene considerata terminata alla scadenza e gli operatori potrebbero non rispondere più.

Potete creare quattro tipi di scadenza:

* **Ritardo dopo l’inizio** dell’attività: La scadenza viene calcolata aggiungendo un periodo di tempo specificato alla data in cui viene attivata l’approvazione.
* **Ritardo dopo una data** specificata: La scadenza viene calcolata aggiungendo un periodo di tempo alla data specificata.
* **Ritardo prima di una data** specificata: La scadenza viene calcolata sottraendo un periodo di tempo da una data specificata.
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

L&#39;approvazione multipla è un meccanismo che consente a tutti gli operatori di approvazione di rispondere. Per ogni risposta viene attivata una transizione.

L&#39;approvazione multipla è utile per i meccanismi di votazione o indagine. Potete contare le risposte ed elaborarne il risultato dopo un determinato periodo aggiungendo una scadenza.

## Diritti richiesti {#required-rights}

Gli operatori di un gruppo devono avere almeno i seguenti diritti per poter rispondere a una richiesta di approvazione:

* Autorizzazioni di scrittura per il flusso di lavoro.
* Autorizzazioni di lettura e scrittura per la cartella contenente le attività da approvare.

Il gruppo Esecuzione flusso di lavoro dispone di tali diritti. Un operatore aggiunto a questo gruppo ha i diritti per rispondere a una richiesta di approvazione.
