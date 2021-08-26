---
product: campaign
title: Prestazioni del database
description: Prestazioni del database
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# Prestazioni del database{#database-performances}

![](../../assets/v7-only.svg)

La maggior parte dei problemi di prestazioni sono collegati alla manutenzione del database. Di seguito sono riportati quattro lead principali per aiutarti a trovare la causa della prestazione lenta:

* Configurazione
* Installazione e configurazione della piattaforma Adobe Campaign
* Manutenzione del database
* Diagnosi in tempo reale

## Configurazione {#configuration}

Verifica che la configurazione iniziale della piattaforma Adobe Campaign sia ancora valida e, se necessario, valuta le esigenze del cliente in termini di recapito messaggi o dimensioni del database. Si consiglia inoltre di eseguire un controllo completo dell&#39;hardware (CPU, RAM, sistema IO).

>[!NOTE]
>
>Per ulteriori informazioni, consulta la [Guida al dimensionamento di Adobe Campaign Harware](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html) .

## Configurazione della piattaforma {#platform-configuration}

Una configurazione inappropriata può influire sulle prestazioni della piattaforma. Nel file **serverConf.xml** ti consigliamo di controllare la configurazione di rete, le opzioni di recapito della piattaforma e la configurazione MTA.

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

* Interrompi o elimina consegne con i seguenti stati: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** o **[!UICONTROL Paused]**.
* Interrompi o elimina i flussi di lavoro in pausa a causa di un errore.
* Interrompi tutti i flussi di lavoro utilizzati per i test che non contengono un’attività **[!UICONTROL End]** e il cui stato rimane quindi **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Se l&#39;operazione richiede molto tempo e libera molto spazio, ciò significa che è necessaria una manutenzione approfondita (ricostruzione dell&#39;indice, ecc.). Per ulteriori informazioni al riguardo, consulta [questa sezione](../../production/using/recommendations.md).

**Monitoraggio dei processi Adobe Campaign**

A seconda delle impostazioni di installazione di Adobe Campaign, è possibile utilizzare due strumenti per il monitoraggio della piattaforma:

* La pagina di produzione dell&#39;istanza. Per ulteriori informazioni, consulta [Monitoraggio manuale](../../production/using/monitoring-processes.md#manual-monitoring).
* Lo script *netreport*. Per ulteriori informazioni, consulta [Monitoraggio automatico tramite script Adobe Campaign](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Specifiche {#specifics}

Potrebbe rendersi necessario eseguire una diagnosi in tempo reale per identificare la causa del problema. Per iniziare, controlla i file di log del processo e della piattaforma, quindi monitora l&#39;attività del database durante la ricreazione del problema. Presta particolare attenzione a quanto segue:

* Il piano di esecuzione della manutenzione
* Query SQL in esecuzione
* Se i processi esterni sono in esecuzione contemporaneamente (pulizia, importazioni, calcolo aggregato, ecc.).
