---
solution: Campaign Classic
product: campaign
title: File di log
description: File di log
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# File di log{#log-files}

I file di registro sono organizzati come segue:

![](assets/d_ncs_directory.png)

Ogni modulo **nlserver** genera un file di registro salvato nella seguente directory: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Il modulo **nlserver syslogd** salva i registri sul disco. Questo modulo è simile al daemon **syslog Unix**, ma è stato adattato per compatibilità tra Unix e Windows. Gli altri moduli  Adobe Campaign non salvano i loro registri sul disco; delegano questa attività al modulo **syslogd** inviandola pacchetti UDP.

Per impostazione predefinita, la piattaforma Adobe Campaign  dispone del modulo **syslogd** installato al suo interno, ma è possibile utilizzare un altro **demone** syslog. Questo modulo crea i file di registro nella directory di **registro** .

I registri dei moduli con più istanze sono memorizzati nella seguente directory: **`<installation directory>`/var/default/log/**. Lo stesso file di registro è condiviso da tutte le istanze (ad es. **web.log**).

I file di registro degli altri moduli sono memorizzati in una sottocartella denominata in base all’istanza. Ogni istanza ha i propri file di registro.

I file di registro con più istanze sono elencati nella tabella seguente:

| File | Descrizione |
|---|---|
| web.log | Registri del modulo Web (console client, rapporti, API SOAP, ecc.) |
| webmdl.log | Registri dal modulo di reindirizzamento |
| watchdog.log | Registri dal modulo di monitoraggio del processo Adobe Campaign  |
| trackinglogd.log | Tracciamento dei registri |

I file di registro delle istanze mono sono elencati nella tabella seguente:

| File | Descrizione |
|---|---|
| mta.log | registri del modulo MTA |
| mtachild.log | Registri di elaborazione della distribuzione dei messaggi |
| wfserver.log | Registri del modulo del server del flusso di lavoro |
| runwf.log | Registri di esecuzione dei flussi di lavoro |
| inMail.log | Registro del modulo di posta elettronica |
| logins.log | Registra tutti i tentativi di accesso per  Adobe Campaign (successo o meno) |

>[!IMPORTANT]
>
>La directory **di reindirizzamento** esiste solo sui server di reindirizzamento. La sottodirectory **url** contiene le corrispondenze degli URL da reindirizzare e il **registro** della sottodirectory contiene i registri di tracciamento. Per generare i registri di tracciamento, il modulo **trackinglogd** deve essere in esecuzione.

Per ottimizzare le prestazioni e l’archiviazione, il file logins.log viene suddiviso in più file, uno ogni giorno (logins.yy-mm-dd.log) con un massimo di 365 file conservati. Il numero di giorni può essere modificato in serverConf.xml, in syslogd (opzione **maxNumberOfLoginsFiles** ). Consultate la documentazione nel file [di configurazione del](../../installation/using/the-server-configuration-file.md#syslogd)server.

Per impostazione predefinita, i file di registro sono limitati a due file da 10 MB per modulo e per istanza. Viene chiamato il secondo file: **`<modulename>`_2.log**. La dimensione dei registri è quindi limitata a 2*10 MB per modulo e per istanza.

Tuttavia, potete conservare file di dimensioni maggiori. Per attivare questo parametro, modificate il valore dell&#39;impostazione **maxFileSizeMb=&quot;10&quot;** nel nodo **syslogd** del file **conf/serverConf.xml** . Questo valore rappresenta la dimensione massima in MB di un file di registro.

Se desiderate mantenere ulteriori livelli di dettaglio nei registri, potete avviare i moduli Adobe Campaign  con il parametro **-verbose** :

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
