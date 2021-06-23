---
product: campaign
title: Migrazione al connettore Adobe Analytics
description: Campaign - Domande frequenti sul connettore Analytics
hide: true
hidefromtoc: true
source-git-commit: 248bd7774c01adb44ce33d0499c2b01d013e75bd
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 6%

---

# Come migrare al connettore Adobe Analytics {#acc-aa-faq}

A partire dalla versione 21.1.3 di Campaign Classic v7, il Connettore dati di Adobe Analytics è diventato obsoleto. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Il 1° agosto 2021, Adobe Campaign Classic verrà rimosso dall’interfaccia utente dei Data Connectors legacy, tuttavia, le integrazioni esistenti di Campaign continueranno a raccogliere e trasmettere dati ad Adobe Analytics fino al 1° marzo 2022. Il 1° marzo 2022 l’integrazione cesserà di raccogliere e trasmettere dati ad Adobe Analytics.

È necessario eseguire la migrazione alla nuova integrazione Adobe Analytics Connector su Adobe Exchange che sostituisce l&#39;integrazione dei Data Connectors legacy, come descritto in [questa pagina](../platform/using/adobe-analytics-connector.md).


>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Cosa è cambiato?

È ora disponibile una nuova integrazione tra Campaign Classic e Adobe Analytics. Di seguito sono elencate le modifiche principali.

* L’integrazione tra l’autenticazione Adobe Campaign Classic e Adobe Analytics è stata spostata da utente/password ad Adobe Identity Management Service (IMS). Di conseguenza, devi implementare Adobe IMS e connetterti a Campaign [tramite un Adobe ID](../integrations/using/about-adobe-id.md) prima di avviare l’implementazione del connettore Analytics.

* La classificazione **Data di contatto**, che deve essere di tipo data, è stata dichiarata obsoleta da Adobe Analytics. Per le integrazioni migrate, rimarrà comunque dello stesso tipo. Per qualsiasi **Data di contatto** creato da Campaign, il tipo sarà **String**.

* **Le** regole di elaborazione vengono create da Adobe Campaign come parte delle nuove integrazioni. Le **Regole di elaborazione** devono essere create manualmente da Adobe Analytics o devono utilizzare direttamente l&#39;implementazione JavaScript lato client. **Le** regole di elaborazione rimarranno intatte per le integrazioni esistenti.

* I flussi di lavoro tecnici incorporati e il loro comportamento restano invariati. Sono state modificate solo le API di backend utilizzate dai flussi di lavoro per inviare/estrarre dati da/verso Adobe Analytics.

* Tieni presente che il processo `nlserver` deve essere configurato con IMS Technical Account User affinché il nuovo connettore funzioni. Questa modifica deve essere fatta per Adobe. Per implementare questo, contatta l’ [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Se utilizzi le API di Adobe Genesis in flussi di lavoro personalizzati per estrarre e inviare i dati da Adobe Analytics, ora devi utilizzare le nuove API di Adobe Analytics 1.4/2.0. [Ulteriori informazioni](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Sei interessato da questo problema?

Se utilizzi il Connettore dati Adobe Analytics esistente (noto in precedenza come integrazione di Genesis) e l’integrazione è stata implementata in una build inferiore a Campaign 21.1.3, questo impatto è notevole.

Scopri come controllare la versione [in questa sezione](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Come si esegue l’aggiornamento?

Devi eseguire l’aggiornamento a Campaign 21.1.3 (o superiore) **prima del 1° marzo 2022**.

In qualità di cliente in hosting, Adobe collaborerà con te per aggiornare le tue istanze alla versione più recente.

In qualità di cliente on-premise/ibrido, è necessario effettuare l’aggiornamento a una delle versioni più recenti per beneficiare della nuova integrazione.

Una volta aggiornate tutte le istanze, potrai [implementare la nuova integrazione](../platform/using/adobe-analytics-connector.md) nel connettore Adobe Analytics e garantire una transizione senza soluzione di continuità.


## Domande frequenti

**Come posso ottenere i registri?**

La configurazione e i flussi di lavoro dell&#39;interfaccia utente sono dotati di **registrazione dettagliata**.

In modalità dettagliata, le intestazioni di richiesta e risposta vengono stampate anche per ogni richiesta API ad Adobe Analytics.

In qualità di utente on-premise, puoi implementare la modalità dettagliata come segue:

* Per attivare la modalità dettagliata per l&#39;interfaccia utente: eseguire nuovamente il processo `web` in modalità dettagliata.
* Per abilitare la modalità dettagliata per i flussi di lavoro **webAnalytics**: seleziona l’opzione **Esegui nel motore** dalle proprietà del flusso di lavoro, quindi esegui nuovamente `wfserver` in modalità dettagliata.

**Amministratore proprietario integrazione non amministratore**

Ulteriori informazioni sull&#39;errore &quot;Integration Owner Not Admin&quot; dei Data Connectors in [questa pagina](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Evar/eventi/suite di rapporti esistenti presenti in analytics non visibili in Campaign**

L&#39;integrazione si basa sui dati su token account tecnici per il funzionamento quotidiano. Se manca l’autorizzazione per una dimensione/metrica/suite di rapporti dal profilo di prodotto associato all’utente dell’account tecnico, le API che utilizziamo non potranno essere utilizzate per tali richieste.

Se leggiamo i dettagli di un componente Analytics (come metriche/dimensioni/segmenti/suite di rapporti), l’API non restituisce questi componenti nel risultato (che potrebbe sembrare qualcosa che sia stato eliminato dal lato Analytics o che non sia presente). L’API di Analytics rifiuterà tali richieste ed eseguirà l’errore.

La soluzione consiste nell’aggiornare il profilo di prodotto nel contesto utente di Analytics del token utente tecnico con i componenti appena creati/mancanti aggiungendo questi componenti in [Adobe Admin Console](https://adminconsole.adobe.com/).

## Collegamenti utili

* [Aggiornare l’ambiente](../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../platform/using/faq-build-upgrade.md)
* [Scarica la build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Rendere la nuova console client disponibile agli utenti](../installation/using/client-console-availability-for-windows.md)
* [Installare la console client di Campaign](../installation/using/installing-the-client-console.md)
