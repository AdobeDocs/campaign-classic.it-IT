---
product: campaign
title: Parametri avanzati
description: Parametri avanzati
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 5%

---

# Parametri avanzati{#advanced-parameters}



La schermata delle proprietà di un’attività ha un **[!UICONTROL Advanced]** scheda che ti consente di definire un comportamento in caso di errori, il periodo di esecuzione dell’attività; e consente di inserire uno script di inizializzazione. Sono disponibili due versioni di questa scheda:

* una versione semplificata (per **[!UICONTROL Start]** e **[!UICONTROL End]** ad esempio)

   ![](assets/wf-advanced-basic.png)

* una versione più dettagliata (per **[!UICONTROL Query]** attività, per esempio)

   ![](assets/wf-advanced-full.png)

I campi da inserire nel **[!UICONTROL Advanced]** Sono descritte in dettaglio nelle sezioni seguenti.

## Nome {#name}

Questo campo contiene il nome interno dell’attività.

## Immagine {#image}

Questo campo ti consente di modificare l’immagine collegata a un’attività. Per ulteriori informazioni, consulta [Modificare le immagini delle attività](managing-activity-images.md).

## Execution {#execution}

Questo campo ti consente di definire l’azione da eseguire quando l’attività viene attivata. Sono disponibili tre opzioni possibili:

Queste opzioni sono generalmente selezionate nel carrello facendo clic con il pulsante destro del mouse sull’attività.

* **[!UICONTROL Normal]**: l’attività viene eseguita come di consueto.
* **[!UICONTROL Do not activate]**: questa attività e tutte le attività seguenti (nello stesso ramo) non vengono eseguite.
* **[!UICONTROL Activate but do not execute]**: questa attività e tutte le attività seguenti (nello stesso ramo) vengono automaticamente interrotte. Questa funzione può essere utile se desideri essere presente all’avvio dell’attività. Per eseguire manualmente l’attività, fai clic con il pulsante destro del mouse sull’attività e seleziona **[!UICONTROL Normal execution]**.

## Affinità {#affinity}

Puoi scegliere di forzare l’esecuzione di un flusso di lavoro o di un’attività del flusso di lavoro su un computer specifico. A questo scopo, devi definire una o più proprietà a livello del flusso di lavoro o dell’attività interessata.

La configurazione del flusso di lavoro ad alta disponibilità è descritta in questo [sezione](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).


## Max. periodo di esecuzione {#max--execution-period}

Questo campo consente di impostare un avviso per il momento in cui l’attività richiede troppo tempo. Non influisce sul funzionamento del flusso di lavoro. Se l&#39;attività non è completata entro l&#39;ora **[!UICONTROL Max. execution period]** è finita, **[!UICONTROL Instance monitoring]** In questa pagina viene visualizzato un avviso per questo flusso di lavoro. Questa pagina è accessibile tramite il **[!UICONTROL Monitoring]** della home page.

## Comportamento {#behavior}

Questo campo ti consente di definire il comportamento da applicare per l’utilizzo di attività asincrone. Sono disponibili due opzioni possibili:

* **[!UICONTROL Several tasks authorized]**: è possibile eseguire diverse attività contemporaneamente, anche se la prima non è terminata.
* **[!UICONTROL The current task has priority]**: I compiti in corso sono prioritari. Fino a quando un&#39;attività è in corso, nessun&#39;altra attività verrà eseguita.

## Fuso orario {#time-zone}

Questo campo ti consente di selezionare il fuso orario dell’attività. Per ulteriori informazioni: [Gestione dei fusi orari](managing-time-zones.md).

## In caso di errori {#in-case-of-errors}

Questo campo ti consente di definire l’azione da eseguire quando l’attività presenta errori. Sono disponibili due opzioni possibili:

* **[!UICONTROL Suspend the process]**: il flusso di lavoro viene arrestato automaticamente. Il suo stato cambia in **[!UICONTROL Failed]**. Una volta risolto il problema, riavvia il flusso di lavoro.
* **[!UICONTROL Ignore]**: questa attività e tutte le attività seguenti (nello stesso ramo) non vengono eseguite. Può essere utile per le attività ricorrenti. Se il ramo ha una pianificazione posizionata a monte, inizia come di consueto alla data di esecuzione successiva.
* **[!UICONTROL Abort on error]**: il flusso di lavoro viene arrestato automaticamente e non può essere riavviato. Il suo stato cambia in **[!UICONTROL Failed]**.

## Script di inizializzazione {#initialization-script}

Questo campo ti consente di inizializzare le variabili o modificare le proprietà dell’attività. Per ulteriori informazioni, consulta: [Script e modelli JavaScript](javascript-scripts-and-templates.md).

## Commento {#comment}

La **[!UICONTROL Comment]** è un campo libero che ti consente di aggiungere una descrizione.
