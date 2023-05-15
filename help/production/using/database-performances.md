---
product: campaign
title: Prestazioni del database
description: Prestazioni del database
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# Prestazioni del database{#database-performances}



La maggior parte dei problemi di prestazioni sono collegati alla manutenzione del database. Di seguito sono riportati quattro lead principali per aiutarti a trovare la causa della prestazione lenta:

* Configurazione
* Installazione e configurazione della piattaforma Adobe Campaign
* Manutenzione del database
* Diagnosi in tempo reale

## Configurazione {#configuration}

Verifica che la configurazione iniziale della piattaforma Adobe Campaign sia ancora valida e, se necessario, valuta le esigenze del cliente in termini di recapito messaggi o dimensioni del database. Si consiglia inoltre di eseguire un controllo completo dell&#39;hardware (CPU, RAM, sistema IO).

>[!NOTE]
>
>Puoi fare riferimento a [Guida al dimensionamento dell&#39;hardware di Adobe Campaign](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html) per informazioni approfondite.

## Configurazione della piattaforma {#platform-configuration}

Una configurazione inappropriata può influire sulle prestazioni della piattaforma. È consigliabile controllare la configurazione di rete, le opzioni di recapito della piattaforma e la configurazione MTA nella sezione **serverConf.xml** file.

## Manutenzione del database {#database-maintenance}

**Attività di pulizia del database**

Assicurati che l&#39;attività di pulizia del database sia operativa. A questo scopo, visualizza i file di registro per vedere se contengono errori. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).

**Piani di manutenzione**

Assicurati che la manutenzione del database sia pianificata ed eseguita correttamente. A questo scopo, contatta l’amministratore del database per ulteriori informazioni:

* Il programma di manutenzione
* Piani di manutenzione eseguiti in precedenza
* Visualizzazione dei registri di script

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Se utilizzi una configurazione di mid-sourcing, è essenziale che i database vengano mantenuti regolarmente. Quando analizzi una consegna sulla piattaforma di marketing, l’istanza di marketing invia informazioni all’istanza di mid-sourcing. Se il processo viene rallentato, l’istanza di marketing viene interessata.

**Gestione delle tabelle di lavoro**

Verificare il numero e la dimensione delle tabelle di lavoro. Quando superano una determinata dimensione, le prestazioni del database ne risentono. Queste tabelle vengono create dai flussi di lavoro e dalle consegne. Rimangono nel database mentre i flussi di lavoro e le consegne sono attivi. Per limitare le dimensioni delle tabelle di lavoro, è possibile eseguire le operazioni seguenti:

* Interrompi o elimina consegne con i seguenti stati: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** oppure **[!UICONTROL Paused]**.
* Interrompi o elimina i flussi di lavoro in pausa a causa di un errore.
* Arresta tutti i flussi di lavoro utilizzati per i test che non contengono un **[!UICONTROL End]** attività e il cui status rimane pertanto **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Se l&#39;operazione richiede molto tempo e libera molto spazio, ciò significa che è necessaria una manutenzione approfondita (ricostruzione dell&#39;indice, ecc.). Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

**Monitoraggio dei processi Adobe Campaign**

A seconda delle impostazioni di installazione di Adobe Campaign, è possibile utilizzare due strumenti per il monitoraggio della piattaforma:

* La pagina di produzione dell&#39;istanza. Per ulteriori informazioni, consulta [Monitoraggio manuale](../../production/using/monitoring-processes.md#manual-monitoring).
* La *netreport* script. Per ulteriori informazioni, consulta [Monitoraggio automatico tramite script Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Specifiche {#specifics}

Potrebbe rendersi necessario eseguire una diagnosi in tempo reale per identificare la causa del problema. Per iniziare, controlla i file di log del processo e della piattaforma, quindi monitora l&#39;attività del database durante la ricreazione del problema. Presta particolare attenzione a quanto segue:

* Il piano di esecuzione della manutenzione
* Query SQL in esecuzione
* Se i processi esterni sono in esecuzione contemporaneamente (pulizia, importazioni, calcolo aggregato, ecc.).
