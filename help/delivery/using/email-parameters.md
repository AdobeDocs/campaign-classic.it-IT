---
product: campaign
title: Configurazione dei parametri e-mail in Adobe Campaign Classic
description: Scopri le opzioni e le impostazioni specifiche per la consegna delle e-mail.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 8%

---

# Parametri e-mail {#email-parameters}

Questa sezione presenta le opzioni e i parametri specifici per la consegna e-mail.

## Ccn e-mail {#email-bcc}

Adobe Campaign consente di memorizzare le e-mail su un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN al target del messaggio.

Una volta attivata l’opzione , per questa consegna viene conservata una copia esatta di tutti i messaggi inviati.

Per ulteriori informazioni sulla configurazione e sulle best practice di E-mail con indirizzi Ccn, consulta [questa sezione](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Ccn e-mail è una funzionalità opzionale. Controlla il contratto di licenza e contatta il responsabile dell’account per attivarla.

Quando crei un nuovo modello di consegna o consegna, Ccn e-mail non è abilitato per impostazione predefinita. Devi attivarla manualmente a livello di consegna e-mail o di modello di consegna.

Per abilitare CCN e-mail per un modello di consegna e-mail, segui i passaggi seguenti:

1. Vai a **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** o **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Seleziona la consegna desiderata o duplica il modello preconfigurato **Email delivery** , quindi seleziona il modello duplicato.
1. Fare clic sul pulsante **Proprietà**.
1. Seleziona la scheda **[!UICONTROL Delivery]**.
1. Seleziona l’opzione **Ccn e-mail** . Una copia di tutti i messaggi inviati per ogni consegna basata su questo modello verrà inviata all’indirizzo Ccn e-mail configurato.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Se le e-mail inviate all’indirizzo CCN vengono aperte e fai clic su di esse, verranno prese in considerazione nelle sezioni **[!UICONTROL Total opens]** e **[!UICONTROL Clicks]** dell’analisi di invio, il che potrebbe causare errori di calcolo.

## Selezione dei formati dei messaggi {#selecting-message-formats}

Puoi modificare il formato dei messaggi e-mail inviati. A questo scopo, modifica le proprietà di consegna e fai clic sulla scheda **[!UICONTROL Delivery]** .

![](assets/s_ncs_user_wizard_email_param.png)

Seleziona il formato dell’e-mail nella sezione inferiore della finestra:

* **[!UICONTROL Use recipient preferences]** (modalità predefinita)

   Il formato del messaggio viene definito in base ai dati memorizzati nel profilo del destinatario e memorizzato per impostazione predefinita nel campo **[!UICONTROL email format]** (@emailFormat). Se un destinatario desidera ricevere i messaggi in un determinato formato, questo sarà il formato inviato. Se il campo non viene compilato, viene inviato un messaggio multipart-alternative (vedi sotto).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   Il messaggio contiene entrambi i formati: testo e HTML. Il formato visualizzato in base alla ricezione dipende dalla configurazione del software di posta del destinatario (multipart-alternative).

   >[!IMPORTANT]
   >
   >Questa opzione include entrambe le versioni del documento. Pertanto, influisce sul tasso di consegna, perché la dimensione del messaggio è maggiore.

* **[!UICONTROL Send all messages in text format]**

   Il messaggio viene inviato in formato testo. Il formato HTML non viene inviato, ma viene utilizzato per la pagina speculare solo quando il destinatario fa clic sul messaggio.

>[!NOTE]
>
>Per ulteriori informazioni sulla definizione del contenuto dell’e-mail, consulta [questa sezione](../../delivery/using/defining-the-email-content.md).

## Generazione della pagina speculare {#generating-mirror-page}

La pagina speculare è una pagina HTML accessibile online tramite un browser web. Il contenuto è identico all’e-mail.

Per impostazione predefinita, la pagina speculare viene generata se il collegamento viene inserito nel contenuto della posta. Per ulteriori informazioni sull’inserimento dei blocchi di personalizzazione, consulta [Blocchi di personalizzazione](../../delivery/using/personalization-blocks.md).

Nelle proprietà di consegna, il campo **[!UICONTROL Mode]** della scheda **[!UICONTROL Validity]** ti consente di modificare la modalità di generazione di questa pagina.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>È necessario che sia stato definito un contenuto HTML per la consegna della pagina speculare da creare.

Oltre alla modalità predefinita, sono disponibili anche le seguenti opzioni:

* **[!UICONTROL Force the generation of the mirror page]**: anche se nella consegna non viene inserito alcun collegamento alla pagina speculare, verrà creata la pagina speculare.
* **[!UICONTROL Do not generate the mirror page]**: non viene generata alcuna pagina speculare, anche se il collegamento è presente nella consegna.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: questa opzione ti consente di accedere al contenuto della pagina speculare, con informazioni sulla personalizzazione, nella finestra del registro di consegna. A questo scopo, dopo la fine della consegna, fai clic sulla scheda **[!UICONTROL Delivery]** e seleziona la riga del destinatario della pagina speculare di cui desideri visualizzare la pagina. Fai clic sul collegamento **[!UICONTROL Display the mirror page for this message...]** .

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Codifica caratteri {#character-encoding}

Nella scheda **[!UICONTROL SMTP]** dei parametri di consegna, la sezione **[!UICONTROL Character encoding]** ti consente di impostare una codifica specifica.

La codifica predefinita è UTF-8. Se alcuni provider di posta elettronica dei tuoi destinatari non supportano la codifica standard UTF-8, puoi impostare una codifica specifica per visualizzare correttamente i caratteri speciali ai destinatari delle e-mail.

Ad esempio, desideri inviare un’e-mail contenente caratteri giapponesi. Per fare in modo che tutti i caratteri vengano visualizzati correttamente ai destinatari in Giappone, è consigliabile utilizzare una codifica che supporti i caratteri giapponesi anziché lo standard UTF-8.

A questo scopo, seleziona l’opzione **[!UICONTROL Force the encoding used for messages]** nella sezione **[!UICONTROL Character encoding]** e scegli una codifica dall’elenco a discesa visualizzato.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Gestione delle e-mail non recapitate {#managing-bounce-emails}

La scheda **[!UICONTROL SMTP]** dei parametri di consegna ti consente di configurare la gestione delle e-mail non recapitate.

Per impostazione predefinita, le e-mail rimbalzate vengono ricevute nella casella di errore predefinita della piattaforma, ma puoi definire un indirizzo di errore specifico per una consegna.

È inoltre possibile definire un indirizzo specifico da questa schermata al fine di esaminare i motivi per i messaggi non recapitati quando questi non potevano essere qualificati automaticamente dall’applicazione. Per ciascuno di questi campi, l&#39;icona **Aggiungi campi personalizzati** consente di aggiungere parametri di personalizzazione.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Per ulteriori informazioni sulla gestione della posta non recapitata, consulta [questa sezione](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

## Aggiunta di intestazioni SMTP {#adding-smtp-headers}

È possibile aggiungere intestazioni SMTP alle consegne. A questo scopo, utilizza la sezione pertinente della scheda **[!UICONTROL SMTP]** nella consegna.

Lo script immesso in questa finestra deve fare riferimento a un’intestazione per riga nel modulo seguente: **name:value**.

Se necessario, i valori vengono codificati automaticamente.

>[!IMPORTANT]
>
>L’aggiunta di uno script per l’inserimento di intestazioni SMTP aggiuntive è un’operazione riservata agli utenti avanzati.
>
>La sintassi di questo script deve essere conforme ai requisiti di questo tipo di contenuto: nessuno spazio inutilizzato, nessuna linea vuota e così via.
