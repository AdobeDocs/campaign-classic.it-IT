---
title: Concetti chiave
seo-title: Domande frequenti sulle funzionalità delle campagne
description: Domande frequenti sui Campaign Classic
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
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 1%

---


# Concetti chiave {#key-concepts}

Scopri i passaggi chiave per iniziare con  Adobe Campaign.

## Posso collegarmi al Campaign Classic con un Adobe ID ? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Grazie all&#39;integrazione con IMS ( Adobe  Identity Management System), gli utenti possono connettersi alla console  Adobe Campaign utilizzando  Adobe ID. Questa integrazione offre i seguenti vantaggi:

* Lo stesso ID può essere utilizzato per tutte le soluzioni  Experience Cloud.
* La connessione viene memorizzata quando si utilizza  Adobe Campaign con diverse integrazioni.
* Criteri di gestione password più sicuri.
* Utilizzo di account di Federated ID (provider di ID esterno).

[Fate clic qui per ulteriori](../../integrations/using/about-adobe-id.md) informazioni sull&#39;accesso ai Campaign Classic con un Adobe ID .

## Qual è la mia versione di Campaign? {#what-is-my-version-of-campaign-}

Controllate la [versione e il numero](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) di build da **Aiuto > Informazioni su...** menu della console client Campaign.

## Quali sono le differenze quando si lavora in sede rispetto a un ambiente ospitato? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic viene fornito con una serie di moduli e opzioni. La disponibilità di questi moduli e la loro configurazione possono dipendere dal [tipo di implementazione](../../installation/using/hosting-models.md) dell&#39;installazione: ospitato (Managed Services) o in sede.

