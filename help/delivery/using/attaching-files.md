---
product: campaign
title: File allegati
description: File allegati
feature: Email
exl-id: db65e83e-276f-4163-98c3-3658a48acffc
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 1%

---

# Allegare file a un’e-mail{#attaching-files}

![](../../assets/common.svg)

## Informazioni sugli allegati e-mail {#about-email-attachments}

Puoi allegare uno o più file a una consegna e-mail.

>[!NOTE]
>
>Per evitare problemi di prestazioni, si consiglia di non includere più di un allegato per e-mail. La soglia consigliata può essere configurata da [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Esistono due casi possibili:

* Seleziona un file e allegalo alla consegna così com’è.
* Personalizza il contenuto dell’allegato per ciascun destinatario. In questo caso, devi creare un **allegato calcolato**: il nome dell’allegato viene calcolato al momento della consegna per ciascun messaggio a seconda del destinatario. Il contenuto può anche essere personalizzato e convertito in formato PDF al momento della consegna, se disponi dei seguenti **Stampa digitale variabile** opzione .

>[!NOTE]
>
>Questo tipo di configurazione viene generalmente eseguito nei modelli di consegna. Per ulteriori informazioni, consulta [Informazioni sui modelli](about-templates.md).

## Allega un file locale {#attaching-a-local-file}

Per allegare un file locale a una consegna, segui la procedura seguente.

>[!NOTE]
>
>Puoi allegare più file a una consegna. Gli allegati possono essere in qualsiasi formato, incluso in formato compresso.

1. Fai clic sul collegamento **[!UICONTROL Attachments]**.
1. Fai clic sul pulsante **[!UICONTROL Add]**.
1. Fai clic su **[!UICONTROL File...]** per selezionare il file da allegare alla consegna.

   ![](assets/s_ncs_user_wizard_email_attachement.png)

Puoi anche trascinare e rilasciare direttamente il file nella consegna **[!UICONTROL Attachments]** oppure utilizza il campo **[!UICONTROL Attach]** icona dalla barra degli strumenti della procedura guidata di consegna,

![](assets/s_ncs_user_wizard_add_file_ico.png)

Una volta selezionato, il file viene immediatamente caricato sul server per essere disponibile al momento della consegna. È elencato nella **[!UICONTROL Attachments]** campo .

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Creazione di un allegato calcolato {#creating-a-calculated-attachment}

Quando si crea un allegato calcolato, il nome dell&#39;allegato può essere calcolato durante l&#39;analisi o la consegna di ciascun messaggio e può dipendere dal destinatario. Può anche essere personalizzato e convertito in PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Per creare un allegato personalizzato, effettua le seguenti operazioni:

1. Fai clic sul collegamento **[!UICONTROL Attachments]**.
1. Fai clic sul pulsante **[!UICONTROL Add]** quindi seleziona **[!UICONTROL Calculated attachment]**.
1. Seleziona il tipo di calcolo dal **[!UICONTROL Type]** elenco a discesa:

![](assets/s_ncs_user_wizard_email01_136.png)

Sono disponibili le seguenti opzioni:

* **Nome file specificato durante la creazione del modello di consegna**
* **Il contenuto del file viene personalizzato e convertito in PDF durante la consegna di ciascun messaggio**
* **Il nome file viene calcolato durante l’analisi della consegna (non può dipendere dal profilo del destinatario)**
* **Il nome file viene calcolato al momento della consegna per ciascun destinatario (può dipendere dal destinatario)**

### Collegamento di un file locale {#attach-a-local-file}

Se l&#39;allegato è un file locale, selezionare l&#39;opzione: **[!UICONTROL File name is specified when creating the delivery template]**. Il file viene selezionato localmente e caricato sul server. Segui i passaggi seguenti:

1. Seleziona il file da caricare nella **[!UICONTROL Local file]** campo .
1. Se necessario, specifica l’etichetta. L’etichetta sostituisce il nome del file quando viene visualizzato nei sistemi di messaggistica. Se non viene specificato nulla, il nome del file viene utilizzato per impostazione predefinita.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Se necessario, seleziona **[!UICONTROL Upload file on the server]**, quindi fai clic su **[!UICONTROL Update on server]** per avviare il trasferimento.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

Il file è quindi disponibile sul server da allegare alle diverse consegne create da questo modello.

### Collegamento di un messaggio personalizzato {#attach-a-personalized-message}

Opzione **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** ti consente di selezionare un file con campi di personalizzazione, ad esempio il cognome e il nome del destinatario desiderato.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Per questo tipo di allegato, applicare i seguenti passaggi di configurazione:

1. Seleziona il file da caricare.
1. Se necessario, specifica l’etichetta.
1. Seleziona **[!UICONTROL Upload file on the server]**, quindi fai clic su **[!UICONTROL Update on server]** per avviare il trasferimento.
1. Puoi visualizzare un’anteprima. A questo scopo, seleziona un destinatario.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analizza la consegna e quindi avviala.

   Ogni destinatario riceve un PDF personalizzato allegato alla consegna.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

>[!NOTE]
>
>Per evitare problemi di prestazioni, se includi al volo immagini scaricate da un URL personalizzato come allegato, ciascuna dimensione immagine non deve superare i 100.000 byte per impostazione predefinita. Questa soglia consigliata può essere configurata da [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

### Allega un file calcolato {#attach-a-calculated-file}

È possibile calcolare il nome dell&#39;allegato durante la preparazione della consegna. A questo scopo, seleziona l’opzione **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**.

>[!NOTE]
>
>Questa opzione viene utilizzata solo quando la consegna viene inviata da un processo esterno o da un flusso di lavoro.

1. Specificare l&#39;etichetta da applicare all&#39;allegato.
1. Specificare il percorso di accesso del file e il nome esatto nella finestra di definizione.

   >[!IMPORTANT]
   >
   >Il file deve essere presente sul server.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analizza e quindi avvia la consegna.

   Il calcolo del nome del file può essere visualizzato nel registro di analisi.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Allega un file personalizzato {#attach-a-personalized-file}

Quando si seleziona l&#39;allegato, è possibile scegliere l&#39;opzione **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. Puoi quindi mappare i dati di personalizzazione dei destinatari con il nome del file da inviare.

>[!NOTE]
>
>Questa opzione viene utilizzata solo quando la consegna viene inviata da un processo esterno o da un flusso di lavoro.

1. Specificare l&#39;etichetta da applicare all&#39;allegato.
1. Specificare il percorso di accesso del file e il nome esatto nella finestra di definizione. Se il nome del file è personalizzato, puoi utilizzare i campi di personalizzazione per i valori pertinenti.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >Il file deve essere presente sul server.

1. Analizza e quindi avvia la consegna.

   Nell&#39;esempio seguente, il file allegato è stato scelto in base al nome definito utilizzando i campi di unione.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Impostazioni allegato {#attachment-settings}

Per le prime due opzioni, puoi scegliere **[!UICONTROL Upload file on the server]** selezionando l’opzione appropriata. La **[!UICONTROL Update the file on the server]** link ti consente di iniziare a caricare.

![](assets/s_ncs_user_wizard_email01_137.png)

Un messaggio indica che il file è stato caricato sul server:

![](assets/s_ncs_user_wizard_email01_1371.png)

Per una modifica del file, viene visualizzato un messaggio di avviso:

![](assets/s_ncs_user_wizard_email01_1372.png)

La **[!UICONTROL Advanced]** La scheda ti consente di definire opzioni avanzate sui file allegati:

* Puoi definire le opzioni di filtro per evitare di inviare il file allegato a tutti i destinatari. Opzione **[!UICONTROL Enable filtering of recipients who will receive the attachment]** attiva un campo di input utilizzato per definire uno script di selezione del destinatario, che deve essere immesso in JavaScript.
* Puoi scrivere il nome del file per personalizzarlo.

   Inserisci il testo nella finestra e utilizza i campi di personalizzazione disponibili nell’elenco a discesa. Nell’esempio seguente, il nome del file è personalizzato per contenere la data odierna e il nome del destinatario.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
