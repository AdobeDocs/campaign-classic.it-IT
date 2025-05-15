---
product: campaign
title: Funzioni obsolete e rimosse di Campaign Classic
description: In questa pagina sono elencate le funzioni obsolete e rimosse di Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 84e6b2fad97f0ca5d6621cff4648e0be0bef7521
workflow-type: ht
source-wordcount: '1652'
ht-degree: 100%

---

# Funzioni obsolete e rimosse {#deprecated-and-removed-features}



Adobe valuta costantemente le funzionalità dei prodotti per identificare le funzioni meno recenti da sostituire con alternative più moderne, al fine di migliorare il valore complessivo per il cliente, sempre con un’attenta considerazione della compatibilità con le versioni precedenti. Poiché Adobe Campaign Classic funziona con strumenti di terze parti, la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate. Le versioni non più compatibili con Adobe Campaign Classic sono elencate di seguito e nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Per comunicare l’imminente rimozione/sostituzione delle funzionalità di Campaign Classic, si applicano le seguenti regole:

* Per prima cosa viene annunciato che una data funzione diventerà obsoleta. Le funzionalità obsolete possono restare disponibili e supportate per gli utenti esistenti, ma non saranno ulteriormente migliorate né documentate.
* La rimozione delle funzionalità obsolete viene effettuata non prima della versione successiva. La data effettiva di rimozione viene annunciata su questa pagina.

Questo processo offre ai clienti almeno un ciclo di pubblicazione per adattare la loro implementazione a una nuova versione o alla funzionalità che sostituirà quella obsoleta, prima della rimozione effettiva.

>[!NOTE]
> Le versioni e le nuove funzionalità di Adobe Campaign sono elencate nelle [Note sulla versione](../../rn/using/latest-release.md).

## Funzioni obsolete {#deprecated-features}

In questa sezione sono elencate le funzionalità contrassegnate come obsolete con le ultime versioni di Campaign Classic.

In genere, le funzioni che si prevede di rimuovere in una versione futura vengono inizialmente catalogate come obsolete. Queste funzionalità non sono più disponibili per i nuovi clienti di Campaign Classic o non devono essere utilizzate per alcuna nuova implementazione. Vengono inoltre rimosse dalla documentazione del prodotto.

I clienti sono invitati a verificare se utilizzano la funzionalità nella distribuzione corrente e a pianificare la modifica della loro implementazione. Consulta la data effettiva di rimozione per pianificare di conseguenza gli aggiornamenti di ambiente e progetto.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funzionalità</strong></td>
   <td><strong>Dettagli</strong></td>
  </tr>
  <tr>
 <td>SDK precedente di Campaign (Neolane)</td>
 <td><p>L’SDK Campaign (Neolane) per applicazioni mobili è ora obsoleto. Al suo posto, puoi utilizzare l’SDK per Adobe Experience Platform Mobile configurando l’estensione Adobe Campaign nell’interfaccia utente di raccolta dati. L’SDK di Adobe Experience Platform Mobile aiuta ad potenziare soluzioni e servizi di Experience Cloud di Adobe nelle app mobili. La configurazione degli SDK viene gestita tramite l’interfaccia utente di raccolta dati, per un’impostazione flessibile e integrazioni estensibili basate su regole. Scopri come configurare il canale app mobile nella <a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/push/push-settings">Documentazione di Campaign v8</a>.</p>
