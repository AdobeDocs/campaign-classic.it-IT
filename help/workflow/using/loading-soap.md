---
product: campaign
title: Caricamento (SOAP)
description: Caricamento (SOAP)
feature: Workflows
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# Caricamento (SOAP){#loading-soap}



>[!CAUTION]
>
>Il **Caricamento (SOAP)** l&#39;attività è disponibile solo se si dispone di **FDA (Federated Data Access)** modulo installato. Controlla il contratto di licenza.

Il **Caricamento (SOAP)** l&#39;attività viene utilizzata in aggiunta al **caricamento dati (RDBMS)** attività quando non è possibile raccogliere dati direttamente tramite l’FDA in un database esterno.

Il funzionamento è il seguente:

1. Scegliere se utilizzare un esempio XML o un file WSDL.

   L&#39;esempio seguente proviene da un flusso di lavoro tecnico del modulo Centro messaggi.

   ![](assets/load_soap_002.png)

1. Per un esempio XML, selezionare un file di esempio. Il file viene analizzato per stabilire un esempio di risultato.

   Per un WSDL, immetti l’URL di accesso corrispondente e genera il codice scheletrico. Il servizio e la chiamata selezionati vengono aggiornati e visualizzati automaticamente.

   ![](assets/soap_load_003.png)

1. Seleziona **[!UICONTROL Click here to view and edit analysis results]** per specificare ogni colonna identificata.

   ![](assets/soap_load_001.png)

   Se desideri aggiornare l’esempio, seleziona **[!UICONTROL Re-analyze the example]**.

   Puoi anche personalizzare il formato dei dati delle colonne tramite **[!UICONTROL Advanced parameters]** collegamento. Per ulteriori informazioni sulla formattazione dei dati importati, consulta questa [sezione](../../platform/using/executing-import-jobs.md).

1. Puoi utilizzare il numero di riga come identificatore e/o specificare che la chiamata SOAP restituisca diversi elementi.
1. Immetti i seguenti script di tabulazione in base alla loro funzione:

   * **[!UICONTROL Initialization]**: stabilisce una connessione SOAP.
   * **[!UICONTROL Iteration]**: esegue la chiamata al servizio SOAP. Il valore restituito per questa funzione deve essere un oggetto XML compatibile con la descrizione dell&#39;esempio o del file WSDL.

     Il codice di questa scheda verrà richiamato in un ciclo da Adobe Campaign fino alla restituzione di un oggetto XML null.

   * **[!UICONTROL Finalization]**: chiude la connessione e/o libera altre risorse create durante l’elaborazione.
