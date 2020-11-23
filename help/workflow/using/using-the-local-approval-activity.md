---
solution: Campaign Classic
product: campaign
title: Utilizzo dell’attività di approvazione locale
description: Scoprite come utilizzare l'attività di approvazione locale
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 1%

---


# Utilizzo dell’attività di approvazione locale{#using-the-local-approval-activity}

L&#39; **[!UICONTROL Local approval]** attività integrata in un flusso di lavoro di targeting consente di impostare un processo di approvazione del destinatario prima dell&#39;invio.

>[!CAUTION]
>
>Per utilizzare questa funzione, è necessario acquistare il modulo Distributed Marketing, che è un&#39;opzione Campaign. Controlla il contratto di licenza.

Per impostare questo caso di utilizzo, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/local_validation_workflow.png)

Le fasi principali del processo di approvazione locale sono:

1. La popolazione risultante dal targeting può essere limitata grazie a un&#39;attività di tipo che utilizza un modello di distribuzione dei dati. **[!UICONTROL Split]**

   ![](assets/local_validation_intro_1.png)

1. L&#39; **[!UICONTROL Local approval]** attività prende il sopravvento e invia un&#39;e-mail di notifica a ciascun supervisore locale. L&#39;attività viene interrotta finché ogni supervisore locale non approva i destinatari assegnati.

   ![](assets/local_validation_intro_4.png)

1. Una volta raggiunta la scadenza di approvazione, il flusso di lavoro viene riavviato. In questo esempio, l&#39; **[!UICONTROL Delivery]** attività viene avviata e la consegna viene inviata alle destinazioni approvate.

   >[!NOTE]
   >
   >Una volta raggiunta la scadenza, i destinatari che non sono stati approvati vengono esclusi dal targeting.

   ![](assets/local_validation_intro_6.png)

1. Alcuni giorni dopo, il secondo tipo di attività invia un messaggio e-mail di notifica a ogni supervisore locale con un riepilogo delle azioni eseguite dai contatti (clic, aperture, ecc.). **[!UICONTROL Local approval]**

   ![](assets/local_validation_intro_5.png)

## Passaggio 1: Creazione del modello di distribuzione dei dati {#step-1--creating-the-data-distribution-template-}

Il modello di distribuzione dei dati consente di limitare la popolazione risultante dal targeting in base al raggruppamento dei dati, consentendo al contempo di assegnare ogni valore a un supervisore locale. In questo esempio, abbiamo definito il **[!UICONTROL Email address domain]** campo come campo di distribuzione e assegnato un dominio a ogni supervisore locale

Per ulteriori informazioni sulla creazione di un modello di distribuzione dei dati, vedere [Limitazione del numero di record di sottoinsiemi per distribuzione](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)dei dati.

1. Per creare il modello di distribuzione dei dati, passare al **[!UICONTROL Resources > Campaign management > Data distribution]** nodo e fare clic su **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. Seleziona la scheda **[!UICONTROL General]**.

   ![](assets/local_validation_data_distribution_2.png)

1. Inserite il **[!UICONTROL Label]** e il **[!UICONTROL Distribution context]**. In questo esempio, abbiamo selezionato lo schema di **[!UICONTROL Recipient]** targeting e il **[!UICONTROL Email domain]** campo come campo di distribuzione. L&#39;elenco dei destinatari sarà suddiviso per dominio.
1. Nel **[!UICONTROL Distribution type]** campo, selezionare l&#39;espressione del valore di limitazione della destinazione nella **[!UICONTROL Distribution]** scheda. Qui, abbiamo scelto **[!UICONTROL Percentage]**.
1. Nel **[!UICONTROL Approval storage]** campo, immettere lo schema di memorizzazione delle approvazioni che corrispondono allo schema di targeting in uso. Qui si utilizza lo schema di memorizzazione predefinito: **[!UICONTROL Local approval of recipients]**.
1. Quindi fate clic sul **[!UICONTROL Advanced parameters]** collegamento.

   ![](assets/local_validation_data_distribution_3.png)

