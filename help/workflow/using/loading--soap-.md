---
solution: Campaign Classic
product: campaign
title: Caricamento (SOAP)
description: Caricamento (SOAP)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# Caricamento (SOAP){#loading-soap}

>[!CAUTION]
>
>L&#39;attività **Caricamento (SOAP)** è disponibile solo se è installato il modulo **FDA (Federated Data Access)**. Controlla il contratto di licenza.

L&#39;attività **Caricamento (SOAP)** viene utilizzata in aggiunta all&#39;attività **caricamento dei dati (RDBMS)** quando non è possibile raccogliere dati direttamente tramite FDA in un database esterno.

L&#39;operazione è la seguente:

1. Scegliere tra l&#39;utilizzo di un esempio XML o di un WSDL.

   L’esempio seguente deriva da un flusso di lavoro tecnico del modulo Centro messaggi.

   ![](assets/load_soap_002.png)

1. Per un esempio XML, selezionate un file di esempio. Il file viene analizzato per stabilire un esempio di risultato.

   Per un WSDL, immettete l&#39;URL di accesso corrispondente, quindi generate il codice di struttura. Il servizio e la chiamata selezionati vengono automaticamente aggiornati e visualizzati.

   ![](assets/soap_load_003.png)

1. Selezionare **[!UICONTROL Click here to view and edit analysis results]** per specificare ogni colonna identificata.

   ![](assets/soap_load_001.png)

   Se si desidera aggiornare l&#39;esempio, selezionare **[!UICONTROL Re-analyze the example]**.

   È inoltre possibile personalizzare il formato dei dati delle colonne tramite il collegamento **[!UICONTROL Advanced parameters]**. Per ulteriori informazioni sulla formattazione dei dati importati, vedere la sezione [](../../platform/using/executing-import-jobs.md).

1. È possibile utilizzare il numero di riga come identificatore e/o specificare che la chiamata SOAP restituisce diversi elementi.
1. Immettere gli script di tabulazione seguenti in base alla funzione:

   * **[!UICONTROL Initialization]**: stabilisce una connessione SOAP.
   * **[!UICONTROL Iteration]**: esegue la chiamata al servizio SOAP. Il risultato di questa funzione deve essere un oggetto XML compatibile con la descrizione dell&#39;esempio o del WSDL.

      Il codice di questa scheda viene chiamato in un ciclo da  Adobe Campaign fino alla restituzione di un oggetto XML nullo.

   * **[!UICONTROL Finalization]**: chiude la connessione e/o libera altre risorse create durante l&#39;elaborazione.

