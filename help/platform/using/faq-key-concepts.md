---
product: campaign
title: Concetti chiave
description: Domande frequenti su Campaign Classic
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f0d884ae-0789-4ad9-a8fa-adeffbb560ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 83%

---

# Concetti chiave {#key-concepts}



Scopri i passaggi chiave per iniziare a utilizzare Adobe Campaign.

## Posso collegarmi a Campaign Classic con un Adobe ID? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Grazie all’integrazione con IMS (Adobe Identity Management System), gli utenti possono collegarsi alla console di Adobe Campaign utilizzando il proprio Adobe ID. Questa integrazione offre i seguenti vantaggi:

* Lo stesso ID può essere utilizzato per tutte le soluzioni Experience Cloud.
* Il collegamento viene memorizzato quando si utilizza Adobe Campaign con diverse integrazioni.
* Policy di gestione password più sicure.
* Utilizzo di account Federated ID (provider di ID esterno).

[Fai clic qui per ulteriori informazioni](../../integrations/using/about-adobe-id.md) sull’accesso a Campaign Classic con un Adobe ID.

## Qual è la mia versione di Campaign? {#what-is-my-version-of-campaign-}

Verifica il [numero della versione e della build](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) dal menu **Help > About…** della console del client di Campaign.

## Quali sono le differenze quando si lavora on-premise rispetto a un ambiente in hosting? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

 Adobe Campaign Classic include una serie di moduli e opzioni. La disponibilità di tali moduli e la loro configurazione possono dipendere dal [tipo di distribuzione](../../installation/using/hosting-models.md) dell’installazione: in hosting (Managed Services), ibrida oppure on-premise.

[Fai clic qui per ulteriori informazioni](../../installation/using/capability-matrix.md).

## Come posso impostare le autorizzazioni per gli utenti? {#how-can-i-set-up-user-permissions-}

In qualità di amministratore di Campaign, puoi impostare le autorizzazioni per gli utenti della tua organizzazione.

Si tratta di una serie di diritti e limitazioni che autorizzano o negano l’autorizzazione a:

* Accedere a determinate funzionalità,
* Accedere a determinati dati,
* Creare, modificare e/o eliminare dati.

[Fai clic qui per ulteriori informazioni](../../platform/using/access-management.md) sulle autorizzazioni per gli utenti.

## Come si garantisce la conformità in materia di privacy con Campaign? {#how-to-be-gdpr-compliant-with-campaign-}

 Adobe Campaign offre una serie di strumenti per aiutarti con la conformità in materia di privacy in relazione a GDPR e CCPA.

Consulta [questo documento](privacy-and-recommendations.md) per scoprire gli strumenti e le funzionalità forniti da Adobe Campaign, nonché le best practice, per aiutarti in materia di conformità ai requisiti GDPR quando utilizzi il nostro servizio. I passaggi di implementazione per Campaign Classic sono descritti in [questo articolo](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

## Quali concetti dell’interfaccia utente di Campaign dovrei conoscere? {#what-are-campaign-user-interface-concepts-i-should-know-}

Consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md) per ulteriori informazioni sulle nozioni di base sull’area di lavoro di Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) [Scopri l’area di lavoro di Campaign nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html?lang=it)

## Come posso selezionare il pubblico dei miei messaggi? {#how-can-i-select-the-target-population-of-my-messages-}

Con Adobe Campaign, puoi utilizzare strategie diverse per creare pubblici e selezionare destinatari.

[Fai clic qui per ulteriori informazioni](../../delivery/using/steps-defining-the-target-population.md).

## Che cos’è un flusso di lavoro? {#what-is-a-workflow-}

 Adobe Campaign include flussi di lavoro per orchestrare l’intera gamma di processi e attività tra i diversi moduli del server dell’applicazione. Questo ambiente grafico completo ti consente di progettare processi inclusi segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc. Il motore del flusso di lavoro esegue e traccia tali processi.

Ad esempio, puoi utilizzare un flusso di lavoro per scaricare un file da un server, decomprimerlo e quindi importare i record contenuti all’interno nel database di Adobe Campaign.

