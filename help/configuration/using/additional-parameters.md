---
title: Parametri aggiuntivi
seo-title: Parametri aggiuntivi
description: Parametri aggiuntivi
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Parametri aggiuntivi{#additional-parameters}

## Definizione dei parametri {#definition-of-parameters}

La piattaforma Adobe Campaign offre due parametri di monitoraggio Web di tipo TRANSACTION standard:

* **importo**: rappresenta l&#39;importo di una transazione,
* **articolo**: rappresenta il numero di elementi in una transazione.

Questi parametri sono definiti nello schema **nms:webTrackingLog** e sono alcuni degli indicatori visualizzati nel reporting.

Per definire parametri aggiuntivi, è necessario estendere questo schema.

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

Puoi visualizzare i valori di questi parametri configurando l&#39;elenco del registro di tracciamento (di una consegna o di un destinatario).

## Configurazione server di reindirizzamento {#redirection-server-configuration}

Nella configurazione del server, potete definire il numero massimo di caratteri da prendere in considerazione per i parametri di tracciamento Web.

>[!IMPORTANT]
>
>L&#39;aumento del numero massimo di caratteri da prendere in considerazione può influenzare le prestazioni di monitoraggio Web della piattaforma.

A tal fine, modificate l’attributo **webTrackingParamSize** dell’ **`<trackinglogd>`** elemento nel file **serverConf.xml** . Questo file viene salvato nella sottodirectory **conf** della directory di installazione di Adobe Campaign.

**Esempio**:

Il valore predefinito è 64 caratteri. Questo valore consente di tenere conto dei parametri standard **amount** and **article** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxxxx&quot;).

Tenendo conto di entrambi i parametri (dimensione del nome + dimensione del valore) indicati nell&#39;esempio dello schema di estensione sopra, potete modificare la configurazione in modo da prendere in considerazione 100 caratteri (&quot;amount=xxxxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Quando la configurazione è stata modificata, è necessario:

* Arrestate il server Web che ospita il modulo di reindirizzamento (Apache, IIS, ecc.),
* Arrestate il server Adobe Campaign: arresto **net nlserver6** in Windows, **/etc/init.d/nlserver6 arresto** in Linux,

   >[!NOTE]
   >
   >A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): server di arresto **del sistema**

* In Linux, eliminate i segmenti di memoria condivisa utilizzando il comando **ipcrm** ,
* Riavvia il server Adobe Campaign: avvio **rete nlserver6** in Windows, avvio **** /etc/init.d/nlserver6 in Linux,

   >[!NOTE]
   >
   >A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): server di avvio **del sistema**

* Riavviate il server Web.

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
>Per Linux, se si aumentano le dimensioni dei parametri **webTrackingParamSize** o **maxSharedLogs** , potrebbe essere necessario aumentare la dimensione della memoria condivisa (SHM).

