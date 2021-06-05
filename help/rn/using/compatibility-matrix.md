---
product: campaign
title: Matrice di compatibilità per Campaign Classic
description: Matrice di compatibilità di Campaign Classic
feature: Panoramica
role: Business Practitioner
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 1d25bdaf0d118ec5788d467c48c3c40c5891e46d
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 99%

---

# Matrice di compatibilità{#compatibility-matrix}

Questo documento elenca tutti i sistemi e i componenti supportati [dalla versione](../../rn/using/latest-release.md) più recente di **Adobe Campaign Classic**. I prodotti e le versioni che non fanno parte di questo elenco non sono compatibili con Adobe Campaign.

Se sei un utente della versione [!DNL Gold Standard], consulta [[!DNL Gold Standard] : matrice di compatibilità](../../rn/using/compatibility-matrix-gs.md).

## Note importanti{#important-notes}

Salvo diversa indicazione, sono supportate tutte le versioni minori.

L’[ultima versione](../../rn/using/latest-release.md) di Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati in questa pagina. Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni, che vengono rimosse dalla matrice di compatibilità nella versione del prodotto successiva. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

Per ulteriori informazioni sugli elementi obsoleti, consulta [questa pagina](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>La matrice viene regolarmente aggiornata con l’aggiunta dei nuovi elementi supportati e la rimozione di quelli obsoleti.

## Sistemi operativi{#OperatingSystems}

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
<p>10 (64 bit)</p>
<p>9 (64 bit)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x (64 bit)</p>
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

## Server web{#WebServers}

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
</td>
</tr>
</tbody>
</table>

## Strumenti{#Tools}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>11</p>
<p>9</p>
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

## Server RDBMS{#RDBMSservers}

>[!NOTE]
>
>Il driver RDBMS deve corrispondere alla versione del server RDBMS.

<table>
<tbody>
<tr>
<td> Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
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
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL è il server di database predefinito per gli ambienti in hosting.

## Connettori CRM{#CRMconnectors}

<table>
<tbody>
<tr>
<td>API connettore Salesforce</td>
<td>
<p>API versione 49</p>
</td>
</tr>
<tr>
<td>Connettore Microsoft Dynamics</td>
<td>
<p>API web: Dynamics 365 locale e online</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Vertica</td>
<td> </td>
</tr>
<tr>
<td>Big Query di Google</td>
<td> </td>
</tr>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td> Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td> Oracle</td>
<td>
<p>19 quater</p>
<p>18 quater</p>
<p>12 quater</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
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
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
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


## Altri argomenti correlati{#Morelikethis}

* [Note sulla versione Campaign Classic](../../rn/using/latest-release.md)
* [Guida all’installazione](../../installation/using/general-architecture.md)
* [Funzioni e sistemi obsoleti](../../rn/using/deprecated-features.md)
* [Procedura di aggiornamento versione](../../production/using/build-upgrade.md)
