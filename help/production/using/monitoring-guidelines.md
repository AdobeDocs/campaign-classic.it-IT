---
title: Linee guida per il monitoraggio
description: Questa sezione presenta le linee guida generali per il monitoraggio di Campaign Classic.
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fdc305ff5bf27aa5cc0a4a9e89ac8ed9d5bead57
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 2%

---


# Linee guida per il monitoraggio {#monitoring-guidelines}

## Pannello di controllo per le istanze {#instance-monitoring-dashboard}

La **[!UICONTROL Monitoring]** scheda, accessibile dalla home page di Campaign Classic, è il punto di ingresso principale per facilitare il monitoraggio dell&#39;istanza.

Fornisce un dashboard di ciò che si verifica nell’istanza: stato (versione build, pacchetti installati, ecc.), indicatori di sistema, registri, flussi di lavoro attualmente in esecuzione, stato delle ultime consegne inviate, ecc.

Informazioni dettagliate sono disponibili [qui](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoraggio dei processi Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitorare l’istanza</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Monitorare i flussi di lavoro</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorare il database</a></p></td>
<td><img src="assets/do-not-localize/icon_Send.svg" width="60px"><p><a href="#monitoring-deliveries">Monitorare le consegne</a></p></td></tr>
</table>

Sono disponibili metodi aggiuntivi per monitorare i diversi processi di Campaign. Offrono diversi modi di monitorare le istanze per garantire la salute del sistema e, infine, per risolvere eventuali problemi che possono verificarsi durante la configurazione dei flussi di lavoro, l&#39;invio di consegne, ecc.

### Monitoraggio dell’istanza {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Strumenti di monitoraggio automatico**

Sono disponibili diversi metodi automatici. per monitorare l’istanza. Ad esempio, potete impostare rapporti e-mail con anomalie rilevate, recuperare un elenco di indicatori in formato XML, ecc. [Fai clic qui](../../production/using/monitoring-processes.md#automatic-monitoring) per ulteriori informazioni.

**Audit trail**

La traccia di controllo consente di visualizzare la cronologia completa delle modifiche relative a opzioni, flussi di lavoro e schemi all’interno dell’istanza. [Fai clic qui](../../production/using/audit-trail.md) per ulteriori informazioni.

**Pannello di controllo Campaign**

Il Pannello di controllo Campaign consente di gestire diverse impostazioni dell’istanza: gestire le autorizzazioni URL, controllare i dettagli dell&#39;istanza come le versioni di build dei server, ecc. Consente inoltre di monitorare lo spazio disponibile sui server SFTP collegati all’istanza. [Fai clic qui](https://docs.adobe.com/content/help/it-IT/control-panel/using/control-panel-home.html) per ulteriori informazioni.

>[!NOTE]
>
>Il Pannello di controllo Campaign è accessibile solo agli utenti Admin e disponibile per tutti i clienti che utilizzano  Adobi Managed Services.

### Flussi di lavoro di monitoraggio {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**HeatMap flusso di lavoro**

Workflow HeatMap ha fornito una rappresentazione visiva di tutti i flussi di lavoro in esecuzione sull’istanza. Consente di monitorare facilmente il carico sull&#39;istanza e pianificare i flussi di lavoro di conseguenza. [Fai clic qui](../../workflow/using/heatmap.md) per ulteriori informazioni.

**Audit trail**

La traccia di controllo consente di visualizzare tutte le modifiche apportate ai flussi di lavoro, nonché i relativi stati correnti. [Clicca qui](../../production/using/audit-trail.md).

**Risoluzione dei problemi dei flussi di lavoro**

È possibile eseguire azioni specifiche quando si verificano problemi con l&#39;esecuzione di un flusso di lavoro. [Fai clic qui](../../production/using/workflow-execution.md) per maggiori informazioni

**Monitoraggio dello stato del flusso di lavoro**

Oltre alla mappa di calore, puoi creare un flusso di lavoro che ti consenta di monitorare lo stato di un set di flussi di lavoro e inviare messaggi ricorrenti alle autorità di vigilanza. [Fai clic qui](../../workflow/using/supervising-workflows.md) per ulteriori informazioni.

**Linee guida generali**

Seguire le linee guida e le best practice per l&#39;utilizzo dei flussi di lavoro può migliorare le prestazioni. Per ulteriori informazioni, consultare le sezioni seguenti:
* [Best practice per l&#39;utilizzo dei flussi di lavoro](../../workflow/using/workflow-best-practices.md)
* [Esecuzione del flusso di lavoro di monitoraggio](../../workflow/using/monitoring-workflow-execution.md)

### Monitoraggio delle consegne {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Rapporti SMTP**

I rapporti SMTP mostrano le statistiche di consegna e gli errori SMTP per dominio. [Fai clic qui](../../production/using/monitoring-processes.md) per ulteriori informazioni.

**Best practice**

[Le procedure ottimali per l&#39;invio e la progettazione](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) delle consegne consentono di migliorare le prestazioni.

**Risoluzione dei problemi** di distribuzione È possibile eseguire azioni specifiche in caso di problemi relativi alle consegne:
* [Problemi di realizzazione](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemi di visualizzazione delle immagini](../../production/using/image-display-issues.md)
* [Problemi relativi alle prestazioni di distribuzione](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [Problemi relativi](../../production/using/temporary-files.md) ai file temporanei - solo modelli di hosting *in sede*

### Monitoraggio del database {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Flusso di lavoro di pulizia del database**

Il flusso di lavoro di pulizia del database consente di eliminare i dati obsoleti dal database. Si consiglia di evitare la crescita esponenziale del database. [Fai clic qui](../../production/using/database-cleanup-workflow.md) per ulteriori informazioni.

**Risoluzione delle prestazioni del database**

È possibile eseguire azioni specifiche quando si verificano problemi con le prestazioni del database. [Fai clic qui](../../production/using/database-performances.md) per ulteriori informazioni.

**Manutenzione del database**

*modelli di hosting interni e ibridi*

È consigliabile eseguire la manutenzione del database su base regolare per evitare un eccessivo consumo di spazio su disco, con conseguente impatto sull&#39;accesso al database. [Fai clic qui](../../production/using/recommendations.md) per ulteriori informazioni.

**Backup e ripristino**

*modelli di hosting interni e ibridi*

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o legati al sistema) su una macchina. [Fai clic qui](../../production/using/backup.md) per ulteriori informazioni. La procedura di restauro è descritta in [questa sezione](../../production/using/restoration.md).

## Principi tecnici Campaign Classic {#campaign-classic-technical-principles}

Le risorse tecniche sono disponibili nella documentazione Campaign Classic. È consigliabile acquisire familiarità con questi argomenti prima di eseguire qualsiasi operazione tecnica sull&#39;istanza.

**Modelli e funzionalità di hosting**

* [Modelli di hosting Campaign Classic](../../installation/using/hosting-models.md)
* [Funzionalità del modello di hosting](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

**Configurazione server**

*Solo modelli di hosting locali e ibridi*

* [Configurazioni server obbligatorie](../../installation/using/campaign-server-configuration.md)
* [Configurazione del file Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configurazione del server per la recapito](../../installation/using/email-deliverability.md)
* [Riga di comando per creare un&#39;istanza e dichiarare un database](../../installation/using/command-lines.md)

**Principi generali**

* [Architettura Campaign Classic](../../production/using/general-architecture.md)
* [Moduli Campaign Classic](../../production/using/operating-principle.md)
* [Opzioni Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Come impostare l&#39;avvio automatico dei moduli](../../production/using/administration.md)
* [Principio di configurazione della campagna](../../production/using/configuration-principle.md)
* [Procedure di risoluzione dei problemi](../../production/using/performance-and-throughput-issues.md)
