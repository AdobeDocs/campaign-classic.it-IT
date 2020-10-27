---
title: Matrice di compatibilità standard Gold
description: Matrice di compatibilità Campaign Classic per la versione Gold Standard
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7p
translation-type: tm+mt
source-git-commit: e615b2420d126cd42ed52257491282b36975f9ff
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 13%

---


# Matrice di compatibilità standard Gold{#compatibility-matrix-gs}

Questo documento elenca tutti i sistemi e i componenti supportati per le build **Adobe Campaign Classic Gold Standard** 19.1. I prodotti e le versioni che non fanno parte di questo elenco non sono compatibili con  Adobe Campaign.

## Note importanti{#important-notes-gs}

Salvo diversa indicazione, sono supportate tutte le versioni minori.

Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati in questa pagina. Poiché versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori,  Adobe Campaign non sarà più compatibile con tali versioni e saranno rimossi dalla nostra matrice di compatibilità nella release successiva del prodotto. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

## Operating Systems{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8,x (64 bit)</p>
<p>7,x (64 bit)</p>
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
<p>7,x (64 bit)</p>
<p><strong>Importante:</strong> Se utilizzi RHEL, devi essere disposto a disabilitare SELLinux o a far scrivere agli architetti regole SELLinux personalizzate per verificare che un SELLinux abilitato non causi problemi con le operazioni Campaign.</p>
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

## Web Servers{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 su Windows Server 2016</p>
<p>8.5 in Windows Server 2012 R2</p>
<p>8.0 su Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 per RHEL7 - CentOS 7, Debian 8/9, Windows (64 bit)</p>
<p>2.2 solo per RHEL6 - CentOS 6 (64 bit)</p>
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
<p>L'applicazione è stata approvata per Java Development Kit (JDK) sviluppato da Oracle e per OpenJDK.</p>
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
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11 g R2</p>
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
<p>Nota: è inoltre possibile utilizzare  Amazon RDS per PostgreSQL con le versioni sopra specificate.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2018</p>
<p>2018 R2</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 e SP2</p>
<p>Avviso: Microsoft SQL Server non è supportato come database principale quando il server Campaign è in esecuzione su Linux. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Ulteriori informazioni</a>.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Avviso: DB2 UDB non è consentito per le nuove installazioni.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL è il server di database predefinito per gli ambienti ospitati.

## CRM connectors{#CRMconnectors-gs}

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
<tr><td>API Oracle On Demand</td>
<td>
<p>API Web Services v1.0</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>API Soap - On-premise: 2007, 2015, 2016</p>
<p>API Soap - Online: 2015, 2016</p>
<p>API Web - In sede e Online: 365, 2016, 2016 Aggiornamento 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
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
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versione 1 SP12 o successiva</p>
</td>
</tr>
<tr><td>Hadoop tramite HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
<tr>
<td>Snowflake </td>
<td> </td>
</tr>
</tbody>
</table>

## Sistemi operativi della console client{#ClientConsoleoperatingsystems-gs}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>Sette</p>
<p>8</p>
<p>10 (consigliato per le istanze giapponesi)</p>
</td>
</tr>
</tbody>
</table>

## SDK per dispositivi mobili{#MobileSDK-gs}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>con SDK per dispositivi mobili build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 12</p>
<p>con build SDK per dispositivi mobili 1.0.25, compatibile con le versioni a 32 e a 64 bit.</p>
</td>
</tr>
</tbody>
</table>

## Browser{#Browsers-gs}

Per i seguenti browser, è supportata la versione più recente: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

Internet Explorer 11 è supportato.

## Più simile{#Morelikethis-gs}

* [Note sulla versione Campaign Classic](../../rn/using/latest-release.md)
* [Guida all&#39;installazione](../../installation/using/general-architecture.md)
* [Funzioni e sistemi obsoleti](../../rn/using/deprecated-features.md)
* [Procedura di aggiornamento build](https://helpx.adobe.com/it/campaign/kb/acc-build-upgrade.html)
