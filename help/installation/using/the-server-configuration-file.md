---
title: Il file di configurazione del server
seo-title: Il file di configurazione del server
description: Il file di configurazione del server
seo-description: null
page-status-flag: never-activated
uuid: 8ef7168b-3543-4830-80b0-65a023158b3f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: da2198a3-7cef-4419-894d-e5bb51bb480c
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '7857'
ht-degree: 5%

---


# Il file di configurazione del server{#the-server-configuration-file}

La configurazione globale di  Adobe Campaign è definita nel file **serverConf.xml** , che si trova nella directory **conf** della directory di installazione. In questa sezione sono elencati tutti i diversi nodi e parametri del file **serverConf.xml** .

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite solo da  Adobe per le distribuzioni ospitate da  Adobe. Per ulteriori informazioni sulle diverse distribuzioni, consultate la sezione Modelli [di](../../installation/using/hosting-models.md) hosting o [questo articolo](https://helpx.adobe.com/it/campaign/kb/acc-on-prem-vs-hosted.html). I passaggi di installazione e configurazione per i modelli ospitati e ibridi sono descritti in questa [sezione](../../installation/using/hosted-model.md).

I primi parametri si trovano all&#39;interno del nodo **condiviso** . Sono correlate all&#39;istanza. Sono potenzialmente utilizzati da tutti i comandi nlserver (nlserver web, nlserver wfserver, ecc.). Le altre sezioni sono correlate a uno specifico sottocomando nlserver.

**Parametri condivisi**

* [autenticazione](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [module](#module)
* [monitoraggio](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**Altri parametri**

* [archiviazione](#archiving)
* [inMail](#inmail)
* [interattivo](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [tubato](#pipelined)
* [riparazione](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracking](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## autenticazione {#authentication}

Di seguito sono elencati i diversi parametri del nodo di **autenticazione** :

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Abilitare il controllo dell'indirizzo IP.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Modalità di identificazione predefinita.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Timeout delle sessioni lunghe in secondi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Timeout token di protezione in secondi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Durata cache: cache delle informazioni sulla sessione in secondi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Timeout sessione in secondi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Di seguito sono elencati i diversi parametri del nodo **autenticazione > XTK** :

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Password dell'account interno.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Zona di sicurezza dell'account interno: zona autorizzata per l'account interno.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Di seguito sono elencati i diversi parametri del nodo **dataStore** . Qui si trovano le origini dati del server.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Directory di esportazione: percorso della directory di destinazione per i dati esportati.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxDirectors<br /> </td> 
   <td> Directory sandbox supplementari: altri percorsi da aggiungere nella sandbox (separati da coma).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '/home/customer/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Ritardo scadenza cache modulo: timeout in secondi dopo il quale una voce della cache viene invalidata. O significa che le voci della cache vengono aggiornate solo al momento della pubblicazione.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> hosts<br /> </td> 
   <td> Maschere DNS: elenco di maschere DNS da usare in questa istanza (separate da virgola, è possibile utilizzare * e ? pattern).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> actionCacheTimeToLive<br /> </td> 
   <td> Ritardo scadenza cache JSSP interazione: timeout in secondi dopo il quale una voce della cache viene invalidata. Un valore negativo indica che la cache viene sempre invalidata. '0', i valori vuoti o non validi sono considerati 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Linguaggio dell'istanza (enumerazione). I valori possibili sono 'fr_FR' (Français), 'en_GB' (inglese), 'en_US' (inglese (USA)), 'de_DE' (Deutsch) e 'ja_JP' (giapponese).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Carica cartella: percorso della directory di destinazione per i dati caricati.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> File autorizzati da scaricare separati da ','. La stringa deve essere un'espressione Java regolare valida. Consultate <a href="../../installation/using/configuring-campaign-server.md#limiting-uploadable-files" target="_blank">Limitazione dei file</a>caricabili.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Archivia i segreti in Vault: utilizzare Hashicorp Vault.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Percorso segreto nell'archivio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Percorso locale del file che contiene il token di archiviazione. $(HOME) può essere utilizzato in questo percorso (ma non in altre variabili env).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> URL archivio di Hashicorp <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Periodo di validità della cache di visualizzazione: timeout in secondi dopo il quale una voce della cache viene invalidata. Un valore negativo indica che la cache viene sempre invalidata. '0', i valori vuoti o non validi sono considerati 60.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath della directory di lavoro.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> workingDirectory: XPath della directory di lavoro. Predefinito: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Di seguito sono elencati i diversi parametri del nodo **dataStore > proxyAdjust** . Gli URL che corrispondono all&#39;espressione regolare vengono rigenerati in base all&#39;URL definito in urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Base da utilizzare per la generazione di URL esterni. Ex: https://server.domain.com<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Espressione regolare per far corrispondere gli URL. Ex: http://server\.lan\.net.*<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Di seguito sono elencati i diversi parametri del nodo **dataStore > dataSource** .

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome origine dati<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

Nel nodo **dataStore > dataSource > dbcnx** , configura le impostazioni di connessione:

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Memorizzazione Unicode<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Area di lavoro<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> crittografato<br /> </td> 
   <td> Password crittografata<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Account<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Password<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Tipo (enumerazione). I valori possibili sono 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL, Greenplum), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' ( Amazon Redshift), 'ODBC' (ODBC (Sybase, SyASE) base IQ), 'Relay' (inoltro HTTP al database remoto).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> timezone<br /> </td> 
   <td> Fuso orario: consultate Gestione del fuso <a href="../../installation/using/time-zone-management.md" target="_blank">orario</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Dati Unicode nel database<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Campi data con fuso orario: consultate Gestione del fuso <a href="../../installation/using/time-zone-management.md" target="_blank">orario</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

Nel nodo **dataStore > dataSource > sqlParams** , configura i parametri SQL:

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Prefisso funzione<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Nel nodo **dataStore > dataSource > pool** , configura i parametri del pool di connessioni associato:

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> liveTestDelaySec<br /> </td> 
   <td> Ritardo tra i controlli di validità della connessione.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Numero di connessione gratuita custodito nella piscina.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Numero massimo di connessioni consentite prima del rifiuto di una nuova connessione. Vedi questa <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">nota tecnica</a>.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Tempo di inattività massimo della connessione. 0 indica il valore predefinito.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Di seguito sono elencati i diversi parametri del nodo **dataStore > virtualDir** . Questa è la configurazione della directory virtuale alla mappatura della directory reale.

Per ulteriori informazioni, vedere [Gestione delle risorse](../../installation/using/configuring-campaign-server.md#managing-public-resources)pubbliche.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome della directory virtuale <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> path<br /> </td> 
   <td> Percorso completo della directory effettiva<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Configurazione predefinita:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Di seguito sono elencati i diversi parametri del nodo **dataStore > preprocessCommand** . Questi sono i comandi autorizzati per la pre-elaborazione dell&#39;attività del flusso di lavoro &quot;Carica file&quot;.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Riga di comando <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etichetta riga di comando<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome riga di comando<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Configurazione predefinita:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Di seguito sono elencati i diversi parametri del nodo **dnsConfig** (configurazione DNS).

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Nome dominio: nome di dominio predefinito. Utilizzato dal comando HELO SMTP. per impostazione predefinita, utilizza i parametri di rete della prima interfaccia di rete dichiarata in Windows; oppure analizza la sezione file/etc/resolv.conf in Linux (dominio o voce di ricerca). <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> Server DNS: elenco separato da virgole di server di nomi di dominio (DNS). Vedi la nota sottostante.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> try<br /> </td> 
   <td> Numero di tentativi per una query DNS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout in millisecondi per una query DNS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Nota su **nameServer**: per impostazione predefinita, utilizza la rete
>parametri della prima interfaccia di rete dichiarata in Windows
>non definito in UNIX. Definisce i server dei nomi di dominio (DNS)
>utilizzato dall&#39;MTA per ottenere la dichiarazione di Mail Exchanger
>un dominio.
>
>Se questo valore non è definito, l&#39;MTA cerca queste informazioni nella configurazione della rete host. Se sono possibili più DNS, i diversi indirizzi DNS devono essere separati da una virgola (ad esempio: (212.155.207.1.212.155.207.2). Se il server di consegna ha diverse interfacce di rete, l&#39;elenco DNS utilizzato dall&#39;MTA è il primo. In questo caso, si consiglia di specificare il parametro **nameServer** per evitare ogni ambiguità.

>[!CAUTION]
>
>Se la configurazione host di rete utilizza DHCP, l&#39;MTA non troverà l&#39;elenco DNS fornito da DHCP. In questo caso, si consiglia di specificare l&#39;elenco DNS nei parametri di rete del pannello di controllo di Windows.

## exec {#exec}

Di seguito sono elencati i diversi parametri del nodo **exec** (esecuzione del comando).

Per ulteriori informazioni, vedere [Limitazione dei comandi](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)esterni autorizzati.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Percorso del file contenente i comandi da aggiungere al inserire nell'elenco Consentiti . <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> Eseguire i comandi come un altro utente.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Di seguito sono elencati i diversi parametri del nodo **htmlToPdf** . Questa è la configurazione del servizio per la conversione di pagine Web in documenti PDF.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Riga di comando per l'esecuzione della conversione (in modalità "altro").<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessCount<br /> </td> 
   <td> Max numero di processi di conversione consentiti alla volta su un computer.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Strumento da utilizzare per la conversione. I valori possibili sono: phantomjs, wkhtmltopdf, altro, disabilitato<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout per una conversione: tempo massimo di conversione in secondi. Oltre tale soglia, il processo di conversione viene interrotto e viene generato un errore.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verbose<br /> </td> 
   <td> Modalità dettagliata: avviare in modalità dettagliata per diagnosticare eventuali errori.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Ritardo in attesa di un processo: ritardo in secondi, quando tutti i processi vengono utilizzati allo stesso tempo e in attesa del rilascio di un processo. Se questo ritardo viene superato, la conversione viene interrotta e viene generato un errore. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esempio di phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## javaScript {#javascript}

Ecco i diversi parametri del nodo **javaScript** . Questa è la configurazione dell&#39;interprete JavaScript.

Per ulteriori informazioni, consulta la documentazione [](../../reporting/using/actions-on-reports.md#memory-allocation) Reporting (Rapporti) e questa [nota tecnica](https://helpx.adobe.com/campaign/kb/out-of-memory-error-in-js-code-activity-in-workflows.html).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Dimensione massima in MB prima di eseguire il Garbage Collector.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Dimensione di ogni blocco di stack in kilo ottetti. Si tratta di un parametro di ottimizzazione della gestione della memoria che la maggior parte degli utenti non dovrebbe regolare. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Di seguito sono elencati i diversi parametri del nodo **mailExchanger** . Questa è la configurazione del server SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> Server SMTP: Indirizzo IP del server SMTP per il trasferimento delle e-mail.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> Porta TCP del server SMTP utilizzata per il trasferimento e-mail.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Ecco i diversi parametri del nodo **modulo** . Questa è la configurazione per il modulo xtk delle restrizioni per gli spazi dei nomi.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Spazio dei nomi predefinito utilizzato per la creazione di una nuova entità.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoring {#monitoring}

Ecco i diversi parametri del nodo di **monitoraggio** . Questa è la configurazione del servizio di monitoraggio.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Tempo massimo di preparazione: durata in secondi dopo la quale un'azione di consegna non deve più essere in preparazione.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Script Unix eseguito dal servizio di monitoraggio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Script Windows che verrà eseguito dal servizio di monitoraggio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Ecco i diversi parametri del nodo **ooconv** . Configurazione del server di conversione documenti.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversioni<br /> </td> 
   <td> Numero massimo di conversioni consentite da un server OpenOffice. Oltre questo numero, il server viene riavviato.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Tempo di inattività massimo del server OpenOffice prima della chiusura forzata.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervallo di porte su cui i server OpenOffice sono in ascolto.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL del server di conversione documenti.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Ecco i diversi parametri del nodo **proxyConfig** . Questa è la configurazione dei parametri proxy.

Per ulteriori informazioni, vedere Configurazione [della connessione](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)proxy.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> Utilizzare un server proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Eccezioni: elenco di indirizzi per i quali i parametri proxy devono essere ignorati.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Server proxy univoco: utilizzate la stessa configurazione per tutti i tipi di proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Proxy HTTP / Proxy sicuro {#http-proxy---secure-proxy-}

Nel nodo **proxyConfig > Proxy HTTP/Proxy** sicuro, configura i seguenti parametri.

Per ulteriori informazioni, vedere Configurazione [della connessione](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)proxy.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Indirizzo del server proxy<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> login<br /> </td> 
   <td> Login per la connessione al server proxy<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Password per la connessione con il server proxy<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta server proxy<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Di seguito sono elencati i diversi parametri del nodo **threadPool** .

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Numero massimo di thread nel pool. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Di seguito sono elencati i diversi parametri del nodo **urlPermission** . Questo è l&#39;elenco di URL a cui il codice JavaScript può accedere.

Elenco di domini ed espressioni regolari che specificano se un URL rilevato nel codice JavaScript può o meno essere utilizzato dal server Adobe Campaign .

Se non è possibile trovare l’URL, l’azione predefinita viene eseguita, in base alla modalità predefinita specificata.

Per ulteriori informazioni, fare riferimento a Protezione connessione [in uscita](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> action<br /> </td> 
   <td> Azione predefinita se l’URL non è nell’elenco autorizzato (enumerazione). I valori possibili sono "ignore" (autorizzazione senza messaggio di avviso, che richiede la disattivazione della protezione), "warning" (autorizzazione e invio di un messaggio di avviso) e "Negativo" (divieto di accesso all'URL).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> negare<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Traccia del debug del meccanismo di selezione URL: emette altri messaggi durante il processo di verifica degli URL.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

Per ciascun URL, aggiungete un nodo **url** con i seguenti parametri:

Per ulteriori informazioni, fare riferimento a Protezione connessione [in uscita](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Nome di dominio o elemento padre del dominio interessato dall’URL: tutto o parte del dominio dell'URL per verificare, accelerare la verifica. L’URL viene verificato rispetto all’espressione regolare solo se il relativo dominio contiene dsnSuffix.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Espressione regolare per definire meglio gli URL di convalida appartenenti a questo dominio: espressione regolare che l’URL deve verificare, se corrisponde a dnsSuffix.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Se un record soddisfa **dnsSuffix** ma non **urlRegEx**, viene esaminato il record seguente.

Ad esempio, per autorizzare l’accesso a tutti gli URL del dominio business.com, possiamo definire due record:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.*&quot;

e

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.*&quot;

Configurazione predefinita:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Di seguito sono elencati i diversi parametri del nodo **xtkJobs** . Configurazione dei processi server.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Periodo di aggiornamento dello stato di memoria dell'elaborazione del server (in ms).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archiviazione {#archiving}

Di seguito sono elencati i diversi parametri del nodo di **archiviazione** . Si tratta della configurazione delle operazioni di archiviazione eseguite in background.

Per ulteriori informazioni, consulta [Attivazione dell’archiviazione delle e-mail (in sede)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> acquisitionLimit<br /> </td> 
   <td> Numero di EML da elaborare contemporaneamente<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archiveType<br /> </td> 
   <td> Strategia di archiviazione dei messaggi inviati (enumerazione). I valori possibili sono 0 (nessuna archiviazione) e 1 (trasferimento dell'archiviazione dei messaggi inviati a un server SMTP).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Dimensioni di un archivio compresso: numero massimo di file in un archivio compresso.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressioneFormat<br /> </td> 
   <td> Formato di compressione utilizzato durante l'archiviazione (enumerazione). I valori possibili sono '0' (nessuna compressione) e '1' (comprimi i messaggi inviati utilizzando il formato zip).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> completionDelay<br /> </td> 
   <td> Ritardo prima dell'archiviazione automatica delle e-mail non elaborate: numero di giorni prima dell'archiviazione delle e-mail non elaborate.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Ritardo (in secondi) tra ciascun evento di aggiornamento.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Numero di giorni prima dell'eliminazione delle e-mail non elaborate.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Destinazione di archiviazione<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Attivare il supporto SMTPS: attiva la distribuzione di e-mail in modalità provvisoria (STARTTLS/SMTPS) se supportata dal server remoto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Numero di connessioni al server SMTP di archiviazione.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Elenco separato da virgole di nomi DNS o indirizzi IP dei relè SMTP da utilizzare. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> Porta IP del server SMTP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Ecco i diversi parametri del nodo **inMail** . Questa è la configurazione del modulo di gestione e-mail in entrata.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Verifica nome istanza: se true, il nome dell'istanza Adobe Campaign  contenuta nelle intestazioni Message-ID deve essere uguale all'istanza corrente. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Indirizzo di inoltro: indirizzo di trasferimento e-mail predefinito non elaborato da una regola. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Indirizzo per gli errori: indirizzo predefinito utilizzato per trasferire le e-mail non valide (codifica MIME non valida). <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignora dimensione messaggio: viene utilizzato per ignorare le dimensioni di un messaggio restituito dai server POP3. In questo caso, il modulo prevede un '.' alla fine dei messaggi. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Periodo di lettura del messaggio: frequenza di polling della coda di messaggi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Numero massimo di registri da aggiornare: definisce il numero massimo di messaggi di registro da tenere in memoria prima di aggiornare il database.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Numero massimo di messaggi da leggere durante la sessione POP3.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Durata della sessione: durata massima della sessione di elaborazione dei messaggi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> Periodo di polling POP3<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Dimensione coda dei messaggi letti<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Timeout della comunicazione con il server POP3. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Frequenza di ricarica del database dei conti da sottoporre a polling.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

Nel nodo **inMail > msgDump** configurate i seguenti parametri. Questa è la configurazione del dump dei messaggi elaborati.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dump<br /> </td> 
   <td> Salvate tutti i messaggi in entrata in formato testo. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Percorso dump del messaggio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interattivo {#interactiond}

Ecco i diversi parametri del nodo **interattivo** . Questa è la configurazione del demone di scrittura per gli eventi Interazione in ingresso.

Per ulteriori informazioni, fare riferimento a [Interazione - Buffer](../../installation/using/interaction---data-buffer.md)dati.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max numero di caratteri memorizzati nella memoria condivisa per i dati delle chiamate.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max numero di eventi memorizzati nella memoria condivisa.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Numero massimo di offerte ammissibili ordinate subito dopo le proposte, da memorizzare per le statistiche.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Durata dell'aggregazione in secondi per le statistiche sui tempi di risposta. 0 significa che lo storage statistico è stato disattivato.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max numero di caratteri memorizzati nella memoria condivisa per identificare gli individui.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Ecco i diversi parametri del nodo **mta** . Questa è la configurazione degli agenti di consegna.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Salvataggio del percorso delle e-mail inviate: se non vuoto, il percorso in cui verranno salvati tutti i file sorgente delle e-mail inviate. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dump directory:iSe non vuoto, copiare le buste MIME dei messaggi di posta elettronica inviati in questa directory. Usata per le riprese di problemi. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Ritardo log query DNS: tempo in millisecondi per visualizzare i registri.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Frequenza delle statistiche di errore: tempo tra generazione di statistiche e archiviazione nel database. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Generate statistiche di errore e archiviatele nel database.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Visualizza il livello dei messaggi di registro. Livello di gravità dei registri scritti nel database. I messaggi di registro generati dall'MTA non vengono sempre scritti nel database. Con questo parametro, potete definire il livello da cui un messaggio deve essere scritto nel database. Se si definisce il livello 2, vengono scritti anche messaggi di livello 1 e 0, mentre se si definisce il livello 1 vengono scritti solo messaggi di livello 1 e 0. I valori possibili sono: 0 (errori), 1 (avviso), 2 (informazioni)<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Dimensione massima della memoria (in MB) che può essere utilizzata da un processo metadati. Al di sopra di questo limite, il processo viene riavviato in modo che la memoria utilizzata venga rilasciata al sistema.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Soglia di connessione da prendere in considerazione. Le statistiche di errore non vengono generate per un determinato percorso se il numero totale di connessioni per il periodo specificato da errorPeriodSec è strettamente inferiore alla soglia.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Soglia di errore da prendere in considerazione: le statistiche di errore non vengono generate per un determinato percorso se il numero totale di errori per il periodo specificato da errorPeriodSec è strettamente inferiore alla soglia.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Soglia del messaggio da prendere in considerazione. Le statistiche di errore non vengono generate per un determinato percorso se il numero totale di messaggi inviati per il periodo specificato da errorPeriodSec è strettamente inferiore alla soglia.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notificationRelay<br /> </td> 
   <td> Relè notifica: HostName:porta utilizzata per inviare le notifiche.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Ritardo prima dell'eliminazione delle e-mail archiviate: numero di giorni prima dell'eliminazione delle e-mail archiviate nella directory specificata in dataLogPath.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> tryLostMessages<br /> </td> 
   <td> Riprova messaggi persi: parti delle consegne verranno riprovate se il processo figlio è morto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Attivare il meccanismo di firma. Questo migliora la sicurezza del tracciamento dei collegamenti nelle e-mail.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Indirizzo del server delle statistiche di consegna, indicato come &lt;dns o ip&gt; <code>[</code>: 
     &lt;port&gt; <code>]</code>. Vedere <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordinate del server</a>di statistiche. 
      <br /> 
     </td> 
   <td> Stringa<br /> </td> 
   <td> Se non è definita, la porta predefinita è 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> Abilita TLS per dominio: abilita TLS configurabile da MX (richiede un server di statistiche aggiornato).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Versione protocollo utilizzata: versione del protocollo di comunicazione (1 per un server v5.11 e 6.0.2, 2 per un server v6.1).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> Se non è definita, viene utilizzata la versione più recente. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Se è impostato su "true", l’istanza utilizza l’MTA <a href="https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html" target="_blank"></a>avanzato.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Modalità di verifica: attiva la modalità di verifica (nessuna trasmissione fisica dei messaggi; utilizzati per la simulazione e i test).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Directory di lavoro: posizione dei file temporanei utilizzati dall'MTA per comunicare con i relativi processi figlio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Campo X-Mailer: valore del campo 'X-Mailer' nell'intestazione della posta SMTP.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

Nel nodo **cache** , configurate i seguenti parametri. Questa è la configurazione della cache del file locale.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Riciclato dopo: punto, espresso in secondi, dopo il quale il file viene automaticamente eliminato dalla cache per recuperare lo spazio di archiviazione.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Dimensione massima cache (Mb).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Frequenza di rimozione: periodo in secondi tra le esecuzioni del meccanismo di rimozione della cache.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relè {#relay}

Nel nodo **mta > relay** configurate i seguenti parametri. Configurazione del server di posta elettronica per la consegna dei messaggi.

Per ulteriori informazioni, fare riferimento al relè [SMTP](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Elenco separato da virgole di nomi DNS o indirizzi IP dei relè SMTP da utilizzare. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta IP del server SMTP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

Nel nodo **mta > master** , configurate i seguenti parametri. Questa è la configurazione del server principale.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Frequenza di polling del database dei processi da distribuire. Questo valore indica la frequenza di polling del database (in secondi). Per ottenere l’elenco dei processi in attesa di consegna, l’MTA controlla regolarmente il database. Se non è previsto alcun processo, il periodo di polling è definito da questo valore. In caso contrario, se un processo è stato trasferito a un server secondario, la durata del polling viene automaticamente ridotta a un secondo, in modo che un nuovo processo possa essere elaborato il prima possibile, ossia non appena un server figlio sarà nuovamente disponibile. Ciò non significa che la query del database verrà eseguita ogni secondo finché non sarà disponibile di nuovo un server figlio. In realtà, l'accesso al database viene eseguito solo quando è disponibile almeno un server figlio.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Periodo di attesa dopo un errore di connessione al database. Un errore di connessione al database è in genere causato dallo stesso server del database. Il server può essere arrestato anche a scopo di manutenzione, ad esempio. Il parametro DataBaseRetryDelay definisce la durata tra due tentativi di connessione in caso di errore di connessione al database.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Periodo di validità per la cache delle chiavi private (DomainKeys). Le chiavi private utilizzate per firmare i messaggi e-mail in seguito alla raccomandazione DomainKeys (http://antispam.yahoo.com/domainkeys) sono memorizzate come opzioni nel database. Il parametro domainKeysReloadPeriodSec definisce quanti secondi il MTA può mantenere queste chiavi in una cache. Dopo questo ritardo, tutte le chiavi devono essere ricaricate dal database.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Numero massimo di server figlio. Rappresenta il numero massimo di server in esecuzione. È consigliabile limitare questo numero a un livello ottimale compatibile con le risorse di memoria del server. Questo può essere controllato durante una consegna. La memoria utilizzata non deve superare un terzo della memoria fisica disponibile altrimenti verrà utilizzato lo swap. Consultate <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Processi</a>figlio MTA.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Numero minimo di server figlio. L'MTA tenta di mantenere in esecuzione almeno questo numero di server. Se sono presenti minori, i nuovi server vengono riavviati ogni secondo fino al raggiungimento di tale valore.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Numero di server figlio all’avvio. Il numero di server secondari è monitorato dinamicamente; all'avvio dell'MTA, viene creato il numero di server secondari indicato da questo valore. Normalmente, i server secondari non possono essere avviati più velocemente di un server al secondo per salvare le risorse host. Tuttavia, all'avvio dell'MTA, questa limitazione viene annullata in modo che i server figlio siano disponibili al più presto.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### bambina {#child}

Nel nodo **mta > secondario** configurate i seguenti parametri. Questa è la configurazione dei server secondari.

Per ulteriori informazioni, consultate Ottimizzazione dell&#39;invio per [e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Argomenti della riga di comando facoltativi <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Timeout fino all’arresto dei server figlio inattivi. Se un server figlio ha un tempo di inattività maggiore di questo parametro, si interrompe automaticamente per liberare le risorse host.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Tempo massimo di conservazione dei messaggi. Se non è stato possibile inviare un messaggio preparato a causa della limitazione o non è stato possibile connettersi all'MTA di destinazione, il messaggio viene abbandonato e verrà elaborato al successivo tentativo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Numero massimo di richieste HTTP parallele a FCM avviate da ogni server figlio.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Numero massimo di messaggi per server figlio. Ogni figlio MTA elabora questo numero di messaggi e muore. È importante specificare un numero tale che le perdite di memoria o di risorse nell'MTA siano innocue (in genere poche migliaia). Anche se non ci sono perdite di memoria note nel codice MTA, i motori JavaScript e XSL incorporati non sono completamente affidabili.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Messaggi in sospeso: numero massimo di messaggi in attesa di consegna in memoria. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Dimensione massima della memoria (in MB) utilizzabile da un processo figlio. Al di sopra di questo limite, il processo viene interrotto in modo che la memoria utilizzata venga rilasciata al sistema. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in secondi) dopo il quale viene abbandonata una connessione SOAP per un connettore di consegna.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Inizia sempre con la massima priorità MX.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Numero massimo di tentativi consecutivi ripresi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

Nel nodo **mta > figlio > smtp** , configurate i seguenti parametri. Questa è la configurazione delle sessioni SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Attiva la distribuzione di e-mail in modalità provvisoria (STARTTLS/SMTPS) se supportata dal server remoto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Timeout sessione inattiva. Questo parametro viene utilizzato solo se la sessione viene riutilizzata per la trasmissione di più messaggi a un determinato dominio. Quando l'MTA ha completato la trasmissione del messaggio, la sessione SMTP utilizzata non viene chiusa sistematicamente. Se un messaggio è pronto per essere inviato per lo stesso dominio, la stessa sessione SMTP verrà riutilizzata ed è per questo che la sessione non viene chiusa automaticamente. Il parametro IdleSessionTimeout consente di definire l’ora durante la quale una sessione SMTP può rimanere attiva in attesa di un altro messaggio. Una volta trascorso il tempo, la sessione viene chiusa automaticamente.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Ritardo iniziale prima di riprovare la connessione. Questo ritardo viene raddoppiato ogni volta che la connessione non riesce.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Numero massimo di sessioni SMTP per server figlio. Per inviare un messaggio, l'MTA inizializza una connessione SMTP con l'MTA del destinatario. Il numero massimo di sessioni SMTP simultanee e attive per un determinato server figlio è limitato da questo valore. Se moltiplicate questo valore per maxSpareServers, viene visualizzato il numero massimo di messaggi che possono essere elaborati contemporaneamente da un determinato server figlio.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Nel nodo **mta > child > smtp > IPAffinity** , configurate i seguenti parametri. Questa è la configurazione della gestione delle affinità con indirizzi IP per il traffico SMTP in uscita ottimizzato.

Per ulteriori informazioni, vedere [Elenco di indirizzi IP da utilizzare](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) e [Gestione del traffico SMTP in uscita con affinità](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Nome dominio: nome di dominio locale collegato all'indirizzo IP. Utilizzato per l'emissione di un comando HELO SMTP.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome logico: nomi collegati all'affinità da parte degli utenti. I nomi sono separati mediante punto e virgola;<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

In **mta > child > smtp > IP** node, configurate i seguenti parametri.

Per ulteriori informazioni, vedere [Elenco di indirizzi IP da utilizzare](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Indirizzo fisico associato. Esempio: '192.168.0.1'<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> ID indirizzo pubblico associato. Utilizzata come chiave per il server di statistiche. Deve essere numerico. See this <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">section</a>.<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> weight<br /> </td> 
   <td> Specifica la frequenza di utilizzo per questo IP, rispetto ad altri IP (i pesi maggiori determinano frequenze più elevate).<br /> </td> 
   <td> Long<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Elenco separato da virgole di maschere di dominio da includere.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Elenco separato da virgole di maschere di dominio da escludere.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Nome computer collegato all'indirizzo IP. Utilizzato per l'emissione di un comando HELO SMTP.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Ecco i diversi parametri del nodo **nmac** . Questa è la configurazione di per le consegne di notifiche push.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Utilizzate il proxy HTTP definito in shared/proxyHTTP. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relè {#relay-1}

Ecco i diversi parametri del nodo **nmac > relay** . Configura l&#39;utilizzo di un relè per la distribuzione dei messaggi (connettore http2 ios).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> address<br /> </td> 
   <td> Indirizzo DNS o nome del relè da utilizzare. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta Relè<br /> </td> 
   <td> Long<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Catena certificati (file PEM). Utile quando si utilizza un server fittizio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## tubato {#pipelined}

Ecco i diversi parametri del nodo **tubato** . Questa è la configurazione del modulo di elaborazione eventi per Pipeline Services.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Nome dell'applicazione generata nella connessione Sviluppatore quando viene salvata la chiave pubblica. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL per ottenere un token gateway.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Chiave privata per ottenere i token (cifrata in AES con l’opzione XtkKey).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Disattiva autenticazione: connettersi ai servizi pipeline senza autenticazione. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> findPipelineEndpoint<br /> </td> 
   <td> URL per scoprire l’URL di Pipeline Services.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Periodo di salvataggio stato: frequenza con cui le informazioni interne del processo vengono salvate in un file. Inattivo se 0. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forzatoPipelineEndpoint<br /> </td> 
   <td> URL di ascolto: forzate l'URL di ascolto dei servizi pipeline. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Porta del server di stato: Porta del server HTTP che consente di eseguire una query sullo stato del processo. Inattivo se 0.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> puntatoreFlushMessageCount<br /> </td> 
   <td> Il puntatore viene memorizzato nel database ogni volta che questo numero di messaggi viene elaborato.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> puntatoreFlushPeriodSec<br /> </td> 
   <td> Ritardo prima della memorizzazione del puntatore: il puntatore sarà memorizzato nel database almeno una volta durante questo periodo (utile in caso di attività bassa).<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThread<br /> </td> 
   <td> Numero di thread per l'elaborazione degli eventi con un connettore JavaScript personalizzato.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThread<br /> </td> 
   <td> Numero di thread per l'elaborazione degli eventi.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> tryPeriodSec<br /> </td> 
   <td> Ritardo tra l'elaborazione in caso di errore.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> tryValiditySec<br /> </td> 
   <td> Abbandonare dopo tale periodo: abbandonare l'evento se l'elaborazione continua a non riuscire dopo tale periodo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## riparazione {#repair}

Di seguito sono elencati i diversi parametri del nodo **Repair** . Questa è la configurazione del modulo di ripristino del database.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> RepairActionDelayMin<br /> </td> 
   <td> Modulo di riparazione azioni di consegna: ritardo (in minuti) dopo il quale le azioni di consegna possono essere elaborate dal modulo di riparazione. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Di seguito sono elencati i diversi parametri del nodo **securityZone** .

Per ulteriori informazioni, vedere [Definizione delle aree](../../installation/using/configuring-campaign-server.md#defining-security-zones)di protezione.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Autorizzate la modalità di debug per le applicazioni Web.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autorizzare l'utente a utilizzare l'applicazione senza una password.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Autorizzare l'utilizzo di HTTP per l'accesso dell'operatore.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorizzate l'utilizzo di SQLDATA nelle espressioni.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Autorizzate i token di sessione utente/password.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etichetta<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome interno<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Non utilizzate il token di protezione.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Visualizza dettagli errore<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Configurazione predefinita:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Di seguito sono elencati i diversi parametri del nodo **securityZone > subNetwork** .

Per ulteriori informazioni, vedere [Definizione delle aree](../../installation/using/configuring-campaign-server.md#defining-security-zones)di protezione.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etichetta<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> mask<br /> </td> 
   <td> Maschera o indirizzo<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome interno<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Maschera o indirizzo del proxy (inverso) utilizzato da questa sub-rete per accedere all'istanza. In questo caso, l'intestazione 'X-Forwarded-For' verrà testata invece del proxy.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Di seguito sono elencati i diversi parametri del nodo **sms** . Questa è la configurazione del modulo di gestione SMS in entrata.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Numero massimo di file di lavoro giorni conservati dal connettore SMPP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Dimensione massima in MB dei file di lavoro SMPP.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Frequenza del fotogramma di continuità della sessione: max intervallo in secondi tra due fotogrammi per notificare che la sessione di ricezione è ancora abilitata.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Frequenza di ricerca: Periodo del sondaggio dell'account SMS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Frequenza di ricarica dell'account: frequenza di ricarica del database degli account da interrogare.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Numero di secondi di ritardo per l'elaborazione SR: solo le SR con una data di recupero precedente a quella corrente, meno la durata in secondi indicata da srReadDelay. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout della comunicazione con il gateway SMS.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Di seguito sono elencati i diversi parametri del nodo **sms > netsize** .

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Timeout in secondi quando si stabilisce una connessione con Netsize.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Ecco i diversi parametri del nodo **stat** . Questa è la configurazione del modulo di statistiche MTA.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Porta di ascolto del server. See this <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">section</a>.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Ecco i diversi parametri del nodo **syslogd** . Questa è la configurazione del modulo di gestione log.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Dimensione massima in MB per un file di registro. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Numero massimo di file logins.log da mantenere. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracking {#tracking}

Ecco i diversi parametri del nodo di **tracciamento** . Configurazione del server di tracciamento.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Disattiva gli URL generati in modo errato dalle build precedenti.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidamentoPeriodSec<br /> </td> 
   <td> Periodo di consolidamento<br /> </td> 
   <td> Long<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Aperture deduplicazione: rimuovete i registri di tracciamento aperti duplicati per limitare gli effetti delle anteprime di posta in lettori di posta come Outlook.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignora fino a X% errori: non aggiornare gli indicatori di tracciamento a condizione che il rapporto delle scritture contabili non ancora prese in considerazione non raggiunga questo valore. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Aggiorna indicatori di errore: durata massima prima che gli indicatori di errore vengano ricalcolati.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatoriDurata<br /> </td> 
   <td> Calcola gli indicatori durante: durata successiva alla data di validità di una consegna dopo la quale gli indicatori consolidati non sono più calcolati.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Numero di registri richiesti da una chiamata al server di tracciamento remoto.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Chiave API per l'integrazione endpoint di Phishbowl Service. In questo modo viene protetto il reindirizzamento degli URL con formazione non corretta generati dalle build meno recenti. <br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpoint per l'integrazione dell'endpoint del servizio Phishbowl. In questo modo viene protetto il reindirizzamento degli URL con formazione non corretta generati dalle build meno recenti.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignora fino a X% del tracciamento: non aggiornare gli indicatori di tracciamento a condizione che il rapporto delle scritture contabili non ancora prese in considerazione non raggiunga questo valore.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aggiorna indicatori di tracciamento: durata massima prima che gli indicatori di tracciamento vengano ricalcolati.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Dimensione della cache degli identificatori del browser.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Ecco i diversi parametri del nodo **trackinglogd** . Questa è la configurazione del demone di scrittura del registro di tracciamento.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Numero massimo di tentativi di scrittura: numero massimo di file che possono essere creati in caso di errore di scrittura nei file di registro.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Dimensione massima del registro: spazio massimo utilizzato dai registri su disco (in MB). Non può essere inferiore a 100 MB. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Numero massimo di log: numero massimo di registri memorizzati nella memoria condivisa. Non può essere inferiore a 10000. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Numero di log prima della rimozione: numero di file di registro inseriti prima di avviare la rimozione dei file di registro. Può non essere inferiore a 50000.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Numero massimo di caratteri salvati nella memoria condivisa per ulteriori parametri di tracciamento Web.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Di seguito sono elencati i diversi parametri del nodo **Web** . Questa è la configurazione del modulo Web.

For additional information, refer to this [section](../../installation/using/configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> Opzioni della JVM passate come stringa.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThread<br /> </td> 
   <td> Numero massimo di thread.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThread<br /> </td> 
   <td> Numero minimo di thread.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Porta di controllo di ascolto Tomcat: fare riferimento a <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configurazione di Tomcat</a>.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Porta di ascolto Tomcat HTTP: fare riferimento a <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configurazione di Tomcat</a>.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Dimensione della coda per le chiamate SubmitDelivery: numero massimo di chiamate SOAP SubmitDelivery che possono essere messe in coda.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notificationRelay<br /> </td> 
   <td> Relè notifica: HostName:porta che abilita il relay delle notifiche.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Avviare il router SOAP in modalità modulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Ecco i diversi parametri del nodo **web > jsp** . Questa è la configurazione dei parametri utilizzati dalle JSP.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> Esecuzione di JSP in modalità debug o meno.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Scarica cartella: percorso di download dei programmi di installazione per le console client.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Percorso del file .fo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL del router SOAP (http://myserver/xxx, http://jni o mailto:xxx).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Il nodo **web > jsp > classpath** contiene l&#39;elenco di tutti i percorsi di classe da utilizzare all&#39;avvio di JVM. Configurazione predefinita:

```
'$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
          $(XTK_INSTALL_DIR)/java/lib/log4j-1.2.11.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Ecco i diversi parametri del nodo **web > jssp** . Questa è la configurazione dei parametri utilizzati dalle JSSP.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectGarbageAfterRequest<br /> </td> 
   <td> Abilita il Garbage Collector del contesto JavaScript dopo ogni query.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Numero massimo di pagine servite da un contesto JavaScript. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Il nodo **web > jsp > classpath** contiene l&#39;elenco di tutti i percorsi di classe da utilizzare all&#39;avvio di JVM.

### relè {#relay-2}

Di seguito sono elencati i diversi parametri del nodo **Web > relay** . Questa è la configurazione del relay per le richieste HTTP tra due aree.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Avviate il modulo di inoltro HTTP all'interno del server Web in modalità di debug.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Carattere(i) proibito(i) (Dominio): elenco di caratteri proibiti nella sezione "autorità" di un URI.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Carattere(i) proibito(i) (Percorso): elenco di caratteri non consentiti nella sezione 'percorso' di un URI.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Valore dell'opzione del modulo 'mod_dir': elenco di file da utilizzare durante una query su una cartella.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Avviate il modulo di inoltro HTTP.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Avviate il modulo di inoltro HTTP all'interno del server Web. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Attendere prima di eliminare l'URL vietato.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Aggiungete un nodo **Web > relay > url** per ciascun URL da inviare (l&#39;ordine di inserimento definisce la priorità) con i seguenti parametri.

Per ulteriori informazioni, vedere Protezione [dinamica delle pagine, relè](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) e [sezione](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> IP autorizzati: elenco separato da virgole di indirizzi IP di origine consentiti per utilizzare il relè per questa maschera.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> negare<br /> </td> 
   <td> Rifiuta l’accesso a questi URL (restituisce un errore HTTP 403)<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Alias DNS da relay: elenco separato da virgole di maschere alias DNS da inviare (ad esempio: '*.adobe.com').<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> L'accesso HTTP è autorizzato indipendentemente dall'area di protezione (come webApps). <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Aggiungi host originale: durante la trasmissione, utilizzate l'intestazione HTTP 'Host' della richiesta originale.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Aggiungi percorso URL iniziale: aggiungete il percorso completo degli URL da inviare all’URL della pagina di destinazione. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Stato di sincronizzazione di una risorsa pubblica (enumerazione). I valori possibili sono "normal" (esecuzione normale), "blacklist" (url aggiunto al elenco Bloccati in caso di errore 404) e "spare" (caricamento di file sul server di riserva, se esistente).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL della pagina di destinazione: fare riferimento a <a href="../../installation/using/configuring-campaign-server.md#configuring-tomcat" target="_blank">Configurazione di Tomcat</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo massimo di esecuzione (in secondi) della richiesta in corso di inoltro.<br /> </td> 
   <td> Long<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Maschera degli URL da inviare (ad esempio: '/nl*', '*.jsp').<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Configurazione predefinita:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Aggiungete un nodo **Web > relay > responseHeader** per ciascuna intestazione HTTP da aggiungere alle risposte inoltrate al relay.

Per ulteriori informazioni, vedere [Gestione delle intestazioni](../../installation/using/configuring-campaign-server.md#managing-http-headers)HTTP.

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Nome intestazione<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> Valore intestazione <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Configurazione predefinita:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### reindirizzamento {#redirection}

Di seguito sono elencati i diversi parametri del nodo **Web > redirection** . Questa è la configurazione del modulo di reindirizzamento.

For additional information, refer to this [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Identificatore organizzazione IMS: identificatore univoco dell’organizzazione all’interno dell’Adobe Marketing Cloud, utilizzato in particolare per il servizio VisitorID e l’SSO IMS. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Valore che descrive il criterio utilizzato per i cookie permanenti (conforme al formato P3P Compact Policy). <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'CAO DSP COR CURa DEVa TAIa NOSTRO AUTOBUS IND UNI COM NAV'<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Elenco di domini separati da virgole da configurare per indicare esplicitamente il dominio in cui impostare il cookie. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Identificatore del database associato all'istanza di tracciamento.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Conteggio log per chiamata: numero di registri restituiti per impostazione predefinita in seguito a una chiamata del metodo GetTrackingLogs.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Pagina per reindirizzamenti scaduti: URL della pagina Web utilizzata per impostazione predefinita dal server di reindirizzamento quando il reindirizzamento per un'azione di consegna è scaduto.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Numero massimo di processi: numero massimo di azioni di consegna nella cache. Può non essere inferiore a 50. <br /> </td> 
   <td> Long<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Avviare il servizio di reindirizzamento.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Avviare il servizio di reindirizzamento in modalità modulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Tracciamento Web: creazione di registri per le pagine visitate da utenti sconosciuti. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Password utilizzata dal server di reindirizzamento.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Di seguito sono elencati i diversi parametri del nodo **Web > redirection > spareServer** .

Per ulteriori informazioni, consultate Tracciamento [ridondante](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Se: il server di tracciamento viene preso in considerazione se l'espressione restituisce true. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Nome<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL server di reindirizzamento aggiuntivo<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Ecco i diversi parametri del nodo **web > spamCheck** . Questa è la configurazione dei parametri di valutazione del punteggio per l&#39;anti-spam e-mail.

Per ulteriori informazioni, vedere [Configurazione di SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Comando da eseguire per valutare il punteggio di un'e-mail relativo all'anti-spam (ad es. 'perl spamcheck.pl').<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Ecco i diversi parametri del nodo **wfserver** . Questa è la configurazione del processo del flusso di lavoro.

Per ulteriori informazioni, consulta Flussi di lavoro e affinità [ad alta disponibilità](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parametro </th> 
   <th> Descrizione </th> 
   <th> Tipo </th> 
   <th> Valore predefinito </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affinità<br /> </td> 
   <td> Affinità<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Parametri di avvio<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Avvio automatico<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Periodo<br /> </td> 
   <td> Long<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID di JavaScript da eseguire all'avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM consumata (in Mb) da un determinato processo.<br /> </td> 
   <td> Long<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notificationRelay<br /> </td> 
   <td> Relè notifica: HostName:porta che abilita il relay delle notifiche.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consultate Riavvio <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank"></a>automatico del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all'inizio. I moduli con priorità bassa vengono avviati per primi e interrotti per ultimo. Il modulo syslogd deve pertanto avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

