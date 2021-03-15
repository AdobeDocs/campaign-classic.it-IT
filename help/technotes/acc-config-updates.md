---
solution: Campaign Classic
product: campaign
title: Nota tecnica
description: Nota tecnica
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 504a948daa60155b7c4970be24bd6d2049e5395b
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 6%

---


# Aggiornamenti alla configurazione di Adobe Campaign - marzo 2021 {#acc-config-updates}

È necessario mantenere aggiornata l&#39;infrastruttura e le impostazioni con le build e le correzioni più recenti dei prodotti. Queste correzioni sono obbligatorie per garantire la continuità del servizio e la sicurezza. Inoltre, devi adattare l’implementazione per allinearla con le modifiche di terze parti.

In qualità di cliente in hosting, Adobe ti informerà a intervalli regolari degli aggiornamenti di build richiesti. Devi eseguire l’aggiornamento in conformità alle raccomandazioni per garantire la conformità.

In qualità di cliente on-premise/ibrido, per motivi di sicurezza, devi effettuare l’aggiornamento a una delle versioni elencate in questa pagina. Inoltre, è necessario eseguire alcune attività manuali per garantire che l’ambiente sia sicuro e pronto per le imminenti modifiche da sistemi di Adobe o di terze parti.

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta l&#39; [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Aggiornamenti di sicurezza

Le versioni più recenti di Campaign presentano una correzione di sicurezza che rafforza la protezione contro i problemi SSRF (Server Side Request Forgery). Ulteriori informazioni [in questa pagina](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html).

**Siete interessati?**

Se l’ambiente si trova in una build inferiore a quelle elencate di seguito, è interessato:

* Gold Standard 11. [Ulteriori informazioni](../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../rn/using/latest-release.md)
* Campaign versione 20.3.3. [Ulteriori informazioni](../rn/using/release--20-3.md)
* Campaign versione 20.2.4. [Ulteriori informazioni](../rn/using/release--20-2.md)
* Campaign versione 20.1.4. [Ulteriori informazioni](../rn/using/release--20-1.md)
* Campaign versione 19.2.4. [Ulteriori informazioni](../rn/using/release--19-2.md)
* Campaign versione 19.1.8. [Ulteriori informazioni](../rn/using/release--19-1.md)

**Come si aggiorna?**

Devi eseguire l’aggiornamento a una delle build più recenti elencate in precedenza.

* In qualità di cliente ibrido, Adobe aggiornerà l’istanza di mid-sourcing alla nuova versione e ti consigliamo vivamente di aggiornare anche la propria istanza di marketing.

   La nuova build è compatibile con almeno Campaign Classic 17.9, ma per evitare problemi di sicurezza, Adobe consiglia vivamente di aggiornare tutte le istanze a una nuova build. 

* In qualità di cliente on-premise, ti viene richiesto di aggiornare le istanze di marketing e mid-sourcing a una build più recente.

>[!CAUTION]
>
>Se per il momento non è possibile eseguire l&#39;aggiornamento, **è necessario contattare il team di assistenza clienti Adobe per applicare manualmente una correzione di sicurezza alle istanze**.


## Aggiornamento della console client di Campaign

La build Gold Standard 11 più recente corregge una regressione che impediva l’utilizzo di alcuni componenti della console client, come il selettore data e la gestione immagini nelle consegne. L’aggiornamento della console è obbligatorio.

[Ulteriori informazioni](../rn/using/gold-standard.md).

>[!NOTE]
>
>La nuova console client per altre versioni sarà presto disponibile.

## Aggiornamento Adobe Identity Management System (IMS)

IMS (Adobe Identity Service) cesserà di supportare le versioni precedenti di Internet Explorer a partire dal **30 giugno 2021**. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

La console client di Campaign è stata aggiornata per garantire la compatibilità con Adobe IMS nelle seguenti versioni di Campaign:

**Siete interessati?**

Se ti connetti a Campaign [tramite un Adobe ID](../integrations/using/about-adobe-id.md), tramite il servizio Adobe Identity (IMS), è obbligatorio effettuare l’aggiornamento a una delle nuove versioni elencate di seguito:

