---
product: campaign
title: Migrazione al connettore Adobe Analytics
description: Campaign - Domande frequenti sul connettore Analytics
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: 89494165a59c0ba6119f37d41893fd0e8733f47d
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 5%

---

# Come migrare le integrazioni di Genesis esistenti al connettore Adobe Analytics {#acc-aa-faq}

![](../../assets/v7-only.svg)

A partire dalla versione 21.1.3 di Campaign Classic v7, il Connettore dati di Adobe Analytics è diventato obsoleto. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Il 1° agosto 2021, Adobe Campaign Classic è stato rimosso dall’interfaccia utente dei Data Connectors legacy, tuttavia, le integrazioni esistenti di Campaign continueranno a raccogliere e trasmettere dati ad Adobe Analytics fino ad agosto 2022. Dopo questa data, l’integrazione cesserà di raccogliere e trasmettere dati ad Adobe Analytics.

You **deve implementare** la nuova integrazione di Adobe Analytics Connector su Adobe Exchange che sostituisce l’integrazione legacy di Data Connectors. Per ulteriori informazioni su Adobe Analytics Connector, consulta [questa pagina](../../platform/using/adobe-analytics-connector.md).

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, leggi il [Domande frequenti](#faq-aa). Per ulteriori informazioni, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Cosa è cambiato?

È ora disponibile una nuova integrazione tra Campaign Classic v7 e Adobe Analytics. Di seguito sono elencate le modifiche principali.

* L’integrazione tra l’autenticazione Adobe Campaign Classic e Adobe Analytics è stata spostata da utente/password ad Adobe Identity Management Service (IMS). Di conseguenza, devi implementare Adobe IMS e connetterti a Campaign [tramite un Adobe ID](../../integrations/using/about-adobe-id.md), prima di avviare l’implementazione di Analytics Connector.

* La **Data contatto** La classificazione, che deve essere di tipo data, è stata dichiarata obsoleta da Adobe Analytics. Per le integrazioni migrate, rimarrà comunque dello stesso tipo. Per qualsiasi **Data contatto** creato da Campaign, il tipo sarà **Stringa**.

* **Regole di elaborazione** sono create da Adobe Campaign come parte di nuove integrazioni. O **Regole di elaborazione** devono essere create manualmente da Adobe Analytics o direttamente utilizzando l’implementazione JavaScript lato client. **Regole di elaborazione** rimarrà intatto per le integrazioni esistenti.

* I flussi di lavoro tecnici incorporati e il loro comportamento restano invariati. Sono state modificate solo le API di backend utilizzate dai flussi di lavoro per inviare/estrarre dati da/verso Adobe Analytics.

* Tieni presente che `nlserver` Il processo deve essere configurato con IMS Technical Account User affinché il nuovo connettore funzioni. Questa modifica deve essere fatta per Adobe. Per implementare questo, contatta [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Se utilizzi le API di Adobe Genesis in flussi di lavoro personalizzati per estrarre e inviare i dati da Adobe Analytics, ora devi utilizzare le nuove API di Adobe Analytics 1.4/2.0. [Ulteriori informazioni](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Sei interessato da questo problema?

Se utilizzi il Connettore dati Adobe Analytics esistente (noto in precedenza come integrazione di Genesis) e l’integrazione è stata implementata in una build inferiore a Campaign 21.1.3, questo impatto è notevole.

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Come si esegue l’aggiornamento?

Devi effettuare l’aggiornamento a Campaign 21.1.3 (o più) **prima del 1 marzo 2022**.

In qualità di cliente in hosting, Adobe collaborerà con te per aggiornare le tue istanze alla versione più recente. Potrai quindi utilizzare [Connettore Adobe Analytics](../../platform/using/adobe-analytics-connector.md).

In qualità di cliente on-premise/ibrido, è necessario effettuare l’aggiornamento a una delle versioni più recenti per beneficiare della nuova integrazione.
Una volta aggiornate tutte le istanze, potrai [implementare la nuova integrazione](../../platform/using/adobe-analytics-provisioning.md) al connettore Adobe Analytics e assicurati una transizione senza soluzione di continuità.

## Domande frequenti{#faq-aa}

**Come posso ottenere i registri?**

La configurazione e i flussi di lavoro dell&#39;interfaccia utente sono dotati di **verboso** registrazione.

In modalità dettagliata, le intestazioni di richiesta e risposta vengono stampate anche per ogni richiesta API ad Adobe Analytics.

In qualità di utente on-premise, puoi implementare la modalità dettagliata come segue:

* Per attivare la modalità dettagliata per l&#39;interfaccia utente: rieseguire il `web` in modalità dettagliata.
* Per attivare la modalità dettagliata per **webAnalytics** flussi di lavoro: seleziona la **Esecuzione nel motore** dalle proprietà del flusso di lavoro e riesegui `wfserver` in modalità dettagliata.

**Che cosa significa l&#39;errore &quot;Integration Owner Not Admin&quot; (Proprietario integrazione non amministratore)?**

Ulteriori informazioni sui Data Connectors `Integration Owner Not Admin` Errore in [questa pagina](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Una volta effettuata la migrazione al nuovo connettore, cosa succede ai dati e alle suite di rapporti precedenti?**

Dopo la migrazione, un nuovo connettore (migrato dal vecchio connettore) inizierà a inviare dati a quella stessa suite di rapporti e i dati esistenti non saranno interessati: verrà aggiunto ai dati esistenti.

**Alcune evar/eventi/suite di rapporti esistenti presenti in Analytics non sono visibili in Campaign. Cosa dovrei fare?**

L&#39;integrazione si basa sui dati su token account tecnici per il funzionamento quotidiano. Se manca l’autorizzazione per una dimensione/metrica/suite di rapporti dal profilo di prodotto associato all’utente dell’account tecnico, le API che utilizziamo non potranno essere utilizzate per tali richieste.

Se leggiamo i dettagli di un componente Analytics (come metriche/dimensioni/segmenti/suite di rapporti), l’API non restituisce questi componenti nel risultato (che potrebbe sembrare qualcosa che sia stato eliminato dal lato Analytics o che non sia presente). L’API di Analytics rifiuterà tali richieste ed eseguirà l’errore.

La soluzione consiste nell&#39;aggiornare il **Profilo prodotto** nel contesto utente di Analytics del token utente tecnico con i componenti appena creati/mancanti aggiungendo questi componenti in [Adobe Admin Console](https://adminconsole.adobe.com/). Per maggiori informazioni, contatta [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Scarica la build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Rendere la nuova console client disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
* [Installare la console client di Campaign](../../installation/using/installing-the-client-console.md)
