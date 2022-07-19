---
product: campaign
title: Inviare un rapporto a un elenco
description: Scopri come inviare un rapporto a un elenco con un flusso di lavoro
feature: Workflows
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# Inviare un rapporto a un elenco{#sending-a-report-to-a-list}

![](../../assets/v7-only.svg)

Questo caso d’uso descrive come generare un **[!UICONTROL Tracking indicators]** rapporti in formato PDF e modalità di invio a un elenco di destinatari.

![](assets/use_case_report_intro.png)

I passaggi principali per l’implementazione di questo caso d’uso sono:

* Creazione di un elenco di destinatari che riceveranno la consegna (consulta: [Passaggio 1: Creazione dell’elenco dei destinatari](#step-1--creating-the-recipient-list)).
* Creazione di un modello di consegna che ti consentirà di generare una nuova consegna ogni volta che il flusso di lavoro viene eseguito (consulta: [Passaggio 2: Creazione del modello di consegna](#step-2--creating-the-delivery-template)).
* Creazione di un flusso di lavoro che consente di generare il rapporto in formato PDF e di inviarlo all’elenco dei destinatari (consulta: [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)).

## Passaggio 1: Creazione dell’elenco dei destinatari {#step-1--creating-the-recipient-list}

Vai a **[!UICONTROL Profiles and targets]** fai clic sulla scheda **[!UICONTROL Lists]** link, quindi il **[!UICONTROL Create]** pulsante . Seleziona **[!UICONTROL New list]** e crea un nuovo elenco di destinatari per il rapporto a cui inviare.

![](assets/use_case_report_1.png)

Per ulteriori informazioni sulla creazione di elenchi, consulta questo [sezione](../../platform/using/creating-and-managing-lists.md).

## Passaggio 2: Creazione del modello di consegna {#step-2--creating-the-delivery-template}

1. Vai a **[!UICONTROL Resources > Templates > Delivery templates]** nodo di Adobe Campaign explorer e duplica il **[!UICONTROL Email delivery]** modello preconfigurato.

   ![](assets/use_case_report_2.png)

   Per ulteriori informazioni sulla creazione di un modello di consegna, consulta questo [sezione](../../delivery/using/about-templates.md).

1. Immetti i vari parametri del modello: etichetta, target (l’elenco dei destinatari creati in precedenza), oggetto e contenuto.

   ![](assets/use_case_report_3.png)

1. Ogni volta che il flusso di lavoro viene eseguito, il **[!UICONTROL Tracking indicators]** viene aggiornato il rapporto (consulta [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)). Per includere nella consegna la versione più recente del rapporto, devi aggiungere un **[!UICONTROL Calculated attachment]**:

   Per ulteriori informazioni sulla creazione di un allegato calcolato, consulta [sezione](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Fai clic sul pulsante **[!UICONTROL Attachments]** collegamento e clic **[!UICONTROL Add]**, quindi seleziona **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Vai a **[!UICONTROL Type]** e seleziona la quarta opzione: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      Il valore immesso nel **[!UICONTROL Label]** il campo non verrà visualizzato nella consegna finale.

   * Passa alla zona di modifica e immetti il percorso di accesso e il nome del file.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >Il file deve essere presente sul server. Il suo percorso e il suo nome devono essere identici a quelli immessi nel **[!UICONTROL JavaScript code]** tipo di attività del flusso di lavoro (consulta: [Passaggio 3: Creazione del flusso di lavoro](#step-3--creating-the-workflow)).

   * Seleziona la **[!UICONTROL Advanced]** scheda e controllo **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Passa all’area di modifica e inserisci il nome da assegnare all’allegato nella consegna finale.

      ![](assets/use_case_report_6bis.png)

## Passaggio 3: Creazione del flusso di lavoro {#step-3--creating-the-workflow}

Il seguente flusso di lavoro è stato creato per questo caso d’uso. Ha tre attività:

* Uno **[!UICONTROL Scheduler]** digitare attività che consente di eseguire il flusso di lavoro una volta al mese,
* Uno **[!UICONTROL JavaScript code]** digitare attività che consente di generare il rapporto in formato PDF,
* uno **[!UICONTROL Delivery]** digitare attività che utilizza il modello di consegna creato in precedenza.

![](assets/use_case_report_8.png)

1. Ora vai al **[!UICONTROL Administration > Production > Technical workflows]** e crea un nuovo flusso di lavoro.

   ![](assets/use_case_report_7.png)

1. Inizia aggiungendo un **[!UICONTROL Scheduler]** digita l’attività e configurala in modo che il flusso di lavoro venga eseguito il primo lunedì del mese.

   ![](assets/use_case_report_9.png)

   Per ulteriori informazioni sulla configurazione della pianificazione, consulta [Scheduler](scheduler.md).

1. Quindi aggiungi una **[!UICONTROL JavaScript code]** digitare activity.

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

   * **var reportName**: inserire il nome interno del rapporto tra virgolette doppie. In questo caso, il nome interno del **Indicatore di tracciamento** il rapporto è &quot;deliveryFeedback&quot;.
   * **percorso var**: inserisci il percorso di salvataggio del file (&quot;tmp/files/&quot;), il nome che desideri assegnare al file (&quot;deliveryFeedback&quot;) e l’estensione del file (&quot;.pdf&quot;). In questo caso, abbiamo utilizzato il nome interno come nome del file. I valori devono essere tra virgolette doppie e separati dal carattere &quot;+&quot;.

      >[!CAUTION]
      >
      >Il file deve essere salvato sul server. È necessario immettere lo stesso percorso e lo stesso nome nel **[!UICONTROL General]** scheda della finestra di modifica per l&#39;allegato calcolato (fare riferimento a: [Passaggio 2: Creazione del modello di consegna](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: immettere il formato di esportazione del file (&quot;PDF&quot;).
   * **var_ctx** (contesto): in questo caso, utilizziamo il **[!UICONTROL Tracking indicators]** nel suo contesto globale.

1. Completare aggiungendo un **[!UICONTROL Delivery]** digita l’attività con le seguenti opzioni:

   * **[!UICONTROL Delivery]**: select **[!UICONTROL New, created from a template]**, quindi seleziona il modello di consegna creato in precedenza.
   * Per **[!UICONTROL Recipients]** e **[!UICONTROL Content]** campi, seleziona **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: select **[!UICONTROL Prepare and start]**.
   * Deselezionare **[!UICONTROL Generate an outbound transition]** e **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)
