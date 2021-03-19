---
solution: Campaign Classic
product: campaign
title: Note sulla versione Gold Standard
description: Note sulla versione per Campaign Classic Gold Standard
feature: Panoramica
role: Professionista
level: Principiante
translation-type: tm+mt
source-git-commit: 1f718e26aeaa5ed5a58dfd0e3bc29d2dd9e995ee
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 85%

---


# Versioni Gold Standard{#gold-standard}

In questa pagina sono elencate le versioni Gold Standard. Ulteriori informazioni su Campaign Gold Standard [in questa pagina](gs-overview.md).

## ![](assets/do-not-localize/green_2.png) Versione Gold Standard 11{#gs-11}

_2 marzo 2021_

La build 9032@10c2709 include la seguente correzione:

* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453, NEO-31454)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Connettiti a [Distribuzione di software di Adobe](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) per scaricare la nuova versione. Scopri come proporre l’aggiornamento della console a tutti gli utenti finali [in questa pagina](../../installation/using/client-console-availability-for-windows.md).


_22 dicembre 2020_

>[!CAUTION]
>
> * Questa versione include un nuovo protocollo di connessione: se ti connetti a Campaign tramite Adobe Identity Service (IMS), l’aggiornamento è obbligatorio per il server Campaign e la console client per poter connettersi a Campaign dopo il **30 giugno 2021**.
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.
> * Se utilizzi l’integrazione dei trigger di Experience Cloud tramite autenticazione oAuth, devi passare all’Adobe I/O come descritto [in questa pagina](../../integrations/using/configuring-adobe-io.md). La modalità di autenticazione oAuth legacy con Campaign verrà ritirata il **30 novembre 2021**.

>
>
Ulteriori informazioni sono disponibili nelle [Domande frequenti sull’aggiornamento a Gold Standard 11](https://helpx.adobe.com/it/campaign/kb/gold-standard-upgrade.html).

La build 9032@d3b452f include i miglioramenti e le correzioni seguenti:

* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.

* L’autenticazione dell’integrazione dei trigger per accedere alla pipeline, originariamente basata sulla configurazione di autenticazione OAUTH, è ora stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/configuring-adobe-io.md)

* Con la [fine del supporto del protocollo binario legacy del servizio APNs per iOS](https://developer.apple.com/news/?id=c88acm2b), tutte le istanze che lo utilizzano vengono aggiornate al protocollo HTTP/2 nella fase di post-aggiornamento.

* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)

