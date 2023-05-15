---
product: campaign
title: Gestire i fusi orari
description: Gestire i fusi orari
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 4%

---

# Gestione dei fusi orari{#managing-time-zones}



Adobe Campaign consente di gestire i periodi di tempo tra diversi paesi interessati dalla stessa istanza. La configurazione applicata viene configurata durante la creazione dell&#39;istanza.

Per ulteriori informazioni sulla configurazione dei fusi orari in Adobe Campaign, consulta [Guida all’installazione di Campaign Classic v7](../../installation/using/time-zone-management.md).

In un flusso di lavoro, puoi adattare i piani di esecuzione dell’attività e collegare un fuso orario specifico a un’attività o all’intero flusso di lavoro. Questa configurazione può essere utile durante l’importazione del file o nel quadro della pianificazione della consegna.

## Pianificazione esecuzione {#execution-scheduling}

Puoi pianificare l’esecuzione delle attività utilizzando lo scheduler (consulta [Scheduler](scheduler.md)). Puoi inoltre utilizzare le opzioni di pianificazione disponibili nelle attività che offrono questa funzionalità. Queste attività offrono un **[!UICONTROL Schedule]** scheda: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, ecc.

Per tutte le attività pianificate, ovvero tutte le attività con opzioni di pianificazione, è possibile selezionare il fuso orario da applicare. Il fuso orario viene selezionato tramite la **[!UICONTROL Advanced]** scheda dell’attività interessata:

![](assets/wf-timezone-in-a-box.png)

I valori possibili sono:

* Fuso orario server

   Utilizza il fuso orario dell’application server di Adobe Campaign.

* Fuso orario utente

   Utilizza il fuso orario dell’operatore Adobe Campaign che esegue il flusso di lavoro.

* Fuso orario del database

   Utilizza il fuso orario del server di database utilizzato.

* Fusi orari specifici

   Utilizza il fuso orario selezionato.

Se la **[!UICONTROL By default]** viene selezionato , viene applicato il fuso orario del flusso di lavoro o, in caso contrario, quello dell&#39;application server.

## Collegamento di un fuso orario a un’attività {#linking-a-time-zone-to-an-activity}

La **[!UICONTROL Advanced]** la scheda delle attività del flusso di lavoro ti consente di selezionarne il fuso orario. Anche se la maggior parte del tempo, il fuso orario dei flussi di lavoro è sufficiente, può essere necessario sovraccaricarlo di tanto in tanto per un’attività specifica, come l’importazione di dati, al fine di collegare le date al loro fuso orario corretto.
