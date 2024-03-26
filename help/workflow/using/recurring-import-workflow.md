---
product: campaign
title: Impostare un’importazione ricorrente
description: Scopri come configurare un modello di flusso di lavoro per le importazioni ricorrenti
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Data Management
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 1%

---

# Impostare un flusso di lavoro di importazione ricorrente {#setting-up-a-recurring-import}



L’utilizzo di un modello di flusso di lavoro è una best practice se devi importare regolarmente file con la stessa struttura.

Questo esempio mostra come preimpostare un flusso di lavoro che può essere riutilizzato per importare nel database Adobe Campaign i profili provenienti da un sistema di gestione delle relazioni con i clienti. Per ulteriori informazioni su tutte le possibili impostazioni per ciascuna attività, consulta questa [sezione](about-activities.md).

1. Crea un nuovo modello di flusso di lavoro da **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Aggiungi le seguenti attività:

   * **[!UICONTROL Data loading (file)]**: definisci la struttura prevista del file contenente i dati da importare.
   * **[!UICONTROL Enrichment]**: riconciliare i dati importati con i dati del database.
   * **[!UICONTROL Split]**: crea filtri per elaborare i record in modo diverso a seconda che possano essere riconciliati o meno.
   * **[!UICONTROL Deduplication]**: deduplica i dati dal file in arrivo prima che vengano inseriti nel database.
   * **[!UICONTROL Update data]**: aggiorna il database con i profili importati.

   ![](assets/import_template_example0.png)

