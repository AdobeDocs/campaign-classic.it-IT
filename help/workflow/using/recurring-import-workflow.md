---
solution: Campaign Classic
product: campaign
title: Impostazione di un'importazione ricorrente
description: Scoprite come configurare un modello di flusso di lavoro per le importazioni ricorrenti.
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---


# Impostazione di un flusso di lavoro di importazione periodico {#setting-up-a-recurring-import}

L’utilizzo di un modello di flusso di lavoro è una procedura consigliata se è necessario importare regolarmente file con la stessa struttura.

Questo esempio mostra come impostare un flusso di lavoro che può essere riutilizzato per importare profili provenienti da un CRM nel database Adobe Campaign . Per ulteriori informazioni su tutte le impostazioni possibili per ogni attività, fare riferimento alla sezione [](../../workflow/using/about-activities.md).

1. Create un nuovo modello di workflow da **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Aggiungete le seguenti attività:

   * **[!UICONTROL Data loading (file)]**: Definire la struttura prevista del file contenente i dati da importare.
   * **[!UICONTROL Enrichment]**: Riconciliare i dati importati con i dati del database.
   * **[!UICONTROL Split]**: Creare filtri per elaborare i record in modo diverso a seconda che possano essere riconciliati o meno.
   * **[!UICONTROL Deduplication]**: Deduplicare i dati dal file in entrata prima di essere inseriti nel database.
   * **[!UICONTROL Update data]**: Aggiornate il database con i profili importati.

   ![](assets/import_template_example0.png)

1. Configurare l&#39;attività **[!UICONTROL Data Loading (file)]**:

   * Definite la struttura prevista caricando un file di esempio. Il file di esempio deve contenere solo poche righe, ma tutte le colonne necessarie per l&#39;importazione. Controllare e modificare il formato del file per essere certi che il tipo di ogni colonna sia impostato correttamente: testo, data, numero intero, ecc. Ad esempio:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * Nella sezione **[!UICONTROL Name of the file to load]**, selezionare **[!UICONTROL Upload a file from the local machine]** e lasciare vuoto il campo. Ogni volta che viene creato un nuovo flusso di lavoro da questo modello, potete specificare qui il file desiderato, purché corrisponda alla struttura definita.

      Potete utilizzare una qualsiasi delle opzioni, ma dovete modificare di conseguenza il modello. Ad esempio, se selezionate **[!UICONTROL Specified in the transition]**, potete aggiungere un&#39;attività **[!UICONTROL File Transfer]** prima di recuperare il file da importare da un server FTP/SFTP. Con la connessione S3 o SFTP, puoi anche importare dati di segmento in  Adobe Campaign con  piattaforma dati cliente in tempo reale del Adobe. Per ulteriori informazioni, consultare la [documentazione](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

      ![](assets/import_template_example1.png)

1. Configurare l&#39;attività **[!UICONTROL Enrichment]**. Lo scopo di questa attività in questo contesto è identificare i dati in arrivo.

   * Nella scheda **[!UICONTROL Enrichment]**, selezionare **[!UICONTROL Add data]** e definire un collegamento tra i dati importati e la dimensione di targeting dei destinatari. In questo esempio, il campo personalizzato **ID CRM** viene utilizzato per creare la condizione di partecipazione. Utilizzare il campo o la combinazione di campi necessari, purché sia possibile identificare record univoci.
   * Nella scheda **[!UICONTROL Reconciliation]**, lasciare l&#39;opzione **[!UICONTROL Identify the document from the working data]** deselezionata.

   ![](assets/import_template_example2.png)

1. Configurate l&#39;attività **[!UICONTROL Split]** per recuperare i destinatari riconciliati in una transizione e i destinatari che non possono essere riconciliati ma che dispongono di dati sufficienti in una seconda transizione.

   La transizione con destinatari riconciliati può quindi essere utilizzata per aggiornare il database. La transizione con destinatari sconosciuti può quindi essere utilizzata per creare nuove voci di destinatari nel database se nel file è disponibile un insieme minimo di informazioni.

   I destinatari che non possono essere riconciliati e che non dispongono di dati sufficienti vengono selezionati in una transizione in uscita complementare e possono essere esportati in un file separato o semplicemente ignorati.

   * Nella scheda **[!UICONTROL General]** dell&#39;attività, selezionare **[!UICONTROL Use the additional data only]** come impostazione di filtraggio e assicurarsi che la **[!UICONTROL Targeting dimension]** sia impostata automaticamente su **[!UICONTROL Enrichment]**.

      Selezionare l&#39;opzione **[!UICONTROL Generate complement]** per verificare se non è possibile inserire alcun record nel database. Se necessario, è possibile applicare ulteriore elaborazione ai dati complementari: esportazione di file, aggiornamento di elenchi, ecc.

   * Nel primo sottoinsieme della scheda **[!UICONTROL Subsets]**, aggiungere una condizione di filtro nella popolazione in entrata per selezionare solo i record per i quali la chiave primaria del destinatario non è uguale a 0. In questo modo, i dati del file riconciliati con i destinatari del database vengono selezionati in tale sottoinsieme.

      ![](assets/import_template_example3.png)

   * Aggiungere un secondo sottoinsieme che selezioni record non riconciliati con dati sufficienti per essere inseriti nel database. Ad esempio: indirizzo e-mail, nome e cognome.

      I sottoinsiemi vengono elaborati nell&#39;ordine di creazione, il che significa che quando viene elaborato questo secondo sottoinsieme, tutti i record già presenti nel database sono già selezionati nel primo sottoinsieme.

      ![](assets/import_template_example3_2.png)

   * Tutti i record non selezionati nei primi due sottoinsiemi sono selezionati in **[!UICONTROL Complement]**.

