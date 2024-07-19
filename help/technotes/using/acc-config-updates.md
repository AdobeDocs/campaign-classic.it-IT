---
product: campaign
title: Nota tecnica - Aggiornamenti alla configurazione di Adobe Campaign
description: Aggiornamenti alla configurazione di Adobe Campaign
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 8%

---

# Aggiornamenti alla configurazione di Adobe Campaign 2021 {#acc-config-updates}



L’infrastruttura e le impostazioni devono essere aggiornate regolarmente con le build e le correzioni di prodotto più recenti. Tali correzioni sono necessarie per garantire la continuità del servizio e la sicurezza. Inoltre, saranno necessari aggiornamenti per allinearsi alle modifiche di terze parti.

In qualità di **cliente in hosting o Managed Services**, Adobe ti informerà degli aggiornamenti di build a intervalli regolari. Per garantire la conformità, sarà necessario eseguire l&#39;aggiornamento in base alle raccomandazioni.

In qualità di **cliente on-premise o ibrido**, devi aggiornare l&#39;implementazione a intervalli regolari in linea con le build rilasciate più recenti.

Per motivi di sicurezza, è ora necessario eseguire l’aggiornamento a una delle versioni elencate di seguito. Oltre ai passaggi di aggiornamento standard, è necessario eseguire alcune attività manuali per garantire che l’ambiente sia sicuro e pronto per le modifiche imminenti da Adobi o sistemi di terze parti.

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Aggiornamenti di sicurezza {#acc-security-updates}

Le ultime versioni di Campaign includono una correzione di sicurezza che rafforza la protezione contro i problemi SSRF (Server Side Request Forgery). Per ulteriori informazioni, consulta [questa pagina](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html).

**Sei interessato da questo problema?**

Se l’ambiente si trova su una build inferiore a quelle elencate di seguito, sei interessato:

* Voce principale: Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../../rn/using/latest-release.md)
* Campaign versione 20.2.5.
* Campaign versione 20.1.4.
* Campaign versione 19.2.4.
* Campaign versione 19.1.8.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

Devi effettuare l’aggiornamento a una delle build più recenti elencate sopra.

* In qualità di cliente ibrido, Adobe ti informerà sulle date di aggiornamento pianificate per le istanze di mid-sourcing. L’Adobe consiglia vivamente di aggiornare anche la tua istanza di marketing.

  La nuova build è compatibile con le versioni precedenti di Campaign Classic 17.9, ma Adobe consiglia vivamente di eseguire un aggiornamento su tutte le istanze per risolvere le vulnerabilità di sicurezza

* In qualità di cliente on-premise, ti viene richiesto di aggiornare le istanze di marketing e mid-sourcing alla build più recente.

>[!CAUTION]
>
>Se non riesci ad eseguire l&#39;aggiornamento entro il periodo di tempo consigliato, **contatta il team di assistenza clienti Adobe per applicare una correzione manuale di sicurezza a breve termine alle istanze**.
>

## Aggiornamento console client Campaign Classic  {#acc-cc-updates}

Per risolvere una regressione identificata di recente, è necessario installare le versioni della console **ora disponibili** seguenti. Questa regressione ha impedito l’utilizzo di alcuni componenti della console client, come il selettore data e la gestione delle immagini nelle consegne. **L&#39;aggiornamento della console** è obbligatorio.

* Ultima build Gold Standard 11 9032@10c2709. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 20.1.4.
* Campaign versione 19.2.4.
* Campaign versione 19.1.8.

## Aggiornamento Adobe Identity Management System (IMS)

Adobe Identity Service (IMS) non supporterà più le versioni precedenti di Internet Explorer a partire dal **30 giugno 2021**. [Ulteriori informazioni](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Per garantire la compatibilità con Adobe IMS è necessario aggiornare la console client di Campaign.

**Sei interessato da questo problema?**

Se ti connetti a Campaign [tramite un Adobe ID](../../integrations/using/about-adobe-id.md), tramite Adobe Identity Management Service (IMS), è obbligatorio eseguire l&#39;aggiornamento a una delle nuove versioni elencate di seguito:

* Voce principale: Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../../rn/using/latest-release.md)
* Campaign versione 20.2.5.
* Campaign versione 20.1.4.
* Campaign versione 19.2.4.
* Campaign versione 19.1.8.

