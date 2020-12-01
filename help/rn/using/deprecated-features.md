---
solution: Campaign Classic
product: campaign
title: Funzioni obsolete e rimosse di Campaign Classic
description: In questa pagina sono elencate le funzioni obsolete e rimosse di Adobe Campaign Classic
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 82c5f4f4c37f295a6c206eb33616ae9223740f36
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 99%

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
   <td><strong>Sostituzione</strong></td>
  </tr>
  <tr>
  <td>Connettori di gestione delle relazioni con i clienti<br></td>
   <td><p>A partire dalla versione Campaign 20.3, i seguenti connettori di gestione delle relazioni con i clienti sono diventati obsoleti:</p>
   <ul>
   <li>API Soap - On-premise: 2007, 2015, 2016</li>
   <li>API Soap - Online: 2015, 2016</li>
   <li>API Web - Microsoft Dynamics CRM locale: Aggiornamento 1 del 2016 del 2016</li>
   <li>API Web - Microsoft Dynamics CRM Online: Aggiornamento 1 del 2016 del 2016</li>
   </ul>
  <p><em>Data effettiva di rimozione: aprile 2021</em></p>
  </td>
 </tr>
  <tr>
  <td>iOS legacy binario<br></td>
  <td><p>A partire dalla release Campaign 20.3, il connettore legacy binario per iOS è diventato obsoleto.<p>
  <p> Se utilizzi questo connettore, devi adattare di conseguenza l’implementazione.
  <a href="https://helpx.adobe.com/it/campaign/kb/migrate-to-apns-http2.html">Ulteriori informazioni</a></p>
  <p><em>Data effettiva di rimozione: aprile 2021</em></p>
  </td>
 </tr>
   <tr>
  <td>Dominio demdex<br></td>
  <td><p> A partire dalla versione di Campaign 20.3, il dominio demdex utilizzato per importare ed esportare i tipi di pubblico in Adobe Experience Cloud è diventato obsoleto.<p>
  <p>Se utilizzi il dominio demdex per l’importazione/esportazione degli account esterni, devi adattare di conseguenza l’implementazione. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Ulteriori informazioni</a></p> 
  <p><em>Data effettiva di rimozione: aprile 2021</em></p>
  </td>
  <tr>
  <td>Autenticazione OAuth (OAuth e JWT)<br></td>
  <td><p> A partire dalla versione di Campaign 20.3, l’autenticazione dell’integrazione dei trigger originariamente basata sulle impostazioni OAUTH per accedere alla pipeline è stata modificata e spostata in Adobe I/O. <p>
  <p>Se utilizzi l’integrazione con i trigger, devi adattare di conseguenza l’implementazione. <a href="../../integrations/using/configuring-adobe-io.md">Ulteriori informazioni</a></p> 
  <p>Per ulteriori informazioni sulla obsolescenza dell’autenticazione OAuth, fare riferimento a questa <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">pagina</a></p> 
  <p><em>Data effettiva di rimozione: aprile 2021</em></p>
  </td>
  </tr>
  <td>Connettori SMS<br></td>
  <td><p> A partire dalla versione Campaign 20.2, i seguenti connettori SMS sono diventati obsoleti.<p>
   <ul>
   <li>NetSize</li>
   <li>SMPP generico (SMPP versione 3.4 che supporta la modalità binaria)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>Comunicazioni CLX</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Se utilizzi uno di questi connettori, devi adattare di conseguenza la tua implementazione. <a href="../../delivery/using/sms-channel.md">Ulteriori informazioni</a></p> 
  <p>Scopri come effettuare la migrazione dei connettori legacy in <a href="https://helpx.adobe.com/it/campaign/kb/sms-connector.html">questa nota tecnica</a>.</p>
  <p><em>Data effettiva di rimozione: aprile 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Canale fax<br></td>
   <td><p>A partire dalla versione Campaign 20.2, il canale fax è diventato obsoleto.</p> 
   <p>Se utilizzi questo canale, devi adattare di conseguenza la tua implementazione. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Ulteriori informazioni</a> sui canali di Campaign.</p>
   <p><em>Data effettiva di rimozione: aprile 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Funzioni rimosse {#removed-features}

In questa sezione sono elencate le funzionalità rimosse da Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area - Funzionalità</strong></td>
   <td><strong>Sostituzione</strong></td> 
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
   <td>A partire dalla versione 19.1 di Campaign, le API Campaign Classic sono disponibili in una pagina dedicata. Se stavi utilizzando il file jsapi.chm legacy, ora devi fare riferimento alla <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">nuova versione online</a>.</td>
  </tr> 
  <tr> 
   <td>Orchestrazione delle campagne - Marketing predittivo</td>
   <td>A partire dalla versione 18.10 di Campaign, le funzionalità di marketing predittivo non sono più disponibili.</td>
  </tr> 
  <tr> 
   <td>Applicazioni web - Micrositi</td>
   <td>A partire dalla versione 18.10 di Campaign, i micrositi non sono più disponibili. Puoi migliorare la protezione limitando l’accesso solo ai domini dedicati nei file di configurazione di Adobe Campaign e utilizzando URL personalizzati in Campaign tramite gli alias DNS. <a href="https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html">Ulteriori informazioni</a></td>
  </tr> 
  <tr> 
   <td>Notifiche push - Connettore binario iOS</td>
   <td>Sulla base della raccomandazione di Apple, Adobe ha rimosso il connettore binario iOS legacy a partire dalla versione 18.10 di Campaign. Il connettore più efficiente e potente basato su HTTP/2 è già disponibile.</td>
  </tr> 
  <tr> 
   <td>API decryptString</td>
   <td><p>A partire dalla versione 18.6 di Campaign, per motivi di sicurezza, l’API <em>decryptString</em> non è più disponibile per impostazione predefinita per le nuove installazioni.</p> 
   <p>Nel contesto di un aggiornamento successivo alla versione 18.6 (e versioni successive), questa API non viene più attivata ed è stata sostituita dalla funzione <em>decryptPassword</em>. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Ulteriori informazioni</a></p></td>
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

## Compatibilità obsoleta {#deprecated-compatibility}

I seguenti sistemi sono obsoleti per Campaign Classic. Consulta la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md) per effettuare l’aggiornamento a una versione più recente o per passare a un nuovo sistema prima del termine della compatibilità.

