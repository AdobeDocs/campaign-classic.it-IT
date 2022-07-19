---
product: campaign
title: Caricare i contenuti della consegna
description: Caricamento del contenuto di una consegna
feature: Workflows
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---

# Caricare i contenuti della consegna{#loading-delivery-content}

![](../../assets/v7-only.svg)

Se il contenuto di consegna è disponibile in un file HTML presente su server Amazon S3, FTP o SFTP, puoi facilmente caricare tale contenuto nelle consegne Adobe Campaign.

Per eseguire questa operazione:

1. Se non hai già definito una connessione tra Adobe Campaign e il server (S)FTP che ospita i file di contenuto, crea un nuovo account esterno S3, FTP o SFTP in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Specifica in questo account esterno l&#39;indirizzo e le credenziali utilizzati per stabilire la connessione al server S3 o (S)FTP.

   Ecco un esempio di account esterno S3:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Crea un nuovo flusso di lavoro, ad esempio da **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Aggiungi un **[!UICONTROL File transfer]** attività nel flusso di lavoro e configuralo specificando

   * Account esterno da utilizzare per la connessione al server S3 o (S)FTP.
   * Il percorso del file sul server S3 o (S)FTP.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Aggiungi un **[!UICONTROL Delivery]** e collegala alla transizione in uscita del **[!UICONTROL File transfer]** attività. Configura come segue:

   * Consegna: In base alle tue esigenze, può trattarsi di una consegna specifica già creata nel sistema o di una nuova consegna basata su un modello esistente.
   * Destinatari: In questo esempio, si considera che il target sia specificato nella consegna stessa.
   * Contenuto: Anche se il contenuto viene importato nell’attività precedente, seleziona **[!UICONTROL Specified in the delivery]**. Poiché il contenuto viene importato direttamente da un file presente in un server remoto, non dispone di un identificatore quando viene elaborato dal flusso di lavoro e non può essere identificato come proveniente dall’evento in entrata.
   * Azione da eseguire: Seleziona **[!UICONTROL Save]** per salvare la consegna e accedervi da **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** una volta eseguito il flusso di lavoro.

   ![](assets/delivery_loadcontent_activityexample.png)

1. In **[!UICONTROL Script]** della scheda **[!UICONTROL Delivery]** aggiungi il seguente comando per caricare il contenuto del file importato nella consegna:

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Salva ed esegui il flusso di lavoro. Viene creata una nuova consegna con il contenuto caricato in **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>Procedure consigliate e risoluzione dei problemi relativi all’utilizzo del server SFTP sono descritte in dettaglio [in questa pagina](../../platform/using/sftp-server-usage.md).
