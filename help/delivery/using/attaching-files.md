---
product: campaign
title: File allegati
description: File allegati
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email
exl-id: db65e83e-276f-4163-98c3-3658a48acffc
source-git-commit: 64a94982ea1eebc30c652e0025eb0aaa0eab1ce9
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 7%

---

# Allegare file a un messaggio e-mail{#attaching-files}

## Informazioni sugli allegati e-mail {#about-email-attachments}

Puoi allegare uno o più file a una consegna e-mail.

>[!NOTE]
>
>Per evitare problemi di prestazioni, si consiglia di non includere più di un allegato per e-mail. La soglia consigliata può essere configurata da [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Esistono due casi possibili:

* Seleziona un file e allegalo alla consegna così com’è.
* Personalizza il contenuto dell’allegato per ciascun destinatario. In questo caso, devi creare un’ **allegato calcolato**: il nome dell’allegato viene calcolato al momento della consegna per ogni messaggio, a seconda del destinatario. Il contenuto può anche essere personalizzato e convertito in formato PDF al momento della consegna, se disponi del **Stampa digitale variabile** opzione.

>[!NOTE]
>
>Questo tipo di configurazione viene generalmente eseguito nei modelli di consegna. Per ulteriori informazioni, consulta [Informazioni sui modelli](about-templates.md).

## Guardrail {#attachments-guardrails}

Per evitare problemi di prestazioni, le immagini incluse nelle e-mail non possono superare i 100 MB. Questo limite, impostato per impostazione predefinita, può essere modificato dal `NmsDelivery_MaxDownloadedImageSize` opzione. Tuttavia, Adobe consiglia vivamente di evitare le immagini di grandi dimensioni nelle consegne e-mail.

L&#39;Adobe consiglia inoltre di limitare le dimensioni e il numero di file allegati. Per impostazione predefinita, è possibile aggiungere un solo file come allegato a un messaggio e-mail. Questa soglia può essere configurata dal `NmsDelivery_MaxRecommendedAttachments` opzione.

Ulteriori informazioni in [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

## Allega un file locale {#attaching-a-local-file}

Per allegare un file locale a una consegna, segui i passaggi seguenti.

>[!NOTE]
>
>Puoi allegare diversi file a una consegna. Gli allegati possono essere in qualsiasi formato, incluso il formato compresso.

1. Fai clic sul collegamento **[!UICONTROL Attachments]**.
1. Fai clic sul pulsante **[!UICONTROL Add]**.
1. Clic **[!UICONTROL File...]** per selezionare il file da allegare alla consegna.

   ![](assets/s_ncs_user_wizard_email_attachement.png)

Puoi anche trascinare direttamente il file nella consegna **[!UICONTROL Attachments]** o utilizza il **[!UICONTROL Attach]** dalla barra degli strumenti della consegna guidata,

![](assets/s_ncs_user_wizard_add_file_ico.png)

Una volta selezionato, il file viene immediatamente caricato sul server per essere disponibile al momento della consegna. È elencato nel **[!UICONTROL Attachments]** campo.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Creazione di un allegato calcolato {#creating-a-calculated-attachment}

Quando si crea un allegato calcolato, il nome dell&#39;allegato può essere calcolato durante l&#39;analisi o la consegna di ogni messaggio e può dipendere dal destinatario. Può anche essere personalizzato e convertito in PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Per creare un allegato personalizzato, effettua le seguenti operazioni:

1. Fai clic sul collegamento **[!UICONTROL Attachments]**.
1. Fai clic su **[!UICONTROL Add]** , quindi seleziona **[!UICONTROL Calculated attachment]**.
1. Selezionare il tipo di calcolo dall&#39;elenco **[!UICONTROL Type]** elenco a discesa:

![](assets/s_ncs_user_wizard_email01_136.png)

Sono disponibili le seguenti opzioni:

* **Il nome del file viene specificato quando si crea il modello di consegna**
* **Il contenuto del file è personalizzato e convertito in PDF durante la consegna di ciascun messaggio**
* **Il nome del file viene calcolato durante l’analisi della consegna (non può dipendere dal profilo del destinatario)**
* **Il nome file viene calcolato al momento della consegna per ciascun destinatario (può dipendere dal destinatario)**

### Come allegare un file locale {#attach-a-local-file}

Se l&#39;allegato è un file locale, selezionare l&#39;opzione: **[!UICONTROL File name is specified when creating the delivery template]**. Il file viene selezionato localmente e caricato sul server. Segui i passaggi seguenti:

1. Seleziona il file da caricare in **[!UICONTROL Local file]** campo.
1. Se necessario, specifica l’etichetta. L’etichetta sostituisce il nome del file quando viene visualizzato nei sistemi di messaggistica. Se non viene specificato nulla, per impostazione predefinita viene utilizzato il nome del file.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Se necessario, selezionare **[!UICONTROL Upload file on the server]** e quindi fare clic su **[!UICONTROL Update on server]** per avviare il trasferimento.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

Il file è quindi disponibile sul server da allegare alle diverse consegne create da questo modello.

### Allegare un messaggio personalizzato {#attach-a-personalized-message}

Opzione **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** consente di selezionare un file con campi di personalizzazione, ad esempio cognome e nome del destinatario.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Per questo tipo di allegato, attenersi ai seguenti passaggi di configurazione:

1. Seleziona il file da caricare.
1. Se necessario, specifica l’etichetta.
1. Seleziona **[!UICONTROL Upload file on the server]** e quindi fare clic su **[!UICONTROL Update on server]** per avviare il trasferimento.
1. Puoi visualizzare un’anteprima. A questo scopo, seleziona un destinatario.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analizza la consegna e avviala.

   Ogni destinatario riceve un PDF personalizzato associato alla consegna.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)



### Allegare un file calcolato {#attach-a-calculated-file}

Puoi calcolare il nome dell’allegato durante la preparazione della consegna. A questo scopo, seleziona l’opzione **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**.

>[!NOTE]
>
>Questa opzione viene utilizzata solo quando la consegna viene inviata da un processo esterno o da un flusso di lavoro.

1. Specificare l&#39;etichetta da applicare all&#39;allegato.
1. Specificare il percorso di accesso del file e il nome esatto nella finestra di definizione.

   >[!IMPORTANT]
   >
   >Il file deve essere presente sul server.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analizza e avvia la consegna.

   Il calcolo del nome file può essere visualizzato nel registro di analisi.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Allegare un file personalizzato {#attach-a-personalized-file}

Quando selezionate l&#39;allegato, potete scegliere l&#39;opzione **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. Puoi quindi mappare i dati di personalizzazione del destinatario con il nome del file da inviare.

>[!NOTE]
>
>Questa opzione viene utilizzata solo quando la consegna viene inviata da un processo esterno o da un flusso di lavoro.

1. Specificare l&#39;etichetta da applicare all&#39;allegato.
1. Specificare il percorso di accesso del file e il nome esatto nella finestra di definizione. Se il nome del file è personalizzato, puoi utilizzare i campi di personalizzazione per i valori pertinenti.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >Il file deve essere presente sul server.

1. Analizza e avvia la consegna.

   Nell’esempio seguente, il file allegato è stato scelto in base al suo nome definito utilizzando i campi di unione.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Impostazioni degli allegati {#attachment-settings}

Per le prime due opzioni, puoi scegliere **[!UICONTROL Upload file on the server]** selezionando l’opzione appropriata. Il **[!UICONTROL Update the file on the server]** ti consente di iniziare a caricare.

![](assets/s_ncs_user_wizard_email01_137.png)

Un messaggio indica che il file è stato caricato sul server:

![](assets/s_ncs_user_wizard_email01_1371.png)

Per la modifica del file, viene visualizzato un messaggio di avvertenza:

![](assets/s_ncs_user_wizard_email01_1372.png)

Il **[!UICONTROL Advanced]** Questa scheda consente di definire le opzioni avanzate per i file allegati:

* Puoi definire le opzioni di filtro per evitare di inviare il file allegato a tutti i destinatari. Opzione **[!UICONTROL Enable filtering of recipients who will receive the attachment]** attiva un campo di input utilizzato per definire uno script di selezione dei destinatari, che deve essere immesso in JavaScript.
* Puoi scrivere nello script il nome del file per personalizzarlo.

  Inserisci il testo nella finestra e utilizza i campi di personalizzazione disponibili nell’elenco a discesa. Nell’esempio seguente, il nome del file viene personalizzato in modo da contenere la data odierna e il nome del destinatario.

  ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
