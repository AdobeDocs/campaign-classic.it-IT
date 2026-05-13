---
product: campaign
title: Principio di funzionamento
description: Principio di funzionamento
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
TQID: https://experienceleague.adobe.com/HCoIXlpEtxAHVh-rj51UD1GTNRnXh8Ir8x4t3QZT9YU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e656c701-3899-4db3-989c-de0980ddfffa
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 530
ht-degree: 7%

---

# Principio di funzionamento{#operating-principle}



Tecnicamente, la piattaforma Adobe Campaign si basa su diversi moduli.

Esistono molti moduli Adobe Campaign. Alcuni operano continuamente, mentre altri vengono avviati occasionalmente per eseguire attività amministrative (ad esempio per configurare la connessione al database) o per eseguire un&#39;attività ricorrente (ad esempio per consolidare le informazioni di tracciamento).

Esistono tre tipi di moduli Adobe Campaign:

* Moduli a più istanze: viene eseguito un unico processo per tutte le istanze. Questo vale per i seguenti moduli: **web**, **syslogd**, **trackinglogd** e **watchdog** (attività dal file **config-default.xml**).
* Moduli a istanza singola: viene eseguito un processo per istanza. Questo vale per i seguenti moduli: **mta**, **wfserver**, **inMail**, **sms** e **stat** (attività dal file **config-`<instance>`.xml**).
* Moduli di utilità: si tratta di moduli eseguiti occasionalmente per eseguire operazioni occasionali o ricorrenti (**cleanup**, **config**, download dei registri di tracciamento e così via).

L&#39;amministrazione del modulo viene eseguita utilizzando lo strumento della riga di comando **nlserver** installato nella directory **bin** della cartella di installazione.

Sintassi generale dello strumento **nlserver**:

**nlserver `<command>` `<command arguments>`**

Per visualizzare l&#39;elenco dei moduli disponibili, utilizzare il comando **nlserver**.

I moduli disponibili sono descritti nella tabella seguente:

| Comando | Descrizione |
|---|---|
| aliasCleansing | Standardizzazione dei valori di enumerazione |
| fatturazione | Invio del report attività di sistema a billing@neolane.net |
| cleanup | Pulizia del database: elimina i dati obsoleti dal database ed esegue un aggiornamento delle statistiche utilizzate dall&#39;optimizer del motore di database. |
| config | Modifica della configurazione server |
| esporta | Esportazione nella riga di comando: consente di inviare alla riga di comando un modello di esportazione creato nella console client di Adobe Campaign |
| fileconvert | Conversione di un file di dimensioni impostate |
| importa | Importazione nella riga di comando: consente di inviare alla riga di comando un modello di importazione creato nella console client di Adobe Campaign. |
| inMail | Mail Analyzer in entrata |
| installsetup | Disponibilità del file di installazione del cliente |
| javascript | Esecuzione di script JavaScript, con accesso alle API SOAP. |
| processo | Elaborazione riga di comando |
| unione | Unione modulo |
| midSourcing | Ripristino delle informazioni di consegna in modalità mid-sourcing |
| monitor | XML Visualizzazione dello stato dei processi server e delle attività pianificate, per istanza. |
| mta | Messaggio di trasferimento agente principale |
| pacchetto | Importazione o esportazione di file di pacchetto di entità |
| pdump | Visualizzazione degli stati dei processi del server |
| prepareda | Preparazione di un’azione di consegna |
| riavvia | Riavvio parziale del server |
| runwf | Esecuzione di un’istanza di flusso di lavoro |
| arresto | Arresto completo del sistema |
| sms | Elaborazione delle notifiche SMS |
| sql | Esecuzione script SQL |
| inizio | Ulteriori avvii |
| stat | Mantiene le statistiche di connessione MTA |
| stop | Arresto parziale del sistema |
| submitda | Invio di un’azione di consegna |
| syslogd | Server di scrittura log and trace |
| tracciamento | Consolidamento e recupero dei registri di tracciamento |
| trackinglogd | Tracciamento della scrittura del registro e rimozione del server |
| watchdog | Istanza di avvio e monitoraggio |
| web | Server applicazioni (HTTP e SOAP) |
| wfserver | Server flusso di lavoro |

>[!IMPORTANT]
>
>Esiste un ultimo modulo: il modulo di tracciamento e inoltro collegato al server applicazioni che, per motivi di prestazioni, viene integrato tramite meccanismi nativi in un server web Apache o IIS tramite una libreria dinamica. Non esiste alcun comando di Adobe Campaign che consenta di avviare o amministrare questo modulo. È quindi necessario utilizzare i comandi del server Web stesso.

L&#39;utilizzo del modulo e la sintassi dei relativi parametri vengono visualizzati utilizzando il comando seguente: **nlserver `[module]` -?**

Esempio:

**nlserver config -?**

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
