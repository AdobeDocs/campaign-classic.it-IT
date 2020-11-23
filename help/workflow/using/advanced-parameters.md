---
solution: Campaign Classic
product: campaign
title: Parametri avanzati
description: Parametri avanzati
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---


# Parametri avanzati{#advanced-parameters}

La schermata delle proprietà di un&#39;attività dispone di una **[!UICONTROL Advanced]** scheda che consente di definire un comportamento in caso di errori, il periodo di esecuzione dell&#39;attività; e consente di inserire uno script di inizializzazione. Sono disponibili due versioni di questa scheda:

* una versione semplificata (ad esempio per **[!UICONTROL Start]** e **[!UICONTROL End]** per le attività)

   ![](assets/wf-advanced-basic.png)

* una versione più dettagliata (ad esempio per l&#39; **[!UICONTROL Query]** attività)

   ![](assets/wf-advanced-full.png)

I campi da inserire nella **[!UICONTROL Advanced]** scheda sono descritti in dettaglio nelle sezioni seguenti.

## Nome {#name}

Questo campo contiene il nome interno dell&#39;attività.

## Immagine {#image}

Questo campo consente di modificare l&#39;immagine collegata a un&#39;attività. Per ulteriori informazioni, consulta: [Gestione delle immagini](../../workflow/using/managing-activity-images.md)dell&#39;attività.

## Esecuzione {#execution}

Questo campo consente di definire l&#39;azione da eseguire quando l&#39;attività viene attivata. Sono possibili tre opzioni:

Queste opzioni sono generalmente selezionate nel carrello facendo clic con il pulsante destro del mouse sull&#39;attività.

* **[!UICONTROL Normal]**: l&#39;attività viene eseguita normalmente.
* **[!UICONTROL Do not activate]**: questa attività e tutte le attività seguenti (nello stesso ramo) non vengono eseguite.
* **[!UICONTROL Activate but do not execute]**: questa attività e tutte le attività seguenti (nello stesso ramo) vengono automaticamente interrotte. Questa funzione può essere utile se si desidera essere presenti all’avvio dell’attività. Per eseguire l&#39;attività manualmente, fare clic con il pulsante destro del mouse sull&#39;attività e selezionare **[!UICONTROL Normal execution]**.

## Affinità {#affinity}

Questo campo consente di forzare l&#39;esecuzione di un&#39;attività su un computer specifico. For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## Max periodo di esecuzione {#max--execution-period}

Questo campo consente di impostare un avviso per il momento in cui l&#39;attività richiede troppo tempo. Non influirà sul flusso di lavoro. Se l’attività non è finita al termine del **[!UICONTROL Max. execution period]** test, nella **[!UICONTROL Instance monitoring]** pagina verrà visualizzato un avviso per il flusso di lavoro. Questa pagina è accessibile dalla **[!UICONTROL Monitoring]** scheda della home page.

## Comportamento {#behavior}

Questo campo consente di definire il comportamento da applicare per l&#39;utilizzo di attività asincrone. Sono disponibili due opzioni:

* **[!UICONTROL Several tasks authorized]**: è possibile eseguire diverse attività contemporaneamente, anche se la prima non è terminata.
* **[!UICONTROL The current task has priority]**: I compiti in corso hanno la priorità. Finché un&#39;attività è in corso, non verrà eseguita alcuna altra attività.

## Fuso orario {#time-zone}

Questo campo consente di selezionare il fuso orario dell&#39;attività. Per ulteriori informazioni: [Gestione dei fusi orari](../../workflow/using/managing-time-zones.md).

## In caso di errori {#in-case-of-errors}

Questo campo consente di definire l&#39;azione da eseguire quando l&#39;attività presenta errori. Sono disponibili due opzioni:

* **[!UICONTROL Stop the process]**: il flusso di lavoro viene arrestato automaticamente. Il suo stato cambia in **[!UICONTROL Failed]**. Una volta risolto il problema, riavviate il flusso di lavoro.
* **[!UICONTROL Ignore]**: questa attività e tutte le attività seguenti (nello stesso ramo) non vengono eseguite. Questa funzione può essere utile per le attività ricorrenti. Se il ramo dispone di un pianificatore posizionato a monte, verrà avviato come di consueto alla data di esecuzione successiva.

## Script di inizializzazione {#initialization-script}

Questo campo consente di inizializzare le variabili o di modificare le proprietà dell&#39;attività. Per ulteriori informazioni, consulta: [Script e modelli](../../workflow/using/javascript-scripts-and-templates.md)JavaScript.

## Commento {#comment}

Il **[!UICONTROL Comment]** campo è un campo gratuito che consente di aggiungere una descrizione.
