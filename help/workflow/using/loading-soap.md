---
product: campaign
title: Caricamento (SOAP)
description: Caricamento (SOAP)
feature: Workflows
hide: true
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
TQID: https://experienceleague.adobe.com/8G5YOa4HCsSoB9veHyexQ9uFvVDTYCj4W2Cv-nsmguw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 251
ht-degree: 4%

---

# Caricamento (SOAP){#loading-soap}



>[!CAUTION]
>
>L&#39;attività **Loading (SOAP)** è disponibile solo se è installato il modulo **FDA (Federated Data Access)**. Controlla il contratto di licenza.

L&#39;attività **Loading (SOAP)** viene utilizzata in aggiunta all&#39;attività **data loading (RDBMS)** quando non è possibile raccogliere dati direttamente tramite FDA in un database esterno.

Il funzionamento è il seguente:

1. Scegliere se utilizzare un esempio XML o un file WSDL.

   L&#39;esempio seguente proviene da un flusso di lavoro tecnico del modulo Centro messaggi.

   ![](assets/load_soap_002.png)

1. Per un esempio XML, selezionare un file di esempio. Il file viene analizzato per stabilire un esempio di risultato.

   Per un WSDL, immetti l’URL di accesso corrispondente e genera il codice scheletrico. Il servizio e la chiamata selezionati vengono aggiornati e visualizzati automaticamente.

   ![](assets/soap_load_003.png)

1. Selezionare **[!UICONTROL Click here to view and edit analysis results]** per specificare ogni colonna identificata.

   ![](assets/soap_load_001.png)

   Per aggiornare l&#39;esempio, selezionare **[!UICONTROL Re-analyze the example]**.

   Puoi anche personalizzare il formato dei dati delle colonne tramite il collegamento **[!UICONTROL Advanced parameters]**. Per ulteriori informazioni sulla formattazione dei dati importati, consulta questa [sezione](../../platform/using/executing-import-jobs.md).

1. Puoi utilizzare il numero di riga come identificatore e/o specificare che la chiamata SOAP restituisce diversi elementi.
1. Immetti i seguenti script di tabulazione in base alla loro funzione:

   * **[!UICONTROL Initialization]**: stabilisce una connessione SOAP.
   * **[!UICONTROL Iteration]**: esegue la chiamata al servizio SOAP. Il valore restituito per questa funzione deve essere un oggetto XML compatibile con la descrizione dell&#39;esempio o del file WSDL.

     Il codice di questa scheda verrà richiamato in un ciclo da Adobe Campaign fino alla restituzione di un oggetto XML null.

   * **[!UICONTROL Finalization]**: chiude la connessione e/o libera altre risorse create durante l&#39;elaborazione.
