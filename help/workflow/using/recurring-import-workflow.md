---
solution: Campaign Classic
product: campaign
title: Impostazione di un’importazione ricorrente
description: Scopri come configurare un modello di flusso di lavoro per le importazioni ricorrenti.
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---

# Impostazione di un flusso di lavoro di importazione ricorrente {#setting-up-a-recurring-import}

L’utilizzo di un modello di flusso di lavoro è una best practice per importare regolarmente file con la stessa struttura.

Questo esempio mostra come impostare un flusso di lavoro che può essere riutilizzato per importare profili provenienti da un sistema di gestione delle relazioni con i clienti nel database Adobe Campaign. Per ulteriori informazioni su tutte le impostazioni possibili per ogni attività, consulta questa [sezione](../../workflow/using/about-activities.md).

1. Crea un nuovo modello di flusso di lavoro da **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Aggiungi le seguenti attività:

   * **[!UICONTROL Data loading (file)]**: Definisci la struttura prevista del file contenente i dati da importare.
   * **[!UICONTROL Enrichment]**: Riconciliare i dati importati con i dati del database.
   * **[!UICONTROL Split]**: Crea filtri per elaborare i record in modo diverso a seconda che possano essere riconciliati o meno.
   * **[!UICONTROL Deduplication]**: Deduplica i dati dal file in arrivo prima di inserirli nel database.
   * **[!UICONTROL Update data]**: Aggiorna il database con i profili importati.

   ![](assets/import_template_example0.png)