1. Accertatevi che l’ **[!UICONTROL Approve the targeted messages]** opzione sia selezionata in modo che tutti i destinatari siano preselezionati dall’elenco dei destinatari da approvare.
1. Nel **[!UICONTROL Delivery label]** campo, abbiamo lasciato l&#39;espressione predefinita (stringa di calcolo del recapito). L&#39;etichetta standard della consegna verrà utilizzata nella notifica di feedback.
1. Nella **[!UICONTROL Grouping field]** sezione, abbiamo selezionato il **[!UICONTROL Gender]** campo come campo di raggruppamento per visualizzare i destinatari nelle notifiche di approvazione e feedback.
1. Nella **[!UICONTROL Edit targeted messages]** sezione sono state selezionate l&#39;applicazione **[!UICONTROL Edit recipients]** Web e il **[!UICONTROL recipientId]** parametro. Nelle notifiche di approvazione e feedback, i destinatari potranno fare clic e indirizzare l’URL dell’applicazione Web. Il parametro URL aggiuntivo sarà **[!UICONTROL recipientId]**.
1. Quindi fate clic sulla **[!UICONTROL Distribution]** scheda. Per ciascun dominio, immettete i campi seguenti:

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: immettere il valore del nome di dominio.
   * **[!UICONTROL Percentage / Fixed]**: per ciascun dominio, immettete il valore massimo. il numero di destinatari a cui si desidera inviare la consegna. In questo esempio, vogliamo limitare la consegna al 10% per dominio.
   * **[!UICONTROL Label]**: immettete l’etichetta del dominio da visualizzare nelle notifiche di approvazione e feedback.
   * **[!UICONTROL Group or operator]**: selezionare l&#39;operatore o il gruppo di operatori assegnati al dominio.

      >[!CAUTION]
      >
      >Accertatevi che agli operatori siano stati assegnati i diritti appropriati.

## Passaggio 2: Creazione del flusso di lavoro di targeting {#step-2--creating-the-targeting-workflow}

Per impostare questo caso di utilizzo, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/local_validation_workflow.png)

Sono state aggiunte le seguenti attività:

* Two **[!UICONTROL Query]** activities,
* Una **[!UICONTROL Intersection]** attività,
* Una **[!UICONTROL Split]** attività,
* Una **[!UICONTROL Local approval]** attività,
* Una **[!UICONTROL Delivery]** attività,
* Una **[!UICONTROL Wait]** attività,
* Una seconda **[!UICONTROL Local approval]** attività,
* Una **[!UICONTROL End]** attività.

### Query, intersezione e divisione {#queries--intersection-and-split}

Il targeting upstream è composto da due query, una intersezione e una divisione. La popolazione risultante dal targeting può essere limitata utilizzando un&#39; **[!UICONTROL Split]** attività che utilizza un modello di distribuzione dei dati.

Per ulteriori informazioni sulla configurazione di un&#39;attività divisa, vedere [Dividi](../../workflow/using/split.md). La creazione di un modello di distribuzione dei dati è dettagliata in [Limitazione del numero di record di sottoinsiemi per distribuzione](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)dei dati.

Se non si desidera limitare la popolazione dalla query, non è necessario utilizzare le attività **[!UICONTROL Query]**, **[!UICONTROL Intersection]** e **[!UICONTROL Split]** . In questo caso, completate il modello di distribuzione dei dati nella prima **[!UICONTROL Local approval]** attività.

1. Nella **[!UICONTROL Record count limitation]** sezione, selezionate l&#39; **[!UICONTROL Limit the selected records]** opzione e fate clic sul **[!UICONTROL Edit]** collegamento.

   ![](assets/local_validation_split_1.png)

1. Select the **[!UICONTROL Keep only the first records after sorting]** option and click **[!UICONTROL Next]**.

   ![](assets/local_validation_split_1bis.png)

1. Nella **[!UICONTROL Sort columns]** sezione, aggiungete il campo a cui viene applicato l&#39;ordinamento. Qui abbiamo scelto il **[!UICONTROL Email]** campo. Fai clic su **[!UICONTROL Next]**.

   ![](assets/local_validation_split_2.png)

1. Selezionate l&#39; **[!UICONTROL By data distribution]** opzione, selezionate il modello di distribuzione creato in precedenza (fate riferimento al [Passaggio 1: Creazione del modello](#step-1--creating-the-data-distribution-template-)di distribuzione dei dati) e fare clic su **[!UICONTROL Finish]**.

   ![](assets/local_validation_split_3.png)

Nel modello di distribuzione, abbiamo scelto di limitare la popolazione al 10% per valore di raggruppamento, che coincide con i valori visualizzati nel flusso di lavoro (340 come input e 34 come output).

![](assets/local_validation_intro_1.png)

### Notifica di approvazione {#approval-notification}

L&#39; **[!UICONTROL Local approval]** attività consente di inviare una notifica a ogni supervisore locale.

Per ulteriori informazioni sulla configurazione dell&#39; **[!UICONTROL Local approval]** attività, consultate l&#39;approvazione [](../../workflow/using/local-approval.md)locale.

![](assets/local_validation_workflow_2.png)

È necessario inserire i campi seguenti:

1. In the **[!UICONTROL Action to execute]** section, select the **[!UICONTROL Target approval notification]** option.
1. In the **[!UICONTROL Distribution context]** section, select the **[!UICONTROL Specified in the transition]** option.

   Se non si desidera limitare la popolazione di destinazione, selezionare l&#39; **[!UICONTROL Explicit]** opzione qui e immettere il modello di distribuzione creato in precedenza nel **[!UICONTROL Data distribution]** campo.

