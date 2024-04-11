---
product: campaign
title: Prestazioni del database
description: Prestazioni del database
feature: Monitoring
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 6%

---

# Prestazioni del database{#database-performances}



La maggior parte dei problemi di prestazioni è collegata alla manutenzione del database. Di seguito sono riportati quattro lead principali per individuare la causa del rallentamento delle prestazioni:

* Configurazione
* Installazione e configurazione della piattaforma Adobe Campaign
* Manutenzione del database
* Diagnosi in tempo reale

## Configurazione {#configuration}

Verifica che la configurazione iniziale della piattaforma Adobe Campaign sia ancora valida e, se necessario, rivaluta le esigenze del cliente in termini di recapito messaggi o dimensioni del database. Si consiglia inoltre di eseguire un controllo hardware completo (CPU, RAM, sistema IO).

>[!NOTE]
>
>Puoi consultare [Guida al dimensionamento dell&#39;hardware Adobe Campaign](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html) per approfondimenti.

## Configurazione della piattaforma {#platform-configuration}

Una configurazione non appropriata può influire sulle prestazioni della piattaforma. È consigliabile controllare la configurazione di rete, le opzioni di recapito messaggi della piattaforma e la configurazione MTA in **serverConf.xml** file.

## Manutenzione del database {#database-maintenance}

**Attività di pulizia del database**

Verificare che l&#39;attività di pulizia del database sia operativa. A tale scopo, visualizzare i file di registro per verificare se contengono errori. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).

**Piani di manutenzione**

Verificare che la manutenzione del database sia pianificata ed eseguita correttamente. A tale scopo, contattare l&#39;amministratore del database per ulteriori informazioni su:

* Il loro programma di manutenzione
* Piani di manutenzione eseguiti in precedenza
* Visualizzazione dei registri degli script

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Se utilizzi una configurazione di mid-sourcing, è essenziale che i database siano gestiti regolarmente. Durante l’analisi di una consegna sulla piattaforma di marketing, l’istanza di marketing invia informazioni all’istanza di mid-sourcing. Se il processo è rallentato, l’istanza di marketing sarà interessata.

**Gestione delle tabelle di lavoro**

Controllare il numero e le dimensioni delle tabelle di lavoro. Se superano una determinata dimensione, le prestazioni del database ne risentono. Queste tabelle vengono create dai flussi di lavoro e dalle consegne. Rimangono nel database mentre i flussi di lavoro e le consegne sono attivi. Per limitare le dimensioni delle tabelle di lavoro, è possibile eseguire le operazioni seguenti:

* Interrompere o eliminare consegne con i seguenti stati: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]**, o **[!UICONTROL Paused]**.
* Arresta o elimina flussi di lavoro sospesi a causa di un errore.
* Arresta tutti i flussi di lavoro utilizzati per i test che non contengono un **[!UICONTROL End]** attività e il cui status rimane pertanto **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Se l’operazione richiede molto tempo e libera molto spazio, è necessaria una manutenzione approfondita (ricostruzione dell’indice, ecc.). Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

**Monitoraggio dei processi in Adobe Campaign**

A seconda delle impostazioni di installazione di Adobe Campaign, è possibile utilizzare due strumenti per il monitoraggio della piattaforma:

* La pagina di produzione dell’istanza. Per ulteriori informazioni, consulta [Monitoraggio manuale](../../production/using/monitoring-processes.md#manual-monitoring).
* Il *netreport* script. Per ulteriori informazioni, consulta [Monitoraggio automatico tramite script di Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Specifiche {#specifics}

Potrebbe essere necessario eseguire una diagnosi in tempo reale per identificare la causa del problema. Inizia controllando i file di registro del processo e della piattaforma, quindi monitora l’attività del database durante la ricreazione del problema. Presta particolare attenzione ai seguenti elementi:

* Il piano di esecuzione della manutenzione
* Query SQL in esecuzione
* Indica se i processi esterni vengono eseguiti contemporaneamente (pulizia, importazioni, calcolo dell&#39;aggregato, ecc.).
