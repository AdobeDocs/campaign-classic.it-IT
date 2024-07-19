---
product: campaign
title: Inviare un rapporto a un elenco
description: Scopri come inviare un rapporto a un elenco con un flusso di lavoro
feature: Workflows
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 1%

---

# Inviare un rapporto a un elenco{#sending-a-report-to-a-list}



Questo caso d&#39;uso descrive come generare un report **[!UICONTROL Tracking indicators]** predefinito mensile in formato PDF e come inviarlo a un elenco di destinatari.

![](assets/use_case_report_intro.png)

I passaggi principali di implementazione per questo caso d’uso sono:

* Creazione di un elenco di destinatari che riceveranno la consegna (vedere: [Passaggio 1: Creazione dell&#39;elenco dei destinatari](#step-1--creating-the-recipient-list)).
* Creazione di un modello di consegna che ti consentirà di generare una nuova consegna ogni volta che viene eseguito il flusso di lavoro (consulta: [Passaggio 2: Creazione del modello di consegna](#step-2--creating-the-delivery-template)).
* Creazione di un flusso di lavoro che ti consentirà di generare il rapporto in formato PDF e di inviarlo all&#39;elenco dei destinatari (consulta: [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)).

## Passaggio 1: creazione dell’elenco dei destinatari {#step-1--creating-the-recipient-list}

Vai alla scheda **[!UICONTROL Profiles and targets]**, fai clic sul collegamento **[!UICONTROL Lists]**, quindi sul pulsante **[!UICONTROL Create]**. Selezionare **[!UICONTROL New list]** e creare un nuovo elenco di destinatari per il report da inviare a.

![](assets/use_case_report_1.png)

Per ulteriori informazioni sulla creazione di elenchi, consulta questa [sezione](../../platform/using/creating-and-managing-lists.md).

## Passaggio 2: creazione del modello di consegna {#step-2--creating-the-delivery-template}

1. Vai al nodo **[!UICONTROL Resources > Templates > Delivery templates]** di Adobe Campaign Explorer e duplica il modello preconfigurato **[!UICONTROL Email delivery]**.

   ![](assets/use_case_report_2.png)

   Per ulteriori informazioni sulla creazione di un modello di consegna, consulta questa [sezione](../../delivery/using/about-templates.md).

1. Immetti i vari parametri del modello: etichetta, destinazione (l’elenco dei destinatari creati in precedenza), oggetto e contenuto.

   ![](assets/use_case_report_3.png)

1. Ogni volta che il flusso di lavoro viene eseguito, il report **[!UICONTROL Tracking indicators]** viene aggiornato (fare riferimento al [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)). Per includere nella consegna la versione più recente del report, è necessario aggiungere **[!UICONTROL Calculated attachment]**:

   Per ulteriori informazioni sulla creazione di un allegato calcolato, consulta questa [sezione](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Fare clic sul collegamento **[!UICONTROL Attachments]** e fare clic su **[!UICONTROL Add]**, quindi selezionare **[!UICONTROL Calculated attachment]**.

     ![](assets/use_case_report_4.png)

   * Passare al campo **[!UICONTROL Type]** e selezionare la quarta opzione: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

     ![](assets/use_case_report_5.png)

     Il valore immesso nel campo **[!UICONTROL Label]** non verrà visualizzato nella consegna finale.

   * Vai alla zona di modifica e immetti il percorso di accesso e il nome del file.

     ![](assets/use_case_report_6.png)

     >[!CAUTION]
     >
     >Il file deve essere presente sul server. Il percorso e il nome devono essere identici a quelli immessi nell&#39;attività di tipo **[!UICONTROL JavaScript code]** del flusso di lavoro (fare riferimento a: [Passaggio 3: creazione del flusso di lavoro](#step-3--creating-the-workflow)).

   * Selezionare la scheda **[!UICONTROL Advanced]** e selezionare **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Vai alla zona di modifica e immetti il nome che desideri assegnare all’allegato nella consegna finale.

     ![](assets/use_case_report_6bis.png)

## Passaggio 3: creazione del flusso di lavoro {#step-3--creating-the-workflow}

Per questo caso d’uso è stato creato il seguente flusso di lavoro. L’impresa svolge tre attività:

* Un&#39;attività di tipo **[!UICONTROL Scheduler]** che consente di eseguire il flusso di lavoro una volta al mese,
* Un&#39;attività di tipo **[!UICONTROL JavaScript code]** che consente di generare il report in formato PDF,
* un&#39;attività di tipo **[!UICONTROL Delivery]** che utilizza il modello di consegna creato in precedenza.

![](assets/use_case_report_8.png)

1. Passare al nodo **[!UICONTROL Administration > Production > Technical workflows]** e creare un nuovo flusso di lavoro.

   ![](assets/use_case_report_7.png)

1. Iniziare aggiungendo un&#39;attività di tipo **[!UICONTROL Scheduler]** e configurarla in modo che il flusso di lavoro venga eseguito il primo lunedì del mese.

   ![](assets/use_case_report_9.png)

   Per ulteriori informazioni sulla configurazione della pianificazione, fare riferimento a [Pianificazione](scheduler.md).

1. Quindi aggiungi un&#39;attività di tipo **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_report_10.png)

   Immetti il seguente codice nella zona di modifica:

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   Vengono utilizzate le seguenti variabili:

   * **var reportName**: immettere il nome interno del report tra virgolette doppie. In questo caso, il nome interno del report **Indicatore di tracciamento** è &quot;deliveryFeedback&quot;.
   * **percorso var**: immettere il percorso di salvataggio del file (&quot;tmp/files/&quot;), il nome che si desidera assegnare al file (&quot;deliveryFeedback&quot;) e l&#39;estensione (&quot;.pdf&quot;). In questo caso, abbiamo utilizzato il nome interno come nome del file. I valori devono essere compresi tra virgolette doppie e separati dal carattere &quot;+&quot;.

     >[!CAUTION]
     >
     >Il file deve essere salvato sul server. Immettere lo stesso percorso e lo stesso nome nella scheda **[!UICONTROL General]** della finestra di modifica per l&#39;allegato calcolato (fare riferimento a: [Passaggio 2: Creazione del modello di consegna](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: immettere il formato di esportazione del file (&quot;PDF&quot;).
   * **var _ctx** (contesto): in questo caso, il report **[!UICONTROL Tracking indicators]** viene utilizzato nel relativo contesto globale.

1. Per terminare, aggiungere un&#39;attività di tipo **[!UICONTROL Delivery]** con le opzioni seguenti:

   * **[!UICONTROL Delivery]**: selezionare **[!UICONTROL New, created from a template]**, quindi selezionare il modello di consegna creato in precedenza.
   * Per i campi **[!UICONTROL Recipients]** e **[!UICONTROL Content]**, selezionare **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: selezionare **[!UICONTROL Prepare and start]**.
   * Deseleziona **[!UICONTROL Generate an outbound transition]** e **[!UICONTROL Process errors]**.

   ![](assets/use_case_report_11.png)