1. Nella **[!UICONTROL Notification]** sezione, selezionate il modello di consegna e l’oggetto da utilizzare per l’e-mail di notifica. Qui è stato scelto il modello predefinito: **[!UICONTROL Local approval notification]**.
1. Nella **[!UICONTROL Approval schedule]** sezione, abbiamo mantenuto la scadenza di approvazione predefinita (3 giorni) e aggiunto un promemoria. La consegna partirà 3 giorni dopo l&#39;inizio dell&#39;approvazione. Una volta raggiunta la scadenza di approvazione, i destinatari che non sono stati approvati non vengono presi in considerazione dal targeting.

L&#39;e-mail di notifica inviata dall&#39; **[!UICONTROL Local approval]** attività ai supervisori locali è la seguente:

![](assets/local_validation_intro_2.png)

### Wait {#wait}

L&#39;attività di attesa consente di posticipare l&#39;inizio della seconda attività di approvazione locale che invierà la notifica di feedback sulla consegna. Nel **[!UICONTROL Duration]** campo è stato immesso il **[!UICONTROL 5d]** valore (5 giorni). Le azioni eseguite dai destinatari per 5 giorni dopo l&#39;invio della consegna saranno incluse nella notifica di feedback.

![](assets/local_validation_workflow_3.png)

### Notifica di feedback {#feedback-notification}

La seconda **[!UICONTROL Local approval]** attività consente di inviare una notifica di feedback sulla consegna a ogni supervisore locale.

![](assets/local_validation_workflow_4.png)

È necessario inserire i campi seguenti.

1. Nella **[!UICONTROL Action to execute]** sezione, scegliete **[!UICONTROL Delivery feedback report]**.
1. Nella **[!UICONTROL Delivery]** sezione, scegliete **[!UICONTROL Specified in the transition]**.
1. Nella **[!UICONTROL Notification]** sezione, selezionate il modello di consegna e l’oggetto da utilizzare per l’e-mail di notifica.

Una volta raggiunta la scadenza configurata nell&#39;attività di attesa, il secondo tipo di attività invia il seguente messaggio e-mail di notifica a ogni supervisore locale: **[!UICONTROL Local approval]**

![](assets/local_validation_intro_3.png)

### Tracciamento approvazione da parte dell’amministratore {#approval-tracking-by-the-administrator}

Ogni volta che viene avviata l&#39;attività di approvazione locale, viene creata un&#39;attività di approvazione. L’amministratore può controllare ciascuna di queste attività di approvazione.

Andate al flusso di lavoro di targeting della campagna e fate clic sulla **[!UICONTROL Local approval tasks]** scheda.

![](assets/local_validation_admin_1.png)

È inoltre possibile accedere all&#39;elenco delle attività di approvazione locale tramite la **[!UICONTROL Approval tasks]** scheda del modello di distribuzione dei dati.

![](assets/local_validation_admin_2.png)

Selezionare l&#39;attività da monitorare e fare clic sul **[!UICONTROL Detail]** pulsante. La **[!UICONTROL General]** scheda dell&#39;attività di approvazione locale consente di visualizzare le informazioni sull&#39;attività. Se necessario, puoi modificare l&#39;approvazione e le date del promemoria.

![](assets/local_validation_admin_3.png)

Questa scheda mostra le informazioni seguenti:

* l’etichetta dell’attività e il relativo ID
* il modello di distribuzione utilizzato
* il numero di messaggi con targeting
* il flusso di lavoro e la campagna collegati
* la programmazione delle attività

La **[!UICONTROL Distribution]** scheda dell&#39;attività consente di visualizzare i registri di approvazione, il relativo stato, il numero di messaggi di destinazione, la data di approvazione e l&#39;operatore che ha approvato la consegna.

![](assets/local_validation_admin_4.png)

Selezionate un registro di approvazione e fate clic sul **[!UICONTROL Detail]** pulsante per visualizzare ulteriori informazioni. La **[!UICONTROL General]** scheda del registro di approvazione locale consente di visualizzare informazioni generali sul registro. Potete inoltre modificare lo stato di approvazione.

![](assets/local_validation_admin_5.png)

Questa scheda mostra le informazioni seguenti:

* l&#39;attività di approvazione collegata
* lo stato di approvazione (**[!UICONTROL Approved]** o **[!UICONTROL Pending]**)
* il modello di distribuzione utilizzato
* l&#39;autorità di vigilanza locale che ha approvato e la data di approvazione
* il numero di messaggi mirati e approvati

Nella **[!UICONTROL Targeted]** scheda del registro di approvazione viene visualizzato l’elenco dei destinatari e il relativo stato di approvazione. Se necessario, potete modificare questo stato.

![](assets/local_validation_admin_6.png)

