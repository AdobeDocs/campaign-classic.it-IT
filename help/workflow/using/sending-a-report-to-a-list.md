---
title: Invio di un report a un elenco
seo-title: Invio di un report a un elenco
description: Invio di un report a un elenco
seo-description: null
page-status-flag: never-activated
uuid: 29759fd8-47f3-47cc-9f7e-263e305fd6fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 41b8a8a8-efac-4e8e-8aea-d4fd06c46e74
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 3%

---


# Invio di un report a un elenco{#sending-a-report-to-a-list}

Questo caso d’uso descrive come generare un rapporto mensile out-of-the-box **[!UICONTROL Tracking indicators]** in formato PDF e come inviarlo a un elenco di destinatari.

![](assets/use_case_report_intro.png)

Le fasi di implementazione principali per questo caso di utilizzo sono:

* Creazione di un elenco dei destinatari che riceveranno la consegna (fare riferimento a: [Passaggio 1: Creazione dell&#39;elenco](#step-1--creating-the-recipient-list)destinatari).
* Creazione di un modello di consegna che consenta di generare una nuova consegna ogni volta che viene eseguito il flusso di lavoro (consultate: [Passaggio 2: Creazione del modello](#step-2--creating-the-delivery-template)di consegna).
* Creazione di un flusso di lavoro per generare il rapporto in formato PDF e inviarlo all’elenco dei destinatari (consultare: [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)).

## Passaggio 1: Creazione dell&#39;elenco dei destinatari {#step-1--creating-the-recipient-list}

Vai all&#39; **[!UICONTROL Profiles and targets]** universo, fai clic sul **[!UICONTROL Lists]** collegamento, poi sul **[!UICONTROL Create]** pulsante. Seleziona **[!UICONTROL New list]** e crea un nuovo elenco di destinatari a cui inviare il rapporto.

![](assets/use_case_report_1.png)

For more on creating lists, refer to this [section](../../platform/using/creating-and-managing-lists.md).

## Passaggio 2: Creazione del modello di consegna {#step-2--creating-the-delivery-template}

1. Passate al **[!UICONTROL Resources > Templates > Delivery templates]** nodo di  Adobe Campaign Explorer e duplicate il modello **[!UICONTROL Email delivery]** out-of-the-box.

   ![](assets/use_case_report_2.png)

   Per ulteriori informazioni sulla creazione di un modello di consegna, consulta questa [sezione](../../delivery/using/about-templates.md).

1. Immettete i vari parametri del modello: label, target (l&#39;elenco dei destinatari creati in precedenza), oggetto e contenuto.

   ![](assets/use_case_report_3.png)

1. Ogni volta che viene eseguito il flusso di lavoro, il **[!UICONTROL Tracking indicators]** rapporto viene aggiornato (fare riferimento al [passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)). Per includere nella consegna la versione più recente del rapporto, è necessario aggiungere un **[!UICONTROL Calculated attachment]**:

   Per ulteriori informazioni sulla creazione di un allegato calcolato, consultare questa [sezione](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Fai clic sul **[!UICONTROL Attachments]** collegamento e fai clic **[!UICONTROL Add]**, quindi seleziona **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Passate al **[!UICONTROL Type]** campo e selezionate la quarta opzione: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      Il valore immesso nel **[!UICONTROL Label]** campo non verrà visualizzato nella consegna finale.

   * Andate nella zona di modifica e immettete il percorso di accesso e il nome del file.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >Il file deve essere presente sul server. Il percorso e il nome devono essere identici a quelli immessi nell&#39;attività di **[!UICONTROL JavaScript code]** tipo del flusso di lavoro (fare riferimento a: [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)).

   * Selezionare la **[!UICONTROL Advanced]** scheda e selezionare **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Passate alla zona di modifica e immettete il nome da assegnare all’allegato nella consegna finale.

      ![](assets/use_case_report_6bis.png)

## Passaggio 3: Creazione del flusso di lavoro {#step-3--creating-the-workflow}

Per questo caso di utilizzo è stato creato il seguente flusso di lavoro. Esso ha tre attività:

* Un tipo **[!UICONTROL Scheduler]** di attività che consente di eseguire il flusso di lavoro una volta al mese,
* Un&#39;attività **[!UICONTROL JavaScript code]** di tipo che consente di generare il rapporto in formato PDF,
* un&#39;attività **[!UICONTROL Delivery]** di tipo che utilizza il modello di consegna creato in precedenza.

![](assets/use_case_report_8.png)

1. Ora passate al **[!UICONTROL Administration > Production > Technical workflows]** nodo e create un nuovo flusso di lavoro.

   ![](assets/use_case_report_7.png)

1. Per iniziare, aggiungete un&#39;attività di tipo e configuratela in modo che il flusso di lavoro venga eseguito il primo lunedì del mese. **[!UICONTROL Scheduler]**

   ![](assets/use_case_report_9.png)

   Per ulteriori informazioni sulla configurazione del pianificatore, vedere [Pianificatore](../../workflow/using/scheduler.md).

1. Quindi aggiungere un&#39;attività **[!UICONTROL JavaScript code]** tipo.

   ![](assets/use_case_report_10.png)

   Immettete il seguente codice nella zona di modifica:

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

   * **var reportName**: immettere il nome interno del rapporto tra virgolette. In questo caso, il nome interno del report indicatore **di** tracciamento è &quot;deliveryFeedback&quot;.
   * **percorso** var: immettete il percorso di salvataggio del file (&quot;tmp/files/&quot;), il nome che desiderate assegnare al file (&quot;deliveryFeedback&quot;) e l’estensione del file (&quot;.pdf&quot;). In questo caso, abbiamo usato il nome interno come nome del file. I valori devono essere compresi tra virgolette doppie e separati dal carattere &quot;+&quot;.

      >[!CAUTION]
      >
      >Il file deve essere salvato sul server. È necessario immettere lo stesso percorso e lo stesso nome nella **[!UICONTROL General]** scheda della finestra di modifica per l&#39;allegato calcolato (fare riferimento a: [Passaggio 2: Creazione del modello](#step-2--creating-the-delivery-template)di consegna).

   * **var exportFormat**: immettere il formato di esportazione del file (&quot;PDF&quot;).
   * **var_ctx** (contesto): in questo caso, utilizziamo la **[!UICONTROL Tracking indicators]** relazione nel suo contesto globale.

1. Per terminare, aggiungi un&#39;attività di **[!UICONTROL Delivery]** tipo con le seguenti opzioni:

   * **[!UICONTROL Delivery]**: selezionate **[!UICONTROL New, created from a template]** e selezionate il modello di consegna creato in precedenza.
   * Per i **[!UICONTROL Recipients]** campi e **[!UICONTROL Content]** , selezionare **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: selezionare **[!UICONTROL Prepare and start]**.
   * Deselezionare **[!UICONTROL Generate an outbound transition]** e **[!UICONTROL Process errors]**.

   ![](assets/use_case_report_11.png)

