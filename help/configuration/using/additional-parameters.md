---
product: campaign
title: Parametri di tracciamento web aggiuntivi
description: Ulteriori informazioni sui parametri per il tracciamento web
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Parametri di tracciamento web aggiuntivi{#additional-parameters}

## Definizione dei parametri {#definition-of-parameters}

La piattaforma Adobe Campaign offre due parametri di tracciamento web di tipo TRANSACTION come standard:

* **quantità**: rappresenta l’importo di una transazione,
* **articolo**: rappresenta il numero di elementi in una transazione.

Questi parametri sono definiti nella **nms:webTrackingLog** e sono alcuni degli indicatori visualizzati nel reporting.

Per definire parametri aggiuntivi, devi estendere questo schema.

**Esempio**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

Puoi visualizzare i valori di questi parametri configurando l’elenco dei registri di tracciamento (di una consegna o di un destinatario).

## Configurazione server di reindirizzamento {#redirection-server-configuration}

Nella configurazione del server, puoi definire il numero massimo di caratteri da considerare per i parametri di tracciamento web.

>[!IMPORTANT]
>
>L’aumento del numero massimo di caratteri da considerare può influire sulle prestazioni di tracciamento web della piattaforma.

A questo scopo, modifica il **webTrackingParamSize** attributo del **`<trackinglogd>`** elemento nel **serverConf.xml** file. Questo file viene salvato in **conf** sottodirectory della directory di installazione di Adobe Campaign.

**Esempio**:

Il valore predefinito è 64 caratteri. Questo valore ti consente di prendere in considerazione **quantità** e **articolo** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;) parametri standard.

Tenendo conto di entrambi i parametri (dimensione del nome + dimensione del valore) indicati nell’esempio di schema di estensione precedente, puoi modificare la configurazione in modo da tenere conto di 100 caratteri (&quot;amount=xxxxxxxx&amp;article=xxxxxx&amp;mode=xxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Dopo aver modificato la configurazione, è necessario:

* Arrestare il server Web che ospita il modulo di reindirizzamento (Apache, IIS, ecc.),
* Arresta il server Adobe Campaign: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,

  >[!NOTE]
  >
  >A partire dalla versione 20.1, si consiglia invece di utilizzare il seguente comando (per Linux): **systemctl stop nlserver**

* In Linux, eliminare i segmenti di memoria condivisa utilizzando **ipcrm** comando,
* Riavvia il server Adobe Campaign: **net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,

  >[!NOTE]
  >
  >A partire dalla versione 20.1, si consiglia invece di utilizzare il seguente comando (per Linux): **systemctl start nlserver**

* Riavvia il server web.

**Esempio**: tenendo conto della configurazione in Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Per Linux, se si aumentano le dimensioni del **webTrackingParamSize** o **maxSharedLogs** , potrebbe essere necessario aumentare le dimensioni della memoria condivisa (SHM).