Un flusso di lavoro può inoltre coinvolgere uno o più operatori da avvisare o che possono effettuare scelte e approvare processi. In questo modo, è possibile creare un’azione di consegna, assegnare un’attività a uno o più operatori per lavorare sul contenuto, specificare dei target e approvare le prove prima di avviare la consegna.

[Fai clic qui per ulteriori informazioni](../../workflow/using/about-workflows.md) sui flussi di lavoro. Puoi inoltre consultare le [best practice per i flussi di lavoro](../../workflow/using/building-a-workflow.md).

## Come si crea e invia una prima e-mail? {#how-to-create-and-send-a-first-email-}

[Fai clic qui per ulteriori informazioni](../../delivery/using/about-email-channel.md).

![](assets/do-not-localize/how-to-video.png) [Scoprilo nel video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html?lang=it)

## Come si inviano i messaggi SMS? {#how-to-send-sms-messages-}

Scopri come configurare la piattaforma e inviare messaggi SMS [in questa sezione](../../delivery/using/sms-channel.md).

## Come si inviano le notifiche push? {#how-to-send-push-notifications-}

Scopri come utilizzare Adobe Campaign per [inviare una notifica push personalizzata](../../delivery/using/create-notifications-ios.md) ai dispositivi iOS e Android tramite app.

## Come si progetta e si condivide un sondaggio online? {#how-to-design-and-share-an-online-survey-}

Scopri come [creare un sondaggio online](../../surveys/using/getting-started-with-surveys.md) con passaggi chiave per progettarlo e pubblicarlo con Campaign Classic.

## Come si crea una pagina di destinazione? {#how-to-create-landing-page-}

Puoi utilizzare l’editor di contenuti digitali di Adobe Campaign per progettare una pagina di destinazione e definire la mappatura con i campi del database.

[Fai clic qui per ulteriori informazioni](../../web/using/creating-a-landing-page.md).

## Come posso tracciare le consegne? {#how-can-i-track-deliveries-}

Puoi tracciare le consegne inviate con Campaign Classic tramite [report di consegna](../../reporting/using/delivery-reports.md) dedicati e quindi monitorare le consegne.

Ulteriori informazioni sulla gestione del tracking in Campaign sono disponibili in [questa pagina](https://helpx.adobe.com/it/campaign/kb/acc-tracking.html).

## Quali sono le best practice per la sicurezza (on-premise)? {#what-are-security-best-practices--on-premise--}

Consulta la [lista di controllo per la configurazione della protezione](https://helpx.adobe.com/it/campaign/kb/acc-security.html) per scoprire gli elementi chiave da verificare per la configurazione e l’irrigidimento della protezione per le distribuzioni on-premise.

## Come si traduce un messaggio di errore? {#how-to-translate-an-error-message-}

Un messaggio di errore viene visualizzato in una lingua straniera? Tutti i messaggi di errore e la relativa traduzione sono elencati in [questa pagina](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=it).

## Posso creare un modulo web e raccogliere le risposte in Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Scopri come [creare un modulo web](../../web/using/about-web-forms.md): progettare, testare, pubblicare un modulo web e raccogliere le risposte.

## Esiste un elenco delle funzioni e delle versioni obsolete? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe valuta costantemente le funzionalità del prodotto e nel tempo pianifica la sostituzione delle funzionalità con versioni migliorate, oppure decide di implementare nuovamente parti selezionate per prepararsi al meglio ad aspettative o estensioni future. Poiché Campaign funziona con strumenti di terze parti, la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate.

[Fai clic qui per ulteriori informazioni](../../rn/using/deprecated-features.md).

## Vengono rilasciati nuovi aggiornamenti della documentazione e materiali di supporto? {#are-there-new-documentation-updates-and-help-materials-released-}

Gli aggiornamenti della documentazione più recenti di Campaign Classic sono elencati [in questa pagina](https://experienceleague.adobe.com/docs/campaign-classic/using/documentation-updates.html?lang=it).

Puoi inoltre consultare le note tecniche più recenti elencate [in questa pagina](https://helpx.adobe.com/it/campaign/kb/article-list.html).