[Fai clic qui per saperne di più](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Come si configurano le autorizzazioni per l’utente? {#how-can-i-set-up-user-permissions-}

In qualità di amministratore di Campaign, puoi impostare le autorizzazioni per gli utenti dell&#39;organizzazione.

Si tratta di una serie di diritti e restrizioni che autorizzano o negano a:

* accesso a determinate funzionalità,
* l&#39;accesso a taluni dati,
* Creare, modificare e/o eliminare i dati.

[Fate clic qui per ulteriori](../../platform/using/access-management.md) informazioni sulle autorizzazioni utente.

## Come garantire la conformità alla privacy con Campaign? {#how-to-be-gdpr-compliant-with-campaign-}

 Adobe Campaign offre una serie di strumenti per aiutarti con la conformità alla privacy per GDPR e CCPA.

Consulta [questo documento](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html) per comprendere gli strumenti e le funzionalità forniti da Adobe Campaign, nonché le procedure ottimali, per aiutarti con la conformità al GDPR quando utilizzi il nostro servizio. I passaggi di implementazione per i Campaign Classic sono descritti in [questo articolo](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

## Quali sono i concetti dell&#39;interfaccia utente di Campaign che dovrei conoscere? {#what-are-campaign-user-interface-concepts-i-should-know-}

Leggi [questa sezione](../../platform/using/adobe-campaign-workspace.md) per saperne di più sulle nozioni di base &#39;area di lavoro di Adobe Campaign. Potete anche guardare [questo video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html).

## Come posso selezionare il pubblico dei miei messaggi? {#how-can-i-select-the-target-population-of-my-messages-}

Con  Adobe Campaign, potete utilizzare strategie diverse per creare audience e selezionare destinatari.

[Fai clic qui per saperne di più](../../delivery/using/steps-defining-the-target-population.md).

## Che cos’è un flusso di lavoro? {#what-is-a-workflow-}

 Adobe Campaign include flussi di lavoro per coordinare l&#39;intera gamma di processi e attività tra i diversi moduli del server applicazioni. Questo ambiente grafico completo vi consente di progettare processi che includono segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e tiene traccia di questi processi.

È possibile utilizzare un flusso di lavoro, ad esempio per scaricare un file da un server, decomprimerlo e quindi importare i record contenuti nel database Adobe Campaign .

Un flusso di lavoro può coinvolgere anche uno o più operatori ai quali inviare una notifica o che possono effettuare scelte e approvare processi. In questo modo, è possibile creare un&#39;azione di consegna, assegnare un&#39;attività a uno o più operatori per lavorare sul contenuto, specificare le destinazioni e approvare le prove prima di iniziare la consegna.

[Fai clic qui per saperne di più](../../workflow/using/about-workflows.md) sui flussi di lavoro. Potete inoltre leggere le best practice relative ai [flussi di lavoro](../../workflow/using/building-a-workflow.md).

## Come creare e inviare una prima e-mail? {#how-to-create-and-send-a-first-email-}

[Fate clic qui per saperne di più](../../delivery/using/about-email-channel.md) o [guardate questo video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-campaign-and-an-email.html) per creare un messaggio e-mail in una campagna.

## Come inviare messaggi SMS? {#how-to-send-sms-messages-}

Scopri come configurare la piattaforma e inviare messaggi SMS [in questa sezione](../../delivery/using/sms-channel.md).

## Come inviare le notifiche push? {#how-to-send-push-notifications-}

Scoprite come utilizzare l&#39;Adobe Campaign  per [inviare una notifica](../../delivery/using/creating-notifications.md) push personalizzata ai dispositivi iOS e Android tramite app.

## Come progettare e condividere un sondaggio online? {#how-to-design-and-share-an-online-survey-}

Scopri come [creare un sondaggio](../../web/using/getting-started-with-surveys.md)online, con i passaggi chiave per progettarlo e pubblicarlo con i Campaign Classic.

## Come creare una pagina di destinazione? {#how-to-create-landing-page-}

È possibile utilizzare  editor di contenuti digitali Adobe Campaign per progettare una pagina di destinazione e definire la mappatura con i campi del database.

[Fai clic qui per saperne di più](../../web/using/creating-a-landing-page.md).

## Come posso tenere traccia delle consegne? {#how-can-i-track-deliveries-}

Puoi tenere traccia delle consegne inviate con Campaign Classic tramite rapporti [di](../../reporting/using/delivery-reports.md) consegna dedicati e quindi monitorare le consegne.

Ulteriori informazioni sulla gestione del tracciamento in Campaign in [questa pagina](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

## Quali sono le procedure ottimali per la sicurezza (in sede)? {#what-are-security-best-practices--on-premise--}

Leggi l&#39;elenco [di controllo della configurazione di](https://helpx.adobe.com/campaign/kb/acc-security.html) sicurezza per scoprire gli elementi chiave da verificare per quanto riguarda la configurazione di sicurezza e l&#39;indurimento per le distribuzioni in sede.

## Come tradurre un messaggio di errore? {#how-to-translate-an-error-message-}

Viene visualizzato un messaggio di errore in una lingua straniera? Tutti i messaggi di errore e la relativa traduzione sono elencati in [questa pagina](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html).

## Posso creare un modulo Web e raccogliere le risposte in Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Come [creare un modulo](../../web/using/about-web-forms.md)Web: progettare, verificare, pubblicare un modulo Web e raccogliere le risposte.

## Esiste un elenco di funzioni e versioni obsolete? {#is-there-a-list-of-deprecated-features-and-versions-}

 Adobe valuta costantemente le capacità del prodotto e nel tempo pianifica di sostituire le funzionalità con versioni più potenti, o decide di reimplementare parti selezionate per essere meglio preparate per future aspettative o estensioni. Poiché Campaign funziona con strumenti di terze parti, la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate.

[Fai clic qui per saperne di più](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html).

## Sono disponibili nuovi aggiornamenti alla documentazione e materiali di aiuto? {#are-there-new-documentation-updates-and-help-materials-released-}

Gli ultimi aggiornamenti della documentazione Campaign Classic sono elencati [in questa pagina](https://docs.adobe.com/content/help/en/campaign-classic/using/documentation-updates.html).

È inoltre possibile fare riferimento alle note tecniche più recenti elencate [in questa pagina](https://helpx.adobe.com/campaign/kb/article-list.html).