### Adobe Campaign versione 20.2 {#compat-20-2-release}

A partire dalla versione 20.2, i seguenti connettori legacy SMS sono diventati obsoleti. Consulta la [sezione Funzioni obsolete](#deprecated-features)

## Fine della compatibilità {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md). Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni: vengono classificate come obsolete e quindi rimosse dalla matrice di compatibilità nella versione del prodotto successiva. Assicurati di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

### Console del client {#client-console-eol}

 La console del client di Adobe Campaign Classic non può più essere eseguita sui seguenti sistemi in quanto sono stati dichiarati obsoleti dai rispettivi editor. I clienti che eseguono la console del client di Campaign in una di queste versioni devono effettuare l’aggiornamento alla versione più recente prima della data effettiva di rimozione. Consulta la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>A partire dalla versione 20.1 di Campaign, la console del client a 32 bit di Campaign Classic non è più compatibile con le versioni più recenti di Campaign. È necessario utilizzare la console del client a 64 bit.


### Sistemi operativi {#o-s-eol}

A partire dalla versione 19.1, Adobe Campaign non è più compatibile con i seguenti sistemi operativi.

* CentOS 6 [Ulteriori informazioni](https://wiki.centos.org/Download)
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

* Java JDK 7. [Ulteriori informazioni](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, tranne quando incorporato in un altro strumento. [Ulteriori informazioni](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Motori di database {#dbe-eol}

Adobe non supporta i seguenti motori di database in quanto sono stati dichiarati obsoleti dai rispettivi editor. I clienti che eseguono queste versioni devono effettuare l’aggiornamento alla versione più recente o passare a un’altra versione.

Per accedere all’elenco delle versioni compatibili, consulta la [Matrice di compatibilità di Campaign ](../../rn/using/compatibility-matrix.md).

**FEDERATED DATA ACCESS (FDA)**

A partire dalla versione 20.2, Adobe Campaign non è più compatibile con i seguenti server FDA:

* DB2 UDB 10.5

A partire dalla versione 19.1 di primavera, Adobe Campaign non è più compatibile con i seguenti server FDA:

* PostgreSQL 9.3. [Ulteriori informazioni](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Ulteriori informazioni](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Ulteriori informazioni](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1. [Ulteriori informazioni](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic non è compatibile con i seguenti server in Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. La versione più recente di DB2 è supportata tramite Federated Data Access (FDA). [Ulteriori informazioni](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Versioni più recenti di Oracle sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Versioni più recenti di PostgreSQL sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Versioni più recenti di SQL Server sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://support.microsoft.com/it-it/lifecycle/search/1044)
* MySQL 5.1. Versioni più recenti di MySQL sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB ha raggiunto la fine del ciclo di vita. [Ulteriori informazioni](https://www.mysql.com/support)
* Teradata 13, 13.1. Versioni più recenti di Teradata sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza ha raggiunto la fine del ciclo di vita. [Ulteriori informazioni](https://it.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData ha raggiunto la fine del ciclo di vita. [Ulteriori informazioni](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0. Versioni più recenti di Sybase sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop tramite HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuerà a supportare le versioni elencate di Hadoop tramite HiveSQL attraverso Federated Data Access (FDA), ma queste versioni vengono unite con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**SERVER RDBMS**

 Adobe Campaign non è compatibile con i seguenti server RDBMS:
* Oracle 10GR2
* PostgreSQL da 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
