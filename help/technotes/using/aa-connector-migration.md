---
product: campaign
title: Migrare al connettore Adobe Analytics
description: Campaign - Domande frequenti sul connettore Analytics
feature: Technote, Analytics Integration
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride v7"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# Come migrare le integrazioni di Genesis esistenti al connettore Adobe Analytics {#acc-aa-faq}

A partire dalla versione 21.1.3 di Campaign Classic v7, il Connettore dati di Adobe Analytics è diventato obsoleto. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=it)

Il 1° agosto 2021 Adobe Campaign Classic è stato rimosso dalla precedente interfaccia utente di Data Connectors, tuttavia, le integrazioni esistenti di Campaign continueranno a raccogliere e trasmettere dati ad Adobe Analytics fino al 17 agosto 2022. Dopo tale data, l’integrazione cesserà di raccogliere e trasmettere dati ad Adobe Analytics.

**devi implementare** la nuova integrazione del connettore Adobe Analytics su Adobe Exchange che sostituisce l&#39;integrazione legacy di Data Connectors. Per ulteriori informazioni su Adobe Analytics Connector, consulta [questa pagina](../../integrations/using/gs-aa.md).

Per qualsiasi domanda su queste modifiche, leggere le [domande frequenti](#faq-aa). Per ulteriori informazioni, contatta [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

>[!NOTE]
>
>Se esegui la migrazione da un connettore dati Adobe Analytics esistente (precedentemente noto come integrazione di Genesis) e utilizzi la nuova architettura di classificazione in Adobe Analytics, sono necessarie versioni di build a partire dalla versione 7.3.1 o 8.4.1 per poter migrare al nuovo connettore Adobe Analytics.

## Cosa è cambiato?

È ora disponibile una nuova integrazione tra Campaign Classic v7 e Adobe Analytics. Le modifiche principali sono elencate di seguito.

* La classificazione **Contact Date**, che è di tipo data, è stata dichiarata obsoleta da Adobe Analytics. Per le integrazioni migrate, rimarrà dello stesso tipo. Per qualsiasi **Data contatto** creata da Campaign, il tipo sarà **Stringa**.

* **Le regole di elaborazione** vengono create da Adobe Campaign come parte delle nuove integrazioni. **Le regole di elaborazione** devono essere create manualmente da Adobe Analytics o utilizzare direttamente l&#39;implementazione JavaScript lato client. **Le regole di elaborazione** rimarranno intatte per le integrazioni esistenti.

* I flussi di lavoro tecnici incorporati e il loro comportamento rimangono gli stessi. Sono state modificate solo le API di back-end utilizzate dai flussi di lavoro per inviare/richiamare dati da/verso Adobe Analytics.

* Affinché il nuovo connettore funzioni, il processo `nlserver` deve essere configurato con l&#39;utente dell&#39;account tecnico IMS. Questa modifica deve essere eseguita per Adobe. Per implementare questo elemento, contatta [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Se eri un’API di Adobe Genesis in flussi di lavoro personalizzati per estrarre e inviare dati da Adobe Analytics, ora devi utilizzare le nuove API di Adobe Analytics 1.4/2.0. [Ulteriori informazioni](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Sei interessato?

Se utilizzi un Connettore dati di Adobe Analytics esistente (precedentemente noto come integrazione di Genesis) e l’integrazione è stata implementata su una build inferiore rispetto a Campaign 21.1.3, sei interessato.

Scopri come controllare la versione [in questa sezione](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Come si esegue l’aggiornamento?

Devi effettuare l&#39;aggiornamento a Campaign 21.1.3 (o più) **prima del 17 agosto 2022**.

In qualità di cliente in hosting, Adobe collaborerà con te per aggiornare le istanze alla versione più recente. Potrai quindi utilizzare [il connettore Adobe Analytics](../../platform/using/gs-aa.md).

In qualità di cliente on-premise/ibrido, devi effettuare l’aggiornamento a una delle versioni più recenti per beneficiare della nuova integrazione.
Una volta aggiornate tutte le istanze, potrai [implementare la nuova integrazione](../../integrations/using/adobe-analytics-provisioning.md) in Adobe Analytics Connector e garantire una transizione senza problemi.

## Domande frequenti{#faq-aa}

**Come posso ottenere i registri?**

I flussi di lavoro e la configurazione dell&#39;interfaccia utente sono dotati di **registrazione dettagliata**.

In modalità dettagliata, vengono stampate anche le intestazioni di richiesta e risposta per ogni richiesta API ad Adobe Analytics.

In qualità di utente on-premise, puoi implementare la modalità dettagliata come segue:

* Per attivare la modalità dettagliata per l&#39;interfaccia utente, eseguire nuovamente il processo `web` in modalità dettagliata.
* Per attivare la modalità dettagliata per i flussi di lavoro **webAnalytics**: selezionare l&#39;opzione **Esegui nel motore** dalle proprietà del flusso di lavoro ed eseguire nuovamente `wfserver` in modalità dettagliata.

**Che cosa significa l&#39;errore &quot;Proprietario integrazione non amministratore&quot;?**

Ulteriori informazioni sull&#39;errore `Integration Owner Not Admin` di Data Connectors in [questa pagina](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Al termine della migrazione al nuovo connettore, cosa succederà ai dati e alle suite di rapporti precedenti?**

Dopo la migrazione, un nuovo connettore (migrato dal vecchio connettore) inizierà a inviare dati alla stessa suite di rapporti e i dati esistenti non saranno interessati: verranno aggiunti ai dati esistenti.

**Alcune evar, eventi o suite di rapporti esistenti presenti in Analytics non sono visibili in Campaign. Cosa devo fare?**

L’integrazione si basa sui dati del token dell’account tecnico per il funzionamento quotidiano. Se manca l’autorizzazione per una dimensione, una metrica o una suite di rapporti dal profilo di prodotto associato all’utente dell’account tecnico, le API che utilizziamo falliranno semplicemente per tali richieste.

Se stiamo leggendo i dettagli di un componente Analytics (come metriche/dimensioni/segmenti/suite di rapporti), l’API non restituirà questi componenti nel risultato (che potrebbe sembrare che qualcosa sia stato eliminato dal lato Analytics o che non sia presente). Le API di Analytics rifiuteranno tali richieste e si verificherà un errore.

La soluzione consiste nell&#39;aggiornare il **profilo di prodotto** nel contesto utente di Analytics del token utente tecnico con i componenti appena creati/mancanti aggiungendo questi componenti in [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Per ulteriori informazioni, contatta [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Collegamenti utili

* [Aggiornare l’ambiente](../../production/using/build-upgrade.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Scarica build Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Rendi la nuova Client Console disponibile agli utenti](../../installation/using/client-console-availability-for-windows.md)
* [Installare la console client di Campaign](../../installation/using/installing-the-client-console.md)
