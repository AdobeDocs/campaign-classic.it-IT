---
title: Funzioni obsolete e rimosse dei Campaign Classic
description: In questa pagina sono elencate le funzioni obsolete e rimosse di Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 63f07746d39fff22a98b3cd4ab7f2294da778ab3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 3%

---


# Funzioni obsolete e rimosse {#deprecated-and-removed-features}

 Adobe valuta costantemente le capacità dei prodotti per identificare le funzioni meno recenti da sostituire con alternative più moderne per migliorare il valore complessivo dei clienti, sempre in considerazione della compatibilità con le versioni precedenti. Poiché Adobe Campaign Classic funziona con strumenti di terze parti, la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate. Le versioni non più compatibili con Adobe Campaign Classic sono elencate di seguito e nella matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità.

Per comunicare l&#39;imminente rimozione/sostituzione delle funzionalità Campaign Classic, si applicano le regole seguenti:

* L&#39;annuncio della deprecazione viene prima. Le funzionalità obsolete possono essere ancora disponibili e supportate per gli utenti esistenti, ma non saranno ulteriormente migliorate né documentate.
* La rimozione di funzionalità obsolete verrà effettuata non prima nella versione successiva. La data di destinazione effettiva per la rimozione è annunciata in questa pagina.

Questo processo offre ai clienti almeno un ciclo di rilascio per adattare la loro implementazione a una nuova versione o successore di una funzionalità obsoleta, prima della rimozione effettiva.

>[!NOTE]
> versioni di Adobe Campaign e nuove funzionalità sono elencate nelle [Note](../../rn/using/latest-release.md)sulla versione.

## Deprecated features {#deprecated-features}

In questa sezione sono elencate le funzionalità contrassegnate come obsolete con le ultime versioni di Campaign Classic.

In genere, le funzioni pianificate per essere rimosse in una versione futura sono impostate per prime come obsolete. Queste funzionalità non sono più disponibili per i nuovi clienti Campaign Classic o non devono essere utilizzate per alcuna nuova implementazione. Vengono anche rimosse dalla documentazione del prodotto.

I clienti sono invitati a verificare se utilizzano la funzionalità o la funzionalità nella distribuzione corrente e a pianificare la modifica della loro implementazione. Fare riferimento alla data di rimozione della destinazione per pianificare l&#39;ambiente e gli aggiornamenti del progetto di conseguenza.