* È stato risolto un problema che poteva causare un errore dei flussi di lavoro durante l’esecuzione di un’attività **Enrichment**. (NEO-17338)

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 10{#gs-10}

_7 luglio 2020_

La build 9032@efd8a94 include la seguente correzione:

È stato risolto un problema che impediva il funzionamento del tracking quando la funzione di firma era disabilitata. (NEO-26411)

>[!CAUTION]
>
>È consigliabile aggiornare la console client con quella disponibile in questa versione. Consulta [questa pagina](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 9{#gs-9}

_22 giugno 2020_

La build 9032@800be2e include le seguenti correzioni:

* Il connettore iOS HTTP2 è stato migliorato (aggiornamenti di terze parti e gestione degli errori). (NEO-25904, NEO-25903, NEO-25799)

Le seguenti correzioni sono legate al meccanismo di sicurezza dei collegamenti di tracking (per ulteriori informazioni, consulta [Lista di controllo sicurezza e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html#signature-mechanism)):

* È stato risolto un problema che impediva il tracking dei “clic di notifica” (notifiche push iOS e Android). (NEO-25965)
* È stato risolto un problema che poteva impedire di aprire/fare clic sugli URL di tracking quando si utilizzavano alcune versioni precedenti di Outlook.  (NEO-25688)
* È stato risolto un problema che impediva il funzionamento del tracking degli URL tramite frammenti nei parametri di personalizzazione (tag di ancoraggio con cancelletto). (NEO-25774)
* È stato risolto un problema riguardante il servizio anti-phishing. (NEO-25283)
* È stato risolto un problema di tracking che si verificava con l’utilizzo di alcune formule personalizzate. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 8{#gs-8}

_29 aprile 2020_

La build 9032@3a9dc9c include le seguenti correzioni:

* Maggiore sicurezza per il tracking dei collegamenti nelle e-mail. Questa opzione è abilitata per impostazione predefinita per tutti i clienti. In aggiunta, è disponibile una funzione di sicurezza avanzata che può essere abilitata contattando l’Assistenza clienti. Ulteriori dettagli sulla funzione e sui passaggi che i clienti non in hosting devono seguire per abilitarla sono disponibili nella [Lista di controllo protezione e privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>In caso di problemi con le notifiche push che utilizzano collegamenti di tracking o con le consegne che utilizzano tag di ancoraggio, si consiglia di disabilitare il nuovo meccanismo di firma per i collegamenti di tracking. La procedura è dettagliata [in questa pagina](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* È stato risolto un problema che poteva impedire la visualizzazione delle immagini nelle consegne in Linea. (NEO-23207)
* È stato risolto un problema dell’attività **File Transfer** che impediva il funzionamento dell’autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)
* È stato risolto un problema che poteva interessare le notifiche push quando inviate con un’elevata frequenza. (NEO-20516)
* È stato risolto un problema nella gestione delle risposte alle offerte che poteva causare arresti anomali del server Web. (NEO-19482)
* È stato corretto un errore nella gestione di LibreOffice che impediva l’esportazione dei report. (NEO-20982)
* È stato risolto un problema che causava un errore durante l’aggiornamento di numerosi flussi di lavoro tramite un’attività di sondaggio.
* Migliorata la gestione di LibreOffice per evitare errori nell’anteprima di file .odt nelle e-mail.
* È stata migliorata la gestione della connessione Apache per evitare la latenza nel servizio Web.
* È stata migliorata la visualizzazione del tag di versione (7 cifre) nel menu **Informazioni su**.
* È stato risolto un problema di regressione nella gestione degli elenchi che impediva la pubblicazione delle offerte.
* È stato risolto un problema di regressione che causava l’arresto anomalo del flusso di lavoro di pulizia.
* È stato risolto un problema di regressione minore nei log del flusso di lavoro di pulizia.

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 6{#gs-6}

_9 marzo 2020_

La build 9032@19f73c5 include la seguente correzione:

* È stato risolto un problema con gli account esterni che utilizzavano FTP su SSL. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 5{#gs-5}

_17 dicembre 2019_

La build 9032@d6b8062 include la seguente correzione:

* È stato risolto un problema di tracking sui seguenti canali di comunicazione: mobile (SMS, MMS), push (iOS, Android) e social network (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 4{#gs-4}

_11 dicembre 2019_

La build 9032@bc4a935 include la seguente correzione:

* È stato risolto un problema di prestazioni riguardante l’invio di messaggi con un database MSSQL. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 3{#gs-3}

_20 novembre 2019_

La build 9032@3468c7b include le seguenti correzioni:

* È stato risolto un problema di accesso tramite l’autenticazione IMS. (NEO-17312)
* È stato risolto un problema che si verificava durante la visualizzazione dei report cumulativi su più consegne. (NEO-18165)
* È stato risolto un problema che poteva bloccare o arrestare il server Web.

## ![](assets/do-not-localize/red_2.png) Versione Gold Standard 2{#gs-2}

_19 settembre 2019_

La build 9032@cee805c include le seguenti correzioni:

* È stato risolto un problema che si verificava con l’utilizzo del connettore di gestione delle relazioni con i clienti per Salesforce. (NEO-17712)
* È stato risolto un problema di indice che poteva causare problemi di prestazioni durante l’invio di messaggi transazionali.

## ![](assets/do-not-localize/red_2.png) Versione 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_13 agosto 2019_

La build 19.1.4 iniziale include le seguenti correzioni:

* È stato risolto un problema dell’attività di pianificazione che generava messaggi di errore indesiderati durante la configurazione guidata. Ripristino dell’aggiornamento da NEO-11662. (NEO-17097)
* È stata corretta una regressione causata dalla NEO-12727 che poteva causare l’arresto dei flussi di lavoro quando un’attività Test veniva eseguita due volte. (NEO-16835)
* È stato risolto un problema che causava la restituzione di un codice HTTP errato (HTTP 200 OK invece di HTTP 403 Non consentito) quando nelle chiamate API veniva utilizzato un token di sessione non valido o scaduto. (NEO-16826)
* È stato risolto un problema con la chiave DKIM che, non essendo più incorporata nelle e-mail, causava problemi di recapito. (NEO-16804)
* Sono stati risolti diversi problemi relativi alla pianificazione dei flussi di lavoro. I flussi di lavoro venivano programmati per un’unica esecuzione giornaliera, senza tenere conto della configurazione del pianificatore. (NEO-16619, NEO-16426)
