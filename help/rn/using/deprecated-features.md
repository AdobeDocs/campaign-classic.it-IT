---
title: Funzioni obsolete e rimosse di Campaign Classic
description: In questa pagina sono elencate le funzioni obsolete e rimosse di Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 0%

---


# Funzioni obsolete e rimosse {#deprecated-and-removed-features}

Adobe valuta costantemente le funzionalità dei prodotti per identificare le funzioni meno recenti da sostituire con alternative più moderne, al fine di migliorare il valore complessivo dei clienti, sempre con un&#39;attenta considerazione della compatibilità con le versioni precedenti. Poiché Adobe Campaign Classic funziona con strumenti di terze parti, la compatibilità viene aggiornata regolarmente, al fine di implementare solo le versioni supportate. Le versioni non più compatibili con Adobe Campaign Classic sono elencate di seguito.

Per comunicare l&#39;imminente rimozione/sostituzione delle funzionalità di Campaign Classic, si applicano le regole seguenti:

* L&#39;annuncio della deprecazione viene prima. Le funzionalità obsolete possono essere ancora disponibili per gli utenti esistenti, ma non saranno ulteriormente migliorate né documentate.
* La rimozione di funzionalità obsolete verrà effettuata non prima nella versione successiva. La data di destinazione effettiva per la rimozione è annunciata in questa pagina.

Questo processo offre ai clienti almeno un ciclo di rilascio per adattare la loro implementazione a una nuova versione o successore di una funzionalità obsoleta, prima della rimozione effettiva.

>[!NOTE]
>Le release di Adobe Campaign e le nuove funzionalità sono elencate nelle note sulla [versione](../../rn/using/latest-release.md).


## Deprecated features {#deprecated-features}

In questa sezione sono elencate le funzionalità contrassegnate come obsolete con le ultime versioni di Campaign Classic.

In genere, le funzioni pianificate per essere rimosse in una versione futura sono impostate per prime su obsoleta, con un&#39;alternativa fornita. Queste funzionalità non sono più disponibili per i nuovi clienti di Campaign Classic o non devono essere utilizzate per alcuna nuova implementazione. Vengono anche rimosse dalla documentazione del prodotto.

Si consiglia ai clienti di verificare se utilizzano la funzionalità o la funzionalità nella distribuzione corrente e di pianificare la modifica della propria implementazione per utilizzare l&#39;alternativa fornita. Fare riferimento alla data di rimozione della destinazione per pianificare l&#39;ambiente e gli aggiornamenti del progetto di conseguenza.

