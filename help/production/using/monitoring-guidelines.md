---
solution: Campaign Classic
product: campaign
title: Linee guida per il monitoraggio
description: Scopri le linee guida e le best practice per monitorare l’istanza e i processi di Campaign.
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 7%

---


# Linee guida per il monitoraggio {#monitoring-guidelines}

## Dashboard di monitoraggio delle istanze {#instance-monitoring-dashboard}

La scheda **[!UICONTROL Monitoring]** , accessibile dalla home page di Campaign Classic, è il punto di ingresso principale per aiutarti a monitorare l’istanza.

Fornisce un dashboard di ciò che sta accadendo sull&#39;istanza: il suo stato (versione build, pacchetti installati, ecc.), gli indicatori di sistema, i registri, i flussi di lavoro attualmente in esecuzione, lo stato delle ultime consegne inviate, ecc.

Informazioni dettagliate sono disponibili [qui](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoraggio dei processi Campaign Classic {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Monitorare l’istanza</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Monitorare i flussi di lavoro</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Monitorare le consegne</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Monitorare il database</a></p></td></tr>
</table>

Sono disponibili ulteriori modi per monitorare i diversi processi di Campaign. Forniscono diversi modi per monitorare le istanze in modo che il sistema sia sano e infine risolvere i problemi che possono verificarsi durante la configurazione dei flussi di lavoro, l’invio di consegne, ecc.

### Monitoraggio dell’istanza {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Strumenti di monitoraggio automatici**

Sono disponibili diversi metodi automatici. per aiutarti a monitorare l’istanza. Ad esempio, puoi impostare rapporti e-mail con anomalie rilevate, recuperare un elenco di indicatori in formato XML, ecc. [Fai clic ](../../production/using/monitoring-processes.md#automatic-monitoring) qui per ulteriori informazioni.

**Audit trail**

La traccia di audit consente di visualizzare la cronologia completa delle modifiche relative a opzioni, flussi di lavoro e schemi all’interno dell’istanza. [Fai clic ](../../production/using/audit-trail.md) qui per ulteriori informazioni.

**Pannello di controllo Campaign**

Il Pannello di controllo Campaign consente di gestire diverse impostazioni dell’istanza: gestisci le autorizzazioni URL, controlla i dettagli dell’istanza come le versioni di build dei server, ecc. Consente inoltre di monitorare lo spazio disponibile sui server SFTP collegati all’istanza. [Fai clic ](https://docs.adobe.com/content/help/it-IT/control-panel/using/control-panel-home.html) qui per ulteriori informazioni.

>[!NOTE]
>
>Il Pannello di controllo Campaign è accessibile a tutti gli utenti amministratori. I passaggi per concedere all&#39;amministratore l&#39;accesso a un utente sono descritti in [questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
>
>Tieni presente che l’istanza deve essere ospitata su AWS e aggiornata con la build [Gold Standard](../../rn/using/gs-overview.md) più recente o con la build [GA più recente (21.1)](../../rn/using/latest-release.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Per verificare se l&#39;istanza è ospitata su AWS, segui i passaggi descritti in [questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

### Monitoraggio dei flussi di lavoro {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow HeatMap**

Il Workflow HeatMap ha fornito una rappresentazione visiva di tutti i flussi di lavoro in esecuzione sull’istanza. Consente di monitorare facilmente il carico sull&#39;istanza e pianificare i flussi di lavoro di conseguenza. [Fai clic ](../../workflow/using/heatmap.md) qui per ulteriori informazioni.

**Audit trail**

La traccia di audit consente di visualizzare tutte le modifiche apportate ai flussi di lavoro e i relativi stati correnti. [Fai clic qui](../../production/using/audit-trail.md).

**Risoluzione dei problemi dei flussi di lavoro**

È possibile eseguire azioni specifiche quando si verificano problemi con l’esecuzione di un flusso di lavoro. [Fai clic ](../../production/using/workflow-execution.md) qui per ulteriori informazioni

**Monitoraggio dello stato del flusso di lavoro**

Oltre alla mappa di calore, puoi creare un flusso di lavoro che ti consenta di monitorare lo stato di un set di flussi di lavoro e inviare messaggi ricorrenti alle autorità di vigilanza. [Fai clic ](../../workflow/using/supervising-workflows.md) qui per ulteriori informazioni.

**Linee guida generali**

Le linee guida e le best practice per l’utilizzo dei flussi di lavoro consentono di migliorare le prestazioni. Per ulteriori informazioni, consulta queste sezioni:
* [Best practice per l’utilizzo dei flussi di lavoro](../../workflow/using/workflow-best-practices.md)
* [Monitoraggio dell’esecuzione dei flussi di lavoro](../../workflow/using/monitoring-workflow-execution.md)

### Monitoraggio delle consegne {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**Rapporti SMTP**

I rapporti SMTP mostrano le statistiche di consegna e gli errori SMTP per dominio. [Ulteriori informazioni](../../production/using/monitoring-processes.md)

**Best practice**

[Le best practice per l’invio e la ](../../delivery/using/delivery-best-practices.md) progettazione delle consegne consentono di migliorare le prestazioni.

****
Risoluzione dei problemi di consegnaÈ possibile eseguire azioni specifiche quando si verificano problemi con le consegne:
* [Problemi di recapito messaggi](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)
* [Problemi di prestazioni di consegna](../../delivery/using/delivery-performances.md)
* [Problemi relativi ai file temporanei](../../production/using/temporary-files.md) : solo modelli di hosting  *on-premise*

### Monitoraggio del database {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Flusso di lavoro di pulizia del database**

Il flusso di lavoro di pulizia del database consente di eliminare i dati obsoleti dal database. Si consiglia di evitare la crescita esponenziale del database. [Fai clic ](../../production/using/database-cleanup-workflow.md) qui per ulteriori informazioni.

**Risoluzione dei problemi di prestazioni del database**

È possibile eseguire azioni specifiche quando si verificano problemi con le prestazioni del database. [Fai clic ](../../production/using/database-performances.md) qui per ulteriori informazioni.

**Manutenzione del database**

*solo modelli di hosting on-premise e ibridi*

Si consiglia di eseguire regolarmente la manutenzione del database per evitare un eccessivo consumo di spazio su disco, con conseguente impatto sull&#39;accesso al database. [Fai clic ](../../production/using/recommendations.md) qui per ulteriori informazioni.

**Backup e ripristino**

*solo modelli di hosting on-premise e ibridi*

Il backup è essenziale per evitare la perdita di dati in caso di problemi (fisici o relativi al sistema) su una macchina. [Fai clic ](../../production/using/backup.md) qui per ulteriori informazioni. La procedura di ripristino è descritta in [questa sezione](../../production/using/restoration.md).

## Principi tecnici Campaign Classic {#campaign-classic-technical-principles}

Le risorse tecniche sono disponibili nella documentazione di Campaign Classic. È consigliabile acquisire familiarità con questi argomenti prima di eseguire qualsiasi operazione tecnica sull’istanza.

**Modelli e funzionalità di hosting**

* [Modelli di hosting Campaign Classic](../../installation/using/hosting-models.md)
* [Funzionalità del modello di hosting](../../installation/using/capability-matrix.md)

**Configurazione del server**

*Solo modelli di hosting on-premise e ibridi*

* [Configurazioni server obbligatorie](../../installation/using/campaign-server-configuration.md)
* [Configurazione del file Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Configurazione del server per il recapito messaggi](../../installation/using/email-deliverability.md)
* [Righe di comando per creare un&#39;istanza e dichiarare un database](../../installation/using/command-lines.md)

**Principi generali**

* [Architettura di Campaign Classic](../../production/using/general-architecture.md)
* [Moduli Campaign Classic](../../production/using/operating-principle.md)
* [Opzioni di Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Come impostare l&#39;avvio automatico dei moduli](../../production/using/administration.md)
* [Principio di configurazione della campagna](../../production/using/configuration-principle.md)
* [Procedure di risoluzione dei problemi](../../production/using/performance-and-throughput-issues.md)
