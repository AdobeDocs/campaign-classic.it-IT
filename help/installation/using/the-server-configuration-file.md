---
product: campaign
title: Il file di configurazione del server
description: Il file di configurazione del server
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 67a6e03318a74b665dc6928028470f98c0abae5e
workflow-type: tm+mt
source-wordcount: '8075'
ht-degree: 3%

---

# Il file di configurazione del server{#the-server-configuration-file}

La configurazione generale di Adobe Campaign è definita nella sezione **serverConf.xml** file, che si trova in **conf** directory della directory di installazione. In questa sezione sono elencati tutti i diversi nodi e parametri di **serverConf.xml** file.

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite solo da Adobe per le distribuzioni in hosting da Adobe. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o a [questa pagina](../../installation/using/capability-matrix.md). I passaggi di installazione e configurazione per i modelli in hosting e ibridi sono descritti in questo [sezione](../../installation/using/hosting-models.md).

I primi parametri si trovano all&#39;interno del **condiviso** nodo. Sono correlati all’istanza. Sono potenzialmente utilizzati da tutti i comandi nlserver (nlserver web, nlserver wfserver, ecc.). Le altre sezioni sono correlate a uno specifico sottocomando nlserver.

**Parametri condivisi**

* [autenticazione](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [esegui](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [JavaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [modulo](#module)
* [monitoraggio](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**Altri parametri**

* [archiviazione](#archiving)
* [inMail](#inmail)
* [interagire](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [pipeline](#pipelined)
* [riparare](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [tracciamento](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## autenticazione {#authentication}

Di seguito sono riportati i diversi parametri di **autenticazione** nodo:

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
   <td> Abilita il controllo degli indirizzi IP.<br /> </td> 
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
   <td> Timeout di sessioni lunghe in secondi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Timeout del token di sicurezza in secondi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Durata cache: cache delle informazioni sulla sessione in secondi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Timeout della sessione in secondi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Di seguito sono riportati i diversi parametri di **authentication (autenticazione) > XTK** nodo:

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
   <td> Password dell’account interno.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Area di sicurezza account interno: area autorizzata per l’account interno.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Di seguito sono riportati i diversi parametri di **dataStore** nodo. Qui vengono definite le origini dati del server.

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
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Directory aggiuntive in modalità sandbox: altri percorsi da aggiungere nella sandbox (separati da virgola).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Ritardo scadenza cache modulo: timeout in secondi dopo il quale una voce della cache viene invalidata. O significa che le voci della cache vengono aggiornate solo al momento della pubblicazione.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> host<br /> </td> 
   <td> Maschere DNS: elenco di maschere DNS utilizzate da questa istanza (separate da virgola, è possibile utilizzare * e ? pattern).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interfaceCacheTimeToLive<br /> </td> 
   <td> Ritardo scadenza della cache JSSP dell’interazione: timeout in secondi dopo il quale una voce della cache viene invalidata. Un valore negativo indica che la cache viene sempre invalidata. '0', i valori vuoti o non validi sono considerati 60.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Linguaggio dell’istanza (enumerazione). I valori possibili sono 'fr_FR' (Français), 'en_GB' (Inglese (Regno Unito)), 'en_US' (Inglese (Stati Uniti)), 'de_DE' (Deutsch) e 'ja_JP' (Giapponese).<br /> </td> 
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
   <td> File autorizzati da scaricare separati da ",". La stringa deve essere un'espressione Java regolare valida. Consulta <a href="file-res-management.md" target="_blank">Limitazione dei file caricabili</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Memorizza i segreti in Vault: usa Hashicorp Vault.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Percorso segreto in Vault<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '/v1/secret/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Percorso locale del file che contiene il token di Vault. $(HOME) può essere utilizzato in questo percorso (ma non in altre variabili env).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> URL di Hashicorp Vault <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Periodo di validità della cache di visualizzazione: timeout in secondi dopo il quale una voce della cache viene invalidata. Un valore negativo indica che la cache viene sempre invalidata. '0', i valori vuoti o non validi sono considerati 60.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath della directory di lavoro.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> workingDirectory : XPath della directory di lavoro. Predefinito: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Di seguito sono riportati i diversi parametri di **dataStore > proxyAdjust** nodo. Gli URL corrispondenti all’espressione regolare vengono rigenerati in base all’URL definito in urlBase.

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
   <td> Base da utilizzare per la generazione di URL esterni. Esempio: https://server.domain.com<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Espressione regolare che corrisponde agli URL. Esempio: http://server\.lan\.net.*<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Di seguito sono riportati i diversi parametri di **dataStore > dataSource** nodo.

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
   <td> nome<br /> </td> 
   <td> Nome origine dati<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> predefinito<br /> </td> 
  </tr> 
 </tbody> 
</table>

In **dataStore > dataSource > dbcnx** configurare le impostazioni di connessione:

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
   <td> Archiviazione Unicode<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Workspace<br /> </td> 
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
   <td> accesso<br /> </td> 
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
   <td> Tipo (enumerazione). I valori possibili sono 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ)), 'Relay' (inoltro HTTP al database remoto).<br /> </td> 
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
   <td> fuso orario<br /> </td> 
   <td> Fuso orario: vedi <a href="../../installation/using/time-zone-management.md" target="_blank">Gestione del fuso orario</a>.<br /> </td> 
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
   <td> Campi data con fuso orario: vedi <a href="../../installation/using/time-zone-management.md" target="_blank">Gestione del fuso orario</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

In **dataStore > dataSource > sqlParams** , configurare i parametri SQL:

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

In **dataStore > dataSource > pool** configurare i parametri del pool di connessioni associato:

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
   <td> aliveTestDelaySec<br /> </td> 
   <td> Ritardo tra i controlli di validità della connessione.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Numero di connessioni gratuite mantenute nel pool.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Numero massimo di connessioni consentite prima di rifiutare una nuova connessione. Vedi questo <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">nota tecnica</a>.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Tempo massimo di inattività della connessione. 0 significa valore predefinito.<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Di seguito sono riportati i diversi parametri di **dataStore > virtualDir** nodo. Configurazione della directory virtuale per il mapping della directory reale.

Per ulteriori informazioni, consulta [Gestione delle risorse pubbliche](file-res-management.md).

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
   <td> nome<br /> </td> 
   <td> Nome della directory virtuale <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> percorso<br /> </td> 
   <td> Percorso completo della directory effettiva<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Di seguito è riportata la configurazione predefinita:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Di seguito sono riportati i diversi parametri di **dataStore > preprocessCommand** nodo. Questi sono i comandi autorizzati per la pre-elaborazione dell’attività del flusso di lavoro &quot;Carica file&quot;.

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
   <td> comando<br /> </td> 
   <td> Riga di comando <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> etichetta<br /> </td> 
   <td> Etichetta della riga di comando<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> nome<br /> </td> 
   <td> Nome riga di comando<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Di seguito è riportata la configurazione predefinita:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Di seguito sono riportati i diversi parametri di **dnsConfig** (configurazione DNS).

Per ulteriori informazioni, consulta questa [sezione](../../installation/using/configuring-campaign-server.md).

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
   <td> Nome di dominio: nome di dominio predefinito. Utilizzato dal comando SMTP HELO. Per impostazione predefinita, utilizza i parametri di rete della prima interfaccia di rete dichiarata in Windows oppure analizza file/etc/resolv.conf in Linux (dominio o voce di ricerca). <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> Server DNS: elenco separato da virgole dei server dei nomi di dominio (DNS). Vedi la nota seguente.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> riprova<br /> </td> 
   <td> Numero di tentativi per una query DNS.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout in millisecondi per una query DNS.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Nota su **nameSevers**: per impostazione predefinita, utilizza la rete
>parametri della prima interfaccia di rete dichiarata in Windows
>non definito in UNIX. Definisce i server dei nomi di dominio (DNS)
>utilizzato dall’MTA per ottenere la dichiarazione di Mail Exchanger per
>un dominio.
>
>Se questo valore non è definito, l’MTA cerca queste informazioni nella configurazione della rete host. Se sono possibili più DNS, i diversi indirizzi DNS devono essere separati da una virgola (ad esempio: 212.155.207.1,212.155.207.2). Se il server di consegna dispone di diverse interfacce di rete, l’elenco DNS utilizzato dall’MTA è il primo. In questo caso, si consiglia di specificare **nameServer** per evitare ambiguità.

>[!CAUTION]
>
>Se la configurazione host di rete utilizza DHCP, l&#39;MTA non troverà l&#39;elenco DNS fornito da DHCP. In questo caso, è consigliabile specificare l&#39;elenco DNS nei parametri di rete del Pannello di controllo di Windows.

## esegui {#exec}

Di seguito sono riportati i diversi parametri di **esegui** (esecuzione del comando).

Per ulteriori informazioni, consulta [Limitazione dei comandi esterni autorizzati](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

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
   <td> Percorso del file contenente i comandi da aggiungere al inserisco nell'elenco Consentiti di. <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> utente<br /> </td> 
   <td> Eseguire i comandi come un altro utente.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Di seguito sono riportati i diversi parametri di **htmlToPdf** nodo. Configurazione del servizio per la conversione di pagine web in documenti PDF.

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
   <td> comando<br /> </td> 
   <td> Riga di comando per eseguire la conversione (in modalità "other").<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max numero di processi di conversione consentiti alla volta in un computer.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> modalità<br /> </td> 
   <td> Strumento da utilizzare per la conversione. I valori possibili sono: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout per una conversione: tempo di conversione massimo in secondi. Oltre questa soglia, il processo di conversione viene interrotto e viene generato un errore.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> verboso<br /> </td> 
   <td> Modalità dettagliata: avvia in modalità dettagliata per diagnosticare i possibili errori.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Ritardo nell’attesa di un processo: ritardo in secondi, quando tutti i processi vengono utilizzati contemporaneamente e quando si attende che un processo si liberi. Se questo ritardo viene superato, la conversione viene interrotta e viene generato un errore. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Esempio di phantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Di seguito sono riportati i diversi parametri di **ims** nodo. Questa è la configurazione per Campaign che si connette a un altro servizio utilizzando [IMS](../../integrations/using/about-adobe-id.md).

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
   <td> authIMSClientId<br /> </td> 
   <td> ID client<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Chiave segreta (crittografata in AES)<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Codice di autorizzazione (crittografato in AES)<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> URL del server IMS<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> ID client account tecnico<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Chiave segreto account tecnico (crittografata in AES)<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> ID account tecnico<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Chiave privata account tecnico (crittografata in AES)<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Di seguito sono riportati i diversi parametri di **JavaScript** nodo. Questa è la configurazione dell’interprete JavaScript.

Per ulteriori informazioni, consulta [Documentazione del reporting](../../reporting/using/actions-on-reports.md#memory-allocation).

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
   <td> max MB<br /> </td> 
   <td> Dimensione massima in megabyte prima di eseguire il garbage collector.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Dimensione di ogni blocco di stack in kilobyte. Si tratta di un parametro di ottimizzazione della gestione della memoria che la maggior parte degli utenti non deve regolare. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Di seguito sono riportati i diversi parametri di **mailExchanger** nodo. Configurazione del server SMTP.

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

## modulo {#module}

Di seguito sono riportati i diversi parametri di **modulo** nodo. Configurazione del modulo xtk delle restrizioni degli spazi dei nomi.

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
   <td> Spazio dei nomi predefinito utilizzato durante la creazione di una nuova entità.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## monitoraggio {#monitoring}

Di seguito sono riportati i diversi parametri di **monitoraggio** nodo. Configurazione del servizio di monitoraggio.

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
   <td> Tempo massimo di preparazione: durata in secondi dopo la quale un’azione di consegna non deve più essere in preparazione.<br /> </td> 
   <td> Lungo<br /> </td> 
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
   <td> Script Windows che deve essere eseguito dal servizio di monitoraggio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Di seguito sono riportati i diversi parametri di **ooconv** nodo. Configurazione del server di conversione dei documenti.

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
   <td> maxConversions<br /> </td> 
   <td> Numero massimo di conversioni che un server OpenOffice può eseguire. Oltre questo numero, il server viene riavviato.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Tempo massimo di inattività del server OpenOffice prima della chiusura forzata.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervallo di porte in cui i server OpenOffice sono in ascolto.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 8101 - 8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL del server di conversione dei documenti.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Di seguito sono riportati i diversi parametri di **proxyConfig** nodo. Configurazione dei parametri proxy.

Per ulteriori informazioni, consulta [Configurazione della connessione proxy](file-res-management.md).

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
   <td> abilitato<br /> </td> 
   <td> Utilizza un server proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> sostituire<br /> </td> 
   <td> Eccezioni: elenco di indirizzi per i quali i parametri proxy devono essere ignorati.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Server proxy univoco: utilizza la stessa configurazione per tutti i tipi di proxy.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Proxy HTTP / Proxy protetto {#http-proxy---secure-proxy-}

In **proxyConfig > Proxy HTTP / Proxy sicuro** , configura i seguenti parametri.

Per ulteriori informazioni, consulta [Configurazione della connessione proxy](file-res-management.md).

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
   <td> indirizzo<br /> </td> 
   <td> Indirizzo del server proxy<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> accesso<br /> </td> 
   <td> Accesso per la connessione al server proxy<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Password per la connessione al server proxy<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> porta<br /> </td> 
   <td> Porta del server proxy<br /> </td> 
   <td> Breve<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Di seguito sono riportati i diversi parametri di **threadPool** nodo.

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
   <td> Lungo<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Di seguito sono riportati i diversi parametri di **urlPermission** nodo. Elenco di URL a cui il codice JavaScript può accedere.

Elenco di domini ed espressioni regolari che specificano se un URL rilevato nel codice JavaScript può o meno essere utilizzato dal server Adobe Campaign.

Se l’URL non viene trovato, viene eseguita l’azione predefinita, in base alla modalità predefinita specificata.

Per ulteriori informazioni, consulta [Protezione delle connessioni in uscita](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> azione<br /> </td> 
   <td> Azione predefinita se l’URL non è incluso nell’elenco delle autorizzazioni (enumerazione). I valori possibili sono "ignore" (autorizza senza messaggio di avviso, che richiede la disabilitazione della protezione), "warn" (autorizza e invia un messaggio di avviso) e "deny" (vieta l’accesso all’URL).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> rifiuta<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Traccia di debug del meccanismo di selezione URL: invia messaggi aggiuntivi durante il processo di verifica URL.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

Questo nodo consente di aggiungere intestazioni specifiche nelle richieste eseguite durante il caricamento di un file da un server esterno. Content Delivery Networks (CND) può richiedere un&#39;intestazione specifica per considerare attendibile il richiedente. Queste intestazioni possono essere utilizzate per migliorare l’attendibilità sulle richieste di Campaign, in particolare durante il download di documenti personalizzati per ciascun destinatario nella fase di esecuzione della consegna. Un numero elevato di richieste di download di risorse può essere interpretato come un attacco DDos. dnsPattern consente di impostare nomi e valori di intestazione specifici per diverse CDN in base al nome di dominio.

```
  <!-- List of custom headers added to request. 
         -->
    <cusHeaders>

    <!-- Pattern of DNS name or domain 
         value :  dnsPattern: All or part of the URL's domain to verify, * is a wild card Default:  -->
      <dnsPattern value="">

    <!-- Header Name and Value 
           headerName :  Header Name 
           headerValue :  Header Value -->
        <headerDef headerName="" headerValue=""/>

      </dnsPattern>

    </cusHeaders> 
```

### url {#url}

Per ogni URL, aggiungi un **url** con i seguenti parametri:

Per ulteriori informazioni, consulta [Protezione delle connessioni in uscita](../../installation/using/configuring-campaign-server.md#url-permissions).

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
   <td> Nome di dominio, o dominio principale, interessato dall’URL: tutto o parte del dominio dell’URL da verificare, per accelerare la verifica. L’URL viene verificato rispetto all’espressione regolare solo se il relativo dominio contiene dsnSuffix.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Espressione regolare per perfezionare la convalida degli URL appartenenti a questo dominio: espressione regolare che l’URL deve verificare, qualora corrisponda a dnsSuffix.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Se un record soddisfa **dnsSuffix** ma non **urlRegEx**, viene esaminato il seguente verbale.

Ad esempio, per autorizzare l’accesso a tutti gli URL del dominio business.com, possiamo definire due record:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

e

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

Di seguito è riportata la configurazione predefinita:

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
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Di seguito sono riportati i diversi parametri di **xtkJobs** nodo. Configurazione dei processi del server.

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
   <td> Periodo di aggiornamento dello stato della memoria per l’elaborazione del server (in ms).<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archiviazione {#archiving}

Di seguito sono riportati i diversi parametri di **archiviazione** nodo. Configurazione delle operazioni di archiviazione eseguite in background.

Per ulteriori informazioni, consulta [Attivazione dell’archiviazione delle e-mail (on-premise)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

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
   <td> Lungo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Strategia di archiviazione dei messaggi inviati (enumerazione). I valori possibili sono "0" (nessuna archiviazione) e "1" (trasferimento dell’archiviazione dei messaggi inviati a un server SMTP).<br /> </td> 
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
   <td> Lungo<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Formato di compressione utilizzato durante l’archiviazione (enumerazione). I valori possibili sono "0" (nessuna compressione) e "1" (comprimi i messaggi inviati utilizzando il formato zip).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Ritardo prima dell’archiviazione automatica delle e-mail non elaborate: numero di giorni prima dell’archiviazione delle e-mail non elaborate.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Ritardo (in secondi) tra ciascun evento di aggiornamento.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Numero di giorni prima dell’eliminazione delle e-mail non elaborate.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Destinazione destinazione di archiviazione<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Attiva il supporto SMTPS: attiva la consegna di e-mail in modalità provvisoria (STARTTLS/SMTPS) quando supportata dal server remoto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Numero di connessioni al server SMTP di archiviazione.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Elenco separato da virgole di nomi DNS o indirizzi IP degli inoltri SMTP da utilizzare. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> Porta IP del server SMTP.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Di seguito sono riportati i diversi parametri di **inMail** nodo. Si tratta della configurazione del modulo di gestione e-mail in entrata.

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
   <td> Verifica il nome dell’istanza: se è true, il nome dell’istanza Adobe Campaign contenuta nelle intestazioni ID messaggio deve essere uguale all’istanza corrente. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Indirizzo di inoltro: indirizzo e-mail predefinito non elaborato da una regola. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Indirizzo per gli errori: indirizzo predefinito utilizzato per trasferire e-mail non valide (codifica MIME non valida). <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignora dimensione messaggio: viene utilizzato per ignorare la dimensione di un messaggio restituito dai server POP3. In questo caso, il modulo richiede un "." alla fine dei messaggi. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Periodo di lettura del messaggio: frequenza di polling della coda dei messaggi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Numero massimo di registri da aggiornare: definisce il numero massimo di messaggi di registro da mantenere in memoria prima di aggiornare il database.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Numero massimo di messaggi da leggere durante la sessione POP3.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Durata sessione: durata massima della sessione di elaborazione dei messaggi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> Periodo di polling POP3<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Dimensione coda dei messaggi letti<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Timeout di comunicazione con il server POP3. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Frequenza di ricarica del database degli account da sottoporre a polling.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

In **inMail > msgDump** , configura i seguenti parametri. Configurazione del dump dei messaggi elaborati.

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
   <td> Salva tutti i messaggi in entrata in formato testo. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Percorso dell’immagine del messaggio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interagire {#interactiond}

Di seguito sono riportati i diversi parametri di **interagire** nodo. Configurazione del daemon di scrittura per gli eventi di interazione in entrata.

Per ulteriori informazioni, consulta [Interazione - Buffer dati](../../installation/using/interaction-data-buffer.md).

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
   <td> Max numero di caratteri memorizzati nella memoria condivisa per i dati di chiamata.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntries<br /> </td> 
   <td> Max numero di eventi archiviati nella memoria condivisa.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Numero massimo di offerte idonee ordinate subito dopo le proposte, da archiviare per le statistiche.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Durata dell’aggregazione in secondi per le statistiche sul tempo di risposta. 0 significa che l’archiviazione delle statistiche è stata disattivata.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max numero di caratteri memorizzati nella memoria condivisa per l’identificazione dei singoli utenti.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Di seguito sono riportati i diversi parametri di **mta** nodo. Si tratta della configurazione degli agenti di consegna.

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
   <td> Percorso di salvataggio delle e-mail inviate: se non è vuoto, indica il percorso in cui verranno salvati tutti i file di origine delle e-mail inviate. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Directory di dump:iSe non è vuota, copiare gli inviluppi MIME dei messaggi di posta inviati in questa directory. Utilizzato per risolvere problemi. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Ritardo dei registri delle query DNS: tempo in millisecondi per visualizzare i registri.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Frequenza delle statistiche di errore: tempo che intercorre tra la generazione delle statistiche e l’archiviazione nel database. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Genera statistiche di errore e le memorizza nel database.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Visualizza il livello dei messaggi di registro. Livello di gravità dei registri scritti nel database. I messaggi di registro generati dall’MTA non sono sempre scritti nel database. Con questo parametro, puoi definire il livello in base al quale ritieni che un messaggio debba essere scritto nel database. Se si definisce il livello 2, vengono scritti anche i messaggi di livello 1 e 0, mentre se si definisce il livello 1, vengono scritti solo i messaggi di livello 1 e 0. I valori possibili sono: 0 (errori), 1 (avviso), 2 (informazioni)<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Dimensione massima della memoria (in MB) utilizzabile da un processo MTA. Al di sopra di questo limite, il processo viene riavviato in modo che la memoria utilizzata venga rilasciata al sistema.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Soglia di connessione da considerare. Le statistiche di errore non vengono generate per un determinato percorso se il numero totale di connessioni per il periodo specificato da errorPeriodSec è notevolmente inferiore alla soglia.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Soglia di errore da considerare: le statistiche di errore non vengono generate per un determinato percorso se il numero totale di errori per il periodo specificato da errorPeriodSec è notevolmente inferiore alla soglia.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Soglia del messaggio da considerare. Le statistiche di errore non vengono generate per un determinato percorso se il numero totale di messaggi inviati per il periodo specificato da errorPeriodSec è notevolmente inferiore alla soglia.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Inoltro notifica: HostName:Porta utilizzata per inoltrare le notifiche.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Ritardo prima dell’eliminazione delle e-mail archiviate: numero di giorni prima dell’eliminazione delle e-mail archiviate nella directory specificata in dataLogPath.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Ritenta messaggi persi: parti delle consegne saranno ritentate se il processo secondario è inattivo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Abilita il meccanismo di firma. Ciò migliora la sicurezza sul tracciamento dei collegamenti nelle e-mail.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Indirizzo del server delle statistiche di consegna, indicato come 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. Consulta 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coordinate del server delle statistiche</a>. 
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
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Se impostato su "true", l’istanza utilizza <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">MTA avanzato</a>.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Modalità di verifica: attiva la modalità di verifica (nessuna trasmissione fisica dei messaggi; utilizzata per la simulazione e i test).<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Directory di lavoro: posizione dei file temporanei utilizzati dall’MTA per comunicare con i relativi processi secondari.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Campo X-Mailer: valore del campo "X-Mailer" nell’intestazione della posta SMTP.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

In **cache** , configura i seguenti parametri. Configurazione della cache dei file locale.

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
   <td> Riciclato dopo: periodo, espresso in secondi, dopo il quale il file viene eliminato automaticamente dalla cache per recuperare spazio di archiviazione.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Dimensione massima della cache (Mb).<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Frequenza di eliminazione: numero di secondi che intercorrono tra le esecuzioni del meccanismo di eliminazione della cache.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relè {#relay}

In **mta > inoltro** , configura i seguenti parametri. Configurazione del server di posta per la consegna dei messaggi.

L’elenco viene gestito nello stesso modo di un elenco di MX restituito da una query DNS MX. Di solito viene utilizzato il primo MX purché sia disponibile, quindi viene utilizzato il successivo e così via.

Per ulteriori informazioni, consulta [Inoltro SMTP](../../installation/using/configuring-campaign-server.md#smtp-relay).

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
   <td> indirizzo<br /> </td> 
   <td> Elenco separato da virgole di nomi DNS o indirizzi IP degli inoltri SMTP da utilizzare. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> porta<br /> </td> 
   <td> Porta IP del server SMTP.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### principale {#master}

In **mta > master** , configura i seguenti parametri. Configurazione del server principale.

Per ulteriori informazioni, consulta questa [sezione](../../installation/using/configuring-campaign-server.md#mta-child-processes).

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
   <td> Frequenza di polling del database dei processi da consegnare. Questo valore indica la frequenza di polling del database in secondi. Per ottenere l’elenco dei processi in attesa di consegna, l’MTA esegue il polling del database su base regolare. In assenza di processi in attesa, il periodo di polling è definito da questo valore. In caso contrario, se un processo è stato trasferito a un server secondario, la durata del polling viene automaticamente ridotta a un secondo, in modo che un nuovo processo possa essere elaborato nuovamente il prima possibile, ovvero non appena un server secondario è nuovamente disponibile. Ciò non significa che la query sul database verrà eseguita ogni secondo finché non sarà nuovamente disponibile un server secondario. L'accesso a un database viene infatti eseguito solo quando almeno un server secondario diventa disponibile.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Periodo di attesa dopo un errore di connessione al database. Un errore di connessione al database è in genere causato dal server di database stesso. Il server può anche essere arrestato per scopi di manutenzione, ad esempio. Il parametro DataBaseRetryDelay definisce la durata tra due tentativi di connessione in caso di errore di connessione al database.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Periodo di validità per la cache delle chiavi private (DomainKeys). Le chiavi private utilizzate per firmare le e-mail che seguono i consigli DomainKeys (http://antispam.yahoo.com/domainkeys) sono memorizzate come opzioni nel database. Il parametro domainKeysReloadPeriodSec definisce il numero di secondi in cui l’MTA può mantenere queste chiavi in una cache. Dopo questo ritardo, tutte le chiavi devono essere ricaricate dal database.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Numero massimo di server secondari. Rappresenta il numero massimo di server in esecuzione. Si consiglia di limitare questo numero a un livello ottimale compatibile con le risorse di memoria del server. Questo può essere verificato durante una consegna. La memoria utilizzata non deve superare un terzo della memoria fisica disponibile, altrimenti verrà utilizzato lo swap. Consulta <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">Processi secondari MTA</a>.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Numero minimo di server secondari. L’MTA tenta di mantenere in esecuzione almeno questo numero di server. Se ne sono presenti meno, i nuovi server vengono riavviati ogni secondo fino al raggiungimento di questo valore.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Numero di server secondari all’avvio. Il numero di server secondari viene monitorato dinamicamente; all’avvio dell’MTA, vengono creati tutti i server secondari indicati da questo valore. Normalmente, i server secondari non possono essere avviati più velocemente di un server al secondo per risparmiare risorse host. Tuttavia, all’avvio dell’MTA, questa limitazione viene annullata in modo che i server secondari siano disponibili il prima possibile.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### secondario {#child}

In **mta > figlio** , configura i seguenti parametri. Configurazione dei server secondari.

Per ulteriori informazioni, consulta [Ottimizzazione dell’invio di e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

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
   <td> Argomenti facoltativi della riga di comando <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Timeout fino all’arresto dei server secondari inattivi. Se un server secondario ha un tempo di inattività maggiore di questo parametro, si disconnetterà automaticamente per liberare risorse host.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Tempo massimo di conservazione dei messaggi. Se un messaggio preparato non può essere inviato a causa di una limitazione o non è stato in grado di connettersi all’MTA di destinazione, il messaggio viene abbandonato e verrà elaborato al nuovo tentativo successivo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Numero massimo di richieste HTTP parallele alla FCM avviate da ciascun server secondario.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Numero massimo di messaggi per server secondario. Ogni elemento secondario MTA elabora questo numero di messaggi e muore. È importante specificare un numero tale che la perdita di memoria o di risorse nell’MTA sia innocua (in genere poche migliaia). Anche se non ci sono perdite di memoria note nel codice MTA, i motori JavaScript e XSL incorporati non sono completamente affidabili.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> Messaggi in sospeso: numero massimo di messaggi in memoria in attesa di essere recapitati. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Dimensione massima della memoria (in MB) utilizzabile da un processo secondario. Al di sopra di questo limite, il processo viene interrotto in modo che la memoria utilizzata venga rilasciata al sistema. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in secondi) dopo il quale viene abbandonata una connessione SOAP per un connettore di consegna.<br /> </td> 
   <td> Lungo<br /> </td> 
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
   <td> Numero massimo di tentativi consecutivi quando viene ripreso.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

In **mta > figlio > smtp** , configura i seguenti parametri. Questa è la configurazione delle sessioni SMTP.

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
   <td> Attiva la consegna di e-mail in modalità provvisoria (STARTTLS/SMTPS) se supportata dal server remoto.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Timeout della sessione di inattività. Questo parametro viene utilizzato solo se la sessione viene riutilizzata per trasmettere diversi messaggi a un determinato dominio. Quando l’MTA ha completato la trasmissione del messaggio, la sessione SMTP utilizzata non viene chiusa sistematicamente. Se un messaggio è pronto per essere inviato per lo stesso dominio, verrà riutilizzata la stessa sessione SMTP, e questo è il motivo per cui la sessione non viene chiusa automaticamente. Il parametro IdleSessionTimeout consente di definire il tempo durante il quale una sessione SMTP può rimanere attiva in attesa di un altro messaggio. Una volta trascorsa la durata, la sessione viene automaticamente chiusa.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Ritardo iniziale prima di ritentare la connessione. Questo ritardo viene raddoppiato ogni volta che la connessione non riesce.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Numero massimo di sessioni SMTP da parte del server secondario. Per inviare un messaggio, l’MTA inizializza una connessione SMTP con l’MTA del destinatario. Questo valore limita il numero massimo di sessioni SMTP simultanee e attive per un determinato server secondario. Se si moltiplica questo valore per maxSpareServers, si ottiene il numero massimo di messaggi che possono essere elaborati contemporaneamente da un determinato server secondario.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

In **mta > figlio > smtp > IPAfinity** , configura i seguenti parametri. Configurazione della gestione delle affinità con gli indirizzi IP per ottimizzare il traffico SMTP in uscita.

Per ulteriori informazioni, consulta [Elenco di indirizzi IP da utilizzare](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) e [Gestione del traffico SMTP in uscita con affinità](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

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
   <td> Nome di dominio: nome di dominio locale collegato all’indirizzo IP. Utilizzato quando si esegue un comando SMTP HELO.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> nome<br /> </td> 
   <td> Nome logico: nomi collegati all’affinità dagli utenti. I nomi sono separati da un punto e virgola;<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

In **mta > figlio > smtp > IP** , configura i seguenti parametri.

Per ulteriori informazioni, consulta [Elenco di indirizzi IP da utilizzare](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

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
   <td> indirizzo<br /> </td> 
   <td> Indirizzo fisico associato. Esempio: '192.168.0.1'<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> ID indirizzo pubblico associato. Utilizzato come chiave per il server delle statistiche. Deve essere numerico. Vedi questo <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">sezione</a>.<br /> </td> 
   <td> Lungo<br /> </td> 
  </tr> 
  <tr> 
   <td> peso<br /> </td> 
   <td> Specifica la frequenza di utilizzo per questo IP, rispetto ad altri IP (i pesi maggiori determinano frequenze più alte).<br /> </td> 
   <td> Lungo<br /> </td> 
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
   <td> Nome computer collegato all'indirizzo IP. Utilizzato quando si esegue un comando SMTP HELO.<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Di seguito sono riportati i diversi parametri di **nmac** nodo. Si tratta della configurazione di per le consegne di notifiche push.

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
   <td> Utilizza il proxy HTTP definito in shared/proxyHTTP. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relè {#relay-1}

Di seguito sono riportati i diversi parametri di **nmac > inoltro** nodo. Questo configura l’utilizzo di un inoltro per la consegna dei messaggi (connettore ios http2).

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
   <td> indirizzo<br /> </td> 
   <td> Indirizzo DNS o nome dell’inoltro da utilizzare. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> porta<br /> </td> 
   <td> Porta di inoltro<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Catena di certificati (file PEM). Utile quando si utilizza un server fittizio.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## pipeline {#pipelined}

Di seguito sono riportati i diversi parametri di **pipeline** nodo. Si tratta della configurazione del modulo di elaborazione degli eventi per i servizi pipeline.

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
   <td> Nome dell’applicazione generata nella connessione Developer quando viene salvata la chiave pubblica. <br /> </td> 
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
   <td> Chiave privata per ottenere i token (crittografata in AES con l’opzione XtkKey).<br /> </td> 
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
   <td> Disabilita autenticazione: connessione ai servizi pipeline senza autenticazione. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> findPipelineEndpoint<br /> </td> 
   <td> URL per individuare l’URL dei servizi di pipeline.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Periodo di salvataggio dello stato: frequenza con cui le informazioni interne del processo vengono salvate in un file. Inattivo se 0. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcedPipelineEndpoint<br /> </td> 
   <td> URL di ascolto: forza l’URL di ascolto dei servizi pipeline. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Porta del server di stato: porta del server HTTP che consente di eseguire una query sullo stato del processo. Inattivo se 0.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> Il puntatore verrà memorizzato nel database ogni volta che questo numero di messaggi viene elaborato.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Ritardo prima della memorizzazione del puntatore: il puntatore verrà memorizzato nel database almeno una volta durante questo periodo (utile in caso di bassa attività).<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Numero di thread per l’elaborazione degli eventi con un connettore JavaScript personalizzato.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Numero di thread per l’elaborazione degli eventi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Ritardo nell’elaborazione in caso di errore.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Abbandona dopo questo periodo: abbandona l’evento se l’elaborazione continua a non riuscire dopo questo periodo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## riparare {#repair}

Di seguito sono riportati i diversi parametri di **riparare** nodo. Configurazione del modulo di ripristino del database.

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
   <td> repairActionDelayMin<br /> </td> 
   <td> Modulo di riparazione delle azioni di consegna: ritardo (in minuti) dopo il quale le azioni di consegna possono essere elaborate dal modulo di riparazione. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Di seguito sono riportati i diversi parametri di **securityZone** nodo.

Per ulteriori informazioni, consulta [Definire le aree di protezione](../../installation/using/security-zones.md).

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
   <td> Autorizza la modalità di debug per le applicazioni web.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Autorizza l’utente a utilizzare l’applicazione senza una password.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Autorizza l’utilizzo di HTTP per l’accesso dell’operatore.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Autorizzare l'utilizzo di SQLDATA nelle espressioni.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Autorizza i token della sessione utente/password.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> etichetta<br /> </td> 
   <td> Etichetta<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> nome<br /> </td> 
   <td> Nome interno<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Non utilizzare il token di sicurezza.<br /> </td> 
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

Di seguito è riportata la configurazione predefinita:

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

Di seguito sono riportati i diversi parametri di **securityZone > subNetwork** nodo.

Per ulteriori informazioni, consulta [Definire le aree di protezione](../../installation/using/security-zones.md).

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
   <td> etichetta<br /> </td> 
   <td> Etichetta<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> maschera<br /> </td> 
   <td> Maschera o indirizzo<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nome<br /> </td> 
   <td> Nome interno<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Maschera o indirizzo del proxy (inverso) utilizzato da questa sottorete per accedere all’istanza. In questo caso, al posto del proxy verrà testata l’intestazione "X-Forwarded-For".<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Di seguito sono riportati i diversi parametri di **sms** nodo. Si tratta della configurazione del modulo di gestione SMS in entrata.

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
   <td> Numero massimo di file di lavoro giornalieri conservati dal connettore SMPP.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Dimensione massima in MB dei file di lavoro SMPP.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Ricorrenza dell’intervallo di continuità della sessione: max. periodo in secondi tra due fotogrammi per notificare che la sessione di ricezione è ancora abilitata.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Frequenza di ricerca: periodo di polling dell’account SMS.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Frequenza di ricarica dell’account: frequenza di ricarica del database degli account da sottoporre a polling.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Numero di secondi di ritardo per l’elaborazione SR: solo gli SR con una data di recupero precedente all’ora corrente meno la durata in secondi fornita da srReadDelay. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout di comunicazione con il gateway SMS.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Di seguito sono riportati i diversi parametri di **sms > netsize** nodo.

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
   <td> Lungo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Di seguito sono riportati i diversi parametri di **stat** nodo. Questa è la configurazione del modulo statistiche MTA.

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
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> porta<br /> </td> 
   <td> Porta di ascolto del server. Vedi questo <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">sezione</a>.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Di seguito sono riportati i diversi parametri di **syslogd** nodo. Questa è la configurazione del modulo Gestione registro.

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
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Dimensione massima in MB per un file di registro. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Numero massimo di file logins.log da mantenere. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## tracciamento {#tracking}

Di seguito sono riportati i diversi parametri di **tracciamento** nodo. Configurazione del server di tracciamento.

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
   <td> Disattiva gli URL non validi generati da build precedenti.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> ConsolidationPeriodSec<br /> </td> 
   <td> Periodo di consolidamento<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Deduplica aperture: rimuovi i registri di tracciamento aperti duplicati per limitare gli effetti delle anteprime dei messaggi nei lettori di posta come Outlook.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignora fino a X% degli errori: non aggiornare gli indicatori di tracciamento fino a quando il rapporto tra i giornali di registrazione non già considerati non raggiunge questo valore. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Aggiorna indicatori di errore: durata massima prima del ricalcolo degli indicatori di errore.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorsDuration<br /> </td> 
   <td> Calcola gli indicatori durante: durata dopo la data di validità di una consegna dopo la quale gli indicatori consolidati non vengono più calcolati.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Numero di registri richiesti dalla chiamata al server di tracciamento remoto.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> Chiave API per l’integrazione dell’endpoint del servizio Phishbowl. Questo protegge il reindirizzamento di URL non validi generati da build precedenti. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Endpoint per l’integrazione dell’endpoint di servizio Phishbowl. Questo protegge il reindirizzamento di URL non validi generati da build precedenti.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignora fino a X% del tracciamento: non aggiornare gli indicatori di tracciamento fino a quando la proporzione di giornali di registrazione non già presi in considerazione non raggiunge questo valore.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Aggiorna indicatori di tracciamento: durata massima prima del ricalcolo degli indicatori di tracciamento.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Dimensione della cache dell'identificatore del browser.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Di seguito sono riportati i diversi parametri di **trackinglogd** nodo. Configurazione del daemon di scrittura del registro di tracciamento.

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
   <td> ID JavaScript da eseguire all’avvio del processo <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Numero massimo di nuovi tentativi di scrittura: numero massimo di file che è possibile creare in caso di errore di scrittura nei file di registro.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Dimensione massima del registro: spazio massimo utilizzato dai registri sul disco (in MB). Non può essere inferiore a 100 MB. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Numero massimo di registri: numero massimo di registri archiviati nella memoria condivisa. Non può essere minore di 10000. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Numero di registri prima dell’eliminazione: numero di registri inseriti prima di avviare l’eliminazione dei file di registro. Non può essere inferiore a 50000.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Numero massimo di caratteri salvati nella memoria condivisa per parametri di tracciamento web aggiuntivi.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Di seguito sono riportati i diversi parametri di **web** nodo. Questa è la configurazione del modulo web.

Per ulteriori informazioni, consulta questa [sezione](configuring-campaign-server.md#default-port-for-tomcat).

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
   <td> Opzioni JVMO<br /> </td> 
   <td> Opzioni della JVM passata come stringa.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Numero massimo di thread.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Numero minimo di thread.<br /> </td> 
   <td> Lungo<br /> </td> 
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
   <td> Porta di controllo ascolto Tomcat: fare riferimento a <a href="configure-tomcat.md" target="_blank">Configurare Tomcat</a>.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Porta di ascolto HTTP Tomcat: fare riferimento a <a href="configure-tomcat.md" target="_blank">Configurare Tomcat</a>.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Dimensione della coda per le chiamate SubmitDelivery: numero massimo di chiamate SOAP SubmitDelivery che possono essere messe in coda.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Inoltro notifica: Nome host:Porta che abilita l'inoltro delle notifiche.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
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

Di seguito sono riportati i diversi parametri di **web > jsp** nodo. Si tratta della configurazione dei parametri utilizzati dalle JSP.

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
   <td> Cartella di download: percorso di download dei programmi di installazione per le console client.<br /> </td> 
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

Il **web > jsp > classpath** Il nodo contiene l&#39;elenco di tutti i percorsi di classe da utilizzare all&#39;avvio di JVM. Di seguito è riportata la configurazione predefinita:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
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

Di seguito sono riportati i diversi parametri di **web > jssp** nodo. Si tratta della configurazione dei parametri utilizzati dai JSSP.

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
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Abilita il garbage collector del contesto JavaScript dopo ogni query.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Numero massimo di pagine servite da un contesto JavaScript. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

Il **web > jsp > classpath** Il nodo contiene l&#39;elenco di tutti i percorsi di classe da utilizzare all&#39;avvio di JVM.

### relè {#relay-2}

Di seguito sono riportati i diversi parametri di **web > inoltro** nodo. Si tratta della configurazione dell’inoltro per le richieste HTTP tra due aree.

Per ulteriori informazioni, consulta questa [sezione](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> Avvia il modulo di inoltro HTTP nel server web in modalità di debug.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Caratteri non consentiti (dominio): elenco di caratteri non consentiti nella sezione "autorità" di un URI.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Caratteri non consentiti (percorso): elenco di caratteri non consentiti nella sezione "percorso" di un URI.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Valore dell’opzione del modulo "mod_dir": elenco di file da utilizzare durante una query su una cartella.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Avvia il modulo di inoltro HTTP.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Avvia il modulo di inoltro HTTP all’interno del server web. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo di attesa prima di eliminare l’URL vietato.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Aggiungi un **web > inoltro > url** nodo per ogni URL da inoltrare (l’ordine di inserimento definisce la priorità) con i seguenti parametri.

Per ulteriori informazioni, consulta [Sicurezza delle pagine dinamiche e inoltri](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) e [sezione](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> IP autorizzati: elenco separato da virgole degli indirizzi IP di origine autorizzati a utilizzare l’inoltro per questa maschera.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> rifiuta<br /> </td> 
   <td> Nega l’accesso a questi URL (restituisce un errore HTTP 403)<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> Alias DNS da inoltrare: elenco separato da virgole di maschere alias DNS da inoltrare (ad esempio: "*.adobe.com").<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> Accesso HTTP autorizzato indipendentemente dall’area di sicurezza (come webApps). <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Aggiungi host originale: utilizza l’intestazione HTTP "Host" della richiesta originale durante l’inoltro.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Aggiungi percorso URL iniziale: aggiungi il percorso completo degli URL da inoltrare all’URL della pagina di destinazione. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> stato<br /> </td> 
   <td> Stato di sincronizzazione di una risorsa pubblica (enumerazione). I valori possibili sono "normal" (esecuzione normale), "blacklist" (URL aggiunto al inserisco nell'elenco Bloccati in caso di errore 404) e "spare" (caricamento di file sul server di riserva, se esistente).<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> normale<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL della pagina di destinazione: fai riferimento a <a href="configure-tomcat.md" target="_blank">Configurare Tomcat</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tempo massimo di esecuzione (in secondi) della richiesta inoltrata.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Maschera degli URL da inoltrare (ad esempio: "/nl*", "*.jsp").<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Di seguito è riportata la configurazione predefinita:

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

Aggiungi un **web > relay > responseHeader** nodo per ogni intestazione HTTP da aggiungere alle risposte inoltrate all’inoltro.

Per ulteriori informazioni, consulta [Gestione delle intestazioni HTTP](../../installation/using/configuring-campaign-server.md#managing-http-headers).

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
   <td> nome<br /> </td> 
   <td> Nome intestazione<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
  <tr> 
   <td> valore<br /> </td> 
   <td> Valore intestazione <br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

Di seguito è riportata la configurazione predefinita:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### reindirizzamento {#redirection}

Di seguito sono riportati i diversi parametri di **web > reindirizzamento** nodo. Configurazione del modulo di reindirizzamento.

Per ulteriori informazioni, consulta questa [sezione](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

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
   <td> ID organizzazione: identificatore univoco dell’organizzazione all’interno di Adobe Experience Cloud, utilizzato in particolare per il servizio VisitorID e l’SSO IMS. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Valore che descrive il criterio utilizzato per i cookie permanenti (conformi al formato P3P Compact Policy). <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> "CAO DSP COR CUR DEVa TAIa OUR BUS IND UNI COM NAV"<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Elenco separato da virgole di domini da configurare per indicare esplicitamente al dominio di impostare i cookie. <br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Identificatore di database associato all’istanza di tracciamento.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Conteggio dei registri per chiamata: numero di registri restituiti per impostazione predefinita in seguito a una chiamata del metodo GetTrackingLogs.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Pagina per reindirizzamenti scaduti: URL della pagina web utilizzata per impostazione predefinita dal server di reindirizzamento quando il reindirizzamento per un’azione di consegna è scaduto.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Numero massimo di processi: numero massimo di azioni di consegna nella cache. Non può essere inferiore a 50. <br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> Se impostato su false, il valore di sourceIP nella risposta restituita da r/test è una stringa vuota. <br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Avvia il servizio di reindirizzamento.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Avvia il servizio di reindirizzamento in modalità modulo.<br /> </td> 
   <td> Booleano<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Tracciamento web: creazione di registri per le pagine visitate da utenti sconosciuti. <br /> </td> 
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

Di seguito sono riportati i diversi parametri di **web > reindirizzamento > spareServer** nodo.

Per ulteriori informazioni, consulta [Tracciamento ridondante](../../installation/using/configuring-campaign-server.md#redundant-tracking).

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
   <td> Preso in considerazione se: il server di tracciamento viene preso in considerazione se l’espressione restituisce true. <br /> </td> 
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

Di seguito sono riportati i diversi parametri di **web > spamCheck** nodo. Si tratta della configurazione dei parametri di valutazione del punteggio anti-spam per e-mail.

Per ulteriori informazioni, consulta [Configurazione di SpamAssassin](../../installation/using/configuring-spamassassin.md).

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
   <td> comando<br /> </td> 
   <td> Comando da eseguire per valutare il punteggio anti-spam di un’e-mail (ad esempio "perl spamcheck.pl").<br /> </td> 
   <td> Stringa<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Di seguito sono riportati i diversi parametri di **wfserver** nodo. Configurazione del processo del flusso di lavoro.

Per ulteriori informazioni, consulta [Flussi di lavoro e affinità ad alta disponibilità](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

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
   <td> Lungo<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID JavaScript da eseguire all’avvio del processo.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Avviso di consumo di memoria: avviso relativo alla quantità di RAM utilizzata (in MB) da un determinato processo.<br /> </td> 
   <td> Lungo<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Inoltro notifica: Nome host:Porta che abilita l'inoltro delle notifiche.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Ora del giorno in cui il processo viene riavviato automaticamente. Consulta <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Riavvio automatico del processo</a>.<br /> </td> 
   <td> Stringa<br /> </td> 
   <td> '06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Priorità all’inizio. I moduli a bassa priorità vengono prima avviati e poi arrestati. Il modulo syslogd deve quindi avere la priorità 0.<br /> </td> 
   <td> Breve<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
