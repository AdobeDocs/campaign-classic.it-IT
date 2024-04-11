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



Questo caso d’uso descrive come generare una versione preconfigurata mensile **[!UICONTROL Tracking indicators]** rapporto in formato PDF e come inviarlo a un elenco di destinatari.

![](assets/use_case_report_intro.png)

I passaggi principali di implementazione per questo caso d’uso sono:

* Creazione di un elenco di destinatari che riceveranno la consegna (consulta: [Passaggio 1: creazione dell’elenco dei destinatari](#step-1--creating-the-recipient-list)).
* Creazione di un modello di consegna che ti consentirà di generare una nuova consegna ogni volta che viene eseguito il flusso di lavoro (consulta: [Passaggio 2: creazione del modello di consegna](#step-2--creating-the-delivery-template)).
* Creazione di un flusso di lavoro che ti consentirà di generare il rapporto in formato PDF e di inviarlo all’elenco dei destinatari (consulta: [Passaggio 3: creazione del flusso di lavoro](#step-3--creating-the-workflow)).

## Passaggio 1: creazione dell’elenco dei destinatari {#step-1--creating-the-recipient-list}

Vai a **[!UICONTROL Profiles and targets]** , fare clic sulla scheda **[!UICONTROL Lists]** , quindi il **[!UICONTROL Create]** pulsante. Seleziona **[!UICONTROL New list]** e crea un nuovo elenco di destinatari al quale inviare il rapporto.

![](assets/use_case_report_1.png)

Per ulteriori informazioni sulla creazione di elenchi, consulta questa [sezione](../../platform/using/creating-and-managing-lists.md).

## Passaggio 2: creazione del modello di consegna {#step-2--creating-the-delivery-template}

1. Vai a **[!UICONTROL Resources > Templates > Delivery templates]** dell&#39;Adobe Campaign explorer e duplicare il **[!UICONTROL Email delivery]** modello preconfigurato.

   ![](assets/use_case_report_2.png)

   Per ulteriori informazioni sulla creazione di un modello di consegna, consulta questa [sezione](../../delivery/using/about-templates.md).

1. Immetti i vari parametri del modello: etichetta, destinazione (l’elenco dei destinatari creati in precedenza), oggetto e contenuto.

   ![](assets/use_case_report_3.png)

1. Ogni volta che il flusso di lavoro viene eseguito, il **[!UICONTROL Tracking indicators]** il report viene aggiornato (fare riferimento a [Passaggio 3: creazione del flusso di lavoro](#step-3--creating-the-workflow)). Per includere nella consegna la versione più recente del rapporto, è necessario aggiungere una **[!UICONTROL Calculated attachment]**:

   Per ulteriori informazioni sulla creazione di un allegato calcolato, consulta questa [sezione](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Fai clic su **[!UICONTROL Attachments]** link e click **[!UICONTROL Add]**, quindi seleziona **[!UICONTROL Calculated attachment]**.

     ![](assets/use_case_report_4.png)

   * Vai a **[!UICONTROL Type]** e selezionare la quarta opzione: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

     ![](assets/use_case_report_5.png)

     Il valore immesso nel **[!UICONTROL Label]** non verrà visualizzato nella consegna finale.

   * Vai alla zona di modifica e immetti il percorso di accesso e il nome del file.

     ![](assets/use_case_report_6.png)

     >[!CAUTION]
     >
     >Il file deve essere presente sul server. Il percorso e il nome devono essere identici a quelli immessi nella **[!UICONTROL JavaScript code]** attività di tipo del flusso di lavoro (consulta: [Passaggio 3: creazione del flusso di lavoro](#step-3--creating-the-workflow)).

   * Seleziona la **[!UICONTROL Advanced]** Tab e check **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Vai alla zona di modifica e immetti il nome che desideri assegnare all’allegato nella consegna finale.

     ![](assets/use_case_report_6bis.png)

## Passaggio 3: creazione del flusso di lavoro {#step-3--creating-the-workflow}

Per questo caso d’uso è stato creato il seguente flusso di lavoro. L’impresa svolge tre attività:

* Uno **[!UICONTROL Scheduler]** digita l’attività che ti consente di eseguire il flusso di lavoro una volta al mese,
* Uno **[!UICONTROL JavaScript code]** digita l’attività che ti consente di generare il rapporto in formato PDF,
* uno **[!UICONTROL Delivery]** digita l’attività che utilizza il modello di consegna creato in precedenza.

![](assets/use_case_report_8.png)

1. Ora vai al **[!UICONTROL Administration > Production > Technical workflows]** e crea un nuovo flusso di lavoro.

   ![](assets/use_case_report_7.png)

1. Per iniziare, aggiungi un **[!UICONTROL Scheduler]** digita l’attività e configurala in modo che il flusso di lavoro venga eseguito il primo lunedì del mese.

   ![](assets/use_case_report_9.png)

   Per ulteriori informazioni sulla configurazione della pianificazione, consulta [Scheduler](scheduler.md).

1. Quindi aggiungi **[!UICONTROL JavaScript code]** attività di tipo.

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

   * **var reportName**: inserisci il nome interno del rapporto tra virgolette. In questo caso, il nome interno del **Indicatore di tracciamento** report è &quot;deliveryFeedback&quot;.
   * **percorso var**: immetti il percorso di salvataggio del file (&quot;tmp/files/&quot;), il nome che desideri assegnare al file (&quot;deliveryFeedback&quot;) e l’estensione (&quot;.pdf&quot;). In questo caso, abbiamo utilizzato il nome interno come nome del file. I valori devono essere compresi tra virgolette doppie e separati dal carattere &quot;+&quot;.

     >[!CAUTION]
     >
     >Il file deve essere salvato sul server. È necessario immettere lo stesso percorso e lo stesso nome nel **[!UICONTROL General]** scheda della finestra di modifica per l&#39;allegato calcolato (fare riferimento a: [Passaggio 2: creazione del modello di consegna](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: inserisci il formato di esportazione del file (&quot;PDF&quot;).
   * **var_ctx** (contesto): in questo caso utilizziamo il **[!UICONTROL Tracking indicators]** nel suo contesto globale.

1. Termina aggiungendo un **[!UICONTROL Delivery]** digita l’attività con le seguenti opzioni:

   * **[!UICONTROL Delivery]**: seleziona **[!UICONTROL New, created from a template]** e seleziona il modello di consegna creato in precedenza.
   * Per **[!UICONTROL Recipients]** e **[!UICONTROL Content]** campi, seleziona **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: seleziona **[!UICONTROL Prepare and start]**.
   * Deseleziona **[!UICONTROL Generate an outbound transition]** e **[!UICONTROL Process errors]**.

   ![](assets/use_case_report_11.png)