1. Configurare l&#39;attività **[!UICONTROL Update data]** situata dopo la prima transizione in uscita dell&#39;attività **[!UICONTROL Split]** configurata in precedenza.

   * Selezionare **[!UICONTROL Update]** come **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo i destinatari già presenti nel database.
   * Nella sezione **[!UICONTROL Record identification]**, selezionare **[!UICONTROL Using reconciliation keys]** e definire una chiave tra la dimensione di targeting e il collegamento creato in **[!UICONTROL Enrichment]**. In questo esempio, viene utilizzato il campo personalizzato **ID CRM**.
   * Nella sezione **[!UICONTROL Fields to update]**, indicare i campi dalla dimensione destinatari da aggiornare con il valore della colonna corrispondente dal file. Se i nomi delle colonne del file sono identici o quasi identici ai nomi dei campi dimensione destinatari, è possibile utilizzare il pulsante bacchetta magica per far corrispondere automaticamente i diversi campi.

      ![](assets/import_template_example6.png)

1. Configurate l&#39;attività **[!UICONTROL Deduplication]** situata dopo la transizione contenente destinatari non riconciliati:

   * Selezionare **[!UICONTROL Edit configuration]** e impostare la dimensione di targeting sullo schema temporaneo generato dall&#39;attività **[!UICONTROL Enrichment]** del flusso di lavoro.

      ![](assets/import_template_example4.png)

   * In questo esempio, il campo e-mail viene utilizzato per trovare profili univoci. Potete utilizzare qualsiasi campo sicuramente compilato e parte di una combinazione univoca.
   * Nella schermata **[!UICONTROL Deduplication method]**, selezionare **[!UICONTROL Advanced parameters]** e selezionare l&#39;opzione **[!UICONTROL Disable automatic filtering of 0 ID records]** per assicurarsi che i record con una chiave primaria uguale a 0 (che devono essere tutti record di questa transizione) non siano esclusi.

   ![](assets/import_template_example7.png)

1. Configurate l&#39;attività **[!UICONTROL Update data]** situata dopo l&#39;attività **[!UICONTROL Deduplication]** configurata in precedenza.

   * Selezionare **[!UICONTROL Insert]** come **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo i destinatari non presenti nel database.
   * Nella sezione **[!UICONTROL Record identification]**, selezionare **[!UICONTROL Directly using the targeting dimension]** e scegliere la dimensione **[!UICONTROL Recipients]**.
   * Nella sezione **[!UICONTROL Fields to update]**, indicare i campi dalla dimensione destinatari da aggiornare con il valore della colonna corrispondente dal file. Se i nomi delle colonne del file sono identici o quasi identici ai nomi dei campi dimensione destinatari, è possibile utilizzare il pulsante bacchetta magica per far corrispondere automaticamente i diversi campi.

      ![](assets/import_template_example8.png)

1. Dopo la terza transizione dell&#39;attività **[!UICONTROL Split]**, aggiungete un&#39;attività **[!UICONTROL Data extraction (file)]** e un&#39;attività **[!UICONTROL File transfer]** se desiderate tenere traccia dei dati non inseriti nel database. Configurate queste attività per esportare la colonna desiderata e per trasferire il file su un server FTP o SFTP in cui potete recuperarlo.
1. Aggiungete un&#39;attività **[!UICONTROL End]** e salvate il modello di workflow.

Ora è possibile utilizzare il modello ed è disponibile per ogni nuovo flusso di lavoro. È quindi necessario specificare il file contenente i dati da importare nell&#39;attività **[!UICONTROL Data loading (file)]**.

![](assets/import_template_example9.png)
