---
product: campaign
title: Principio di funzionamento
description: Principio di funzionamento
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Principio di funzionamento{#operating-principle}



Tecnicamente, la piattaforma Adobe Campaign è basata su diversi moduli.

Ci sono molti moduli Adobe Campaign. Alcuni funzionano continuamente, mentre altri vengono avviati occasionalmente per eseguire attività amministrative (ad esempio per configurare la connessione al database) o per eseguire un&#39;attività ricorrente (ad esempio per consolidare le informazioni di tracciamento).

Esistono tre tipi di moduli Adobe Campaign:

* Moduli a più istanze: viene eseguito un singolo processo per tutte le istanze. Questo vale per i seguenti moduli: **web**, **syslogd**, **trackinglogd** e **cane da guardia** (dalle attività **config-default.xml** file).
* Moduli di istanza mono: viene eseguito un processo per istanza. Questo vale per i seguenti moduli: **mta**, **wfserver**, **inMail**, **sms** e **stat** (dalle attività **config-`<instance>`.xml** file).
* Moduli di utilità: si tratta di moduli che vengono eseguiti occasionalmente per eseguire operazioni occasionali o ricorrenti (**pulizia**, **config**, il download dei registri di tracciamento, ecc.).

L’amministrazione del modulo viene eseguita utilizzando lo strumento della riga di comando **nlserver** installati in **bidone** della cartella di installazione.

La sintassi generale del **nlserver** lo strumento è il seguente:

**nlserver `<command>``<command arguments>`**

Per l’elenco dei moduli disponibili, utilizza il **nlserver** comando.

I moduli disponibili sono descritti nella seguente tabella:

| Comando | Descrizione |
|---|---|
| aliasCleansing | Standardizzazione dei valori di enumerazione |
| fatturazione | Invio del rapporto sull’attività del sistema a billing@neolane.net |
| pulizia | Pulizia del database: elimina i dati obsoleti dal database ed esegue un aggiornamento delle statistiche utilizzate dall&#39;ottimizzatore del motore di database. |
| config | Modifica della configurazione del server |
| esportare | Esportazione nella riga di comando: consente di inviare alla riga di comando un modello di esportazione creato nella console client di Adobe Campaign |
| fileconvert | Conversione di un file di dimensioni impostate |
| importare | Importazione nella riga di comando: consente di inviare alla riga di comando un modello di importazione creato nella console client di Adobe Campaign. |
| inMail | Analizzatore di posta in entrata |
| installazione | Disponibilità del file di installazione del cliente |
| javascript | Esecuzione di script JavaScript con accesso alle API SOAP. |
| lavoro | Elaborazione della riga di comando |
| merge | Unione dei moduli |
| midSourcing | Recupero delle informazioni di consegna in modalità mid-sourcing |
| monitor | Visualizzazione XML dello stato dei processi server e delle attività pianificate, per istanza. |
| mta | Messaggio di trasferimento dell&#39;agente principale |
| pacchetto | Importazione o esportazione di file di pacchetto di entità |
| scampo | Visualizzazione degli stati del processo del server |
| prepara | Preparazione di un’azione di consegna |
| riavvio | Riavvio parziale del server |
| becco | Esecuzione di un’istanza di flusso di lavoro |
| arresto | Spegnimento del sistema completo |
| sms | Elaborazione delle notifiche SMS |
| sql | Esecuzione script SQL |
| start | Inizio aggiuntivi |
| stat | Mantiene le statistiche di connessione MTA |
| stop | Spegnimento parziale del sistema |
| sottomissione | Invio di un’azione di consegna |
| syslogd | Server di registrazione e traccia |
| tracciamento | Consolidamento e recupero dei registri di tracciamento |
| trackinglogd | Tracking del server di scrittura e pulizia del registro |
| cane da guardia | Avvio e monitoraggio dell&#39;istanza |
| web | Server applicazioni (HTTP e SOAP) |
| wfserver | Server flusso di lavoro |

>[!IMPORTANT]
>
>Esiste un ultimo modulo: il modulo di tracking e relay collegato al server applicativo che, per motivi di prestazioni, è integrato tramite meccanismi nativi in un server web Apache o IIS tramite una libreria dinamica. Nessun comando Adobe Campaign consente di avviare o amministrare questo modulo. È quindi necessario utilizzare i comandi del server Web stesso.

L’utilizzo del modulo e la sintassi dei relativi parametri vengono visualizzati utilizzando il seguente comando: **nlserver `[module]` -?**

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
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