* Gold Standard 11. [Ulteriori informazioni](../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../rn/using/latest-release.md)
* Campaign versione 20.3.3. [Ulteriori informazioni](../rn/using/release--20-3.md)
* Campaign versione 20.2.4. [Ulteriori informazioni](../rn/using/release--20-2.md)
* Campaign versione 20.1.4. [Ulteriori informazioni](../rn/using/release--20-1.md)
* Campaign versione 19.2.4. [Ulteriori informazioni](../rn/using/release--19-2.md)
* Campaign versione 19.1.8. [Ulteriori informazioni](../rn/using/release--19-1.md)

Queste versioni sono dotate di un nuovo protocollo di connessione: l’aggiornamento è obbligatorio per il server Campaign e la console client per poter connettersi a Campaign dopo il **30 giugno 2021**.

**Come si aggiorna?**

Come cliente in hosting, non è necessaria alcuna azione: Adobe ha già aggiornato le istanze a una versione più recente.

In qualità di cliente on-premise/ibrido, è necessario eseguire l’aggiornamento a una delle versioni più recenti per beneficiare della nuova console client e garantire una transizione senza soluzione di continuità **prima del 30 giugno 2021**.

Una volta aggiornate tutte le istanze, è necessario aggiornare anche la console client a questa versione.

* Scopri come accedere a [Distribuzione di software di Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Scopri come installare la console](../installation/using/installing-the-client-console.md) client di Campaign.

## Integrazione con Experience Cloud Triggers

Il servizio di autenticazione oAuth legacy ha raggiunto la fine del ciclo di vita. L’autenticazione dell’integrazione dei trigger, originariamente basata su oAUTH per accedere alla pipeline, è stata spostata in Adobe I/O. Sarà ritirato il **30 aprile 2021**. [Ulteriori informazioni](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

**Siete interessati?**

Se le istanze sono in esecuzione su una versione **precedente a Campaign 19.1.8, 20.2.4, Gold Standard 11**, utilizza una versione precedente dell’integrazione Triggers tramite autenticazione oAuth: **è necessario passare ad Adobe I/O**.

**Come si aggiorna?**

Una volta aggiornate le istanze a una versione più recente, tutti i clienti devono seguire la procedura [per passare alla nuova modalità di autenticazione](../integrations/using/configuring-adobe-io.md). Questo richiede la generazione del nuovo token di Adobe I/O e il suo utilizzo nell’implementazione.  

Inoltre, per gli ambienti ibridi, i clienti devono assicurarsi che la pipeline sia configurata sull’istanza di mid-sourcing. [Ulteriori informazioni](../integrations/using/configuring-pipeline.md).

[Scopri come effettuare la migrazione ad Adobe I/O](../integrations/using/configuring-adobe-io.md).

## Aggiornamenti APN

### API del provider APN basato su HTTP/2

Il servizio APN (Apple Push Notification Service) non supporterà più il protocollo binario legacy a partire dal **31 marzo 2021**. [Leggi tutto](https://developer.apple.com/news/?id=c88acm2b).

**Sei interessato?**

Se le istanze sono in esecuzione su una versione **precedente a Campaign 21.1,** e inviano notifiche push con il protocollo binario Apple legacy, devi eseguire l’aggiornamento all’API del provider APN basata su HTTP/2.

**Come si aggiorna?**

Come cliente in hosting, non è necessaria alcuna azione: Adobe ha già aggiornato le istanze all’API basata su HTTP/2.

In qualità di cliente on-premise/ospitato, devi aggiornare la configurazione. [Scopri come migrare a HTTP/2](https://helpx.adobe.com/it/campaign/kb/migrate-to-apns-http2.html)

### Aggiornamenti dei certificati principali di APN

Il 29 marzo 2021, un aggiornamento dell’infrastruttura APN (Apple Push Notification Service) interesserà il canale Adobe Campaign Classic iOS. Una modifica alla configurazione del sistema operativo è **obbligatoria** per evitare l&#39;interruzione del canale push iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Siete interessati?**

Se utilizzi Campaign per inviare notifiche push su dispositivi iOS, sei interessato.

**Come si aggiorna?**

Come cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nell&#39;ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione senza soluzione di continuità **prima del 29 marzo 2021**.

[Scopri come incorporare il nuovo certificato](ios-certificate-update.md).


## Collegamenti utili

* [Aggiornare l’ambiente](../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../platform/using/faq-build-upgrade.md)
* [Scarica la build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Rendere la nuova console client disponibile agli utenti](../installation/using/client-console-availability-for-windows.md)
