---
product: campaign
title: Domande frequenti sulle impostazioni di Campaign
description: Domande frequenti su Campaign Classic
feature: Troubleshooting, Application Settings
audience: platform
content-type: reference
level: Beginner, Intermediate, Experienced
topic-tags: starting-with-adobe-campaign
exl-id: 50bed489-2a0f-4123-a326-3d68c8295662
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 70%

---

# Domande frequenti sulle impostazioni di Campaign {#settings-faq}



Scopri le configurazioni principali per impostare l’istanza di Campaign in base alle tue esigenze.

## Posso cambiare la lingua dell’interfaccia di Campaign? {#can-i-change-the-language-of-campaign-interface-}

La lingua di Campaign viene selezionata al momento della creazione dell’istanza. Non puoi modificarla in un secondo momento. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/creating-an-instance-and-logging-on.md).

L’interfaccia utente di Adobe Campaign è disponibile in 4 lingue: inglese, francese, tedesco e giapponese. Tieni presente che la console del client e il server devono essere impostati nella stessa lingua. Ogni istanza di Campaign può essere eseguita in una sola lingua.

Per l’inglese, durante l’installazione di Campaign puoi selezionare inglese US o inglese GB, che differiscono nei formati di data e ora. Per ulteriori informazioni su tali differenze, consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## Posso utilizzare Campaign Classic con altre soluzioni Adobe? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Puoi combinare le funzionalità di consegna e le funzionalità avanzate di gestione delle campagne di Adobe Campaign con una serie di soluzioni create per aiutarti a personalizzare la user experience.

Fai clic qui per scoprire [come lavorare con altre soluzioni Adobe](../../integrations/using/about-campaign-integrations.md) e [come impostare IMS in Campaign](../../integrations/using/about-adobe-id.md).

## Come posso impostare le funzionalità di tracciamento nella mia istanza di Campaign? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

In qualità di utente esperto, puoi configurare le funzionalità di tracking nella tua istanza di Campaign.

[Fai clic qui per ulteriori informazioni](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Come configurare il recapito messaggi e-mail? {#how-to-configure-email-deliverability-}

Oltre alla [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it), consulta le raccomandazioni tecniche per il recapito messaggi per scoprire come configurare la tua istanza per massimizzare le funzionalità di consegna di Campaign.

[Fai clic qui per ulteriori informazioni](../../delivery/using/about-deliverability.md).

## Come posso implementare l’approvazione dei contenuti? {#how-can-i-implement-content-approval-}

Campaign ti consente di impostare processi di approvazione per i passaggi principali della campagna di marketing, in modalità collaborativa. Per ogni campagna puoi approvare il target di consegna, i contenuti e i costi. Gli operatori Adobe Campaign incaricati dell’approvazione possono ricevere una notifica tramite e-mail e accettare o rifiutare l’approvazione dalla console o tramite una connessione web.

[Fai clic qui per ulteriori informazioni](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) e per scoprire i passaggi per implementare l’approvazione dei contenuti della tua consegna in Campaign.

## Come posso accedere ai dati memorizzati in un database esterno? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign offre l’opzione Federated Data Access (FDA) per elaborare le informazioni archiviare in uno o più database esterni: puoi accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.

[Fai clic qui per ulteriori informazioni](../../installation/using/connecting-to-database.md).

## A quali database esterni posso collegare Campaign? {#which-external-databases-can-i-connect-campaign-to-}

I database esterni compatibili con Campaign tramite Federated Data Access (FDA) sono elencati nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

## Adobe Campaign può integrarsi con il protocollo LDAP? {#can-adobe-campaign-integrate-with-ldap-}

In qualità di cliente on-premise/ibrido, puoi integrare Campaign Classic con la tua directory LDAP.

[Fai clic qui per scoprire come](../../installation/using/connecting-through-ldap.md).

## Come posso impostare i connettori di gestione delle relazioni con i clienti in Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign fornisce diversi connettori di gestione delle relazioni con i clienti per collegare la piattaforma Adobe Campaign ai sistemi di terze parti. Questi connettori di gestione delle relazioni con i clienti ti consentono di sincronizzare contatti, account, acquisti, ecc. Facilitano l’integrazione dell’applicazione con varie applicazioni di terze parti e aziendali.

Questi connettori consentono un’integrazione rapida e semplice dei dati: Adobe Campaign fornisce un assistente dedicato per la raccolta e la selezione dalle tabelle disponibili nella gestione delle relazioni con i clienti. Ciò garantisce la sincronizzazione bidirezionale per far sì che i dati siano sempre aggiornati in tutti i sistemi.

Consulta [Configurare i connettori di gestione delle relazioni con i clienti](../../platform/using/crm-connectors.md) per scoprire come sincronizzare il tuo strumento di gestione delle relazioni con i clienti con Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) Guarda questo video relativo al caso d&#39;uso sull&#39;[integrazione di Adobe Campaign e Microsoft Dynamics 365](https://helpx.adobe.com/it/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Come si esegue la cancellazione della Soft Cache quando i problemi riguardano nello specifico il computer o l’utente? {#perform-soft-cache-clear}

In caso di problemi quali la corretta riflessione dei nuovi loghi, in grado di esportare correttamente i dati specifici per il computer o l’utente, potresti dover eseguire una cancellazione della Soft Cache con Windows (Windows 7, Windows XP, Windows 10).

Dopo aver effettuato l’accesso, passa a **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. In seguito, effettua la disconnessione e accedi nuovamente.

![](assets/faq_soft_cache.png)

Se questo non risolve il problema, prova a cancellare la Hard Cache eseguendo i passaggi seguenti.

## Come si esegue la cancellazione della Hard Cache quando i problemi riguardano nello specifico il computer o l’utente? {#perform-hard-cache-clear}

In caso di problemi quali la corretta riflessione dei nuovi loghi, in grado di esportare correttamente i dati specifici per il computer o l’utente, potresti dover eseguire una cancellazione della Hard Cache con Windows (Windows 7, Windows XP, Windows 10).

1. Nella console del client, scegli **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**.

1. Effettua la disconnessione e chiudi la console del client (rich client).

1. Vai ai seguenti percorsi, in base alla versione del sistema operativo in uso:

   * Windows 7: C:\Users\&lt; Nome utente >\AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\&lt; Nome utente >\Application Data\Neolane\NL_5

   Qui troverai molti file xml denominati nlclient-config-&lt; valore alfanumerico >.xml.

1. Elimina questi file xml e le cartelle associate.

   >[!IMPORTANT]
   >
   >Non eliminare il file nlclient_cnx.xml.

1. Accedi alla console del client.
