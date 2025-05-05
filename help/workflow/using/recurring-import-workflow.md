---
product: campaign
title: Impostare un’importazione ricorrente
description: Scopri come configurare un modello di flusso di lavoro per le importazioni ricorrenti
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Impostare un flusso di lavoro di importazione ricorrente {#setting-up-a-recurring-import}



L’utilizzo di un modello di flusso di lavoro è una best practice se devi importare regolarmente file con la stessa struttura.

Questo esempio mostra come preimpostare un flusso di lavoro che può essere riutilizzato per importare nel database Adobe Campaign i profili provenienti da un sistema di gestione delle relazioni con i clienti. Per ulteriori informazioni su tutte le possibili impostazioni per ogni attività, consulta questa [sezione](about-activities.md).

1. Crea un nuovo modello di workflow da **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Aggiungi le seguenti attività:

   * **[!UICONTROL Data loading (file)]**: definire la struttura prevista del file contenente i dati da importare.
   * **[!UICONTROL Enrichment]**: riconciliare i dati importati con i dati del database.
   * **[!UICONTROL Split]**: creare filtri per elaborare i record in modo diverso a seconda che siano stati riconciliati o meno.
   * **[!UICONTROL Deduplication]**: deduplicare i dati dal file in ingresso prima che vengano inseriti nel database.
   * **[!UICONTROL Update data]**: aggiornare il database con i profili importati.

   ![](assets/import_template_example0.png)

1. Configurare l&#39;attività **[!UICONTROL Data Loading (file)]**:

   * Definisci la struttura prevista caricando un file di esempio. Il file di esempio deve contenere solo poche righe, ma tutte le colonne necessarie per l’importazione. Controlla e modifica il formato del file per assicurarti che il tipo di ciascuna colonna sia impostato correttamente: testo, data, numero intero, ecc. Ad esempio:

     ```
     lastname;firstname;birthdate;email;crmID
     Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
     ```

   * Nella sezione **[!UICONTROL Name of the file to load]**, selezionare **[!UICONTROL Upload a file from the local machine]** e lasciare vuoto il campo. Ogni volta che viene creato un nuovo flusso di lavoro da questo modello, è possibile specificare il file desiderato, purché corrisponda alla struttura definita.

     Puoi utilizzare una qualsiasi delle opzioni, ma devi modificare il modello di conseguenza. Ad esempio, se selezioni **[!UICONTROL Specified in the transition]**, puoi aggiungere un&#39;attività **[!UICONTROL File Transfer]** prima di recuperare il file da importare da un server FTP/SFTP. Con la connessione S3 o SFTP, puoi anche importare i dati dei segmenti in Adobe Campaign con Adobe Real-time Customer Data Platform. Per ulteriori informazioni, consulta questa [documentazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=it).

     ![](assets/import_template_example1.png)

1. Configurare l&#39;attività **[!UICONTROL Enrichment]**. Lo scopo di questa attività in questo contesto è identificare i dati in arrivo.

   * Nella scheda **[!UICONTROL Enrichment]**, seleziona **[!UICONTROL Add data]** e definisci un collegamento tra i dati importati e la dimensione di targeting dei destinatari. In questo esempio, per creare la condizione di unione viene utilizzato il campo personalizzato **ID CRM**. Utilizzare il campo o la combinazione di campi necessari per identificare record univoci.
   * Nella scheda **[!UICONTROL Reconciliation]**, lasciare deselezionata l&#39;opzione **[!UICONTROL Identify the document from the working data]**.

   ![](assets/import_template_example2.png)

1. Configurare l&#39;attività **[!UICONTROL Split]** per recuperare i destinatari riconciliati in una transizione e i destinatari che non è stato possibile riconciliare ma che dispongono di un numero sufficiente di dati in una seconda transizione.

   La transizione con i destinatari riconciliati può quindi essere utilizzata per aggiornare il database. La transizione con destinatari sconosciuti può quindi essere utilizzata per creare nuove voci di destinatari nel database, se nel file è disponibile un set minimo di informazioni.

   I destinatari che non possono essere riconciliati e che non dispongono di un numero sufficiente di dati vengono selezionati in una transizione in uscita complementare e possono essere esportati in un file separato o semplicemente ignorati.

   * Nella scheda **[!UICONTROL General]** dell&#39;attività, selezionare **[!UICONTROL Use the additional data only]** come impostazione di filtro e assicurarsi che **[!UICONTROL Targeting dimension]** sia impostato automaticamente su **[!UICONTROL Enrichment]**.

     Selezionare l&#39;opzione **[!UICONTROL Generate complement]** per verificare se non è possibile inserire un record nel database. Se necessario, puoi applicare ulteriori elaborazioni ai dati complementari: esportazione di file, aggiornamento di elenchi, ecc.

   * Nel primo sottoinsieme della scheda **[!UICONTROL Subsets]**, aggiungere una condizione di filtro al gruppo in ingresso per selezionare solo i record per i quali la chiave primaria del destinatario non è uguale a 0. In questo modo, i dati del file riconciliati con i destinatari del database vengono selezionati in tale sottoinsieme.

     ![](assets/import_template_example3.png)

   * Aggiungere un secondo sottoinsieme per selezionare record non riconciliati con un numero di dati sufficiente per essere inseriti nel database. Ad esempio: indirizzo e-mail, nome e cognome.

     I sottoinsiemi vengono elaborati in base al relativo ordine di creazione, il che significa che quando viene elaborato questo secondo sottoinsieme, tutti i record già presenti nel database vengono già selezionati nel primo sottoinsieme.

     ![](assets/import_template_example3_2.png)

   * Tutti i record non selezionati nei primi due sottoinsiemi vengono selezionati in **[!UICONTROL Complement]**.

1. Configurare l&#39;attività **[!UICONTROL Update data]** che si trova dopo la prima transizione in uscita dell&#39;attività **[!UICONTROL Split]** configurata in precedenza.

   * Selezionare **[!UICONTROL Update]** come **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo i destinatari già presenti nel database.
   * Nella sezione **[!UICONTROL Record identification]** selezionare **[!UICONTROL Using reconciliation keys]** e definire una chiave tra la dimensione di targeting e il collegamento creato in **[!UICONTROL Enrichment]**. In questo esempio viene utilizzato il campo personalizzato **ID CRM**.
   * Nella sezione **[!UICONTROL Fields to update]**, indica i campi della dimensione destinatari da aggiornare con il valore della colonna corrispondente del file. Se i nomi delle colonne dei file sono identici o quasi identici ai nomi dei campi dimensione dei destinatari, puoi utilizzare il pulsante bacchetta magica per far corrispondere automaticamente i diversi campi.

     ![](assets/import_template_example6.png)

1. Configura l&#39;attività **[!UICONTROL Deduplication]** che si trova dopo la transizione contenente i destinatari non riconciliati:

   * Selezionare **[!UICONTROL Edit configuration]** e impostare la dimensione di targeting sullo schema temporaneo generato dall&#39;attività **[!UICONTROL Enrichment]** del flusso di lavoro.

     ![](assets/import_template_example4.png)

   * In questo esempio, il campo e-mail viene utilizzato per trovare profili univoci. Puoi utilizzare qualsiasi campo che sei sicuro di avere compilato e che fa parte di una combinazione univoca.
   * Nella schermata **[!UICONTROL Deduplication method]**, selezionare **[!UICONTROL Advanced parameters]** e selezionare l&#39;opzione **[!UICONTROL Disable automatic filtering of 0 ID records]** per assicurarsi che i record con una chiave primaria uguale a 0 (che dovrebbe essere tutti i record di questa transizione) non siano esclusi.

   ![](assets/import_template_example7.png)

1. Configurare l&#39;attività **[!UICONTROL Update data]** che si trova dopo l&#39;attività **[!UICONTROL Deduplication]** configurata in precedenza.

   * Selezionare **[!UICONTROL Insert]** come **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo destinatari non presenti nel database.
   * Nella sezione **[!UICONTROL Record identification]**, selezionare **[!UICONTROL Directly using the targeting dimension]** e scegliere la dimensione **[!UICONTROL Recipients]**.
   * Nella sezione **[!UICONTROL Fields to update]**, indica i campi della dimensione destinatari da aggiornare con il valore della colonna corrispondente del file. Se i nomi delle colonne dei file sono identici o quasi identici ai nomi dei campi dimensione dei destinatari, puoi utilizzare il pulsante bacchetta magica per far corrispondere automaticamente i diversi campi.

     ![](assets/import_template_example8.png)

1. Dopo la terza transizione dell&#39;attività **[!UICONTROL Split]**, aggiungere un&#39;attività **[!UICONTROL Data extraction (file)]** e un&#39;attività **[!UICONTROL File transfer]** per tenere traccia dei dati non inseriti nel database. Configura queste attività per esportare la colonna necessaria e trasferire il file su un server FTP o SFTP dove puoi recuperarlo.
1. Aggiungi un&#39;attività **[!UICONTROL End]** e salva il modello di flusso di lavoro.

Ora è possibile utilizzare il modello, disponibile per ogni nuovo flusso di lavoro. È sufficiente quindi specificare il file contenente i dati da importare nell&#39;attività **[!UICONTROL Data loading (file)]**.

![](assets/import_template_example9.png)
