---
product: campaign
title: Approvazione locale
description: Approvazione locale
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# Approvazione locale{#local-approval}

![](../../assets/common.svg)

Quando viene integrata in un flusso di lavoro di targeting, l’ attività **[!UICONTROL Local approval]** ti consente di impostare un processo di approvazione del destinatario prima che la consegna venga inviata.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Per utilizzare questa attività, è necessario aver acquistato il modulo Marketing distribuito , che è un’opzione Campaign. Controlla il contratto di licenza.

Per un esempio dell&#39;attività **[!UICONTROL Local approval]** con un modello di distribuzione, fai riferimento a [Utilizzo dell&#39;attività di approvazione locale](using-the-local-approval-activity.md).

Inizia immettendo un’etichetta per l’attività e il campo **[!UICONTROL Action to execute]** :

![](assets/local_validation_1.png)

* Seleziona l’opzione **[!UICONTROL Target approval notification]** per inviare un messaggio e-mail di notifica alle autorità di vigilanza locali prima della consegna, chiedendo loro di approvare i destinatari assegnati.

   ![](assets/local_validation_intro_2.png)

* **Query** incrementale: consente di eseguire una query e pianificarne l’esecuzione. Consulta la sezione [Incremental query](incremental-query.md) .

   ![](assets/local_validation_intro_3.png)

## Notifica di approvazione di Target {#target-approval-notification}

In questo caso, l’attività **[!UICONTROL Local approval]** viene posizionata tra il targeting a monte e la consegna:

![](assets/local_validation_2.png)

I campi da inserire nel caso di una notifica per l’approvazione del target sono i seguenti:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: seleziona l’ **[!UICONTROL Specified in the transition]** opzione se utilizzi un’attività di  **[!UICONTROL Split]** tipo per limitare la popolazione target. In questo caso, il modello di distribuzione viene inserito nell’attività divisa. Se non stai limitando la popolazione target, seleziona l’opzione **[!UICONTROL Explicit]** qui e immetti il modello di distribuzione nel campo **[!UICONTROL Data distribution]** .

   Per ulteriori informazioni sulla creazione di un modello di distribuzione dei dati, consulta [Limitazione del numero di record di sottoinsiemi per distribuzione dei dati](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * Seleziona il modello di consegna e l’oggetto da utilizzare per la notifica e-mail. È disponibile un modello predefinito: **[!UICONTROL Local approval notification]**. Puoi anche aggiungere una descrizione che verrà visualizzata sopra gli elenchi dei destinatari nelle notifiche di approvazione e feedback.
   * Specifica la **[!UICONTROL Approval type]** che corrisponde alla scadenza dell&#39;approvazione (data o scadenza dall&#39;inizio dell&#39;approvazione). A questa data, il flusso di lavoro viene riavviato e i destinatari che non sono stati approvati non vengono presi in considerazione nel targeting. Una volta inviate le notifiche, l’attività viene messa in coda in modo che le autorità di vigilanza locali possano approvare i loro contatti.

      >[!NOTE]
      >
      >Per impostazione predefinita, all’avvio del processo di approvazione, l’attività viene sospesa per tre giorni.

      È inoltre possibile aggiungere uno o più promemoria per informare le autorità di vigilanza locali che la scadenza si sta avvicinando. A questo scopo, fai clic sul collegamento **[!UICONTROL Add a reminder]** .

* **[!UICONTROL Complementary set]**: l’ **[!UICONTROL Generate complement]** opzione ti consente di generare un secondo set che include tutti i target non approvati.

   >[!NOTE]
   >
   >Questa opzione è disabilitata per impostazione predefinita.

## Report di feedback sulla consegna {#delivery-feedback-report}

In questo caso, l’attività **[!UICONTROL Local approval]** viene inserita dopo la consegna:

![](assets/local_validation_4.png)

Nel caso di un rapporto di feedback sulla consegna, devono essere inseriti i campi seguenti:

![](assets/local_validation_workflow_4.png)

* Seleziona l’opzione **[!UICONTROL Specified in the transition]** se la consegna è stata inserita durante un’attività precedente. Seleziona **[!UICONTROL Explicit]** per specificare la consegna nell’attività di approvazione locale.
* Seleziona il modello di consegna e l’oggetto dell’e-mail di notifica. Esiste un modello predefinito: **[!UICONTROL Local approval notification]**.

## Esempio: Approvazione di una consegna del flusso di lavoro {#example--approving-a-workflow-delivery}

Questo esempio mostra come impostare un processo di approvazione per una consegna di flusso di lavoro. Per ulteriori informazioni sulla creazione di flussi di lavoro di consegna, consulta l’ [Esempio: sezione workflow di consegna](delivery.md#example--delivery-workflow).

Un operatore può approvare una consegna in uno dei due modi seguenti: utilizzare la pagina web collegata nel messaggio e-mail o tramite la console.

* Approvazione web

   L’e-mail inviata agli operatori del gruppo Amministratore consente di approvare la destinazione della consegna. Il messaggio utilizza il testo definito e l’espressione JavaScript viene sostituita dal valore calcolato (in questo caso, &#39;574&#39;)

   Per approvare la consegna, fai clic sul collegamento pertinente e accedi alla console Adobe Campaign.

   ![](assets/new-workflow-valid-webaccess.png)

   Effettua una scelta e fai clic sul pulsante **[!UICONTROL Submit]** .

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* Approvazione tramite la console

   Nella struttura ad albero, il nodo **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** contiene l&#39;elenco delle attività che devono essere approvate dall&#39;operatore attualmente connesso. Nell’elenco deve essere visualizzata una riga. Fai doppio clic su questa riga per rispondere. Viene visualizzata la seguente finestra:

![](assets/new-workflow-7.png)

Selezionare **Sì**, quindi fare clic su **[!UICONTROL Approve]**. Un messaggio ti informa che la risposta è stata registrata.

Torna alla schermata del flusso di lavoro: Dopo circa dieci secondi, il diagramma viene visualizzato come segue:

![](assets/new-workflow-8.png)

Il flusso di lavoro ha eseguito l’attività **[!UICONTROL Delivery control]** , il che in questo caso significa avviare la consegna creata in precedenza. Il flusso di lavoro è stato completato senza errori.