Queste versioni includono un nuovo protocollo di connessione: è necessario eseguire l’aggiornamento affinché il server Campaign e la console client possano connettersi a Campaign dopo il **30 giugno 2021**.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

In qualità di cliente in hosting, Adobe collaborerà con te per aggiornare a breve le istanze alla versione più recente.

In qualità di cliente on-premise/ibrido, devi effettuare l’aggiornamento a una delle versioni più recenti per beneficiare della nuova console client e garantire una transizione senza soluzione di continuità **prima del 30 giugno 2021**.

Una volta aggiornate tutte le istanze, anche la console client deve essere aggiornata a questa versione.

* Scopri come accedere a [Distribuzione di software Adobe](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

* [Scopri come installare la console client di Campaign](../../installation/using/installing-the-client-console.md).

## Integrazione con Experience Cloud Triggers {#acc-triggers-updates}

Il servizio di autenticazione OAuth legacy ha raggiunto la fine del ciclo di vita. L’autenticazione dell’integrazione dei trigger, originariamente basata sulla configurazione di autenticazione OAuth per accedere alla pipeline, è stata spostata in Adobe I/O. La modalità di autenticazione OAuth legacy con la campagna [ è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) il **settembre 2021**. Gli ambienti in hosting usufruiscono di una proroga fino al **23 febbraio 2022**. Se sei un cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto fino a febbraio 2022. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md#step-optional).

**Sei interessato da questo problema?**

Se le istanze sono in esecuzione su una versione **precedente a Campaign 19.1.8, 20.2.4, Gold Standard 11**, si utilizza una versione precedente dell&#39;integrazione Triggers tramite autenticazione oAuth: **è necessario eseguire l&#39;aggiornamento a una versione più recente e passare a Adobe I/O**.

L’aggiornamento a una delle nuove versioni elencate di seguito è obbligatorio:

* Voce principale: Gold Standard 11. [Ulteriori informazioni](../../rn/using/gold-standard.md)
* Campaign versione 21.1.1. [Ulteriori informazioni](../../rn/using/latest-release.md)
* Campaign versione 20.2.5.
* Campaign versione 19.1.8.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

Dopo aver aggiornato le istanze a una versione più recente, tutti i clienti devono seguire la [procedura per passare alla nuova modalità di autenticazione](../../integrations/using/about-triggers.md#implement). Questo richiede di generare il nuovo token di Adobe I/O e utilizzarlo nell’implementazione.  

Inoltre, per gli ambienti ibridi, i clienti devono assicurarsi che la pipeline sia configurata sull’istanza di mid-sourcing. [Ulteriori informazioni](../../integrations/using/configuring-pipeline.md).

[Scopri come effettuare la migrazione ad Adobe I/O](../../integrations/using/about-triggers.md#implement).

## Aggiornamenti APNs {#acc-apns-updates}

### API provider APNs basata su HTTP/2

A partire dal **31 marzo 2021**, il servizio APN (Apple Push Notification Service) non supporta più il protocollo binario legacy. [Ulteriori informazioni](https://developer.apple.com/news/?id=c88acm2b).

**Sei interessato?**

Se le istanze sono in esecuzione su una versione **precedente a Campaign 21.1,** e invii notifiche push con il protocollo binario legacy di Apple, devi eseguire l’aggiornamento all’API del provider APNs basata su HTTP/2.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

In qualità di cliente in hosting, se hai effettuato l’aggiornamento alla nuova build, Adobe ha già aggiornato le istanze all’API basata su HTTP/2.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione.

### Aggiornamenti dei certificati radice APN

Il 29 marzo 2021, un aggiornamento dell’infrastruttura del servizio di notifica push di Apple (APNs) ha interessato il canale Adobe Campaign Classic iOS. Una modifica alla configurazione del sistema operativo è **obbligatoria** per evitare l&#39;interruzione del canale push di iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=7gx0a2lp).

**Sei interessato da questo problema?**

Se utilizzi Campaign per inviare notifiche push su dispositivi iOS, sei interessato.

**Come si esegue l’aggiornamento?**

In qualità di cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nel tuo ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione fluida **prima del 29 marzo 2021**.

[Scopri come incorporare il nuovo certificato](ios-certificate-update.md).

## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Scarica build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Rendi la nuova Client Console disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
