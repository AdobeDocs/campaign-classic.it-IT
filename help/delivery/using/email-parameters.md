---
solution: Campaign Classic
product: campaign
title: Configurazione dei parametri e-mail in Adobe Campaign Classic
description: Ulteriori informazioni sulle opzioni e le impostazioni specifiche per la distribuzione delle e-mail.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: e84387c7c396c60c429c3f625870a97a7fdaef5a
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 8%

---


# Parametri e-mail {#email-parameters}

Questa sezione presenta le opzioni e i parametri specifici per la distribuzione delle e-mail.

## Ccn e-mail {#email-bcc}

 Adobe Campaign consente di memorizzare le e-mail in un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN alla destinazione del messaggio.

Una volta attivata l&#39;opzione, per questa consegna viene conservata una copia esatta di tutti i messaggi inviati.

Per ulteriori informazioni sulla configurazione e sulle procedure ottimali di CCN e-mail, consultare [questa sezione](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Ccn e-mail è una funzionalità opzionale. Controlla il contratto di licenza e contatta il responsabile dell’account per attivarla.

Quando si crea un nuovo modello di consegna o consegna, per impostazione predefinita CCN e-mail non è attivato. È necessario attivarlo manualmente a livello di consegna e-mail o di modello di consegna.

Per abilitare Ccn e-mail per un modello di consegna e-mail, effettuate le seguenti operazioni:

1. Passare a **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** o **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Seleziona la consegna desiderata o duplica il modello **Posta elettronica** fornito out-of-the-box, quindi seleziona il modello duplicato.
1. Fare clic sul pulsante **Proprietà**.
1. Seleziona la scheda **[!UICONTROL Delivery]**.
1. Selezionare l&#39;opzione **Ccn e-mail**. Una copia di tutti i messaggi inviati per ogni consegna basata su questo modello verrà inviata all&#39;indirizzo CCN e-mail configurato.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Se le e-mail inviate all&#39;indirizzo CCN vengono aperte e su cui si fa clic, queste verranno prese in considerazione nelle **[!UICONTROL Total opens]** e **[!UICONTROL Clicks]** dell&#39;analisi di invio, il che potrebbe causare errori di calcolo.

## Selezione dei formati dei messaggi {#selecting-message-formats}

Potete modificare il formato dei messaggi e-mail inviati. A questo scopo, modificate le proprietà di consegna e fate clic sulla scheda **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_email_param.png)

Selezionate il formato del messaggio e-mail nella sezione inferiore della finestra:

* **[!UICONTROL Use recipient preferences]** (modalità predefinita)

   Il formato del messaggio viene definito in base ai dati memorizzati nel profilo del destinatario e memorizzato per impostazione predefinita nel campo **[!UICONTROL email format]** (@emailFormat). Se un destinatario desidera ricevere i messaggi in un determinato formato, questo sarà il formato inviato. Se il campo non è compilato, viene inviato un messaggio alternativo multiparte (vedi sotto).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   Il messaggio contiene entrambi i formati: text e HTML. Il formato visualizzato in base alla ricezione dipende dalla configurazione del software di posta del destinatario (multipart-alternative).

   >[!IMPORTANT]
   >
   >Questa opzione include entrambe le versioni del documento. Di conseguenza, influisce sulla frequenza di consegna, poiché la dimensione del messaggio è maggiore.

* **[!UICONTROL Send all messages in text format]**

   Il messaggio viene inviato in formato testo. Il formato HTML non verrà inviato, ma utilizzato per la pagina mirror solo quando il destinatario fa clic sul messaggio.

>[!NOTE]
>
>Per ulteriori informazioni sulla definizione del contenuto dell&#39;e-mail, vedere [questa sezione](../../delivery/using/defining-the-email-content.md).

## Generazione della pagina mirror {#generating-mirror-page}

La pagina mirror è una pagina HTML accessibile online tramite un browser Web. Il contenuto è identico al messaggio e-mail.

