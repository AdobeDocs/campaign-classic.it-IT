---
product: campaign
title: “Versioni [!DNL Gold Standard]”
description: Note sulla versione e Matrice di compatibilità per Campaign Classic [!DNL Gold Standard]
feature: Release Notes
role: User
level: Beginner
hidefromtoc: true
hide: true
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: ht
source-wordcount: '1774'
ht-degree: 100%

---

# Versioni [!DNL Gold Standard]{#gold-standard}



Puoi trovare in questa pagina le note sulla versione e la matrice di compatibilità per le versioni [!DNL Gold Standard].

## Note sulla versione [!DNL Gold Standard]


### [!DNL Gold Standard] versione 12{#gs-12}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_7 settembre 2021_

La build 9032@554dbcd include la seguente correzione:

* È stato risolto un problema che causava un errore 500 durante l’apertura del collegamento a un’applicazione web in una consegna in linea con il tracciamento abilitato.

_27 agosto 2021_

La build 9032@99a3894 include le seguenti correzioni:

* La funzione di firma di tracciamento è stata migliorata per evitare errori collegati al modo in cui strumenti di terze parti (client e-mail, browser Internet, ecc.) gestiscono i caratteri speciali. I parametri URL sono ora codificati.
* È stato risolto un problema relativo ai selettori di date che poteva causare la visualizzazione di un messaggio di errore di blocco nella console. (NEO-36345)

### [!DNL Gold Standard] versione 11{#gs-11}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_14 aprile 2021_

La build 9032@d030c36 include la seguente correzione:

