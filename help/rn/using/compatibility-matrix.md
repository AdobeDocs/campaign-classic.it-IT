---
product: campaign
title: Matrice di compatibilità per Campaign Classic
description: Matrice di compatibilità di Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 100%

---

# Matrice di compatibilità{#compatibility-matrix}



Questo documento elenca tutti i sistemi e i componenti supportati dalla [versione più recente](../../rn/using/latest-release.md) di **Adobe Campaign Classic v7**. I prodotti e le versioni che non fanno parte di questo elenco non sono compatibili con Adobe Campaign.

Se sei un utente della versione [!DNL Gold Standard], consulta [[!DNL Gold Standard] : matrice di compatibilità](../../rn/using/gold-standard.md#compatibility-matrix-gs).

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
<p>7.x</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (a partire da Campaign v7.3)</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019 (a partire da Campaign v7.2)</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Se utilizzi RHEL, disabilita SELinux o fai in modo che gli architetti scrivano regole SELinux personalizzate per evitare che il SELinux abilitato causi problemi alle attività di Campaign.

## Server web{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 su Windows Server 2016 e 2019</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 per RHEL7 - CentOS 7, Debian 8/9, Windows</p>
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
<p>Campaign supporta Java Development Kit (JDK) sviluppato da Oracle e OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (e versioni precedenti se integrate nel sistema)</p>
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

## Sistemi di gestione del database relazionale (RDBMS){#RDBMSservers}

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
<p>14.x (a partire da Campaign v7.3.2)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>Nota:</strong> è inoltre possibile utilizzare Amazon RDS per PostgreSQL con le versioni sopra specificate.</p>
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
<p><strong>Importante:</strong> Microsoft SQL Server non è supportato come database primario quando il server Campaign è in esecuzione su Linux. <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux/prerequisites-of-campaign-installation-in-linux.html?lang=it#database-access-layers">Ulteriori informazioni</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* Il driver RDBMS deve corrispondere alla versione del server RDBMS.
>
>* PostgreSQL è il RDBMS per gli ambienti in hosting.

## Connettori CRM{#CRMconnectors}

I sistemi CRM per la gestione delle relazioni con i clienti compatibili con Adobe Campaign sono elencati di seguito. [Ulteriori informazioni](../../platform/using/crm-connectors.md) sui connettori CRM per Campaign.

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
<p>API web</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

Di seguito sono elencati i database esterni compatibili con il [modulo Federated Data Access](../../installation/using/about-fda.md) di Adobe Campaign. La compatibilità dipende dal [modello di hosting](../../installation/using/hosting-models.md).

Dagli ambienti **Managed Services** (in hosting), **Ibrido** e **On-Premise** è possibile collegare Campaign ai seguenti sistemi di database esterni:

<table>
<tbody>
<td><strong>Sistema di database</strong></td>
<td><strong>Versione del database</strong></td>
<td><strong>Versione di Campaign</strong></td>
<tr>
<td> Amazon Redshift</td>
<td><p> </p>
<td>Minimo v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>BigQuery Google</td>
<td> </td>
<td>Minimo 7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>Minimo v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>Minimo 7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>Minimo v7.0 19.1.4</td>
</tr>
</tbody>
</table>

Negli ambienti **ibridi** e **on-premise** è possibile collegare Campaign ai seguenti sistemi di database esterni: Questi sistemi **non sono compatibili** con gli ambienti Campaign **Managed Services** (in hosting).

<table>
<tbody>
<td><strong>Sistema di database</strong></td>
<td><strong>Versione del database</strong></td>
<td><strong>Versione di Campaign</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>Minimo v7.0 19.1.4</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>Minimo v7.3 </p>
<p>Minimo v7.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>Minimo v7.0</td>
</tr>
<tr>
<td> Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>Minimo v7.0</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versione 1 SPS 12</p>
</td>
<td>Minimo v7.0</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 e SP2</p>
</td>
<td>Minimo v7.0</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15,7</p>
</td>
<td>Minimo v7.0</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (ultima versione)</p>
</td>
<td>Minimo v7.0</td>
</tr>
<tr><td>Hadoop tramite HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>Minimo v7.0</td>
</tr>
</tbody>
</table>



## Console client {#ClientConsoleoperatingsystems}

Per utilizzare la [console client di Campaign](../../installation/using/installing-the-client-console.md) sono **necessari** i seguenti sistemi operativi e browser.

### Sistemi operativi

<table>
<tbody>
<td><strong>Sistema</strong></td>
<td><strong>Versione sistema operativo</strong></td>
<td><strong>Versione di Campaign</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>Minimo v7.3 </p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>Minimo v7.2.1 </p>
<p></p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 Runtime

Per la console client di Campaign è obbligatoria la versione più recente di Microsoft Edge WebView2.

Scarica Microsoft Edge WebView2 dal [sito web per sviluppatori Microsoft](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## SDK per dispositivi mobili{#MobileSDK}

Puoi utilizzare Campaign per [inviare notifiche push](../../delivery/using/about-mobile-app-channel.md) sui sistemi operativi elencati di seguito, utilizzando l’[SDK mobile associato](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

Puoi anche utilizzare l’SDK per Adobe Experience Platform Mobile configurando l’estensione Adobe Campaign nell’interfaccia utente di raccolta dati.

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (a partire da Campaign v7.3), 9.0, 8.x, 7.x</p>
<p>con Mobile SDK build 1.1.1</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>con Mobile SDK build 1.0.26, compatibile con le versioni a 32 e 64 bit. iOS 15 è supportato a partire da Campaign v7.3</p>
</td>
</tr>
</tbody>
</table>

## Browser{#Browsers}

I seguenti browser, nella loro versione più recente, sono compatibili con Campaign per l’[accesso web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## Altri argomenti correlati{#Morelikethis}

* [Note sulla versione Campaign Classic](../../rn/using/latest-release.md)
* [Architettura generale di Campaign](../../installation/using/general-architecture.md)
* [Consigli sui requisiti hardware in base alle dimensioni](../../technotes/using/hardware-sizing.md)
* [Funzioni e sistemi obsoleti](../../rn/using/deprecated-features.md)
* [Procedura di aggiornamento versione](../../production/using/build-upgrade.md)
