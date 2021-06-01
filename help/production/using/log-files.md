---
product: campaign
title: File di registro
description: File di registro
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# File di registro{#log-files}

I file di registro sono organizzati come segue:

![](assets/d_ncs_directory.png)

Ogni modulo **nlserver** genera un file di registro salvato nella seguente directory: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Il modulo **nlserver syslogd** salva i registri sul disco. Questo modulo è simile a Unix **syslog daemon**, ma è stato adattato per la compatibilità tra Unix e Windows. Gli altri moduli Adobe Campaign non salvano i loro registri sul disco; delegano questa attività al modulo **syslogd** inviandolo pacchetti UDP.

Per impostazione predefinita, la piattaforma Adobe Campaign dispone del modulo **syslogd** installato al suo interno, ma è possibile utilizzare un altro **daemon syslog**. Questo modulo crea i file di registro nella directory **log**.

I registri dei moduli con più istanze sono memorizzati nella seguente directory: **`<installation directory>`/var/default/log/**. Lo stesso file di registro è condiviso da tutte le istanze (ad es. **web.log**).

I registri degli altri moduli vengono memorizzati in una sottocartella denominata dopo l’istanza. Ogni istanza ha i propri file di registro.

I file di registro con più istanze sono elencati nella tabella seguente:

| File | Descrizione |
|---|---|
| web.log | Registri dei moduli web (console client, rapporti, API SOAP, ecc.) |
| webmdl.log | Registri dal modulo di reindirizzamento |
| watchdog.log | Registri dal modulo di monitoraggio del processo Adobe Campaign |
| trackinglogd.log | Registri di tracciamento |

I file di registro mono-instance sono elencati nella seguente tabella:

| File | Descrizione |
|---|---|
| mta.log | Registri del modulo MTA |
| mtachild.log | Log di elaborazione della consegna dei messaggi |
| wfserver.log | Registri del modulo server del flusso di lavoro |
| runwf.log | Registri di esecuzione del flusso di lavoro |
| inMail.log | Registro del modulo di posta non recapitata |
| logins.log | Registra tutti i tentativi di accesso ad Adobe Campaign (con successo o meno) |

>[!IMPORTANT]
>
>La directory **redir** esiste solo sui server di reindirizzamento. La sottodirectory **url** contiene le corrispondenze degli URL da reindirizzare e la sottodirectory **log** contiene i registri di tracciamento. Per generare i registri di tracciamento, il modulo **trackinglogd** deve essere in esecuzione.

Per l&#39;ottimizzazione delle prestazioni e dello storage, il file logins.log viene suddiviso in più file, uno ogni giorno (logins.yy-mm-dd.log) con un massimo di 365 file conservati. Il numero di giorni può essere modificato nel serverConf.xml, sotto syslogd (**maxNumberOfLoginsFiles** opzione). Vedi la documentazione sul [file di configurazione del server](../../installation/using/the-server-configuration-file.md#syslogd).

Per impostazione predefinita, i registri sono limitati a due file da 10 MB per modulo e per istanza. Viene chiamato il secondo file: **`<modulename>`_2.log**. La dimensione dei log è quindi limitata a 2*10 MB per modulo e per istanza.

È tuttavia possibile conservare file di dimensioni maggiori. Per abilitare questa opzione, modifica il valore dell&#39;impostazione **maxFileSizeMb=&quot;10&quot;** nel nodo **syslogd** del file **conf/serverConf.xml**. Questo valore rappresenta la dimensione massima in MB di un file di registro.

Se desideri mantenere ulteriori livelli di dettaglio nei registri, puoi avviare i moduli Adobe Campaign con il parametro **-verbose** :

**nlserver start  `<MODULE>`@`<INSTANCE>` -verbose**