* È stata corretta una regressione della console client che causava messaggi di errore persistenti nella schermata di connessione IMS. (NEO-34821)
* Questa build della console è necessaria per mantenere l’[accesso IMS](../../technotes/using/ims-updates.md).

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!CAUTION]
>
> * Se ti connetti a Campaign con il tuo Adobe ID, tramite Adobe Identity Management Service (IMS), è necessario eseguire l’aggiornamento affinché il server Campaign e la console client possano connettersi a Campaign dopo il **30 giugno 2021**. [Ulteriori informazioni](../../technotes/using/ims-updates.md)
> * Questa versione include una [correzione di sicurezza](https://helpx.adobe.com/it/security/products/campaign/apsb21-04.html): l’aggiornamento è obbligatorio per rafforzare la sicurezza dell’ambiente.
> * Se utilizzi l’integrazione Experience Cloud Triggers tramite autenticazione OAuth, devi passare ad Adobe I/O come descritto [in questa pagina](../../integrations/using/about-triggers.md#implement). La modalità di autenticazione OAuth legacy con Campaign [è stata ritirata](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) a **settembre 2021**. Gli ambienti in hosting usufruiscono di una proroga fino al **23 febbraio 2022**. Se sei un cliente on-premise o ibrido, contatta l’Assistenza clienti Adobe per estendere il supporto fino a febbraio 2022. Devi fornire ad Adobe [l’AppID dell’applicazione OAuth](../../integrations/using/configuring-pipeline.md#step-optional).
>
>Per ulteriori informazioni, consulta questa [[!DNL Gold Standard] sezione](../../rn/using/gold-standard.md).

_2 marzo 2021_

La build 9032@10c2709 include la seguente correzione:

* È stata corretta una regressione che impediva l’utilizzo di alcuni componenti della console, come il selettore data e la gestione delle immagini nelle consegne. (NEO-31453, NEO-31454)

**È obbligatorio solo l’aggiornamento della console. Non è richiesto alcun aggiornamento del server.**

>[!NOTE]
>
> Per scaricare la nuova versione, accedi ad [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html). Per informazioni su come proporre l’aggiornamento della console a tutti gli utenti finali, visita [questa pagina](../../installation/using/client-console-availability-for-windows.md).

_22 dicembre 2020_

La build 9032@d3b452f include i miglioramenti e le correzioni seguenti:

* Il protocollo di connessione è stato aggiornato per adeguarlo al nuovo meccanismo di autenticazione IMS.

* L’autenticazione dell’integrazione dei trigger per accedere alla pipeline, originariamente basata sulla configurazione di autenticazione OAUTH, è ora stata modificata e spostata in Adobe I/O. [Ulteriori informazioni](../../integrations/using/about-triggers.md#implement)

* Con la [fine del supporto del protocollo binario legacy del servizio APNs per iOS](https://developer.apple.com/news/?id=c88acm2b), tutte le istanze che lo utilizzano vengono aggiornate al protocollo HTTP/2 nella fase di post-aggiornamento.

* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-27777)

* È stato risolto un problema che poteva causare un errore dei flussi di lavoro durante l’esecuzione di un’attività **Enrichment**. (NEO-17338)

### [!DNL Gold Standard] versione 10{#gs-10}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_7 luglio 2020_

La build 9032@efd8a94 include la seguente correzione:

È stato risolto un problema che impediva il funzionamento del tracking quando la funzione di firma era disabilitata. (NEO-26411)

>[!CAUTION]
>
>È consigliabile aggiornare la console client con quella disponibile in questa versione. Consulta [questa pagina](../../installation/using/installing-the-client-console.md)

### [!DNL Gold Standard] versione 9{#gs-9}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_22 giugno 2020_

La build 9032@800be2e include le seguenti correzioni:

* Il connettore iOS HTTP2 è stato migliorato (aggiornamenti di terze parti e gestione degli errori). (NEO-25904, NEO-25903, NEO-25799)

Le seguenti correzioni sono legate al meccanismo di sicurezza dei collegamenti di tracking (per ulteriori informazioni, consulta [Lista di controllo sicurezza e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html#signature-mechanism)):

* È stato risolto un problema che impediva il tracking dei “clic di notifica” (notifiche push iOS e Android). (NEO-25965)
* È stato risolto un problema che poteva impedire di aprire/fare clic sugli URL di tracking quando si utilizzavano alcune versioni precedenti di Outlook.  (NEO-25688)
* È stato risolto un problema che impediva il funzionamento del tracking degli URL tramite frammenti nei parametri di personalizzazione (tag di ancoraggio con cancelletto). (NEO-25774)
* È stato risolto un problema riguardante il servizio anti-phishing. (NEO-25283)
* È stato risolto un problema di tracking che si verificava con l’utilizzo di alcune formule personalizzate. (NEO-25277)

### [!DNL Gold Standard] versione 8{#gs-8}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_29 aprile 2020_

La build 9032@3a9dc9c include le seguenti correzioni:

* Maggiore sicurezza per il tracking dei collegamenti nelle e-mail. Questa opzione è abilitata per impostazione predefinita per tutti i clienti. In aggiunta, è disponibile una funzione di sicurezza avanzata che può essere abilitata contattando l’Assistenza clienti. Ulteriori dettagli sulla funzione e sui passaggi che i clienti non in hosting devono seguire per abilitarla sono disponibili nella [Lista di controllo protezione e privacy](https://helpx.adobe.com/it/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>In caso di problemi con le notifiche push che utilizzano collegamenti di tracking o con le consegne che utilizzano tag di ancoraggio, si consiglia di disabilitare il nuovo meccanismo di firma per i collegamenti di tracking. La procedura è dettagliata [in questa pagina](https://helpx.adobe.com/it/campaign/kb/acc-security.html#signature-mechanism)

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

### [!DNL Gold Standard] versione 6{#gs-6}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_9 marzo 2020_

La build 9032@19f73c5 include la seguente correzione:

* È stato risolto un problema con gli account esterni che utilizzavano FTP su SSL. (NEO-20498)

### [!DNL Gold Standard] versione 5{#gs-5}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_17 dicembre 2019_

La build 9032@d6b8062 include la seguente correzione:

* È stato risolto un problema di tracking sui seguenti canali di comunicazione: mobile (SMS, MMS), push (iOS, Android) e social network (Facebook, X, in precedenza noto come Twitter). (NEO-19595)

### [!DNL Gold Standard] versione 4{#gs-4}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_11 dicembre 2019_

La build 9032@bc4a935 include la seguente correzione:

* È stato risolto un problema di prestazioni riguardante l’invio di messaggi con un database MSSQL. (NEO-17558)

### [!DNL Gold Standard] versione 3{#gs-3}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_20 novembre 2019_

La build 9032@3468c7b include le seguenti correzioni:

* È stato risolto un problema di accesso tramite l’autenticazione IMS. (NEO-17312)
* È stato risolto un problema che si verificava durante la visualizzazione dei report cumulativi su più consegne. (NEO-18165)
* È stato risolto un problema che poteva bloccare o arrestare il server Web.

### [!DNL Gold Standard] versione 2{#gs-2}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_19 settembre 2019_

La build 9032@cee805c include le seguenti correzioni:

* È stato risolto un problema che si verificava con l’utilizzo del connettore di gestione delle relazioni con i clienti per Salesforce. (NEO-17712)
* È stato risolto un problema di indice che poteva causare problemi di prestazioni durante l’invio di messaggi transazionali.

### Versione 19.1.4 - Build 9032{#release-19-1-4-build-9032}

[!BADGE Obsoleta]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Obsoleta"}

_13 agosto 2019_

La build 19.1.4 iniziale include le seguenti correzioni:

* È stato risolto un problema dell’attività di pianificazione che generava messaggi di errore indesiderati durante la configurazione guidata. Ripristino dell’aggiornamento da NEO-11662. (NEO-17097)
* È stata corretta una regressione causata dalla NEO-12727 che poteva causare l’arresto dei flussi di lavoro quando un’attività Test veniva eseguita due volte. (NEO-16835)
* È stato risolto un problema che causava la restituzione di un codice HTTP errato (HTTP 200 OK invece di HTTP 403 Non consentito) quando nelle chiamate API veniva utilizzato un token di sessione non valido o scaduto. (NEO-16826)
* È stato risolto un problema con la chiave DKIM che, non essendo più incorporata nelle e-mail, causava problemi di recapito. (NEO-16804)
* Sono stati risolti diversi problemi relativi alla pianificazione dei flussi di lavoro. I flussi di lavoro venivano programmati per un’unica esecuzione giornaliera, senza tenere conto della configurazione del pianificatore. (NEO-16619, NEO-16426)


## Matrice di compatibilità per [!DNL Gold Standard]{#compatibility-matrix-gs}

Questa sezione elenca tutti i sistemi e i componenti supportati per le build 19.1 di **Adobe Campaign Classic[!DNL Gold Standard]**. Prodotti e versioni non compresi in questo elenco non sono compatibili con questa versione di Adobe Campaign.

>[!CAUTION]
>Salvo diversa indicazione, sono supportate tutte le versioni minori.
>
>Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati in questa pagina. Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni, che vengono rimosse dalla matrice di compatibilità nella versione del prodotto successiva. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.
>

### Sistemi operativi{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bit)</p>
<p>7.x (64 bit)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 bit)</p>
<p>8 (64 bit)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bit)</p>
<p><strong>Importante:</strong> se utilizzi RHEL, disabilita SELinux o fai in modo che gli architetti scrivano regole SELinux personalizzate per evitare che il SELinux abilitato causi problemi alle attività di Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### Server web{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 su Windows Server 2016</p>
<p>8.5 su Windows Server 2012 R2</p>
<p>8.0 su Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 per RHEL7 - CentOS 7, Debian 8/9, Windows (64 bit)</p>
<p>2.2 per RHEL6 - CentOS 6 (64 bit)</p>
</td>
</tr>
</tbody>
</table>

### Strumenti{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>L’applicazione è stata approvata per Java Development Kit (JDK) sviluppato da Oracle e per OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (e versioni precedenti se integrate nel sistema)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### Server RDBMS{#RDBMSservers-gs}

>[!NOTE]
>
>Il driver RDBMS deve corrispondere alla versione del server RDBMS.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Nota: è inoltre possibile utilizzare Amazon RDS per PostgreSQL con le versioni sopra specificate.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 e SP2</p>
<p>Avvertenza: Microsoft SQL Server non è supportato come database primario quando il server Campaign è in esecuzione su Linux.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Avviso: per le nuove installazioni non è consentito DB2 UDB.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL è il server di database predefinito per gli ambienti in hosting.

### Connettori CRM{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>API connettore Salesforce</td>
<td>
<p>API versione 37</p>
</td>
</tr>
<tr>
<td>API SFDC</td>
<td>
<p>API versione 21</p>
<p>API versione 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>API Soap - On-premise: 2007, 2015, 2016</p>
<p>API Soap - Online: 2015, 2016</p>
<p>API web - On-premise e online: 365, 2016, 2016 aggiornamento 1</p>
</td>
</tr>
</tbody>
</table>

### Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td> Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 e SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15,7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versione 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop tramite HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>

### Console client {#ClientConsoleoperatingsystems}

`:warning:` Per utilizzare la console client di Campaign sono necessari i seguenti sistemi operativi e browser.

#### Sistemi operativi

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (consigliato per le istanze giapponesi)</p>
</td>
</tr>
</tbody>
</table>

#### Browser

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### Mobile SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>per Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>con la build 1.0.27 dell’SDK per dispositivi mobili.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>con la build 1.0.26 dell’SDK per dispositivi mobili, compatibile con le versioni a 32 e a 64 bit.</p>
</td>
</tr>
</tbody>
</table>

### Browser{#Browsers}

I seguenti browser sono compatibili con Campaign per accesso web.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Versione più recente</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Versione più recente</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Versione più recente</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Versione più recente</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
