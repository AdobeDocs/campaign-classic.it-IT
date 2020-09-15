---
title: Rilascio Gold Standard
seo-title: Rilascio Gold Standard
description: Rilascio Gold Standard
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ac2d993f525eb918ad5e15104eb3ede9eeadfb43
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 14%

---


# Rilascio Gold Standard{#gold-standard}

In qualità di utente Gold Standard, potete beneficiare automaticamente dell&#39;aggiornamento Gold Standard con l&#39;ultima versione stabile senza alcuna azione.

I clienti interni e ibridi possono inoltre beneficiare dei rilasci Gold Standard.

Questa è la nostra versione di supporto a lungo termine. Se effettui la migrazione da una build precedente, ti consigliamo di eseguire prima l&#39;aggiornamento a questa versione.

In questa pagina sono elencate le versioni di Gold Standard.

Per ulteriori informazioni sull&#39;aggiornamento Gold Standard, consultate questo [articolo](https://helpx.adobe.com/it/campaign/kb/gold-standard.html).

## ![](assets/do-not-localize/limited_2.png) Rilascio Gold Standard 10{#gs-10}

_7 luglio 2020_

La build 9032@efd8a94 include la seguente correzione:

È stato risolto un problema che impediva il funzionamento del tracciamento quando la funzione di firma era disabilitata. (NEO-26411)

>[!CAUTION]
>
>È consigliabile aggiornare la console client con quella disponibile in questa versione. Refer to this [page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Release Gold Standard 9{#gs-9}

_22 giugno 2020_

La build 9032@800be2e include le seguenti correzioni:

* Il connettore iOS HTTP2 è stato migliorato (aggiornamenti di terze parti e gestione degli errori). (NEO-25904, NEO-25903, NEO-25799)

Le seguenti correzioni sono correlate al meccanismo di sicurezza dei collegamenti di tracciamento (vedere l&#39;elenco di controllo [](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)Sicurezza e Privacy):

* È stato risolto un problema che impediva il monitoraggio dei &quot;clic di notifica&quot; (notifiche push iOS e Android). (NEO-25965)
* È stato risolto un problema che poteva impedire di aprire/fare clic sugli URL di tracciamento quando si utilizzavano alcune versioni precedenti di Outlook.  (NEO-25688)
* È stato risolto un problema che impediva il funzionamento del tracciamento degli URL tramite frammenti nei parametri di personalizzazione (tag di ancoraggio con cancelletto). (NEO-25774)
* È stato risolto un problema con il servizio anti-phishing. (NEO-25283)
* È stato risolto un problema di tracciamento quando si utilizzavano formule di tracciamento personalizzate specifiche. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Release Gold Standard 8{#gs-8}

_29 aprile 2020_

La build 9032@3a9dc9c include le seguenti correzioni:

* Miglioramento della protezione per il tracciamento dei collegamenti nelle e-mail. Questa opzione è abilitata per impostazione predefinita per tutti i clienti. In aggiunta, è disponibile una funzione di sicurezza avanzata che può essere abilitata contattando l’Assistenza clienti. Ulteriori dettagli sulla funzione e sui passaggi che i clienti non in hosting devono seguire per abilitarla sono disponibili nella [Lista di controllo protezione e privacy](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>In caso di problemi con le notifiche push tramite i collegamenti di tracciamento o le consegne tramite i tag di ancoraggio, si consiglia di disabilitare il nuovo meccanismo di firma per il tracciamento dei collegamenti. La procedura è dettagliata in questa [pagina](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* È stato risolto un problema che poteva impedire la visualizzazione delle immagini sulle consegne di linea. (NEO-23207)
* È stato risolto un problema con l’attività **File Transfer** che impediva il funzionamento dell’autenticazione basata su chiave SFTP su Debian 9. (NEO-23183)
* È stato risolto un problema che poteva interessare la notifica push quando inviata ad alta frequenza. (NEO-20516)
* È stato risolto un problema nella gestione delle risposte delle offerte che poteva causare arresti anomali del server Web. (NEO-19482)
* È stato corretto un errore in Gestione LibreOffice che impediva l’esportazione dei rapporti. (NEO-20982)
* È stato risolto un problema che causava un errore durante l’aggiornamento di numerosi flussi di lavoro tramite un’attività di sondaggio.
* Migliorata la gestione di LibreOffice per evitare errori nell’anteprima delle e-mail con file .odt.
* È stata migliorata la gestione della connessione Apache per evitare la latenza nel servizio Web.
* Migliorata la visualizzazione del tag di versione (7 cifre) nel menu **Informazioni su** .
* Risolto un problema di regressione nella gestione degli elenchi che impediva la pubblicazione delle offerte.
* È stato risolto un problema di regressione che causava l’arresto anomalo del flusso di lavoro di pulizia.
* È stato risolto un problema di regressione minore nei log del flusso di lavoro di pulizia.

## ![](assets/do-not-localize/green_2.png) Release Gold Standard 6{#gs-6}

_9 marzo 2020_

La build 9032@19f73c5 include la seguente correzione:

* È stato risolto un problema con gli account esterni che utilizzavano FTP su SSL. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Release Gold Standard 5{#gs-5}

_17 dicembre 2019_

La build 9032@d6b8062 include la seguente correzione:

* È stato risolto un problema di tracciamento sui seguenti canali di comunicazione: mobile (SMS, MMS), push (iOS, Android) e social network (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Release Gold Standard 4{#gs-4}

_11 dicembre 2019_

La build 9032@bc4a935 include la seguente correzione:

* È stato risolto un problema di prestazioni durante l&#39;invio di messaggi con un database MSSQL. (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Rilascio Gold Standard 3{#gs-3}

_20 novembre 2019_

La build 9032@3468c7b include le seguenti correzioni:

* È stato risolto un problema di accesso tramite l&#39;autenticazione IMS. (NEO-17312)
* È stato risolto un problema che si verificava durante la visualizzazione dei rapporti cumulativi su più consegne. (NEO-18165)
* È stato risolto un problema che poteva bloccare o arrestare il server Web.

## ![](assets/do-not-localize/red_2.png) Release Gold Standard 2{#gs-2}

_19 settembre 2019_

La build 9032@cee805c include le seguenti correzioni:

* È stato risolto un problema durante l&#39;utilizzo del connettore CRM per Salesforce. (NEO-17712)
* È stato risolto un problema di indice che poteva causare problemi di prestazioni durante l&#39;invio di messaggi transazionali.

## ![](assets/do-not-localize/red_2.png) Versione 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_13 agosto 2019_

La build 19.1.4 iniziale include le seguenti correzioni:

* È stato risolto un problema con l&#39;attività del pianificatore che generava messaggi di errore indesiderati durante la configurazione guidata. Ripristino dell&#39;aggiornamento da NEO-11662. (NEO-17097)
* È stata corretta una regressione causata dalla NEO-12727 che poteva causare l&#39;arresto dei flussi di lavoro quando un&#39;attività Test veniva eseguita due volte. (NEO-16835)
* È stato risolto un problema che causava la restituzione di un codice HTTP errato (HTTP 200 OK invece di HTTP 403 Non consentito) quando nelle chiamate API veniva utilizzato un token di sessione non valido o scaduto. (NEO-16826)
* È stato risolto un problema con la chiave DKIM che non era più incorporata nelle e-mail, causando problemi di recapito. (NEO-16804)
* Sono stati risolti diversi problemi relativi alla pianificazione del flusso di lavoro. I flussi di lavoro venivano pianificati una volta al giorno senza tenere conto della configurazione del pianificatore. (NEO-16619, NEO-16426)
