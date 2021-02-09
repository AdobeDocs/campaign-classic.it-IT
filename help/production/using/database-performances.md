---
solution: Campaign Classic
product: campaign
title: Prestazioni del database
description: Prestazioni del database
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---


# Prestazioni del database{#database-performances}

La maggior parte dei problemi di prestazioni sono collegati alla manutenzione del database. Di seguito sono riportati quattro principali lead per individuare la causa di prestazioni lente:

* Configurazione
* Installazione e configurazione della piattaforma Adobe Campaign 
* Manutenzione del database
* Diagnosi in tempo reale

## Configurazione {#configuration}

Verificare che la configurazione iniziale  piattaforma Adobe Campaign sia ancora valida e, se necessario, rivalutare le esigenze del cliente in termini di recapito o dimensioni del database. È inoltre consigliabile eseguire un controllo hardware completo (CPU, RAM, sistema IO).

>[!NOTE]
>
>Per ulteriori informazioni, fare riferimento a [ Guida alle dimensioni di Adobe Campaign Harware](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

## Configurazione della piattaforma {#platform-configuration}

Una configurazione non appropriata potrebbe influire sulle prestazioni della piattaforma. È consigliabile controllare la configurazione di rete, le opzioni di recapito della piattaforma e la configurazione MTA nel file **serverConf.xml**.

## Manutenzione del database {#database-maintenance}

**Attività di pulizia del database**

Verificare che l&#39;attività di pulizia del database sia operativa. A questo scopo, visualizzate i file di registro per verificare se contengono errori. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).

**Piani di manutenzione**

Assicuratevi che la manutenzione del database sia pianificata ed eseguita correttamente. A questo scopo, contattate l&#39;amministratore del database per ulteriori informazioni:

* Il programma di manutenzione
* Piani di manutenzione precedentemente eseguiti
* Visualizzazione dei registri di script

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Se si utilizza una configurazione mid-sourcing, è essenziale che i database vengano mantenuti regolarmente. Quando si analizza una consegna sulla piattaforma di marketing, l&#39;istanza di marketing invia informazioni all&#39;istanza mid-sourcing. Se il processo è rallentato, l&#39;istanza di marketing verrà influenzata.

**Gestione delle tabelle di lavoro**

Verificare il numero e la dimensione delle tabelle di lavoro. Quando superano una certa dimensione, vengono compromesse le prestazioni del database. Queste tabelle vengono create da flussi di lavoro e consegne. Rimangono nel database mentre i flussi di lavoro e le consegne sono attive. Per limitare la dimensione delle tabelle di lavoro, è possibile eseguire le operazioni seguenti:

* Interrompi o elimina le consegne con i seguenti stati: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** o **[!UICONTROL Paused]**.
* Interrompi o elimina flussi di lavoro in pausa a causa di un errore.
* Arrestate tutti i flussi di lavoro utilizzati per i test che non contengono un&#39;attività **[!UICONTROL End]** e il cui stato rimane quindi **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Se l&#39;operazione richiede molto tempo e libera molto spazio, ciò significa che è necessaria una manutenzione approfondita (ricostruzione dell&#39;indice, ecc.). Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

**del processo Adobe Campaign**

A seconda  impostazioni di installazione di Adobe Campaign, è possibile utilizzare due strumenti per il monitoraggio della piattaforma:

* La pagina di produzione dell&#39;istanza. Per ulteriori informazioni, consultare [Monitoraggio manuale](../../production/using/monitoring-processes.md#manual-monitoring).
* Lo script *netreport*. Per ulteriori informazioni, vedere [Monitoraggio automatico tramite  script Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Specifiche {#specifics}

Potrebbe essere necessario eseguire una diagnosi in tempo reale per identificare la causa del problema. Per iniziare, controllate i file di registro di processo e piattaforma, quindi controllate l&#39;attività del database durante la ricreazione del problema. Prestare particolare attenzione ai seguenti elementi:

* Il piano di esecuzione della manutenzione
* Query SQL eseguite
* Se i processi esterni sono in esecuzione contemporaneamente (pulizia, importazioni, calcolo aggregato, ecc.).
