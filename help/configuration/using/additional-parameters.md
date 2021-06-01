---
product: campaign
title: Parametri di web tracking aggiuntivi
description: Ulteriori informazioni sui parametri per il web tracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---

# Parametri aggiuntivi{#additional-parameters}

## Definizione dei parametri {#definition-of-parameters}

La piattaforma Adobe Campaign offre due parametri standard per il web tracking di tipo TRANSAZIONE:

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

Puoi visualizzare i valori di questi parametri configurando l’elenco dei registri di tracciamento (di una consegna o di un destinatario).

## Reindirizzamento della configurazione del server {#redirection-server-configuration}

Nella configurazione del server, puoi definire il numero massimo di caratteri da prendere in considerazione per i parametri di web tracking.

>[!IMPORTANT]
>
>L’aumento del numero massimo di caratteri da prendere in considerazione può influire sulle prestazioni di web tracking della piattaforma.

A questo scopo, modifica l&#39;attributo **webTrackingParamSize** dell&#39;elemento **`<trackinglogd>`** nel file **serverConf.xml** . Questo file viene salvato nella sottodirectory **conf** della directory di installazione di Adobe Campaign.

**Esempio**:

Il valore predefinito è 64 caratteri. Questo valore ti consente di tenere conto dei parametri standard **amount** e **article** (&quot;amount=xxxxxxxxxxxx&amp;article=xxxxxxxx&quot;).

Tenendo conto di entrambi i parametri (dimensione del nome + dimensione del valore) indicati nell&#39;esempio di schema dell&#39;estensione di cui sopra, puoi modificare la configurazione per prendere in considerazione 100 caratteri (&quot;amount=xxxxxxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Quando la configurazione è stata modificata, devi:

* Arrestare il server web che ospita il modulo di reindirizzamento (Apache, IIS, ecc.),
* Arresta il server Adobe Campaign: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,

   >[!NOTE]
   >
   >A partire da 20.1, si consiglia di utilizzare invece il seguente comando (per Linux): **sistema arrestare nlserver**

* In Linux, elimina i segmenti di memoria condivisa utilizzando il comando **ipcrm** ,
* Riavvia il server Adobe Campaign: **net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,

   >[!NOTE]
   >
   >A partire da 20.1, si consiglia di utilizzare invece il seguente comando (per Linux): **sistema avviare nlserver**

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
>Per Linux, se si aumentano le dimensioni dei parametri **webTrackingParamSize** o **maxSharedLogs**, potrebbe essere necessario aumentare le dimensioni della memoria condivisa (SHM).
