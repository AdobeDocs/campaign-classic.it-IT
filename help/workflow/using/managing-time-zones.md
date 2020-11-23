---
solution: Campaign Classic
product: campaign
title: Gestione dei fusi orari
description: Gestione dei fusi orari
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 3%

---


# Gestione dei fusi orari{#managing-time-zones}

 Adobe Campaign consente di gestire i ritardi temporali tra i vari paesi interessati dalla stessa istanza. La configurazione applicata viene configurata durante la creazione dell&#39;istanza.

Per ulteriori informazioni sulla configurazione dei fusi orari in  Adobe Campaign, consulta questa [sezione](../../installation/using/time-zone-management.md).

In un flusso di lavoro, potete adattare i programmi di esecuzione dell&#39;attività e collegare un fuso orario specifico a un&#39;attività o all&#39;intero flusso di lavoro. Questa configurazione può essere utile quando si importa il file o nel quadro della programmazione della consegna.

## Pianificazione esecuzione {#execution-scheduling}

È possibile pianificare l&#39;esecuzione delle attività utilizzando il pianificatore (fare riferimento a [Scheduler](../../workflow/using/scheduler.md)). Potete inoltre utilizzare le opzioni di pianificazione disponibili nelle attività che offrono questa funzionalità. Queste attività offrono una **[!UICONTROL Schedule]** scheda: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, ecc.

Per tutte le attività pianificate, ovvero tutte le attività con opzioni di programmazione, è possibile selezionare il fuso orario da applicare. Il fuso orario viene selezionato tramite la **[!UICONTROL Advanced]** scheda dell&#39;attività interessata:

![](assets/wf-timezone-in-a-box.png)

I valori possibili sono:

* Fuso orario server

   Utilizza il fuso orario del server applicazione Adobe Campaign .

* Fuso orario utente

   Utilizza il fuso orario dell&#39;operatore Adobe Campaign  che esegue il flusso di lavoro.

* Fuso orario database

   Utilizza il fuso orario del server del database utilizzato.

* Fusi orari specifici

   Utilizza il fuso orario selezionato.

Se il **[!UICONTROL By default]** valore è selezionato, viene applicato il fuso orario del flusso di lavoro o, in caso contrario, quello del server dell&#39;applicazione.

## Collegamento di un fuso orario a un&#39;attività {#linking-a-time-zone-to-an-activity}

La **[!UICONTROL Advanced]** scheda delle attività del flusso di lavoro consente di selezionarne il fuso orario. Anche se la maggior parte del tempo, il fuso orario dei flussi di lavoro è sufficiente, può essere necessario sovraccaricarlo di tanto in tanto per un&#39;attività specifica, come l&#39;importazione di dati, al fine di collegare le date al loro fuso orario corretto.
