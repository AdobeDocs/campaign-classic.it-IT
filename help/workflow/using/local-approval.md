---
title: Approvazione locale
seo-title: Approvazione locale
description: Approvazione locale
seo-description: null
page-status-flag: never-activated
uuid: 4de59c8a-e229-4c8d-acab-2b116cafb70b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a223641e-93e1-42ef-bb6b-8e1a0f8f6a65
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---


# Approvazione locale{#local-approval}

Se integrata in un flusso di lavoro di targeting, l&#39; **[!UICONTROL Local approval]** attività consente di impostare un processo di approvazione del destinatario prima dell&#39;invio.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Per utilizzare questa attività, è necessario aver acquistato il modulo Distributed Marketing, che è un&#39;opzione Campaign. Controlla il contratto di licenza.

Per un esempio dell&#39; **[!UICONTROL Local approval]** attività con un modello di distribuzione, fare riferimento a [Utilizzo dell&#39;attività](../../workflow/using/using-the-local-approval-activity.md)di approvazione locale.

Per iniziare, immettete un&#39;etichetta per l&#39;attività e il **[!UICONTROL Action to execute]** campo:

![](assets/local_validation_1.png)

* Selezionate l’ **[!UICONTROL Target approval notification]** opzione per inviare un messaggio e-mail di notifica ai supervisori locali prima della consegna, chiedendo loro di approvare i destinatari assegnati.

   ![](assets/local_validation_intro_2.png)

* **Query** incrementale: consente di eseguire una query e pianificarne l&#39;esecuzione. Refer to the [Incremental query](../../workflow/using/incremental-query.md) section.

   ![](assets/local_validation_intro_3.png)

## Notifica di approvazione di Target {#target-approval-notification}

In questo caso, l&#39; **[!UICONTROL Local approval]** attività viene posizionata tra targeting upstream e la distribuzione:

![](assets/local_validation_2.png)

I campi da inserire nel caso di una notifica per l&#39;approvazione target sono:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: selezionate l&#39; **[!UICONTROL Specified in the transition]** opzione se utilizzate un&#39;attività di **[!UICONTROL Split]** tipo per limitare la popolazione di destinazione. In questo caso, il modello di distribuzione viene immesso nell&#39;attività divisa. Se non si limita la popolazione di destinazione, selezionare l&#39; **[!UICONTROL Explicit]** opzione qui e immettere il modello di distribuzione nel **[!UICONTROL Data distribution]** campo.

   Per ulteriori informazioni sulla creazione di un modello di distribuzione dei dati, vedere [Limitazione del numero di record di sottoinsiemi per distribuzione](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)dei dati.

* **[!UICONTROL Approval management]**

   * Selezionate il modello di consegna e l’oggetto da utilizzare per la notifica e-mail. A default template is available: **[!UICONTROL Local approval notification]**. Puoi anche aggiungere una descrizione che verrà visualizzata sopra gli elenchi dei destinatari nelle notifiche di approvazione e feedback.
   * Specificare **[!UICONTROL Approval type]** che corrisponde alla scadenza dell&#39;approvazione (data o scadenza dall&#39;inizio dell&#39;approvazione). A questa data, il flusso di lavoro viene riavviato e i destinatari che non sono stati approvati non vengono presi in considerazione nel targeting. Una volta inviate le notifiche, l&#39;attività viene messa in coda in modo che le autorità di vigilanza locali possano approvare i loro contatti.

      >[!NOTE]
      >
      >Per impostazione predefinita, all&#39;avvio del processo di approvazione, l&#39;attività viene sospesa per tre giorni.

      È inoltre possibile aggiungere uno o più promemoria per informare i supervisori locali che la scadenza si sta avvicinando. A tale scopo, fare clic sul **[!UICONTROL Add a reminder]** collegamento.

* **[!UICONTROL Complementary set]**: l’ **[!UICONTROL Generate complement]** opzione consente di generare un secondo set che include tutte le destinazioni non approvate.

   >[!NOTE]
   >
   >Questa opzione è disabilitata per impostazione predefinita.

## Report di feedback sulla consegna {#delivery-feedback-report}

In questo caso, l&#39; **[!UICONTROL Local approval]** attività viene posizionata dopo la consegna:

![](assets/local_validation_4.png)

Nel caso di un rapporto di feedback sulla consegna, è necessario inserire i campi seguenti:

![](assets/local_validation_workflow_4.png)

* Selezionate l&#39; **[!UICONTROL Specified in the transition]** opzione se la consegna è stata inserita durante un&#39;attività precedente. Selezionare **[!UICONTROL Explicit]** per specificare la consegna nell&#39;attività di approvazione locale.
* Selezionate il modello di consegna e l’oggetto dell’e-mail di notifica. Esiste un modello predefinito: **[!UICONTROL Local approval notification]**.

## Esempio: Approvazione della distribuzione di un flusso di lavoro {#example--approving-a-workflow-delivery}

Questo esempio mostra come impostare un processo di approvazione per la distribuzione di un flusso di lavoro. Per ulteriori informazioni sulla creazione di flussi di lavoro di consegna, consulta l’ [esempio: sezione del flusso di lavoro](../../workflow/using/delivery.md#example--delivery-workflow) di distribuzione.

Un operatore può approvare una consegna in uno dei due modi seguenti: utilizzare la pagina Web collegata nel messaggio e-mail o tramite la console.

* Approvazione Web

   L’e-mail inviata agli operatori del gruppo Amministratore consente di approvare la destinazione di consegna. Il messaggio utilizza il testo definito e l&#39;espressione JavaScript viene sostituita dal valore calcolato (in questo caso, &#39;574&#39;)

   Per approvare la consegna, fai clic sul collegamento pertinente e accedi alla console Adobe Campaign .

   ![](assets/new-workflow-valid-webaccess.png)

   Scegliere e fare clic sul **[!UICONTROL Submit]** pulsante.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* Approvazione tramite console

   Nella struttura ad albero, il **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** nodo contiene l&#39;elenco delle attività che devono essere approvate dall&#39;operatore attualmente connesso. Nell&#39;elenco deve essere visualizzata una riga. Fate doppio clic su questa riga per rispondere. Viene visualizzata la finestra seguente:

![](assets/new-workflow-7.png)

Selezionare **Sì**, quindi fare clic su **[!UICONTROL Approve]**. Un messaggio vi informa che la risposta è stata registrata.

Torna alla schermata del flusso di lavoro: Dopo circa dieci secondi, il diagramma viene visualizzato come segue:

![](assets/new-workflow-8.png)

Il flusso di lavoro ha eseguito l’ **[!UICONTROL Delivery control]** attività, il che in questo caso significa avviare la consegna precedentemente creata. Il flusso di lavoro è terminato senza errori.
