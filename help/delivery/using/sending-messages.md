---
title: Invio di un'e-mail con Adobe Campaign Classic
description: Scopri i parametri specifici per la distribuzione di e-mail in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c800c20fff89b97f6fa38b3c659ca765765e157

---


# Invio di un messaggio e-mail{#sending-an-email}

Per approvare il messaggio e-mail e inviarlo ai destinatari della consegna che si sta creando, fate clic **[!UICONTROL Send]**.

La procedura dettagliata per la convalida e l&#39;invio di una consegna è descritta nelle sezioni seguenti:

* [Convalida della consegna](../../delivery/using/steps-validating-the-delivery.md)
* [Invio della consegna](../../delivery/using/steps-sending-the-delivery.md)

Le sezioni seguenti descrivono i parametri specifici per la distribuzione delle e-mail.

## Archiviazione di e-mail {#archiving-emails}

Adobe Campaign consente di archiviare le e-mail in un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN alla destinazione del messaggio. Una volta attivata l&#39;opzione, per questa consegna viene conservata una copia esatta di tutti i messaggi inviati.

Per ulteriori informazioni sulla configurazione di Email BCC, consulta [questa sezione](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Questa funzione è facoltativa. Controllare il contratto di licenza e contattare il responsabile commerciale di riferimento per attivarlo.

Quando si crea un nuovo modello di consegna o consegna, Ccn e-mail non è abilitato per impostazione predefinita, anche se l&#39;opzione è stata acquistata. È necessario attivarlo manualmente in ogni consegna o modello in cui si desidera utilizzarlo.

A questo scopo, effettuate le seguenti operazioni:

1. Vai a **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** o **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Selezionate la consegna desiderata o duplicate il modello di consegna **** e-mail fornito con il prodotto, quindi selezionate il modello duplicato.
1. Fate clic sul pulsante **Proprietà** .
1. Selezionate la **[!UICONTROL Delivery]** scheda.
1. Selezionate la casella **Archivia e-mail** per conservare una copia di tutti i messaggi inviati per la consegna o per ogni consegna basata su questo modello.

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
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : questa opzione consente di accedere al contenuto della pagina mirror, con informazioni sulla personalizzazione, nella finestra del registro di distribuzione. A questo scopo, al termine della consegna, fare clic sulla **[!UICONTROL Delivery]** scheda e selezionare la riga del destinatario di cui si desidera visualizzare la pagina mirror. Fate clic sul **[!UICONTROL Display the mirror page for this message...]** collegamento.

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

Lo script immesso in questa finestra deve fare riferimento a un&#39;intestazione per riga nel modulo seguente: **name:value**.

Se necessario, i valori vengono codificati automaticamente.

>[!CAUTION]
>
>L&#39;aggiunta di uno script per l&#39;inserimento di intestazioni SMTP aggiuntive è riservata agli utenti avanzati.
>
>La sintassi di questo script deve essere conforme ai requisiti di questo tipo di contenuto: nessuno spazio inutilizzato, nessuna linea vuota, ecc.
