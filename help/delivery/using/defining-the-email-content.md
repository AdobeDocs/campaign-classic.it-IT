---
product: campaign
title: Definizione del contenuto delle e-mail in Adobe Campaign Classic
description: Scopri come definire il contenuto delle e-mail quando utilizzi Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 1%

---

# Definizione del contenuto dell’e-mail {#defining-the-email-content}

## Mittente {#sender}

Per definire il nome e l’indirizzo del mittente che verranno visualizzati nell’intestazione dei messaggi inviati, fai clic sul collegamento **[!UICONTROL From]** .

![](assets/s_ncs_user_wizard_email02.png)

Questa finestra ti consente di inserire tutte le informazioni necessarie per creare le intestazioni dei messaggi e-mail. Queste informazioni possono essere personalizzate. A tal fine, utilizza i pulsanti a destra dei campi di input per inserire i campi di personalizzazione.

Per scoprire come inserire e utilizzare i campi di personalizzazione, consulta la sezione [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md) .

>[!NOTE]
>
>* Per impostazione predefinita, l’indirizzo del mittente viene utilizzato per le risposte.
>* I parametri di intestazione non devono essere vuoti. Per impostazione predefinita, contengono i valori immessi durante la configurazione della procedura guidata di distribuzione. Per ulteriori informazioni, consultare la [Guida all&#39;installazione](../../installation/using/deploying-an-instance.md).
>* L’indirizzo del mittente è obbligatorio per consentire l’invio di un’e-mail (standard RFC).
>* Adobe Campaign controlla la sintassi degli indirizzi e-mail immessi.


>[!IMPORTANT]
>
>Nel contesto dei controlli implementati dai provider di accesso a Internet (ISP) per combattere le e-mail non richieste (spam), l’Adobe consiglia di creare account e-mail corrispondenti agli indirizzi specificati per le consegne e le risposte. Rivolgiti all’amministratore del sistema di messaggistica.

## Oggetto del messaggio {#message-subject}

L’oggetto del messaggio viene configurato nel campo corrispondente. Puoi immetterlo direttamente nel campo oppure fare clic sul collegamento **[!UICONTROL Subject]** per immettere uno script. Il collegamento di personalizzazione ti consente di inserire i campi del database nell’oggetto.

>[!IMPORTANT]
>
>L’oggetto del messaggio è obbligatorio.

![](assets/s_ncs_user_wizard_email_object.png)

Il contenuto del campo viene sostituito dal valore nel profilo del destinatario al momento dell’invio del messaggio.

Ad esempio, nel messaggio precedente, l’oggetto del messaggio viene personalizzato per ciascun destinatario con i dati del suo profilo.

>[!NOTE]
>
>L’utilizzo dei campi di personalizzazione è presentato in [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md).

È inoltre possibile inserire emoticon nella riga dell&#39;oggetto tramite la finestra a comparsa **[!UICONTROL Insert emoticon]**.

## Contenuto del messaggio {#message-content}

>[!IMPORTANT]
>
>Per motivi di privacy, è consigliabile utilizzare HTTPS per tutte le risorse esterne.

Il contenuto del messaggio è definito nella sezione inferiore della finestra di configurazione della consegna.

I messaggi vengono inviati in formato HTML o testo per impostazione predefinita, in base alle preferenze del destinatario. È consigliabile creare contenuti in entrambi i formati per garantire la corretta visualizzazione dei messaggi in qualsiasi sistema di posta elettronica. Per ulteriori informazioni, consulta [Selezione dei formati dei messaggi](#selecting-message-formats).

* Per importare un contenuto HTML, utilizza il pulsante **[!UICONTROL Open]** . Puoi anche incollare il codice sorgente direttamente nella sottoscheda **[!UICONTROL Source]** .

   Se utilizzi [Digital Content Editor](../../web/using/about-campaign-html-editor.md) (DCE), fai riferimento a [Selezione di un modello di contenuto](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!IMPORTANT]
   >
   >Il contenuto HTML deve essere creato in precedenza e quindi importato in Adobe Campaign. L’editor HTML non è progettato per la creazione di contenuti.

   La sottoscheda **[!UICONTROL Preview]** ti consente di visualizzare il rendering di ciascun contenuto per un destinatario. I campi di personalizzazione e gli elementi condizionali del contenuto vengono sostituiti con le informazioni corrispondenti per il profilo selezionato.

   I pulsanti della barra degli strumenti consentono di accedere alle azioni standard e ai parametri di formattazione della pagina HTML.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   È possibile inserire immagini nei messaggi da un file locale o da una libreria di immagini in Adobe Campaign. A questo scopo, fai clic sull’icona **[!UICONTROL Image]** e seleziona l’opzione appropriata.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   Le immagini della libreria sono accessibili tramite la cartella **[!UICONTROL Resources>Online>Public resources]** nella struttura delle cartelle. Fai riferimento anche a [Aggiunta di immagini](#adding-images).

   L’ultimo pulsante nella barra degli strumenti ti consente di inserire campi di personalizzazione.

   >[!NOTE]
   >
   >L’utilizzo dei campi di personalizzazione è presentato in [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md).

   Le schede nella parte inferiore della pagina ti consentono di visualizzare il codice HTML della pagina che stai creando e di visualizzare il rendering del messaggio con la sua personalizzazione. Per avviare questa visualizzazione, fai clic su **[!UICONTROL Preview]** e seleziona un destinatario utilizzando il pulsante **[!UICONTROL Test personalization]** nella barra degli strumenti. Puoi selezionare un destinatario dalla destinazione o dalle destinazioni definite o scegliere un altro destinatario.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   Puoi convalidare il messaggio HTML. Puoi anche visualizzare il contenuto dell’intestazione dell’e-mail.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* Per importare un contenuto di testo, utilizza il pulsante **[!UICONTROL Open]** o la scheda **[!UICONTROL Text Content]** per immettere il contenuto del messaggio quando viene visualizzato in formato testo. Utilizza i pulsanti della barra degli strumenti per accedere alle azioni relative al contenuto. L’ultimo pulsante ti consente di inserire campi di personalizzazione.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   Per quanto riguarda il formato HTML, fai clic sulla scheda **[!UICONTROL Preview]** nella parte inferiore della pagina per visualizzare il rendering del messaggio con la relativa personalizzazione.

   ![](assets/s_ncs_user_wizard_email01_142.png)

<!--## Selecting message formats {#selecting-message-formats}

You can change the format of email messages sent. To do this, edit the delivery properties and click the **[!UICONTROL Delivery]** tab.

![](assets/s_ncs_user_wizard_email_param.png)

Select the format of the email in the lower section of the window:

* **[!UICONTROL Use recipient preferences]** (default mode)

  The message format is defined according to the data stored in the recipient profile and stored by default in the **[!UICONTROL email format]** field (@emailFormat). If a recipient wishes to receive messages in a certain format, this is the format sent. If the field is not filled in, a multipart-alternative message is sent (see below).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  The message contains both formats: text and HTML. The format displayed on reception depends on the configuration of the recipient's mail software (multipart-alternative).

  >[!IMPORTANT]
  >
  >This option includes both versions of the document. It therefore impacts the delivery rate, because the message size is greater.

* **[!UICONTROL Send all messages in text format]**

  The message is sent in text format. HTML format will not be sent, but used for the mirror page only when the recipient clicks on the message.-->

## Definizione del contenuto interattivo {#amp-for-email-format}

Adobe Campaign consente di provare il nuovo formato interattivo [AMP per e-mail](https://amp.dev/about/email/), che consente di inviare e-mail dinamiche a determinate condizioni.

Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/defining-interactive-content.md).

## Utilizzo della gestione dei contenuti {#using-content-management}

Puoi definire il contenuto della consegna utilizzando i moduli di gestione dei contenuti direttamente nella procedura guidata di consegna. A questo scopo, devi fare riferimento al modello di pubblicazione della gestione dei contenuti da utilizzare, nella scheda **[!UICONTROL Advanced]** delle proprietà di consegna.

![](assets/s_ncs_content_in_delivery.png)

Una scheda aggiuntiva consente di inserire contenuto che verrà integrato e formattato automaticamente in base alle regole di gestione dei contenuti.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla gestione dei contenuti in Adobe Campaign, consulta [questa sezione](../../delivery/using/about-content-management.md).

## Inserimento di emoticon {#inserting-emoticons}

Puoi inserire emoticon nel contenuto dell’e-mail.

1. Fai clic sull&#39;icona **[!UICONTROL Insert emoticon]** .
1. Seleziona un emoticon dalla finestra a comparsa.

   ![](assets/emoticon_4.png)

1. Al termine, fai clic sul pulsante **[!UICONTROL Close]** .

Per personalizzare l’elenco degli emoticon, consulta questa [pagina](../../delivery/using/customizing-emoticon-list.md).

## Aggiunta di immagini {#adding-images}

Le consegne e-mail in formato HTML possono contenere immagini. Dalla procedura guidata di consegna, puoi importare una pagina HTML contenente immagini o inserire immagini direttamente utilizzando l’editor HTML tramite l’icona **[!UICONTROL Image]** .

Le immagini possono essere:

* Un&#39;immagine locale o un&#39;immagine chiamata da un server
* Immagine memorizzata nella libreria delle risorse pubbliche di Adobe Campaign

   Le risorse pubbliche sono accessibili tramite il nodo **[!UICONTROL Resources > Online]** della gerarchia Adobe Campaign. Sono raggruppati in una libreria e possono essere inclusi nei messaggi e-mail, ma possono anche essere utilizzati per campagne, attività o per la gestione dei contenuti.

* Una risorsa condivisa con Adobe Experience Cloud. Fai riferimento a [questa sezione](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md).

>[!IMPORTANT]
>
>Per includere immagini nei messaggi e-mail tramite la procedura guidata di consegna, l’istanza di Adobe Campaign deve essere configurata per abilitare la gestione delle risorse pubbliche. Questa procedura può essere eseguita dalla procedura guidata di distribuzione. Per ulteriori informazioni sulla configurazione, consulta [questa sezione](../../installation/using/deploying-an-instance.md) .

La procedura guidata di consegna consente di aggiungere al contenuto dei messaggi le immagini locali o le immagini memorizzate nella libreria. A questo scopo, fai clic sul pulsante **[!UICONTROL Image]** nella barra degli strumenti del contenuto HTML.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>Affinché i destinatari possano visualizzare le immagini incluse nei messaggi ricevuti, questi messaggi devono essere disponibili su un server accessibile dall’esterno.

Per gestire le immagini tramite la procedura guidata di consegna:

1. Fai clic sull’icona **[!UICONTROL Tracking & Images]** nella barra degli strumenti.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. Seleziona **[!UICONTROL Upload images]** nella scheda **[!UICONTROL Images]** .
1. Puoi quindi scegliere se includere le immagini nel messaggio e-mail.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* Puoi caricare manualmente le immagini senza attendere la fase di analisi della consegna. A questo scopo, fai clic sul collegamento **[!UICONTROL Upload the images straightaway...]** .
* Puoi specificare un altro percorso per l’accesso alle immagini sul server di tracciamento. A questo scopo, inseriscilo nel campo **[!UICONTROL Images URL]** . Questo valore sostituisce il valore definito nei parametri della procedura guidata di installazione.

Quando apri un contenuto HTML con immagini incluse nella procedura guidata di consegna, un messaggio ti consente di caricare immediatamente le immagini, in base ai parametri di consegna.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>I percorsi di accesso all’immagine vengono modificati durante il caricamento manuale o durante l’invio dei messaggi.

### Invio di un messaggio con immagini {#sending-a-message-with-images}

>[!NOTE]
>
>Per evitare problemi di prestazioni, se includi al volo immagini scaricate da un URL personalizzato come [allegato](../../delivery/using/attaching-files.md), per impostazione predefinita ogni dimensione dell&#39;immagine non deve superare i 100.000 byte. Questa soglia consigliata può essere configurata dall&#39; [elenco delle opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md#delivery).

Ecco un esempio di consegna con quattro immagini:

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

Queste immagini provengono da una directory locale o da un sito Web, come è possibile verificare dalla scheda **[!UICONTROL Source]**.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

Fai clic sull’icona **[!UICONTROL Tracking & Images]** e quindi sulla scheda **[!UICONTROL Images]** per iniziare a rilevare le immagini nel messaggio.

Per ogni immagine rilevata, puoi visualizzarne lo stato:

* Se un&#39;immagine viene memorizzata localmente o in un altro server, anche se è visibile dall&#39;esterno (ad esempio su un sito Internet), verrà rilevata come **[!UICONTROL Not yet online]**.
* Le immagini vengono rilevate come **[!UICONTROL Already online]** se sono state caricate in precedenza durante la creazione di un’altra consegna.
* Nella procedura guidata di distribuzione puoi definire URL per i quali il rilevamento delle immagini non è abilitato: il caricamento di queste immagini sarà **[!UICONTROL Skipped]**.

>[!NOTE]
>
>Le immagini sono identificate dal relativo contenuto e non dai percorsi di accesso. Ciò significa che un&#39;immagine caricata in precedenza con un nome diverso o in una directory diversa verrà rilevata come **[!UICONTROL Already online]**.

Durante la fase di analisi, le immagini vengono caricate automaticamente sul server in modo che siano accessibili dall&#39;esterno, ad eccezione delle immagini locali che devono essere caricate in precedenza.

Puoi lavorare avanti e caricare le immagini in modo che possano essere visualizzate da altri operatori Adobe Campaign. Questo può essere utile se si lavora in collaborazione. A questo scopo, fai clic su **[!UICONTROL Upload the images straightaway...]** per caricare le immagini sul server.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>Gli URL delle immagini nell’e-mail e i loro nomi in particolare vengono modificati.

Una volta che le immagini sono online, puoi visualizzare le modifiche ai loro nomi e percorsi dalla scheda **[!UICONTROL Source]** del messaggio.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

Se selezioni **[!UICONTROL Include the images in the email]**, puoi scegliere quali immagini includere nella colonna corrispondente.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>Se nel messaggio sono incluse immagini locali, devi confermare le modifiche al codice sorgente del messaggio.

## Inserimento di un codice a barre in un messaggio e-mail{#inserting-a-barcode-in-an-email}

Il modulo di generazione dei codici a barre consente di creare diversi tipi di codici a barre conformi a numerosi standard comuni, inclusi i codici a barre 2D.

È possibile generare in modo dinamico un codice a barre come bitmap utilizzando un valore definito utilizzando i criteri del cliente. I codici a barre personalizzati possono essere inclusi nelle campagne e-mail. Il destinatario può stampare il messaggio e mostrarlo alla società emittente per la scansione (ad esempio durante il check-out).

Per inserire un codice a barre in un messaggio e-mail, posiziona il cursore nel contenuto in cui desideri visualizzarlo, quindi fai clic sul pulsante di personalizzazione. Seleziona **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Quindi configura i seguenti elementi in base alle tue esigenze:

1. Selezionare il tipo di codice a barre.

   * Per il formato 1D, in Adobe Campaign sono disponibili i seguenti tipi: Codabar, Codice 128, GS1-128 (precedentemente EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 di 5, POSTNET e Royal Mail (RM4SCC).

      Esempio di codice a barre 1D:

      ![](assets/barcode_insert_08.png)

   * I tipi DataMatrix e PDF417 riguardano il formato 2D.

      Esempio di codice a barre 2D:

      ![](assets/barcode_insert_09.png)

   * Per inserire un codice QR, selezionare questo tipo e immettere il tasso di correzione errori da applicare. Questo tasso definisce la quantità di informazioni ripetute e la tolleranza al deterioramento.

      ![](assets/barcode_insert_06.png)

      Esempio di codice QR:

      ![](assets/barcode_insert_12.png)

1. Immettere le dimensioni del codice a barre da inserire nell&#39;e-mail: la configurazione della scala consente di aumentare o ridurre le dimensioni del codice a barre da x1 a x10.
1. Il campo **[!UICONTROL Value]** consente di definire il valore del codice a barre. Un valore può corrispondere a un&#39;offerta speciale e può essere la funzione di un criterio, può essere il valore di un campo di database collegato ai clienti.

   Questo esempio mostra un codice a barre di tipo EAN-8 a cui è stato aggiunto il numero di account di un destinatario. Per aggiungere questo numero di account, fai clic sul pulsante di personalizzazione a destra del campo **[!UICONTROL Value]** e seleziona **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. Il campo **[!UICONTROL Height]** consente di configurare l’altezza dei codici a barre senza modificarne la larghezza, modificando la quantità di spazio tra ciascuna barra.

   Non esiste un controllo di ingresso restrittivo a seconda del tipo di codice a barre. Se un valore di un codice a barre non è corretto, sarà visibile solo in modalità **Anteprima**, dove il codice a barre verrà barrato in rosso.

   >[!NOTE]
   >
   >Il valore assegnato a un codice a barre dipende dal relativo tipo. Ad esempio, un tipo EAN-8 deve avere esattamente 8 numeri.
   >
   >Il pulsante di personalizzazione a destra del campo **[!UICONTROL Value]** ti consente di aggiungere dati oltre al valore stesso. Questo arricchisce il codice a barre, purché sia accettato dallo standard.
   >
   >Ad esempio, se si utilizza un codice a barre di tipo GS1-128 e si desidera immettere il numero di conto di un destinatario oltre al valore, fare clic sul pulsante di personalizzazione e selezionare **[!UICONTROL Recipient > Account number]**. Se il numero di conto del destinatario selezionato viene immesso correttamente, il codice a barre ne tiene conto.

Una volta configurati questi elementi, puoi finalizzare l’e-mail e inviarla. Per evitare errori, assicurati sempre che il contenuto sia visualizzato correttamente prima di eseguire una consegna facendo clic sulla scheda **[!UICONTROL Preview]** .

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Se il valore di un codice a barre non è corretto, la relativa bitmap viene visualizzata in rosso.

![](assets/barcode_insert_11.png)

<!--## Sending emails on Japanese mobiles {#sending-emails-on-japanese-mobiles}

### Email formats for Japanese mobiles {#email-formats-for-japanese-mobiles}

Adobe Campaign manages three specific Japanese formats for email on mobiles: **Deco-mail** (DoCoMo mobiles), **Decore Mail** (Softbank mobiles) and **Decoration Mail** (KDDI AU mobiles). These formats impose particular coding, structure, and size constraints. Learn more about limitations and recommendations in [this section](#limitations-and-recommendations).

In order for the recipient to correctly receive messages in one of these formats, we recommend selecting **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** in the corresponding profile:

![](assets/deco-mail_03.png)

However, if you leave the **[!UICONTROL Email format]** option as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]**, Adobe Campaign will automatically detect (when sending the email) the Japanese format to use so that the message is correctly displayed.

This automatic detection system is based on the list of predefined domains defined in the **[!UICONTROL Management of Email Formats]** mail rule set. For more on managing email formats, refer to [this page](../../installation/using/email-deliverability.md#managing-email-formats).

### Limitations and recommendations {#limitations-and-recommendations}

A certain number of constraints apply for sending emails that will be read on a mobile operated by a Japanese provider (Softbank, DoCoMo, KDDI AU).

Therefore, you must:

* Only use images in JPEG or GIF format
* Create a delivery with text and HTML sections that are strictly lower than 10 000 bytes (for KDDI AU and DoCoMo)
* Use images with a total size (before encoding) that is lower than 100 KB
* Do not use more than 20 images per message
* Use a reduced size HTML format (a limited number of tags are available for each operator)

>[!NOTE]
>
>Limitations specific to each operator are to be taken into account when creating your message. Refer to:  
>
>* For DoCoMo, refer to [this page](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* For KDDI AU, refer to [this page](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* For Softbank, refer to [this page](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)

### Testing the email content {#testing-the-email-content}

#### Previewing the message {#previewing-the-message}

Adobe Campaign allows you to check that your message format is adapted to be sent to a Japanese mobile.

Once you have defined your content and entered the email subject, you can check the display and formatting when the message is created.

In the **[!UICONTROL Preview]** tab of the content editing window, clicking **[!UICONTROL More... > Deco-mail diagnostic]** allows you to:

* Check that the HTML content tags conform to the Japanese format restrictions
* Check that the number of images in the message does not exceed the limit imposed by the format (20 images)
* Check the total message size (less than 100kB)

  ![](assets/deco-mail_06.png)

#### Running typology rule {#running-typology-rule}

In addition to the previewing diagnosis, a second check is carried out when sending a proof or a delivery: a specific typology rule, **[!UICONTROL Deco-mail check]**, is started during the analysis.

>[!IMPORTANT]
>
>This typology rule is only executed if at least one of the recipients is configured to receive emails in **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** or **[!UICONTROL Decoration Mail (KDDI AU)]** format.

This typology rule allows you to make sure that the delivery respects the [format constraints](#limitations-and-recommendations) defined by the Japanese operators, particularly in relation to the total size of the email, the size of the HTML and text sections, the number of images in the messages, and the tags in the HTML content.

#### Sending proofs {#sending-proofs}

You can send proofs to test your delivery. When you send the proof, if you are using substitution addresses, please enter addresses that correspond to the email format of the profile used.

For example, you can replace a profile's address by test@softbank.ne.jp if the email format for this profile was defined beforehand on **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

### Sending messages {#sending-messages}

To send an email to recipients with Japanese email formats with Campaign, two options are possible:

* Create two deliveries: one only for Japanese recipients and another for other recipients - refer to [this section](#designing-a-specific-delivery-for-japanese-formats).
* Create a single delivery and Adobe Campaign will automatically detect the format to use - refer to [this section](#designing-a-delivery-for-all-formats).

#### Designing a specific delivery for Japanese formats {#designing-a-specific-delivery-for-japanese-formats}

You can create a workflow that contains two deliveries: one to be read on a Japanese mobile and another for recipients with a standard email format.

To do this, use the **[!UICONTROL Split]** activity in your workflow and define the Japanese email formats (Deco-mail, Decoration Mail and Decore Mail) as filtering conditions.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

#### Designing a delivery for all formats {#designing-a-delivery-for-all-formats}

When Adobe Campaign dynamically manages the formats according to the domain (profiles with email formats defined as **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** or **[!UICONTROL Text]** ), you can send the same delivery to all of your recipients.

The message contact will display correctly for the users on Japanese mobiles, just as for the standard recipients.

>[!IMPORTANT]
>
>Make sure to respect the special features associated with each Japanese email format (Deco-mail, Decoration Mail, and Decore Mail). For more information on limitations, refer to [this section](#limitations-and-recommendations).-->
