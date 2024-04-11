---
product: campaign
title: Linee guida per il monitoraggio
description: Scopri le linee guida e le best practice per monitorare l’istanza e i processi di Campaign
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 18%

---

# Linee guida per il monitoraggio {#monitoring-guidelines}



## Dashboard di monitoraggio delle istanze {#instance-monitoring-dashboard}

Il **[!UICONTROL Monitoring]** , accessibile dalla home page di Campaign Classic, è il punto di ingresso principale per facilitare il monitoraggio dell’istanza.

Fornisce un dashboard di ciò che accade nell’istanza: il suo stato (versione della build, pacchetti installati, ecc.), gli indicatori di sistema, i registri, i flussi di lavoro attualmente in esecuzione, lo stato delle ultime consegne inviate, ecc.

Informazioni dettagliate sono disponibili [qui](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoraggio dei processi di Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitorare l’istanza</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Monitorare i flussi di lavoro</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Monitorare le consegne</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorare il database</a></p></td></tr>
</table>

Sono disponibili altri modi per monitorare i diversi processi di Campaign. Offrono diversi modi per monitorare le istanze per garantire che il sistema sia integro e, infine, risolvere i problemi che possono verificarsi durante la configurazione dei flussi di lavoro, l’invio di consegne, ecc.

### Monitoraggio dell’istanza {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Strumenti di monitoraggio automatico**

Sono disponibili diversi metodi automatici. per aiutarti a monitorare l’istanza. Ad esempio, puoi impostare rapporti e-mail con anomalie rilevate, recuperare un elenco di indicatori in formato XML e così via. Per ulteriori informazioni, [fai clic qui](../../production/using/monitoring-processes.md#automatic-monitoring).

**Audit trail**

L’Audit trail consente di visualizzare la cronologia completa delle modifiche relative alle opzioni, ai flussi di lavoro e agli schemi all’interno dell’istanza. Per ulteriori informazioni, [fai clic qui](../../production/using/audit-trail.md).

**Pannello di controllo**

Il Pannello di controllo Campaign ti consente di gestire diverse impostazioni dell’istanza: gestire le autorizzazioni URL, controllare i dettagli dell’istanza come le versioni di build dei server, ecc. Consente inoltre di monitorare lo spazio disponibile sui server SFTP connessi all’istanza. Per ulteriori informazioni, [fai clic qui](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it).

>[!NOTE]
>
>Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
>
>La tua istanza deve essere ospitata su AWS e aggiornata con [build GA più recente](../../rn/using/rn-overview.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=it).

### Monitoraggio dei flussi di lavoro {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

Workflow HeatMap fornisce una rappresentazione visiva di tutti i flussi di lavoro in esecuzione sull’istanza. Consente di monitorare facilmente il carico sull’istanza e pianificare i flussi di lavoro di conseguenza. Per ulteriori informazioni, [fai clic qui](../../workflow/using/heatmap.md).

**Audit trail**

Audit trail consente di visualizzare tutte le modifiche apportate nei flussi di lavoro, nonché i relativi stati correnti. [Fai clic qui](../../production/using/audit-trail.md).

**Risoluzione dei problemi dei flussi di lavoro**

È possibile eseguire azioni specifiche quando si verificano problemi con l’esecuzione di un flusso di lavoro. [Fai clic qui](../../production/using/workflow-execution.md) per ulteriori informazioni

**Monitoraggio dello stato del flusso di lavoro**

Oltre alla mappa di calore, puoi creare un flusso di lavoro per monitorare lo stato di un set di flussi di lavoro e inviare messaggi ricorrenti ai supervisori. Per ulteriori informazioni, [fai clic qui](../../workflow/using/supervising-workflows.md).

**Linee guida generali**

Seguire le linee guida e le best practice durante l’utilizzo dei flussi di lavoro può contribuire a migliorare le prestazioni. Per ulteriori informazioni, consulta le sezioni seguenti:
* [Best practice per l’utilizzo dei flussi di lavoro](../../workflow/using/workflow-best-practices.md)
* [Monitoraggio dell’esecuzione dei flussi di lavoro](../../workflow/using/monitoring-workflow-execution.md)

### Monitoraggio delle consegne {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Rapporti SMTP**

I rapporti SMTP visualizzano le statistiche di consegna e gli errori SMTP per dominio. [Ulteriori informazioni](../../production/using/monitoring-processes.md)

**Best practice**

[Best practice per l’invio e la progettazione della consegna](../../delivery/using/delivery-best-practices.md) può aiutarti a migliorare le loro prestazioni.

**Risoluzione dei problemi di consegna**
Quando si verificano problemi con le consegne, è possibile eseguire azioni specifiche:
* [Problemi di recapito messaggi](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)
* [Problemi di prestazioni della consegna](../../delivery/using/delivery-performances.md)
* [Problemi relativi ai file temporanei](../../production/using/temporary-files.md) - *solo modelli di hosting locale*

### Monitoraggio del database {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Flusso di lavoro di pulizia del database**

Il flusso di lavoro di pulizia del database consente di eliminare i dati obsoleti dal database. Si consiglia di evitare la crescita esponenziale del database. Per ulteriori informazioni, [fai clic qui](../../production/using/database-cleanup-workflow.md).

**Risoluzione dei problemi di prestazioni del database**

È possibile eseguire azioni specifiche quando si verificano problemi con le prestazioni del database. Per ulteriori informazioni, [fai clic qui](../../production/using/database-performances.md).

**Manutenzione del database**

*solo modelli di hosting on-premise e ibridi*

È consigliabile eseguire regolarmente la manutenzione del database per evitare un consumo eccessivo di spazio su disco, con conseguente impatto sull&#39;accesso al database. Per ulteriori informazioni, [fai clic qui](../../production/using/recommendations.md).

**Backup e ripristino**

*solo modelli di hosting on-premise e ibridi*

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o di sistema) su una macchina. [Fai clic qui](../../production/using/backup.md) per ulteriori informazioni. La procedura di ripristino è descritta in [questa sezione](../../production/using/restoration.md).

## Principi tecnici Campaign Classic {#campaign-classic-technical-principles}

Le risorse tecniche sono disponibili nella documentazione di Campaign Classic. È consigliabile familiarizzare con questi argomenti prima di eseguire qualsiasi operazione tecnica sull’istanza.

**Modelli di hosting e funzionalità**

* [Modelli di hosting Campaign Classic](../../installation/using/hosting-models.md)
* [Funzionalità del modello di hosting](../../installation/using/capability-matrix.md)

**Configurazione del server**

*Solo modelli di hosting on-premise e ibridi*

* [Configurazioni server](../../installation/using/configuring-campaign-server.md)
* [Configurazione del file Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configurazione del server per il recapito messaggi](../../installation/using/email-deliverability.md)
* [Righe di comando per creare un&#39;istanza e dichiarare un database](../../installation/using/command-lines.md)

**Principi generali**

* [Architettura Campaign Classic](../../production/using/general-architecture.md)
* [Moduli Campaign Classic](../../production/using/operating-principle.md)
* [Opzioni Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Come impostare l&#39;avvio automatico dei moduli](../../production/using/administration.md)
* [Principio di configurazione di Campaign](../../production/using/configuration-principle.md)
* [Procedure per la risoluzione dei problemi](../../production/using/performance-and-throughput-issues.md)