1. Configura l&#39;attività **[!UICONTROL Data Loading (file)]**:

   * Definisci la struttura prevista caricando un file di esempio. Il file di esempio deve contenere solo poche righe ma tutte le colonne necessarie per l’importazione. Controlla e modifica il formato del file per assicurarti che il tipo di ogni colonna sia impostato correttamente: testo, data, numero intero, ecc. Ad esempio:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * Nella sezione **[!UICONTROL Name of the file to load]** , seleziona **[!UICONTROL Upload a file from the local machine]** e lascia vuoto il campo. Ogni volta che viene creato un nuovo flusso di lavoro da questo modello, puoi specificare qui il file desiderato, purché corrisponda alla struttura definita.

      Puoi utilizzare una qualsiasi delle opzioni ma devi modificare di conseguenza il modello. Ad esempio, se selezioni **[!UICONTROL Specified in the transition]**, puoi aggiungere un’attività **[!UICONTROL File Transfer]** prima di recuperare il file da importare da un server FTP/SFTP. Con la connessione S3 o SFTP, puoi anche importare i dati dei segmenti in Adobe Campaign con Adobe Real-time Customer Data Platform. Per ulteriori informazioni, consulta questa [documentazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

      ![](assets/import_template_example1.png)

1. Configura l&#39;attività **[!UICONTROL Enrichment]** . Lo scopo di questa attività in questo contesto è quello di identificare i dati in arrivo.

   * Nella scheda **[!UICONTROL Enrichment]** , seleziona **[!UICONTROL Add data]** e definisci un collegamento tra i dati importati e la dimensione di targeting dei destinatari. In questo esempio, il campo personalizzato **ID CRM** viene utilizzato per creare la condizione di unione. Utilizzare il campo o la combinazione di campi necessari, purché sia possibile identificare record univoci.
   * Nella scheda **[!UICONTROL Reconciliation]** , lascia deselezionata l’opzione **[!UICONTROL Identify the document from the working data]** .

   ![](assets/import_template_example2.png)

1. Configura l’attività **[!UICONTROL Split]** per recuperare i destinatari riconciliati in una transizione e i destinatari che non possono essere riconciliati ma che dispongono di dati sufficienti in una seconda transizione.

   La transizione con i destinatari riconciliati può quindi essere utilizzata per aggiornare il database. La transizione con destinatari sconosciuti può quindi essere utilizzata per creare nuove voci dei destinatari nel database se nel file è disponibile un set minimo di informazioni.

   I destinatari che non possono essere riconciliati e che non dispongono di abbastanza dati vengono selezionati in una transizione in uscita di complemento e possono essere esportati in un file separato o semplicemente ignorati.

   * Nella scheda **[!UICONTROL General]** dell’attività, seleziona **[!UICONTROL Use the additional data only]** come impostazione di filtro e assicurati che **[!UICONTROL Targeting dimension]** sia impostato automaticamente su **[!UICONTROL Enrichment]**.

      Seleziona l&#39;opzione **[!UICONTROL Generate complement]** per vedere se non è possibile inserire alcun record nel database. Se necessario, puoi quindi applicare un ulteriore trattamento ai dati complementari: esportazione di file, aggiornamento di elenchi, ecc.

   * Nel primo sottoinsieme della scheda **[!UICONTROL Subsets]** , aggiungi una condizione di filtro al gruppo in entrata per selezionare solo i record per i quali la chiave primaria del destinatario non è uguale a 0. In questo modo, i dati del file riconciliati con i destinatari del database vengono selezionati in quel sottoinsieme.

      ![](assets/import_template_example3.png)

   * Aggiungi un secondo sottoinsieme che seleziona record non riconciliati con dati sufficienti per essere inseriti nel database. Ad esempio: indirizzo e-mail, nome e cognome.

      I sottoinsiemi vengono elaborati nell’ordine di creazione, il che significa che quando questo secondo sottoinsieme viene elaborato, tutti i record già esistenti nel database vengono già selezionati nel primo sottoinsieme.

      ![](assets/import_template_example3_2.png)

   * Tutti i record non selezionati nei primi due sottoinsiemi vengono selezionati in **[!UICONTROL Complement]**.

1. Configura l’attività **[!UICONTROL Update data]** situata dopo la prima transizione in uscita dell’attività **[!UICONTROL Split]** configurata in precedenza.

   * Seleziona **[!UICONTROL Update]** come **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo i destinatari già presenti nel database.
   * Nella sezione **[!UICONTROL Record identification]** , seleziona **[!UICONTROL Using reconciliation keys]** e definisci una chiave tra la dimensione di targeting e il collegamento creato in **[!UICONTROL Enrichment]**. In questo esempio viene utilizzato il campo personalizzato **ID CRM** .
   * Nella sezione **[!UICONTROL Fields to update]** , indica i campi della dimensione destinatari da aggiornare con il valore della colonna corrispondente dal file . Se i nomi delle colonne del file sono identici o quasi identici ai nomi dei campi della dimensione destinatari, è possibile utilizzare il pulsante bacchetta magica per associare automaticamente i diversi campi.

      ![](assets/import_template_example6.png)

1. Configura l’attività **[!UICONTROL Deduplication]** situata dopo la transizione contenente i destinatari non riconciliati:

   * Seleziona **[!UICONTROL Edit configuration]** e imposta la dimensione di targeting sullo schema temporaneo generato dall&#39;attività **[!UICONTROL Enrichment]** del flusso di lavoro.

      ![](assets/import_template_example4.png)

   * In questo esempio, il campo e-mail viene utilizzato per trovare profili univoci. Puoi utilizzare qualsiasi campo di cui sei sicuro che sia compilato e parte di una combinazione unica.
   * Nella schermata **[!UICONTROL Deduplication method]** , seleziona **[!UICONTROL Advanced parameters]** e seleziona l’opzione **[!UICONTROL Disable automatic filtering of 0 ID records]** per assicurarti che i record con una chiave primaria uguale a 0 (tutti i record di questa transizione) non siano esclusi.

   ![](assets/import_template_example7.png)

1. Configura l&#39;attività **[!UICONTROL Update data]** situata dopo l&#39;attività **[!UICONTROL Deduplication]** configurata in precedenza.

   * Seleziona **[!UICONTROL Insert]** come **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo i destinatari non presenti nel database.
   * Nella sezione **[!UICONTROL Record identification]** , seleziona **[!UICONTROL Directly using the targeting dimension]** e scegli la dimensione **[!UICONTROL Recipients]**.
   * Nella sezione **[!UICONTROL Fields to update]** , indica i campi della dimensione destinatari da aggiornare con il valore della colonna corrispondente dal file . Se i nomi delle colonne del file sono identici o quasi identici ai nomi dei campi della dimensione destinatari, è possibile utilizzare il pulsante bacchetta magica per associare automaticamente i diversi campi.

      ![](assets/import_template_example8.png)

1. Dopo la terza transizione dell&#39;attività **[!UICONTROL Split]** , aggiungi un&#39;attività **[!UICONTROL Data extraction (file)]** e un&#39;attività **[!UICONTROL File transfer]** se desideri tenere traccia dei dati non inseriti nel database. Configura queste attività per esportare la colonna necessaria e per trasferire il file su un server FTP o SFTP in cui puoi recuperarlo.
1. Aggiungi un’attività **[!UICONTROL End]** e salva il modello di flusso di lavoro.

Ora è possibile utilizzare il modello ed è disponibile per ogni nuovo flusso di lavoro. È quindi necessario specificare il file contenente i dati da importare nell’attività **[!UICONTROL Data loading (file)]**.

![](assets/import_template_example9.png)