1. Configurare **[!UICONTROL Data Loading (file)]** attività:

   * Definisci la struttura prevista caricando un file di esempio. Il file di esempio deve contenere solo poche righe, ma tutte le colonne necessarie per l’importazione. Controlla e modifica il formato del file per assicurarti che il tipo di ciascuna colonna sia impostato correttamente: testo, data, numero intero, ecc. Ad esempio:

     ```
     lastname;firstname;birthdate;email;crmID
     Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
     ```

   * In **[!UICONTROL Name of the file to load]** sezione, seleziona **[!UICONTROL Upload a file from the local machine]** e lasciare vuoto il campo. Ogni volta che viene creato un nuovo flusso di lavoro da questo modello, è possibile specificare il file desiderato, purché corrisponda alla struttura definita.

     Puoi utilizzare una qualsiasi delle opzioni, ma devi modificare il modello di conseguenza. Ad esempio, se selezioni **[!UICONTROL Specified in the transition]**, è possibile aggiungere una **[!UICONTROL File Transfer]** prima di recuperare il file da importare da un server FTP/SFTP. Con la connessione S3 o SFTP, puoi anche importare i dati dei segmenti in Adobe Campaign con Adobe Real-time Customer Data Platform. Per ulteriori informazioni, consulta questa [documentazione](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

     ![](assets/import_template_example1.png)

1. Configurare **[!UICONTROL Enrichment]** attività. Lo scopo di questa attività in questo contesto è identificare i dati in arrivo.

   * In **[!UICONTROL Enrichment]** , seleziona **[!UICONTROL Add data]** e definisci un collegamento tra i dati importati e la dimensione di targeting dei destinatari. In questo esempio, la proprietà **ID CRM** per creare la condizione di unione viene utilizzato un campo personalizzato. Utilizzare il campo o la combinazione di campi necessari per identificare record univoci.
   * In **[!UICONTROL Reconciliation]** , lasciare **[!UICONTROL Identify the document from the working data]** deselezionata.

   ![](assets/import_template_example2.png)

1. Configurare **[!UICONTROL Split]** attività per recuperare i destinatari riconciliati in una transizione e i destinatari che non è stato possibile riconciliare ma che dispongono di un numero sufficiente di dati in una seconda transizione.

   La transizione con i destinatari riconciliati può quindi essere utilizzata per aggiornare il database. La transizione con destinatari sconosciuti può quindi essere utilizzata per creare nuove voci di destinatari nel database, se nel file è disponibile un set minimo di informazioni.

   I destinatari che non possono essere riconciliati e che non dispongono di un numero sufficiente di dati vengono selezionati in una transizione in uscita complementare e possono essere esportati in un file separato o semplicemente ignorati.

   * In **[!UICONTROL General]** scheda dell’attività, seleziona **[!UICONTROL Use the additional data only]** come impostazione di filtro e assicurarsi che il **[!UICONTROL Targeting dimension]** è impostato automaticamente su **[!UICONTROL Enrichment]**.

     Controlla la **[!UICONTROL Generate complement]** per verificare se non è possibile inserire un record nel database. Se necessario, puoi applicare ulteriori elaborazioni ai dati complementari: esportazione di file, aggiornamento di elenchi, ecc.

   * Nel primo sottoinsieme del **[!UICONTROL Subsets]** , aggiungi una condizione di filtro al gruppo in entrata per selezionare solo i record per i quali la chiave primaria del destinatario non è uguale a 0. In questo modo, i dati del file riconciliati con i destinatari del database vengono selezionati in tale sottoinsieme.

     ![](assets/import_template_example3.png)

   * Aggiungere un secondo sottoinsieme per selezionare record non riconciliati con un numero di dati sufficiente per essere inseriti nel database. Ad esempio: indirizzo e-mail, nome e cognome.

     I sottoinsiemi vengono elaborati in base al relativo ordine di creazione, il che significa che quando viene elaborato questo secondo sottoinsieme, tutti i record già presenti nel database vengono già selezionati nel primo sottoinsieme.

     ![](assets/import_template_example3_2.png)

   * Tutti i record non selezionati nei primi due sottoinsiemi vengono selezionati nel **[!UICONTROL Complement]**.

1. Configurare **[!UICONTROL Update data]** attività situata dopo la prima transizione in uscita del **[!UICONTROL Split]** attività configurata in precedenza.

   * Seleziona **[!UICONTROL Update]** as **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo i destinatari già presenti nel database.
   * In **[!UICONTROL Record identification]** sezione, seleziona **[!UICONTROL Using reconciliation keys]** e definisci una chiave tra la dimensione di targeting e il collegamento creato in **[!UICONTROL Enrichment]**. In questo esempio, la proprietà **ID CRM** viene utilizzato un campo personalizzato.
   * In **[!UICONTROL Fields to update]** sezione, indica i campi della dimensione destinatari da aggiornare con il valore della colonna corrispondente del file. Se i nomi delle colonne dei file sono identici o quasi identici ai nomi dei campi dimensione dei destinatari, puoi utilizzare il pulsante bacchetta magica per far corrispondere automaticamente i diversi campi.

     ![](assets/import_template_example6.png)

1. Configurare **[!UICONTROL Deduplication]** attività situata dopo la transizione contenente destinatari non riconciliati:

   * Seleziona **[!UICONTROL Edit configuration]** e imposta la dimensione di targeting sullo schema temporaneo generato dal **[!UICONTROL Enrichment]** attività del flusso di lavoro.

     ![](assets/import_template_example4.png)

   * In questo esempio, il campo e-mail viene utilizzato per trovare profili univoci. Puoi utilizzare qualsiasi campo che sei sicuro di avere compilato e che fa parte di una combinazione univoca.
   * In **[!UICONTROL Deduplication method]** schermata, seleziona **[!UICONTROL Advanced parameters]** e controlla **[!UICONTROL Disable automatic filtering of 0 ID records]** per assicurarsi che i record con una chiave primaria uguale a 0 (che deve essere costituita da tutti i record di questa transizione) non vengano esclusi.

   ![](assets/import_template_example7.png)

1. Configurare **[!UICONTROL Update data]** attività situata dopo il **[!UICONTROL Deduplication]** attività configurata in precedenza.

   * Seleziona **[!UICONTROL Insert]** as **[!UICONTROL Operation type]** poiché la transizione in entrata contiene solo destinatari non presenti nel database.
   * In **[!UICONTROL Record identification]** sezione, seleziona **[!UICONTROL Directly using the targeting dimension]** e scegli la **[!UICONTROL Recipients]** dimensione.
   * In **[!UICONTROL Fields to update]** sezione, indica i campi della dimensione destinatari da aggiornare con il valore della colonna corrispondente del file. Se i nomi delle colonne dei file sono identici o quasi identici ai nomi dei campi dimensione dei destinatari, puoi utilizzare il pulsante bacchetta magica per far corrispondere automaticamente i diversi campi.

     ![](assets/import_template_example8.png)

1. Dopo la terza transizione del **[!UICONTROL Split]** attività, aggiungi un **[!UICONTROL Data extraction (file)]** attività e un **[!UICONTROL File transfer]** se desideri tenere traccia dei dati non inseriti nel database. Configura queste attività per esportare la colonna necessaria e trasferire il file su un server FTP o SFTP dove puoi recuperarlo.
1. Aggiungi un **[!UICONTROL End]** e salva il modello di workflow.

Ora è possibile utilizzare il modello, disponibile per ogni nuovo flusso di lavoro. È sufficiente quindi specificare il file contenente i dati da importare nel **[!UICONTROL Data loading (file)]** attività.

![](assets/import_template_example9.png)