<p>Data di rimozione prevista: 31 luglio 2025 </p>
</td>
</tr>
<tr>
 <td>Social Marketing con Facebook</td>
 <td><p>Il Social Marketing con Facebook è ora obsoleto. Per pubblicare sui social media o lavorare con Adobe per creare un canale personalizzato, è possibile utilizzare l’integrazione con X (precedentemente noto come Twitter).</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>Connettore ACS</td>
 <td><p>Il connettore ACS (offerta Prime) è ora obsoleto. È possibile utilizzare le funzionalità di esportazione/importazione di Campaign per estrarre e inserire dati in entrambi i prodotti.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Funzioni rimosse {#removed-features}

In questa sezione sono elencate le funzionalità rimosse da Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Funzionalità</strong></td>
   <td><strong>Dettagli</strong></td>
  <tr>  
      <tr>
  <td>Connettore dati Adobe Analytics<br></td>
   <td><p>Connettore dati Adobe Analytics è stato rimosso il 17 agosto 2022. È stato dichiarato obsoleto con la versione 21.1.3 di Campaign.</p>
   <p>Se utilizzi questo connettore, devi adattare di conseguenza l’implementazione. <a href="../../integrations/using/gs-aa.md">Ulteriori informazioni</a></p>
  </td>
 </tr>
    <tr>
  <td>Rapporto tecnico di monitoraggio del recapito<br></td>
   <td><p>Il rapporto tecnico di monitoraggio del recapito non è più disponibile. È stato dichiarato obsoleto con la versione 21.1.3 di Campaign.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>Autenticazione OAuth (OAuth e JWT)<br></td>
  <td><p> L’autenticazione dell’integrazione di Triggers per accedere alla pipeline, originariamente basata sulla configurazione di autenticazione OAuth, è ora stata cambiata e spostata in Adobe I/O. Questa modalità di autenticazione è stata dichiarata obsoleta con la versione 20.3 di Campaign.<p>
  <p>Se utilizzi l’integrazione Triggers, consulta <a href="../../integrations/using/about-triggers.md#implement">questa pagina</a> per informazioni su come adattare la tua implementazione.</p> 
  <p>Per ulteriori informazioni sulla obsolescenza dell’autenticazione OAuth, fare riferimento a questa <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">pagina</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Generazione rapporti<br></td>
   <td><p>In seguito alla fine del ciclo di vita di Adobe Flash Player, il rapporto si misurazione e il motore di rendering del grafico non sono più disponibili. <a href="../../reporting/using/creating-a-new-report.md">Ulteriori informazioni</a></p>
  </tr>
  <tr>  
   <td>Canale fax<br></td>
   <td><p>A partire dalla versione Campaign 21.1.3, il canale fax non è più disponibile. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Ulteriori informazioni</a></p>
  </tr>
  <tr>
  <td>Dominio demdex<br></td>
  <td><p> A partire dalla versione di Campaign 21.1.3, il dominio demdex utilizzato per importare ed esportare i tipi di pubblico in Adobe Experience Cloud è diventato obsoleto. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Ulteriori informazioni</a></p> 
  </td>
  </tr>
   <tr> 
   <td>Autenticazione Windows NT<br></td>
   <td><p>A partire dalla versione 20.3 di Campaign, l’autenticazione con Windows NT è stata rimossa dai metodi di autenticazione disponibili per la configurazione di un nuovo database con Microsoft SQL Server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Ulteriori informazioni</a></p></td>
  </tr>
   <tr> 
   <td>Archiviazione di e-mail basata su file<br></td>
   <td><p>A partire dalla versione 20.2 di Campaign, l’archiviazione di e-mail basata su file non è più disponibile. L’archiviazione delle e-mail è ora disponibile tramite un indirizzo e-mail CCN dedicato. <a href="../../installation/using/email-archiving.md">Ulteriori informazioni</a></p></td>
  </tr> 
   <tr> 
   <td>Gestione lead</td>
   <td><p>A partire dalla versione 20.2 di Campaign, il pacchetto Gestione lead non è più disponibile. Funzionalità simili possono essere implementate tramite altre attività del flusso di lavoro native e modifiche apportate ai modelli di dati.</p></td>
   </tr>
   <tr>
   <td>Documentazione sulle API di Campaign - file jsapi.chm</td>
   <td>A partire dalla versione 19.1 di Campaign, le API Campaign Classic sono disponibili in una pagina dedicata. Se stavi utilizzando il file jsapi.chm legacy, ora devi fare riferimento alla <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it">nuova versione online</a>.</td>
  </tr> 
  <tr> 
   <td>Orchestrazione delle campagne - Marketing predittivo</td>
   <td>A partire dalla versione 18.10 di Campaign, le funzionalità di marketing predittivo non sono più disponibili.</td>
  </tr> 
  <tr> 
   <td>Applicazioni web - Micrositi</td>
   <td>A partire dalla versione 18.10 di Campaign, i micrositi non sono più disponibili. Puoi migliorare la protezione limitando l’accesso solo ai domini dedicati nei file di configurazione di Adobe Campaign e utilizzando URL personalizzati in Campaign tramite gli alias DNS.</td>
  </tr> 
  <tr> 
   <td>Notifiche push - Connettore binario iOS</td>
   <td>Sulla base della raccomandazione di Apple, Adobe ha rimosso il connettore binario iOS legacy a partire dalla versione 18.10 di Campaign. Il connettore più efficiente e potente basato su HTTP/2 è già disponibile.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>A partire dalla versione 18.6 di Campaign, per motivi di sicurezza, l’API <em>decryptString</em> non è più disponibile per impostazione predefinita per le nuove installazioni.</p> 
   <p>Nel contesto di un aggiornamento successivo alla versione 18.6 (e versioni successive), questa API non viene più attivata ed è stata sostituita dalla funzione <em>decryptPassword</em>. <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Ulteriori informazioni</a></p></td>
  </tr> 
   <tr> 
   <td>Canale mobile - Messaggi push MMS e WAP</td>
   <td>A partire dalla versione 18.4 di Campaign, i canali push MMS e Wap non sono più disponibili. In sostituzione, puoi utilizzare le consegne <a href="../../delivery/using/sms-channel.md">SMS</a> e <a href="../../delivery/using/about-mobile-app-channel.md">Push</a>.</td>
  </tr> 
   <tr> 
   <td>Canale mobile - LINE v1</td>
   <td>A partire dalla versione 18.4 di Campaign, il pacchetto LINE Connect non è più disponibile. Adobe consiglia di utilizzare il nuovo pacchetto LINE Channel come alternativa. <a href="../../delivery/using/line-channel.md">Ulteriori informazioni</a></td>
  </tr>
 </tbody> 
</table>

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

## Fine della compatibilità {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md). Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni: vengono classificate come obsolete e quindi rimosse dalla matrice di compatibilità nella versione del prodotto successiva. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

### Console client {#client-console-eol}

 La console del client di Adobe Campaign Classic non può più essere eseguita sui seguenti sistemi in quanto sono stati dichiarati obsoleti dai rispettivi editor. I clienti che eseguono la console del client di Campaign in una di queste versioni devono effettuare l’aggiornamento alla versione più recente prima della data effettiva di rimozione. Consulta la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>A partire dalla versione 20.1 di Campaign, la console del client a 32 bit di Campaign Classic non è più compatibile con le versioni più recenti di Campaign. È necessario utilizzare la console del client a 64 bit.

### Sistemi operativi {#o-s-eol}

* A partire dalla versione 7.3.1, Adobe Campaign non è più compatibile con Windows 8 e Windows Server 2012.

* A partire dalla versione 22.1, Adobe Campaign non è più compatibile con CentOs 8.x (64 bit). CentOS Linux 8 ha raggiunto la fine del ciclo di vita (EOL) il 31 dicembre 2021. [Ulteriori informazioni](https://www.centos.org/centos-linux-eol/).

  Se utilizzavi questo sistema operativo, adatta di conseguenza la tua implementazione. CentOS 7.x (64 bit) e RHEL 8.x/7.x (64 bit) sono ancora supportati.

* A partire dalla versione 21.1.3, Adobe Campaign non è più compatibile con Debian 8.

* A partire dalla versione 19.1, Adobe Campaign non è più compatibile con i seguenti sistemi operativi.

   * CentOs 6. [Ulteriori informazioni](https://wiki.centos.org/Download)
   * Debian 7. [Ulteriori informazioni](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x. [Ulteriori informazioni](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008. [Ulteriori informazioni](https://support.microsoft.com/it-it/lifecycle/search/1163)
   * SLES 11. [Ulteriori informazioni](https://www.suse.com/lifecycle)

### Server web {#web-server-eol}

A partire dalla versione 19.1 di primavera, Adobe Campaign non è più compatibile con il seguente server web.

* Apache 2.2. [Ulteriori informazioni](https://httpd.apache.org/)
* Microsoft IIS 7. [Ulteriori informazioni](https://support.microsoft.com/it-it/lifecycle/search/810)

### Strumenti {#tools-eol}

A partire dalla versione 19.1 di primavera, Adobe Campaign non è più compatibile con i seguenti strumenti.

* Java JDK 7. [Ulteriori informazioni](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, tranne quando incorporato in un altro strumento. [Ulteriori informazioni](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Motori di database {#dbe-eol}

Adobe non supporta i seguenti motori di database in quanto sono stati dichiarati obsoleti dai rispettivi editor. I clienti che eseguono queste versioni devono effettuare l’aggiornamento alla versione più recente o passare a un’altra versione.

Per accedere all’elenco delle versioni compatibili, consulta la [Matrice di compatibilità di Campaign](../../rn/using/compatibility-matrix.md).

**FEDERATED DATA ACCESS (FDA)**

A partire dalla versione 20.2, Adobe Campaign non è più compatibile con i seguenti server FDA:

* DB2 UDB 10.5

A partire dalla versione 19.1 di primavera, Adobe Campaign non è più compatibile con i seguenti server FDA:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 - 14.1.

Campaign Classic non è compatibile con i seguenti server in Federated Data Access (FDA). Utilizza versioni o sistemi più recenti.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* Le versioni PostgreSQL fino a 9.6 hanno raggiunto la fine del ciclo di vita.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* InfiniDB ha raggiunto la fine del ciclo di vita.
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. Netezza ha raggiunto la fine del ciclo di vita.
* AsterData 5.0. AsterData ha raggiunto la fine del ciclo di vita.
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0.
* Hadoop tramite HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuerà a supportare le versioni elencate di Hadoop tramite HiveSQL attraverso Federated Data Access (FDA), ma queste versioni vengono unite con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVER RDBMS**

A partire dalla versione 19.1 di primavera, Adobe Campaign non è più compatibile con i seguenti server RDBMS:

* Oracle 10GR2
* PostgreSQL da 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

Le versioni PostgreSQL fino a 9.6 hanno raggiunto la fine del ciclo di vita. Non sono pertanto supportate da Adobe Campaign.

### Connettori SMS {#sms-eol}

A partire dalla versione 20.2, i seguenti connettori legacy SMS sono diventati obsoleti. Adobe Campaign non è compatibile con:

* SMPP generico (SMPP versione 3.4 che supporta la modalità binaria)
* Sybase365 (SAP SMS 365)
* Comunicazioni CLX
* Tele2
* O2
* iOS

### Connettori CRM {#crm-connectors}

A partire da Campaign 21.1, i seguenti connettori CRM non sono più compatibili con Campaign:

* API Soap - On-premise: 2007, 2015, 2016
* API Soap - Online: 2015, 2016
* API web: Microsoft Dynamics CRM 2016
* API web: Microsoft Dynamics CRM 2016 aggiornamento 1
* API Oracle On Demand
