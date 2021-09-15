---
product: campaign
title: Nota tecnica
description: Nota tecnica
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: b458ac67733a2f0e508df729add37d9a78dbcbd8
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 11%

---

# Aggiornamenti alla configurazione di Adobe Campaign 2021 {#acc-config-updates}

![](../../assets/v7-only.svg)

L&#39;infrastruttura e le impostazioni devono essere aggiornate regolarmente con le build e le correzioni più recenti dei prodotti. Tali correzioni sono necessarie per garantire la continuità del servizio e la sicurezza. Inoltre, gli aggiornamenti saranno necessari per allinearsi con le modifiche di terze parti.

In qualità di **cliente ospitato o Managed Services**, Adobe ti informerà degli aggiornamenti di build a intervalli regolari. Sarà necessario eseguire l’aggiornamento in conformità alle raccomandazioni per garantire la conformità.

In qualità di **Cliente on-premise o ibrido**, devi aggiornare l’implementazione a intervalli regolari in linea con le ultime build rilasciate.

Per motivi di sicurezza, ora devi effettuare l’aggiornamento a una delle versioni elencate di seguito. Oltre ai passaggi standard di aggiornamento, è necessario eseguire alcune attività manuali per garantire che l’ambiente sia sicuro e pronto per le imminenti modifiche da sistemi di Adobe o di terze parti.

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Aggiornamenti di sicurezza {#acc-security-updates}

Le versioni più recenti di Campaign presentano una correzione di sicurezza che rafforza la protezione contro i problemi di Server Side Request Forgery (SSRF). Per ulteriori informazioni, consulta [questa pagina](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html).

**Sei interessato da questo problema?**

Se l’ambiente si trova in una build inferiore a quelle elencate di seguito, è interessato:

* Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../../rn/using/latest-release.md)
* Campaign versione 20.2.4. [Ulteriori informazioni](../../rn/using/release--20-2.md)
* Campaign versione 20.1.4. [Ulteriori informazioni](../../rn/using/release--20-1.md)
* Campaign versione 19.2.4. [Ulteriori informazioni](../../rn/using/release--19-2.md)
* Campaign versione 19.1.8. [Ulteriori informazioni](../../rn/using/release--19-1.md)

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

Devi eseguire l’aggiornamento a una delle build più recenti elencate in precedenza.

* In qualità di cliente ibrido, Adobe ti informerà delle date di aggiornamento pianificate per le istanze di mid-sourcing. L’Adobe consiglia vivamente di aggiornare anche l’istanza di marketing.

   La nuova build è compatibile con le versioni precedenti di Campaign Classic 17.9, ma Adobe consiglia vivamente un aggiornamento su tutte le istanze per risolvere le vulnerabilità relative alla sicurezza

* In qualità di cliente on-premise, ti viene richiesto di aggiornare le istanze di marketing e mid-sourcing alla build più recente.

>[!CAUTION]
>
>Se non è possibile eseguire l&#39;aggiornamento entro il periodo di tempo consigliato, **contatta il team di assistenza clienti Adobe per applicare una correzione manuale di sicurezza a breve termine alle istanze**.

## Aggiornamento della console client di Campaign Classic  {#acc-cc-updates}

Per risolvere una regressione identificata di recente, è necessario installare le versioni della console **ora disponibili** riportate di seguito. Questa regressione impediva l’utilizzo di alcuni componenti della console client, come il selettore data e la gestione delle immagini nelle consegne. **Aggiornamenti** della console obbligatori.

* Build Gold Standard 11 più recente 9032@10c2709. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 20.1.4. [Ulteriori informazioni](../../rn/using/release--20-1.md)
* Campaign versione 19.2.4. [Ulteriori informazioni](../../rn/using/release--19-2.md)
* Campaign versione 19.1.8. [Ulteriori informazioni](../../rn/using/release--19-1.md)

## Aggiornamento Adobe Identity Management System (IMS)

Il servizio Adobe Identity (IMS) smetterà di supportare le versioni precedenti di Internet Explorer dal **30 giugno 2021**. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

È necessario un aggiornamento della console client di Campaign per garantire la compatibilità con Adobe IMS.

**Sei interessato da questo problema?**

Se ti connetti a Campaign [tramite un Adobe ID](../../integrations/using/about-adobe-id.md), tramite Adobe Identity Management Service (IMS), è obbligatorio effettuare l’aggiornamento a una delle nuove versioni elencate di seguito:

* Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../../rn/using/latest-release.md)
* Campaign versione 20.2.5. [Ulteriori informazioni](../../rn/using/release--20-2.md)
* Campaign versione 20.1.4. [Ulteriori informazioni](../../rn/using/release--20-1.md)
* Campaign versione 19.2.4. [Ulteriori informazioni](../../rn/using/release--19-2.md)
* Campaign versione 19.1.8. [Ulteriori informazioni](../../rn/using/release--19-1.md)

Queste versioni sono dotate di un nuovo protocollo di connessione: l’aggiornamento è obbligatorio per il server Campaign e la console client per poter connettersi a Campaign dopo il **30 giugno 2021**.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

In qualità di cliente in hosting, Adobe collaborerà con te per aggiornare le tue istanze alla versione più recente a breve.

In qualità di cliente on-premise/ibrido, è necessario eseguire l’aggiornamento a una delle versioni più recenti per beneficiare della nuova console client e garantire una transizione senza soluzione di continuità **prima del 30 giugno 2021**.

Una volta aggiornate tutte le istanze, è necessario aggiornare anche la console client a questa versione.

* Scopri come accedere a [Distribuzione di software di Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Scopri come installare la console](../../installation/using/installing-the-client-console.md) client di Campaign.

## Integrazione con Experience Cloud Triggers {#acc-triggers-updates}

Il servizio di autenticazione oAuth legacy ha raggiunto la fine del ciclo di vita. L’autenticazione dell’integrazione dei trigger, originariamente basata su oAUTH per accedere alla pipeline, è stata spostata in Adobe I/O. La modalità di autenticazione oAuth legacy con Campaign [è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) il **18 agosto 2021**. Gli ambienti ospitati beneficiano di un’estensione fino al **30 novembre 2021**. In qualità di cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto fino al 30 novembre 2021. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) .

**Sei interessato da questo problema?**

Se le istanze sono in esecuzione su una versione **precedente a Campaign 19.1.8, 20.2.4, Gold Standard 11**, utilizza una versione precedente dell’integrazione Triggers tramite autenticazione oAuth: **è necessario eseguire l&#39;aggiornamento a una versione più recente e passare ad Adobe I/O**.

L’aggiornamento a una delle nuove versioni elencate di seguito è obbligatorio:

* Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../../rn/using/latest-release.md)
* Campaign versione 20.2.5. [Ulteriori informazioni](../../rn/using/release--20-2.md)
* Campaign versione 19.1.8. [Ulteriori informazioni](../../rn/using/release--19-1.md)

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

Una volta aggiornate le istanze a una versione più recente, tutti i clienti devono seguire la procedura [per passare alla nuova modalità di autenticazione](../../integrations/using/configuring-adobe-io.md). È necessario generare il nuovo token di Adobe I/O e utilizzarlo nell’implementazione.  

Inoltre, per gli ambienti ibridi, i clienti devono assicurarsi che la pipeline sia configurata sull’istanza di mid-sourcing. [Ulteriori informazioni](../../integrations/using/configuring-pipeline.md).

[Scopri come effettuare la migrazione ad Adobe I/O](../../integrations/using/configuring-adobe-io.md).

## Aggiornamenti APN {#acc-apns-updates}

### API del provider APN basato su HTTP/2

A partire dal **31 marzo 2021**, il servizio APN (Apple Push Notification Service) non supporta più il protocollo binario legacy. [Leggi tutto](https://developer.apple.com/news/?id=c88acm2b).

**Sei interessato?**

Se le istanze sono in esecuzione su una versione **precedente a Campaign 21.1,** e invii notifiche push con il protocollo binario Apple legacy, devi eseguire l’aggiornamento all’API del provider APN basata su HTTP/2.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

In qualità di cliente in hosting, se hai effettuato l’aggiornamento alla nuova build, Adobe ha già aggiornato le istanze all’API basata su HTTP/2.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione. [Scopri come migrare a HTTP/2](https://helpx.adobe.com/it/campaign/kb/migrate-to-apns-http2.html)

### Aggiornamenti dei certificati principali di APN

Il 29 marzo 2021, un aggiornamento dell’infrastruttura APN (Apple Push Notification Service) ha interessato il canale iOS Adobe Campaign Classic. Una modifica alla configurazione del sistema operativo è **obbligatoria** per evitare l&#39;interruzione del canale push iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Sei interessato da questo problema?**

Se utilizzi Campaign per inviare notifiche push su dispositivi iOS, sei interessato.

**Come si esegue l’aggiornamento?**

Come cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nell&#39;ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione senza soluzione di continuità **prima del 29 marzo 2021**.

[Scopri come incorporare il nuovo certificato](ios-certificate-update.md).

## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Scarica la build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Rendere la nuova console client disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