### Versione di Adobe Campaign 18.6 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area</strong></td>
   <td><strong>Feature</strong></td> 
   <td><strong>Sostituzione</strong></td> 
  </tr> 
   <tr> 
   <td>Javascript SDK Security<br> </td>
   <td>decryptString<br> </td>
   <td><p>Per motivi di sicurezza, l'API <em>deryptString</em> non è più disponibile per impostazione predefinita per le nuove installazioni.</p> 
   <p>Nel contesto di un post-aggiornamento a 18.6 (e versioni successive), questa API non viene più attivata ed è stata sostituita dalla funzione <em>deryptPassword</em> .</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Versione di Adobe Campaign 18.4 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area</strong></td>
   <td><strong>Feature</strong></td> 
   <td><strong>Sostituzione</strong></td> 
  </tr> 
   <tr> 
   <td>Archiviazione e-mail<br> </td>
   <td>Archiviazione basata su file<br> </td>
   <td><p>L'archiviazione delle e-mail è ora disponibile tramite un indirizzo e-mail CCN dedicato. <a href="../../installation/using/email-archiving.md">Ulteriori</a>informazioni.</p> 
   <p><em>Data di rimozione destinazione: Release Campaign 20.2 - Giugno 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Gestione dei lead<br> </td>
   <td>Lead<br> </td>
   <td><p>Il pacchetto Lead Management in Adobe Campaign Classic ha semplificato il processo di creazione e manutenzione dell’intero ciclo di vita della gestione dei lead. Funzionalità simili possono essere implementate tramite altre attività di flusso di lavoro native e modifiche apportate ai modelli di dati.</p> 
   <p><em>Data di rimozione destinazione: Release Campaign 20.2 - Giugno 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Compatibilità obsoleta {#deprecated-compatibility}

### Versione di Adobe Campaign 20.1 {#compat-20-1-release}

A partire dalla release del 20.1 febbraio, il sistema seguente è diventato obsoleto per Campaign Classic. La compatibilità terminerà con la release 20.2 - giugno 2020.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area</strong></td>
   <td><strong>Sostituzione</strong></td> 
  </tr> 
   <tr> 
   <td>Console Client Classic Campaign 32 bit<br> </td>
   <td><p>Console client Campaign Classic 64 bit</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Versione di Adobe Campaign 19.2  {#compat-19-2-release}

A partire dalla versione 19.2 di Autunno, i seguenti sistemi operativi sono obsoleti per Campaign Classic. La compatibilità terminerà nel 2020.

* Server Web: Apache 2.2. [Ulteriori informazioni](https://wiki.centos.org/About/Product)
* Sistema operativo: CentOS 6. [Ulteriori informazioni](https://wiki.centos.org/About/Product)

Fare riferimento alla matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) compatibilità per effettuare l&#39;aggiornamento a una versione più recente o passare a un nuovo sistema.

## Funzioni rimosse {#removed-features}

In questa sezione sono elencate le funzionalità rimosse da Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Area - Feature</strong></td>
   <td><strong>Sostituzione</strong></td> 
   <td><strong>Versione</strong></td> 
  </tr> 
   <tr> 
   <td>Documentazione sulle API delle campagne - file jsapi.chm<br> </td>
   <td>Le API Campaign Classic sono ora disponibili in una pagina dedicata. Se utilizzi il file jsapi.chm, ora consulta <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">la nuova versione</a>online.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Orchestrazione campagna - Predictive marketing</td>
   <td>Gran parte delle capacità di marketing predittivo in Adobe Campaign Classic è stato il consumo di modelli predittivi. Anche se l'attività del flusso di lavoro di marketing predittivo verrà rimossa in una versione futura, Adobe Campaign continuerà a supportare l'uso e l'uso di modelli predittivi da origini esterne attraverso altre attività del flusso di lavoro.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Applicazioni Web - Micrositi</td>
   <td>Migliorate la sicurezza limitando l'accesso ai soli domini dedicati nei file di configurazione di Adobe Campaign. Puoi ancora utilizzare URL personalizzati in Campaign utilizzando alias DNS. <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">Ulteriori</a>informazioni.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Notifiche push - Connettore binario iOS<br> </td>
   <td>In base alla raccomandazione di Apple, Adobe rimuoverà il connettore binario iOS legacy. È già disponibile il connettore HTTP/2 più efficiente e potente.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Canale mobile - Messaggi push MMS e WAP</td>
   <td>I canali MMS e Wap Push non sono più disponibili. In sostituzione, potete utilizzare gli <a href="../../delivery/using/sms-channel.md">SMS</a> e le consegne <a href="../../delivery/using/about-mobile-app-channel.md">push</a> .</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Canale mobile - LINE v1</td>
   <td>Il pacchetto LINE Connect non è più disponibile per l'installazione in Adobe Campaign Classic. Adobe consiglia di utilizzare il nuovo pacchetto LINE Channel per inviare messaggi LINE. <a href="../../delivery/using/line-channel.md">Ulteriori</a>informazioni.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Fine della compatibilità {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic è compatibile con tutti i sistemi e gli strumenti elencati nella matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità. Quando versioni specifiche di questi sistemi e strumenti di terze parti raggiungono la fine del ciclo di vita (EOL) con i rispettivi creatori, Adobe Campaign non è più compatibile con tali versioni: vengono annunciati come obsoleti e quindi rimossi dalla nostra matrice di compatibilità nella release successiva del prodotto. Verificare di disporre delle versioni supportate di tutti i sistemi elencati nella matrice di compatibilità per evitare problemi.

### Console client {#client-console-eol}

Adobe Campaign Classic Client Console non può più essere eseguito sui seguenti sistemi perché è stato dichiarato obsoleto dal relativo editor. I clienti che eseguono Campaign Client Console in una di queste versioni devono effettuare l&#39;aggiornamento alla versione più recente prima della data di rimozione del target. Fare riferimento alla matrice [di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)compatibilità.

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Sistemi operativi {#o-s-eol}

A partire dalla versione 19.1, Adobe Campaign non è più compatibile con i seguenti sistemi operativi.

* Debian 7. [Ulteriori](https://wiki.debian.org/DebianReleases)informazioni.
* RHEL 6.x [Ulteriori](https://access.redhat.com/support/policy/updates/errata)informazioni.
* Windows Server 2008. [Ulteriori](https://support.microsoft.com/en-us/lifecycle/search/1163)informazioni.
* SLES 11. [Ulteriori](https://www.suse.com/lifecycle)informazioni.

### Server Web {#web-server-eol}

A partire dalla release 19.1 di primavera, Adobe Campaign non è più compatibile con il seguente server Web.

* Microsoft IIS 7. [Ulteriori](https://support.microsoft.com/en-us/lifecycle/search/810)informazioni.

### Strumenti {#tools-eol}

A partire dalla release 19.1 di primavera, Adobe Campaign non è più compatibile con i seguenti strumenti.

* Java JDK 7. [Ulteriori](http://www.oracle.com/technetwork/java/javase/eol-135779.html)informazioni.
* Libre Office 3.5 / 4.3 / 5.x, tranne quando incorporato in un altro strumento. [Ulteriori](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)informazioni.

### Motori di database {#dbe-eol}

Adobe non supporta i seguenti motori di database perché sono stati dichiarati obsoleti dal relativo editor. I clienti che eseguono queste versioni devono effettuare l&#39;aggiornamento alla versione più recente o passare a un&#39;altra.

Fare riferimento alla matrice [di compatibilità di](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) Campaign Classic per accedere all&#39;elenco delle versioni compatibili.

**FEDERATED DATA ACCESS (FDA)**

A partire dalla release 19.1 di primavera, Adobe Campaign non è più compatibile con i seguenti server FDA.

* Oracle 11G. [Ulteriori](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)informazioni.
* PostgreSQL 9.3. [Ulteriori](https://www.postgresql.org/support/versioning)informazioni.
* MySQL 5.5. &lt;[Ulteriori](http://www.fromdual.com/support-for-mysql-from-oracle)informazioni.
* DB2 9.5. [Ulteriori](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)informazioni.
* Teradata 14 - 14.1. [Ulteriori](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)informazioni.

Campaign Classic non è compatibile con i seguenti server in Federated Data Access (FDA).

* DB2 UDB 9.5, 9.7. La versione più recente di DB2 è supportata tramite Federated Data Access (FDA). [Ulteriori](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)informazioni.
* Oracle 9i, 10G R2. Le versioni più recenti di Oracle sono supportate tramite Federated Data Access (FDA). [Ulteriori](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)informazioni.
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Versioni più recenti di PostgreSQL sono supportate tramite Federated Data Access (FDA). [Ulteriori](https://www.postgresql.org/support/versioning)informazioni.
* MSSQL 2000, 2005, 2008 R2. Versioni più recenti di SQL Server sono supportate tramite Federated Data Access (FDA). [Ulteriori](https://support.microsoft.com/en-us/lifecycle/search/1044)informazioni.
* MySQL 5.1. Le versioni più recenti di MySQL sono supportate tramite Federated Data Access (FDA). [Ulteriori](https://en.wikipedia.org/wiki/InfiniDB)informazioni.
* InfiniDB ha raggiunto la fine del ciclo di vita. [Ulteriori](https://www.mysql.com/support)informazioni.
* Teradata 13, 13.1. Versioni più recenti di Teradata sono supportate tramite Federated Data Access (FDA). [Ulteriori](https://www.info.teradata.com/download.cfm?ItemID=1007255)informazioni.
* Netezza 6.02, 7.0. Netezza raggiunse la fine della vita. [Ulteriori](https://en.wikipedia.org/wiki/Netezza)informazioni.
* AsterData 5.0. AsterData ha raggiunto la fine del ciclo di vita. [Ulteriori](https://en.wikipedia.org/wiki/Aster_Data_Systems)informazioni.
* Sybase IQ 15.2, 15.4, 15.5 e Sybase ASE 15.0. Versioni più recenti di Sybase sono supportate tramite Federated Data Access (FDA). [Ulteriori](https://sites.google.com/site/dbatipsandtricks/time-tracker)informazioni.
* Hadoop tramite HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic continuerà a supportare le versioni elencate di Hadoop tramite HiveSQL tramite Federated Data Access (FDA), ma queste versioni vengono unite con: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) e HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Adobe Campaign non è compatibile con i seguenti server RDBMS:
* Oracle 10GR2, 11G
* PostgreSQL da 9.0 a 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
