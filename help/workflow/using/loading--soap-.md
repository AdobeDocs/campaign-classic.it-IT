---
title: Caricamento (SOAP)
seo-title: Caricamento (SOAP)
description: Caricamento (SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 5%

---


# Caricamento (SOAP){#loading-soap}

>[!CAUTION]
>
>L&#39;attività di **caricamento (SOAP)** è disponibile solo se è installato il modulo **FDA (Federated Data Access)** . Controlla il contratto di licenza.

L&#39;attività di **caricamento (SOAP)** viene utilizzata in aggiunta all&#39;attività di caricamento dei **dati (RDBMS)** quando non è possibile raccogliere i dati direttamente tramite FDA in un database esterno.

L&#39;operazione è la seguente:

1. Scegliere tra l&#39;utilizzo di un esempio XML o di un WSDL.

   L’esempio seguente deriva da un flusso di lavoro tecnico del modulo Centro messaggi.

   ![](assets/load_soap_002.png)

1. Per un esempio XML, selezionate un file di esempio. Il file viene analizzato per stabilire un esempio di risultato.

   Per un WSDL, immettete l&#39;URL di accesso corrispondente, quindi generate il codice di struttura. Il servizio e la chiamata selezionati vengono automaticamente aggiornati e visualizzati.

   ![](assets/soap_load_003.png)

1. Selezionare **[!UICONTROL Click here to view and edit analysis results]** per specificare ogni colonna identificata.

   ![](assets/soap_load_001.png)

   Se desiderate aggiornare l&#39;esempio, selezionate **[!UICONTROL Re-analyze the example]**.

   Puoi anche personalizzare il formato dei dati delle colonne tramite il **[!UICONTROL Advanced parameters]** collegamento. Per ulteriori informazioni sulla formattazione dei dati importati, consultare questa [sezione](../../platform/using/importing-data.md#import-wizard).

1. È possibile utilizzare il numero di riga come identificatore e/o specificare che la chiamata SOAP restituisce diversi elementi.
1. Immettere gli script di tabulazione seguenti in base alla funzione:

   * **[!UICONTROL Initialization]**: stabilisce una connessione SOAP.
   * **[!UICONTROL Iteration]**: esegue la chiamata al servizio SOAP. Il risultato di questa funzione deve essere un oggetto XML compatibile con la descrizione dell&#39;esempio o del WSDL.

      Il codice di questa scheda viene chiamato in un ciclo da  Adobe Campaign fino alla restituzione di un oggetto XML nullo.

   * **[!UICONTROL Finalization]**: chiude la connessione e/o libera altre risorse create durante l&#39;elaborazione.

