---
product: campaign
title: Matrice di compatibilità per Campaign Classic
description: Matrice di compatibilità di Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 100%

---

# Matrice di compatibilità {#compatibility-matrix}

L’[ultima versione](../../rn/using/latest-release.md) di Adobe Campaign Classic v7 è compatibile con tutti i sistemi e gli strumenti elencati in questa pagina. Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni, che vengono rimosse dalla matrice di compatibilità nella versione del prodotto successiva. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi. Per ulteriori informazioni sugli elementi obsoleti, consulta [questa pagina](../../rn/using/deprecated-features.md).

Salvo diversa indicazione, sono supportate tutte le versioni minori.

>[!CAUTION]
>
>Questa matrice viene regolarmente aggiornata con l’aggiunta dei nuovi sistemi e strumenti supportati e la rimozione di quelli obsoleti.

## Sistemi operativi {#OperatingSystems}

In qualità di cliente on-premise/ibrido, devi installare Adobe Campaign in uno dei sistemi operativi elencati di seguito. Ulteriori informazioni sui passaggi per l’installazione di Campaign Classic v7 sono disponibili in [questa pagina](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Sistema operativo</strong></td>
<td><strong>Versione del sistema operativo</strong></td>
<td><strong>Versione minima di Campaign</strong></td>
<tr>
<td>
<p>Debian</p>
</td>
<td>
<p>11</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Red Hat Enterprise Linux (RHEL)</p>
</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Windows Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Se utilizzi RHEL, è necessario disabilitare [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) o a fare in modo che gli architetti scrivano regole SELinux personalizzate per evitare che il SELinux abilitato causi problemi alle attività di Campaign.

## Server web {#WebServers}

In qualità di cliente on-premise/ibrido, a seconda del sistema operativo in uso, devi integrare Campaign in uno dei server web elencati di seguito. Ulteriori informazioni sui passaggi di configurazione dei server web sono disponibili in [questa pagina](../../installation/using/integration-into-a-web-server-for-windows.md) (per Windows) e in [questa pagina](../../installation/using/integration-into-a-web-server-for-linux.md) (per Linux).

<table>
<tbody>
<td><strong>Server web</strong></td>
<td><strong>Versione server web</strong></td>
<tr>
<td>
<p>Microsoft IIS</p>
</td>
<td>
<p>10.0</p>
</td>
</tr>
<tr>
<td>
<p>Apache</p>
</td>
<td>
<p>2,4</p>
</td>
</tr>
</tbody>
</table>

## Strumenti {#Tools}

In qualità di cliente on-premise/ibrido, devi installare e configurare gli strumenti elencati di seguito. [Ulteriori informazioni](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Strumento</strong></td>
<td><strong>Versione</strong></td>
<td><strong>Versione minima di Campaign</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>Per ulteriori informazioni, consulta <a href="../../installation/using/application-server.md#jdk" target="_blank">questa pagina</a>.</p>
</td>
<td>
<p>17</p>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>obbligatorio a partire dalla versione v7.4.1</p>
<p>obbligatorio a partire dalla versione v7.4.1</p>
<p>fino alla versione v7.4.1</p>
<p>fino alla versione v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (e versioni precedenti se integrate nel sistema)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Sistemi di gestione del database relazionale (RDBMS) {#RDBMSservers}

In qualità di cliente on-premise/ibrido, devi installare e configurare uno dei database elencati di seguito. [Ulteriori informazioni](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Sistema di database</strong></td>
<td><strong>Versione del database</strong></td>
<td><strong>Versione minima di Campaign</strong></td>
<tr>
<td>
<p>Oracle</p>
</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>PostgreSQL</p>
</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Microsoft SQL Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* Il driver RDBMS deve corrispondere alla versione del server RDBMS.
>
>* Microsoft SQL Server non è supportato come database principale quando il server Campaign è in esecuzione su Linux. [Ulteriori informazioni](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* È inoltre possibile utilizzare Amazon RDS per PostgreSQL con le versioni sopra specificate.
>
>* PostgreSQL è il RDBMS per gli ambienti in hosting/Managed Cloud Services.


## Connettori CRM {#CRMconnectors}

I sistemi CRM per la gestione delle relazioni con i clienti compatibili con Adobe Campaign sono elencati di seguito. [Ulteriori informazioni](../../platform/using/crm-connectors.md) sui connettori CRM per Campaign.

<table>
<tbody>
<tr>
<td>
<p>API connettore Salesforce</p>
</td>
<td>
<p>API versione 49</p>
</td>
</tr>
<tr>
<td>
<p>Connettore Microsoft Dynamics</p>
</td>
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
<td><strong>Versione minima di Campaign</strong></td>
<tr>
<td> Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>BigQuery Google</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

Negli ambienti **ibridi** e **on-premise** è possibile collegare Campaign ai seguenti sistemi di database esterni: Questi sistemi **non sono compatibili** con gli ambienti Campaign **Managed Services** (in hosting).

<table>
<tbody>
<td><strong>Sistema di database</strong></td>
<td><strong>Versione del database</strong></td>
<td><strong>Versione minima di Campaign</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
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
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (a partire da Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 e SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15,7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (ultima versione)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop tramite HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Console client {#ClientOS}

Per utilizzare la [console client di Campaign](../../installation/using/installing-the-client-console.md) sono **necessari** i seguenti sistemi operativi e browser.

### Sistemi operativi

<table>
<tbody>
<td><strong>Sistema</strong></td>
<td><strong>Versione sistema operativo</strong></td>
<td><strong>Versione minima di Campaign</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 Runtime {#webview}

Per la console client di Campaign è obbligatoria la versione più recente di Microsoft Edge WebView2.

Scarica Microsoft Edge WebView2 dal [sito web per sviluppatori Microsoft](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## Mobile SDK {#MobileSDK}

Puoi anche utilizzare Campaign per [inviare notifiche push](../../delivery/using/about-mobile-app-channel.md) tramite Adobe Experience Platform Mobile SDK configurando l’estensione Adobe Campaign nell’interfaccia utente di raccolta dati.

L’SDK di Campaign è [obsoleto](deprecated-features.md) a partire da Campaign v7.4. Per garantire una transizione fluida delle implementazioni esistenti verso AEP Mobile SDK, puoi continuare a utilizzarlo sui sistemi operativi elencati di seguito<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>con Mobile SDK build 1.1.1</p>
<p>Android 13 e 14 sono supportati a partire da Campaign v7.4.</p>
<p>Android 12 è supportato a partire da Campaign v7.3</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>con Mobile SDK build 1.0.26</p>
<p>Apple iOS 15 è supportato a partire da Campaign v7.3. </p>
<p>Apple iOS 16 e 17 sono supportati a partire da Campaign v7.4.</p>
</td>
</tr>
</tbody>
</table>

## Browser {#Browsers}

I seguenti browser, nella loro versione più recente, sono compatibili con Campaign per l’[accesso web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Note sulla versione Campaign Classic](../../rn/using/latest-release.md)
>* [Architettura generale di Campaign](../../installation/using/general-architecture.md)
>* [Consigli sui requisiti hardware in base alle dimensioni](../../technotes/using/hardware-sizing.md)
>* [Funzioni e sistemi obsoleti](../../rn/using/deprecated-features.md)
>* [Procedura di aggiornamento build](../../production/using/build-upgrade.md)
