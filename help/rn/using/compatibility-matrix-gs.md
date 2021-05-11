---
solution: Campaign Classic
product: campaign
title: Matrice di compatibilità per Campaign [!DNL Gold Standard]
description: 'Matrice di compatibilità di Campaign Classic per la versione [!DNL Gold Standard] '
feature: Panoramica
role: Business Practitioner
level: Beginner
exl-id: 5c0ccaf6-7f82-4e4b-9247-261dbd0f127c
translation-type: tm+mt
source-git-commit: 62b2fdd807a654ab81d19a1b5c0d8ac88648e45c
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 90%

---

# Matrice di compatibilità per [!DNL Gold Standard]{#compatibility-matrix-gs}

Questo documento elenca tutti i sistemi e i componenti supportati per le build **Adobe Campaign Classic[!DNL Gold Standard]** 19.1. Prodotti e versioni non compresi in questo elenco non sono compatibili con questa versione di Adobe Campaign.

## Note importanti{#important-notes-gs}

Salvo diversa indicazione, sono supportate tutte le versioni minori.

Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati in questa pagina. Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni, che vengono rimosse dalla matrice di compatibilità nella versione del prodotto successiva. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

## Sistemi operativi{#OperatingSystems-gs}

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

## Server web{#WebServers-gs}

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

## Strumenti{#Tools-gs}

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

## Server RDBMS{#RDBMSservers-gs}

>[!NOTE]
>
>Il driver RDBMS deve corrispondere alla versione del server RDBMS.

<table>
<tbody>
<tr>
<td> Oracle</td>
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
<p>Attenzione: Microsoft SQL Server non è supportato come database principale quando il server Campaign è in esecuzione su Linux. <a href="https://docs.adobe.com/content/help/it/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Ulteriori informazioni</a>.</p>
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

## Connettori di gestione delle relazioni con i clienti{#CRMconnectors-gs}

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
<tr><td> API Oracle On Demand</td>
<td>
<p>API Web Services v1.0</p>
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

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td> Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td> Oracle</td>
<td>
<p>12 quater</p>
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


## Console client {#ClientConsoleoperatingsystems}

:warning: Per utilizzare la console client di Campaign sono necessari i seguenti sistemi operativi e browser.

### Sistemi operativi

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

### Browser

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
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

## SDK per dispositivi mobili{#MobileSDK}

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

## Browser{#Browsers}

I seguenti browser sono compatibili con Campaign per Web Access.

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

## Articoli simili{#Morelikethis-gs}

* [Note sulla versione Campaign Classic](../../rn/using/latest-release.md)
* [Guida all’installazione](../../installation/using/general-architecture.md)
* [Funzioni e sistemi obsoleti](../../rn/using/deprecated-features.md)
* [Procedura di aggiornamento build](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html)
