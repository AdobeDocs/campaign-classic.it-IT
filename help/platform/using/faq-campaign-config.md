---
title: Domande frequenti sulle impostazioni delle campagne
seo-title: Come configurare Campaign
description: Domande frequenti su Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c5a9823b2feb6e2f721a2ad15dc08c1abe672054

---


# Domande frequenti sulle impostazioni delle campagne {#settings-faq}

Scopri le configurazioni chiave per configurare l&#39;istanza di Campaign in base alle tue esigenze.

## Posso cambiare la lingua dell&#39;interfaccia di Campaign? {#can-i-change-the-language-of-campaign-interface-}

La lingua della campagna viene selezionata al momento della creazione dell&#39;istanza. Non si può cambiare dopo. For more on this, refer to [this section](../../installation/using/creating-an-instance-and-logging-on.md).

L&#39;interfaccia utente di Adobe Campaign è disponibile in 4 lingue: Inglese, francese, tedesco e giapponese. Tenere presente che la console client e il server devono essere impostati con la stessa lingua. Ogni istanza Campaign può essere eseguita in una sola lingua.

Per l&#39;inglese, durante l&#39;installazione di Campaign, potete selezionare Inglese USA o Inglese Regno Unito: differiscono per i formati di data e ora. For more on these differences refer to [this section](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## Posso utilizzare Campaign Classic con altre soluzioni Adobe? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Puoi combinare le funzionalità di consegna e le funzionalità avanzate di gestione delle campagne di Adobe Campaign con un set di soluzioni create per aiutarti a personalizzare l&#39;esperienza degli utenti.

Fai clic qui per scoprire [come lavorare con altre soluzioni](../../integrations/using/about-campaign-integrations.md) Adobe e [come configurare IMS in Campaign](../../integrations/using/about-adobe-id.md).

## Come posso impostare le funzionalità di tracciamento nell&#39;istanza di Campaign? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

In qualità di utente esperto, puoi configurare le funzionalità di tracciamento nell&#39;istanza Campaign.

[Fai clic qui per saperne di più](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Come configurare la recapito delle e-mail? {#how-to-configure-email-deliverability-}

Oltre alla guida [introduttiva sulla](https://docs.adobe.com/content/help/en/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html)recapito, leggi la sezione sulla configurazione della recapito delle e-mail per comprendere come configurare la tua istanza per massimizzare le funzionalità di distribuzione delle campagne.

[Fai clic qui per saperne di più](../../installation/using/email-deliverability.md).

## Come posso implementare l&#39;approvazione dei contenuti? {#how-can-i-implement-content-approval-}

Campaign consente di impostare i processi di approvazione per i passaggi principali della campagna di marketing, in modalità collaborativa. Per ogni campagna puoi approvare target di consegna, contenuti e costi. Gli operatori Adobe Campaign incaricati dell&#39;approvazione possono ricevere notifiche via e-mail e accettare o rifiutare l&#39;approvazione dalla console o tramite una connessione Web.

[Fai clic qui per saperne di più](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) e scoprire i passaggi per implementare l&#39;approvazione dei contenuti di distribuzione in Campaign.

## Come posso accedere ai dati memorizzati in un database esterno? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign fornisce l&#39;opzione Federated Data Access (FDA) per elaborare le informazioni memorizzate in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

[Fai clic qui per saperne di più](../../platform/using/connecting-to-database.md).

## A quali database esterni posso collegare Campaign? {#which-external-databases-can-i-connect-campaign-to-}

I database esterni compatibili con Campaign tramite Federated Data Access (FDA) sono elencati nella matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità.

## Adobe Campaign può integrarsi con LDAP? {#can-adobe-campaign-integrate-with-ldap-}

In qualità di clienti interni/ibridi, puoi integrare Campaign Classic con la tua directory LDAP.

[Clicca qui per scoprire come](../../installation/using/connecting-through-ldap.md).

## Come posso impostare i connettori CRM in Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign fornisce diversi connettori CRM per collegare la piattaforma Adobe Campaign ai sistemi di terze parti. Questi connettori CRM consentono di sincronizzare contatti, account, acquisti, ecc. Facilitano l&#39;integrazione dell&#39;applicazione con diverse applicazioni di terze parti e aziendali.

Questi connettori consentono un&#39;integrazione rapida e semplice dei dati: Adobe Campaign fornisce una procedura guidata dedicata per la raccolta e la selezione delle risorse tra le tabelle disponibili in CRM. Questo garantisce la sincronizzazione bidirezionale per garantire che i dati siano sempre aggiornati in tutti i sistemi.

Leggi [Configurare i connettori](../../platform/using/crm-connectors.md) CRM per apprendere come sincronizzare lo strumento CRM con Adobe Campaign. Guardate questo video sull&#39;integrazione con [Adobe Campaign e Microsoft Dynamics 365](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Come eseguire Soft Cache Clear quando i problemi sono specifici del computer o dell&#39;utente? {#perform-soft-cache-clear}

In caso di problemi come il nuovo logo che si riflette correttamente, in grado di esportare con successo i dati specifici del computer o dell&#39;utente, potrebbe essere necessario eseguire una cancellazione della cache software con Windows (Windows 7, Windows XP, Windows 10).

Dopo aver effettuato l&#39;accesso, andate a **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. Dopo questo, disconnettetevi ed effettuate nuovamente l&#39;accesso.

![](assets/faq_soft_cache.png)

Se questo non è ancora utile, provate a cancellare la cache rigida eseguendo i passaggi indicati di seguito.

## Come eseguire Hard Cache Clear quando i problemi sono specifici del computer o dell&#39;utente? {#perform-hard-cache-clear}

In caso di problemi quali il riflesso corretto dei nuovi logo, in grado di esportare con successo i dati specifici del computer o dell&#39;utente, potrebbe essere necessario eseguire una cancellazione dalla cache rigida con Windows (Windows 7, Windows XP, Windows 10).

1. Nella console client, scegliete **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**.

1. Disconnettetevi e chiudete la console client (client avanzato).

1. Andate nelle seguenti posizioni, in base alla versione del sistema operativo in uso:

   * Windows 7: C:\Users\&lt; Nome utente > \AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\&lt; Nome utente >\Application Data\Neolane\NL_5
   Qui troverete molti file xml denominati nlclient-config-&lt; valore alfanumerico >.xml.

1. Eliminate questi file xml e le cartelle associate.

   >[!CAUTION]
   >
   >Non eliminate il file nlclient_cnx.xml.

1. Accedere alla console client.