Per impostazione predefinita, la pagina mirror viene generata se il collegamento viene inserito nel contenuto della posta. Per ulteriori informazioni sull&#39;inserimento dei blocchi di personalizzazione, consultare [Blocchi di personalizzazione](../../delivery/using/personalization-blocks.md).

Nelle proprietà di consegna, il campo **[!UICONTROL Mode]** della scheda **[!UICONTROL Validity]** consente di modificare la modalità di generazione per questa pagina.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>È necessario che sia stato definito un contenuto HTML per la distribuzione della pagina mirror da creare.

Oltre alla modalità predefinita, sono disponibili anche le seguenti opzioni:

* **[!UICONTROL Force the generation of the mirror page]**: anche se non viene inserito alcun collegamento alla pagina mirror, verrà creata la pagina mirror.
* **[!UICONTROL Do not generate the mirror page]**: non viene generata alcuna pagina mirror, anche se il collegamento è presente nella consegna.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: questa opzione consente di accedere al contenuto della pagina mirror, con informazioni sulla personalizzazione, nella finestra del registro di distribuzione. A questo scopo, dopo la fine della consegna, fare clic sulla scheda **[!UICONTROL Delivery]** e selezionare la riga del destinatario di cui si desidera visualizzare la pagina mirror. Fare clic sul collegamento **[!UICONTROL Display the mirror page for this message...]**.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Codifica caratteri {#character-encoding}

Nella scheda **[!UICONTROL SMTP]** dei parametri di consegna, la sezione **[!UICONTROL Character encoding]** consente di impostare una codifica specifica.

La codifica predefinita è UTF-8. Se alcuni provider di posta elettronica dei destinatari non supportano la codifica standard UTF-8, è possibile impostare una codifica specifica per visualizzare correttamente i caratteri speciali ai destinatari delle e-mail.

Ad esempio, si desidera inviare un messaggio e-mail contenente caratteri giapponesi. Per essere certi che tutti i caratteri verranno visualizzati correttamente ai destinatari in Giappone, è possibile utilizzare una codifica che supporti i caratteri giapponesi anziché l&#39;UTF-8 standard.

A questo scopo, selezionate l&#39;opzione **[!UICONTROL Force the encoding used for messages]** nella sezione **[!UICONTROL Character encoding]** e scegliete una codifica dall&#39;elenco a discesa visualizzato.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Gestione dei messaggi e-mail di rimbalzo {#managing-bounce-emails}

La scheda **[!UICONTROL SMTP]** dei parametri di consegna consente di configurare la gestione dei messaggi di rimbalzo.

Per impostazione predefinita, le e-mail rimbalzate vengono ricevute nella casella di errore predefinita della piattaforma, ma è possibile definire un indirizzo di errore specifico per la consegna.

È inoltre possibile definire un indirizzo specifico da questa schermata al fine di esaminare i motivi per i messaggi di rimbalzo quando questi non potevano essere automaticamente qualificati dall&#39;applicazione. Per ciascuno di questi campi, l&#39;icona **Aggiungi campi personalizzati** consente di aggiungere parametri di personalizzazione.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Per ulteriori informazioni sulla gestione della posta indesiderata, vedere [questa sezione](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

## Aggiunta di intestazioni SMTP {#adding-smtp-headers}

È possibile aggiungere intestazioni SMTP alle consegne. A tal fine, utilizzare la sezione pertinente della scheda **[!UICONTROL SMTP]** nella consegna.

Lo script immesso in questa finestra deve fare riferimento a un&#39;intestazione per riga nel modulo seguente: **name:value**.

Se necessario, i valori vengono codificati automaticamente.

>[!IMPORTANT]
>
>L’aggiunta di uno script per l’inserimento di intestazioni SMTP aggiuntive è un’operazione riservata agli utenti avanzati.
>
>La sintassi di questo script deve essere conforme ai requisiti di questo tipo di contenuto: nessuno spazio inutilizzato, nessuna linea vuota e così via.
