---
product: campaign
title: File di registro
description: File di registro
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 4%

---

# File di registro{#log-files}



I file di registro sono organizzati come segue:

![](assets/d_ncs_directory.png)

Ogni **nlserver** Il modulo genera un file di registro salvato nella seguente directory: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Il **nlserver syslogd** Il modulo salva i registri sul disco. Questo modulo è simile a Unix **daemon syslog**, ma è stato adattato per garantire la compatibilità tra Unix e Windows. Gli altri moduli Adobe Campaign non salvano i registri sul disco, ma delegano questa attività al **syslogd** inviando pacchetti UDP.

Per impostazione predefinita, la piattaforma Adobe Campaign presenta **syslogd** su di esso, ma è possibile utilizzarne un altro **daemon syslog**. Questo modulo crea i file di registro in **log** directory.

I registri dei moduli a più istanze sono memorizzati nella seguente directory: **`<installation directory>`/var/default/log/**. Lo stesso file di registro viene condiviso da tutte le istanze (ad es. **web.log**).

I registri degli altri moduli vengono memorizzati in una sottocartella denominata in base all’istanza. Ogni istanza dispone di propri file di registro.

I file di registro a più istanze sono elencati nella tabella seguente:

| File | Descrizione |
|---|---|
| web.log | Registri dei moduli web (console client, rapporti, API SOAP, ecc.) |
| webmdl.log | Registri dal modulo di reindirizzamento |
| watchdog.log | Registri dal modulo di monitoraggio dei processi di Adobe Campaign |
| trackinglogd.log | Registri di tracciamento |

I file di registro mono-istanza sono elencati nella tabella seguente:

| File | Descrizione |
|---|---|
| mta.log | registri del modulo mta |
| mtachild.log | Registri di elaborazione della consegna dei messaggi |
| wfserver.log | Registri del modulo server del flusso di lavoro |
| runwf.log | Registri di esecuzione del flusso di lavoro |
| inMail.log | Registro moduli e-mail non recapitate |
| logins.log | Registra tutti i tentativi di accesso ad Adobe Campaign (riusciti o meno) |

>[!IMPORTANT]
>
>Il **redir** la directory esiste solo nei server di reindirizzamento. Il **url** la sottodirectory contiene le corrispondenze degli URL da reindirizzare e la sottodirectory **log** contiene i registri di tracciamento. Per generare i registri di tracciamento, **trackinglogd** il modulo deve essere in esecuzione.

Per ottimizzare le prestazioni e l&#39;archiviazione, il file logins.log viene suddiviso in più file, uno ogni giorno (logins.yy-mm-dd.log) con un massimo di 365 file conservati. Il numero di giorni può essere modificato in serverConf.xml, in syslogd (**maxNumberOfLoginsFiles** opzionale). Consulta la documentazione su [file di configurazione del server](../../installation/using/the-server-configuration-file.md#syslogd).

Per impostazione predefinita, i registri sono limitati a due file da 10 MB per modulo e per istanza. Il secondo file si chiama: **`<modulename>`_2.log**. La dimensione dei tronchi è pertanto limitata a 2&#42;10 MB per modulo e per istanza.

È tuttavia possibile conservare file di dimensioni maggiori. Per abilitare questa impostazione, modifica il valore di **maxFileSizeMb=&quot;10&quot;** impostazione in **syslogd** nodo del **conf/serverConf.xml** file. Questo valore rappresenta la dimensione massima in MB di un file di registro.

Se desideri mantenere ulteriori livelli di dettaglio nei registri, puoi avviare i moduli Adobe Campaign con **-verboso** parametro:

**nlserver start `<MODULE>`@`<INSTANCE>` -verboso**