<table> 
 <tbody> 
   <tr>
   <td><strong>Feature</strong></td>
   <td><strong>Sostituzione</strong></td> 
  </tr>
   <tr>
  <td>Connettori SMS<br></td>
  <td><p> A partire dalla release 20.2, i seguenti connettori SMS sono obsoleti.<p>
   <ul>
   <li>NetSize</li>
   <li>SMPP generico (SMPP versione 3.4 che supporta la modalità binaria)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>Comunicazioni CLX</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Se si utilizza uno di questi connettori, è necessario adattare di conseguenza la propria implementazione. <a href="../../delivery/using/sms-channel.md">Ulteriori informazioni</a></p> 
  <p>Scopri come migrare i connettori legacy in <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">questa nota tecnica</a>.</p>
  <p><em>Data di rimozione destinazione: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Canale fax<br></td>
   <td><p>A partire dalla release 20.2, il canale Fax è diventato obsoleto.</p> 
   <p>Se utilizzi questo canale, devi adattare di conseguenza la tua implementazione. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Ulteriori</a> informazioni sui canali Campaign.</p>
   <p><em>Data di rimozione destinazione: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Funzioni rimosse {#removed-features}

In questa sezione sono elencate le funzionalità rimosse dai Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area - Feature</strong></td>
   <td><strong>Sostituzione</strong></td> 
  </tr> 
   <tr> 
   <td>Archiviazione delle e-mail basata su file<br></td>
   <td><p>A partire dalla release di Campaign 20.2, l'archiviazione delle e-mail basate su file non è più disponibile. L'archiviazione delle e-mail è ora disponibile tramite un indirizzo e-mail CCN dedicato. <a href="../../installation/using/email-archiving.md">Ulteriori informazioni</a></p></td>
  </tr> 
   <tr> 
   <td>Gestione dei lead</td>
   <td><p>A partire dalla release Campaign 20.2, il pacchetto Lead Management non è più disponibile. Funzionalità simili possono essere implementate tramite altre attività di flusso di lavoro native e modifiche apportate ai modelli di dati.</p></td>
   </tr>
   <tr>
   <td>Documentazione sulle API delle campagne - file jsapi.chm</td>
   <td>A partire dalla release Campaign 19.1, le API Campaign Classic sono disponibili in una pagina dedicata. Se utilizzi il file jsapi.chm precedente, ora fai riferimento alla nuova versione <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html"></a>online.</td>
  </tr> 
  <tr> 
   <td>Orchestrazione campagna - Predictive marketing</td>
   <td>A partire dalla versione Campaign 18.10, le funzionalità di marketing predittivo non sono più disponibili.</td>
  </tr> 
  <tr> 
   <td>Applicazioni Web - Micrositi</td>
   <td>A partire dalla versione della campagna 18.10, i micrositi non sono più disponibili. Puoi migliorare la sicurezza limitando l'accesso solo ai domini dedicati  file di configurazione Adobe Campaign e utilizzando gli URL personalizzati in Campaign utilizzando gli alias DNS. <a href="https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html">Ulteriori informazioni</a></td>
  </tr> 
  <tr> 
   <td>Notifiche push - Connettore binario iOS</td>
   <td>In base alla raccomandazione di Apple,  Adobe ha rimosso il connettore binario iOS legacy avviando la release 18.10 di Campaign. È già disponibile il connettore HTTP/2 più efficiente e potente.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>A partire dalla release Campaign 18.6, per motivi di sicurezza, l'API <em>decifrptString</em> non è più disponibile per impostazione predefinita per le nuove installazioni.</p> 
   <p>Nel contesto di un post-aggiornamento a 18.6 (e versioni successive), questa API non viene più attivata ed è stata sostituita dalla funzione <em>deryptPassword</em> . <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Ulteriori informazioni</a></p></td>
  </tr> 
   <tr> 
   <td>Canale mobile - Messaggi push MMS e WAP</td>
   <td>A partire dalla release Campaign 18.4, i canali MMS e Wap Push non sono più disponibili. In sostituzione, potete utilizzare gli <a href="../../delivery/using/sms-channel.md">SMS</a> e le consegne <a href="../../delivery/using/about-mobile-app-channel.md">push</a> .</td>
  </tr> 
   <tr> 
   <td>Canale mobile - LINE v1</td>
   <td>A partire dalla versione di Campaign 18.4, il pacchetto LINE Connect non è più disponibile.  Adobe consiglia di utilizzare il nuovo pacchetto LINE Channel come sostituzione. <a href="../../delivery/using/line-channel.md">Ulteriori informazioni</a></td>
  </tr> 
 </tbody> 
</table>

## Compatibilità obsoleta {#deprecated-compatibility}

I seguenti sistemi sono obsoleti per Campaign Classic. Fare riferimento alla matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) compatibilità per effettuare l&#39;aggiornamento a una versione più recente o per passare a un nuovo sistema prima del termine della compatibilità.

###  versione Adobe Campaign 20.2 {#compat-20-2-release}

A partire dalla versione 20.2, il sistema seguente è diventato obsoleto per Campaign Classic. La compatibilità terminerà con la release 20.3 - settembre 2020.

* Console client: Windows 7
* Connettori SMS legacy (vedere la sezione Funzioni obsolete di seguito)

###  versione Adobe Campaign 19.2  {#compat-19-2-release}

