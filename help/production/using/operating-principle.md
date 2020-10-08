---
title: Principio di funzionamento
seo-title: Principio di funzionamento
description: Principio di funzionamento
seo-description: null
page-status-flag: never-activated
uuid: a15929ca-5b1f-499a-a883-43fd0a318c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 5e9c17ad-14d2-4173-9fc9-0e48a21426c8
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 1%

---


# Principio di funzionamento{#operating-principle}

Tecnicamente, la piattaforma Adobe Campaign  è basata su diversi moduli.

Ci sono molti moduli  Adobe Campaign. Alcuni funzionano in modo continuo, mentre altri vengono avviati occasionalmente per eseguire attività amministrative (ad esempio per configurare la connessione al database) o per eseguire un&#39;attività ricorrente (ad esempio, per consolidare le informazioni di tracciamento).

Esistono tre tipi di moduli Adobe Campaign :

* Moduli a istanza multipla: viene eseguito un singolo processo per tutte le istanze. Questo vale per i seguenti moduli: **web**, **syslogd**, **trackinglogd** e **watchdog** (attività dal file **config-default.xml** ).
* Moduli a istanza mono: viene eseguito un processo per istanza. Questo vale per i seguenti moduli: **mta**, **wfserver**, **inMail**, **sms** e **stat** (attività del **`<instance>`** file config-.xml).
* Moduli di utilità: si tratta di moduli che vengono eseguiti occasionalmente per eseguire operazioni occasionali o ricorrenti (**pulizia**, **configurazione**, scaricamento dei registri di tracciamento, ecc.).

L&#39;amministrazione del modulo viene eseguita utilizzando il **server** della riga di comando installato nella directory **bin** della cartella di installazione.

La sintassi generale dello strumento **nlserver** è la seguente:

**nlserver`<command>``<command arguments>`**

Per l&#39;elenco dei moduli disponibili, utilizzare il comando **nlserver** .

I moduli disponibili sono descritti nella tabella seguente:

| Comando | Descrizione |
|---|---|
| aliasCleansing | Standardizzazione dei valori di enumerazione |
| fatturazione | Invio del rapporto sulle attività del sistema a billing@neolane.net |
| pulizia | Pulizia del database: elimina i dati obsoleti dal database ed esegue un aggiornamento delle statistiche utilizzate dall&#39;ottimizzatore del motore del database. |
| config | Modifica della configurazione del server |
| copybase | Copia di un database |
| export | Esportazione alla riga di comando: consente di inviare alla riga di comando un modello di esportazione creato nella console client Adobe Campaign  |
| fileconvert | Conversione di un file di dimensioni impostate |
| import | Importazione alla riga di comando: consente di inviare alla riga di comando un modello di importazione creato nella console client Adobe Campaign . |
| inMail | Analizzatore di posta in entrata |
| installsetup | Disponibilità del file di installazione del cliente |
| javascript | Esecuzione di script JavaScript, con accesso alle API SOAP. |
| job | Elaborazione della riga di comando |
| merge | Unione dei moduli |
| midSourcing | Recupero delle informazioni di consegna in modalità mid-sourcing |
| monitor | XML Visualizzazione dello stato dei processi server e delle attività pianificate, per istanza. |
| mta | Messaggio di trasferimento agente principale |
| package | Importazione o esportazione di file di pacchetto di entità |
| pdump | Visualizzazione degli stati del processo del server |
| prepara | Preparazione di un&#39;azione di consegna |
| riavvio | Riavvio parziale del server |
| runwf | Esecuzione di un&#39;istanza di workflow |
| arresto | Interruzione del sistema |
| sms | Elaborazione delle notifiche SMS |
| sql | Esecuzione script SQL |
| start | Ulteriori avvii |
| stat | Mantiene le statistiche di connessione MTA |
| stop | Chiusura parziale del sistema |
| sottomissione | Invio di un&#39;azione di consegna |
| syslogd | Server di registrazione e traccia per la scrittura |
| tracking | Consolidamento e recupero dei registri di tracciamento |
| trackinglogd | Tracciamento del registro di scrittura e rimozione del server |
| cane da guardia | Avvio e monitoraggio dell’istanza |
| web | Server applicazione (HTTP e SOAP) |
| wfserver | Server flussi di lavoro |

>[!CAUTION]
>
>Esiste un ultimo modulo: il modulo di tracciamento e relay collegato al server applicazione che, per motivi di prestazioni, è integrato tramite meccanismi nativi in un server Web Apache o IIS tramite una libreria dinamica. Nessun comando Adobe Campaign  consente di avviare o amministrare il modulo. È pertanto necessario utilizzare i comandi del server Web stesso.

L&#39;utilizzo del modulo e la sintassi dei relativi parametri vengono visualizzati utilizzando il seguente comando: **nlserver`[module]`-?**

Esempio:

**configurazione nlserver -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```

