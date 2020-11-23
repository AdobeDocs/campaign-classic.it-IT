---
solution: Campaign Classic
product: campaign
title: Invio di un’e-mail con Adobe Campaign Classic
description: Informazioni sui parametri di consegna delle e-mail
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 8%

---


# Invio di un messaggio e-mail{#sending-an-email}

Per approvare il messaggio e-mail e inviarlo ai destinatari della consegna che si sta creando, fate clic su **[!UICONTROL Send]**.

La procedura dettagliata per la convalida e l&#39;invio di una consegna è descritta nelle sezioni seguenti:

* [Convalida della consegna](../../delivery/using/steps-validating-the-delivery.md)
* [Invio della consegna](../../delivery/using/steps-sending-the-delivery.md)

Le sezioni seguenti descrivono i parametri specifici per la distribuzione delle e-mail.

## Ccn e-mail {#archiving-emails}

 Adobe Campaign consente di memorizzare le e-mail in un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN alla destinazione del messaggio. Una volta attivata l&#39;opzione, per questa consegna viene conservata una copia esatta di tutti i messaggi inviati.

Per ulteriori informazioni sulla configurazione e sulle procedure ottimali di CCN per e-mail, consulta [questa sezione](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Ccn e-mail è una funzionalità opzionale. Controlla il contratto di licenza e contatta il responsabile dell’account per attivarla.

Quando si crea un nuovo modello di consegna o consegna, per impostazione predefinita CCN e-mail non è attivato. È necessario attivarlo manualmente a livello di consegna e-mail o di modello di consegna.

Per abilitare Ccn e-mail per un modello di consegna e-mail, effettuate le seguenti operazioni:

1. Vai a **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** o **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Selezionate la consegna desiderata o duplicate il modello di consegna **** e-mail fornito con il prodotto, quindi selezionate il modello duplicato.
1. Click the **Properties** button.
1. Seleziona la scheda **[!UICONTROL Delivery]**.
1. Selezionate l’opzione Ccn **e-mail** . Una copia di tutti i messaggi inviati per ogni consegna basata su questo modello verrà inviata all&#39;indirizzo CCN e-mail configurato.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >Se le e-mail inviate all&#39;indirizzo CCN vengono aperte e si fa clic su di esse, queste verranno prese in considerazione nell&#39;analisi **[!UICONTROL Total opens]** e **[!UICONTROL Clicks]** dall&#39;analisi di invio, il che potrebbe causare errori di calcolo.

## Generazione della pagina mirror {#generating-the-mirror-page}

La pagina mirror è una pagina HTML accessibile online tramite un browser Web. Il contenuto è identico al messaggio e-mail.

Per impostazione predefinita, la pagina mirror viene generata se il collegamento viene inserito nel contenuto della posta. Per ulteriori informazioni sull’inserimento dei blocchi di personalizzazione, consulta Blocchi [di](../../delivery/using/personalization-blocks.md)personalizzazione.

Nelle proprietà di consegna, il **[!UICONTROL Mode]** campo della **[!UICONTROL Validity]** scheda consente di modificare la modalità di generazione della pagina.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>È necessario che sia stato definito un contenuto HTML per la distribuzione della pagina mirror da creare.

Oltre alla modalità predefinita, sono disponibili anche le seguenti opzioni:

* **[!UICONTROL Force the generation of the mirror page]** : anche se non viene inserito alcun collegamento alla pagina mirror, verrà creata la pagina mirror.
* **[!UICONTROL Do not generate the mirror page]** : non viene generata alcuna pagina mirror, anche se il collegamento è presente nella consegna.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : questa opzione consente di accedere al contenuto della pagina mirror, con informazioni sulla personalizzazione, nella finestra del registro di distribuzione. A questo scopo, dopo la fine della consegna, fare clic sulla **[!UICONTROL Delivery]** scheda e selezionare la riga del destinatario di cui si desidera visualizzare la pagina mirror. Fate clic sul **[!UICONTROL Display the mirror page for this message...]** collegamento.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Gestione dei messaggi e-mail di rimbalzo {#managing-bounce-emails}

La **[!UICONTROL SMTP]** scheda dei parametri di consegna consente di configurare la gestione dei messaggi di rimbalzo.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Per impostazione predefinita, le e-mail rimbalzate vengono ricevute nella casella di errore predefinita della piattaforma, ma è possibile definire un indirizzo di errore specifico per la consegna.

È inoltre possibile definire un indirizzo specifico da questa schermata al fine di esaminare i motivi per i messaggi di rimbalzo quando questi non potevano essere automaticamente qualificati dall&#39;applicazione. Per ciascuno di questi campi, l&#39;icona &quot;aggiungi campi personalizzati&quot; consente di aggiungere parametri di personalizzazione.

## Codifica dei caratteri {#character-encoding}

Nella **[!UICONTROL SMTP]** scheda dei parametri di consegna, la **[!UICONTROL Character encoding]** sezione consente di impostare una codifica specifica.

La codifica predefinita è UTF-8. Se alcuni provider di posta elettronica dei destinatari non supportano la codifica standard UTF-8, è possibile impostare una codifica specifica per visualizzare correttamente i caratteri speciali ai destinatari delle e-mail.

Ad esempio, si desidera inviare un messaggio e-mail contenente caratteri giapponesi. Per essere certi che tutti i caratteri verranno visualizzati correttamente ai destinatari in Giappone, è possibile utilizzare una codifica che supporti i caratteri giapponesi anziché l&#39;UTF-8 standard.

A questo scopo, selezionate l&#39; **[!UICONTROL Force the encoding used for messages]** opzione nella **[!UICONTROL Character encoding]** sezione e scegliete una codifica dall&#39;elenco a discesa visualizzato.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Aggiunta di intestazioni SMTP {#adding-smtp-headers}

È possibile aggiungere intestazioni SMTP alle consegne. A tal fine, utilizzare la sezione pertinente della **[!UICONTROL SMTP]** scheda nella consegna.

The script entered in this window must reference one header per line in the following form: **name:value**.

Se necessario, i valori vengono codificati automaticamente.

>[!CAUTION]
>
>L’aggiunta di uno script per l’inserimento di intestazioni SMTP aggiuntive è un’operazione riservata agli utenti avanzati.
>
>La sintassi di questo script deve essere conforme ai requisiti di questo tipo di contenuto: nessuno spazio inutilizzato, nessuna linea vuota e così via.