A partire dalla versione 19.2, i seguenti sistemi operativi sono obsoleti per Campaign Classic. La compatibilità terminerà nel 2020.

* Server Web: Apache 2.2.
* Sistema operativo: CentOS 6.

Fare riferimento alla matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) compatibilità per effettuare l&#39;aggiornamento a una versione più recente o passare a un nuovo sistema.

## Fine della compatibilità {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati nella matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità. Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori,  Adobe Campaign non è più compatibile con tali versioni: vengono annunciati come obsoleti e quindi rimossi dalla nostra matrice di compatibilità nella release successiva del prodotto. Verificare di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

### Console client {#client-console-eol}

Adobe Campaign Classic Client Console non può più essere eseguito sui seguenti sistemi perché è stato dichiarato obsoleto dal relativo editor. I clienti che eseguono Campaign Client Console in una di queste versioni devono effettuare l&#39;aggiornamento alla versione più recente prima della data di rimozione del target. Fare riferimento alla matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità.

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>A partire dalla versione di Campaign 20.1, la console client Campaign Classic 32 bit non è più compatibile con le versioni più recenti di Campaign. È necessario utilizzare la console client a 64 bit.


### Sistemi operativi {#o-s-eol}

A partire dalla versione 19.1,  Adobe Campaign non è più compatibile con i seguenti sistemi operativi.

* Debian 7. [Ulteriori informazioni](https://wiki.debian.org/DebianReleases)
* RHEL 6.x [Ulteriori informazioni](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Ulteriori informazioni](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Ulteriori informazioni](https://www.suse.com/lifecycle)

### Server Web {#web-server-eol}

A partire dalla release 19.1 di primavera,  Adobe Campaign non è più compatibile con il server Web seguente.

* Microsoft IIS 7. [Ulteriori informazioni](https://support.microsoft.com/en-us/lifecycle/search/810)

### Strumenti {#tools-eol}

A partire dalla release 19.1 di primavera,  Adobe Campaign non è più compatibile con i seguenti strumenti.

* Java JDK 7. [Ulteriori informazioni](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, tranne quando incorporato in un altro strumento. [Ulteriori informazioni](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Motori di database {#dbe-eol}

 Adobe non supporta i seguenti motori di database perché sono stati dichiarati obsoleti dal relativo editor. I clienti che eseguono queste versioni devono effettuare l&#39;aggiornamento alla versione più recente o passare a un&#39;altra.

Per accedere all&#39;elenco delle versioni compatibili, fare riferimento alla matrice [di compatibilità](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) Campaign Classic.

**FEDERATED DATA ACCESS (FDA)**

A partire dalla release 19.1 di primavera,  Adobe Campaign non è più compatibile con i seguenti server FDA.

* PostgreSQL 9.3. [Ulteriori informazioni](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Ulteriori informazioni](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Ulteriori informazioni](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1. [Ulteriori informazioni](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic non è compatibile con i seguenti server in Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. La versione più recente di DB2 è supportata tramite Federated Data Access (FDA). [Ulteriori informazioni](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Le versioni più recenti di Oracle sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Versioni più recenti di PostgreSQL sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Versioni più recenti di SQL Server sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Le versioni più recenti di MySQL sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB ha raggiunto la fine del ciclo di vita. [Ulteriori informazioni](https://www.mysql.com/support)
* Teradata 13, 13.1. Versioni più recenti di Teradata sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza raggiunse la fine della vita. [Ulteriori informazioni](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData ha raggiunto la fine del ciclo di vita. [Ulteriori informazioni](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0. Versioni più recenti di Sybase sono supportate tramite Federated Data Access (FDA). [Ulteriori informazioni](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop tramite HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuerà a supportare le versioni elencate di Hadoop tramite HiveSQL tramite Federated Data Access (FDA), ma queste versioni vengono unite con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

 Adobe Campaign non è compatibile con i seguenti server RDBMS:
* Oracle 10GR2
* PostgreSQL da 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
