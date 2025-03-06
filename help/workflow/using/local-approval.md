---
product: campaign
title: Approvazione locale
description: Approvazione locale
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 3%

---

# Approvazione locale{#local-approval}



Se integrata in un flusso di lavoro di targeting, l&#39;attività **[!UICONTROL Local approval]** ti consente di impostare un processo di approvazione del destinatario prima che la consegna venga inviata.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Per utilizzare questa attività, devi aver acquistato il modulo Marketing distribuito, che è un’opzione di Campaign. Controlla il contratto di licenza.

Per un esempio dell&#39;attività **[!UICONTROL Local approval]** con un modello di distribuzione, vedere [Utilizzo dell&#39;attività di approvazione locale](using-the-local-approval-activity.md).

Per iniziare, immetti un&#39;etichetta per l&#39;attività e il campo **[!UICONTROL Action to execute]**:

![](assets/local_validation_1.png)

* Selezionare l&#39;opzione **[!UICONTROL Target approval notification]** per inviare un&#39;e-mail di notifica ai supervisori locali prima della consegna, chiedendo l&#39;approvazione dei destinatari assegnati.

  ![](assets/local_validation_intro_2.png)

* **Query incrementale**: consente di eseguire una query e pianificarne l&#39;esecuzione. Consulta la sezione [Incremental query](incremental-query.md).

  ![](assets/local_validation_intro_3.png)

## Notifica per approvazione target {#target-approval-notification}

In questo caso, l&#39;attività **[!UICONTROL Local approval]** viene inserita tra il targeting a monte e la consegna:

![](assets/local_validation_2.png)

I campi da inserire in caso di notifica per l’approvazione del target sono:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: selezionare l&#39;opzione **[!UICONTROL Specified in the transition]** se si utilizza un&#39;attività di tipo **[!UICONTROL Split]** per limitare la popolazione di destinazione. In questo caso, il modello di distribuzione viene inserito nell’attività di suddivisione. Se non si desidera limitare la popolazione di destinazione, selezionare l&#39;opzione **[!UICONTROL Explicit]** e immettere il modello di distribuzione nel campo **[!UICONTROL Data distribution]**.

  Per ulteriori informazioni sulla creazione di un modello di distribuzione dati, vedere [Limitazione del numero di record di sottoinsiemi per distribuzione dati](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * Seleziona il modello di consegna e l’oggetto che verrà utilizzato per la notifica e-mail. È disponibile un modello predefinito: **[!UICONTROL Local approval notification]**. Puoi anche aggiungere una descrizione che verrà visualizzata sopra gli elenchi dei destinatari nelle notifiche di approvazione e feedback.
   * Specifica il **[!UICONTROL Approval type]** che corrisponde alla scadenza dell&#39;approvazione (data o scadenza dall&#39;inizio dell&#39;approvazione). In questa data, il flusso di lavoro viene riavviato e i destinatari che non sono stati approvati non vengono presi in considerazione nel targeting. Dopo l’invio delle notifiche, l’attività viene messa in coda in modo che i supervisori locali possano approvare i loro contatti.

     >[!NOTE]
     >
     >Per impostazione predefinita, all’avvio del processo di approvazione, l’attività viene sospesa per tre giorni.

     Puoi anche aggiungere uno o più promemoria per informare i supervisori locali che la scadenza si sta avvicinando. A tale scopo, fare clic sul collegamento **[!UICONTROL Add a reminder]**.

* **[!UICONTROL Complementary set]**: l&#39;opzione **[!UICONTROL Generate complement]** consente di generare un secondo set che include tutte le destinazioni non approvate.

  >[!NOTE]
  >
  >Questa opzione è disabilitata per impostazione predefinita.

## Rapporto del feedback sulla consegna {#delivery-feedback-report}

In questo caso, l&#39;attività **[!UICONTROL Local approval]** viene inserita dopo la consegna:

![](assets/local_validation_4.png)

Nel caso di un rapporto sul feedback della consegna, è necessario inserire i campi seguenti:

![](assets/local_validation_workflow_4.png)

* Seleziona l&#39;opzione **[!UICONTROL Specified in the transition]** se la consegna è stata immessa durante un&#39;attività precedente. Selezionare **[!UICONTROL Explicit]** per specificare la consegna nell&#39;attività di approvazione locale.
* Seleziona il modello di consegna e l’oggetto dell’e-mail di notifica. Modello predefinito: **[!UICONTROL Local approval notification]**.

## Esempio: approvazione di una consegna di flusso di lavoro {#example--approving-a-workflow-delivery}

Questo esempio mostra come impostare un processo di approvazione per una consegna di flusso di lavoro. Per ulteriori informazioni sulla creazione di flussi di lavoro di consegna, consulta la sezione [Esempio: flusso di lavoro di consegna](delivery.md#example--delivery-workflow).

Un operatore può approvare una consegna in uno dei due modi seguenti: utilizzando la pagina web collegata nel messaggio e-mail o tramite la console.

* Approvazione web

  L’e-mail inviata agli operatori del gruppo Amministratore ti consente di approvare il target di consegna. Il messaggio utilizza il testo definito e l’espressione JavaScript viene sostituita dal valore calcolato (in questo caso, &quot;574&quot;)

  Per approvare la consegna, fai clic sul collegamento pertinente e accedi alla console Adobe Campaign.

  ![](assets/new-workflow-valid-webaccess.png)

  Scegliere e fare clic sul pulsante **[!UICONTROL Submit]**.

  ![](assets/new-workflow-valid-webaccess-confirm.png)

* Approvazione tramite la console

  Nella struttura ad albero, il nodo **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** contiene l&#39;elenco delle attività che devono essere approvate dall&#39;operatore attualmente connesso. L’elenco deve visualizzare una riga. Fare doppio clic su questa riga per rispondere. Viene visualizzata la seguente finestra:

![](assets/new-workflow-7.png)

Seleziona **Sì**, quindi fai clic su **[!UICONTROL Approve]**. Viene visualizzato un messaggio per informare che la risposta è stata registrata.

Torna alla schermata del flusso di lavoro: dopo circa dieci secondi, il diagramma viene visualizzato come segue:

![](assets/new-workflow-8.png)

Il flusso di lavoro ha eseguito l&#39;attività **[!UICONTROL Delivery control]**, che in questo caso significa avviare la consegna creata in precedenza. Il flusso di lavoro è stato completato senza errori.
