---
product: campaign
title: Parametri avanzati
description: Parametri avanzati
feature: Workflows, Data Management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 5%

---

# Parametri avanzati{#advanced-parameters}



La schermata delle proprietà di un&#39;attività include una scheda **[!UICONTROL Advanced]** che consente di definire un comportamento in caso di errori, il periodo di esecuzione dell&#39;attività e di immettere uno script di inizializzazione. Questa scheda è disponibile in due versioni:

* una versione semplificata (per **[!UICONTROL Start]** e **[!UICONTROL End]** attività, ad esempio)

  ![](assets/wf-advanced-basic.png)

* una versione più dettagliata (per l&#39;attività **[!UICONTROL Query]**, ad esempio)

  ![](assets/wf-advanced-full.png)

I campi da immettere nella scheda **[!UICONTROL Advanced]** sono descritti nelle sezioni seguenti.

## Nome {#name}

Questo campo contiene il nome interno dell’attività.

## Immagine {#image}

Questo campo consente di modificare l’immagine collegata a un’attività. Per ulteriori informazioni, consulta [Modificare le immagini dell&#39;attività](managing-activity-images.md).

## Execution {#execution}

Questo campo ti consente di definire l’azione da eseguire quando l’attività viene attivata. Sono disponibili tre opzioni:

Queste opzioni vengono generalmente selezionate nel carrello facendo clic con il pulsante destro del mouse sull’attività.

* **[!UICONTROL Normal]**: l&#39;attività viene eseguita come di consueto.
* **[!UICONTROL Do not activate]**: questa attività e tutte le seguenti attività (nello stesso ramo) non vengono eseguite.
* **[!UICONTROL Activate but do not execute]**: questa attività e tutte le seguenti attività (nello stesso ramo) vengono arrestate automaticamente. Questa opzione può essere utile se si desidera essere presenti all&#39;avvio dell&#39;attività. Per eseguire l&#39;attività manualmente, fare clic con il pulsante destro del mouse sull&#39;attività e selezionare **[!UICONTROL Normal execution]**.

## Affinità {#affinity}

Puoi scegliere di forzare l’esecuzione di un flusso di lavoro o di un’attività del flusso di lavoro su un computer specifico. A questo scopo, devi definire una o più propensione a livello del flusso di lavoro o dell’attività interessata.

La configurazione del flusso di lavoro ad alta disponibilità è descritta in questa [sezione](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).


## Max periodo di esecuzione {#max--execution-period}

Questo campo consente di impostare un avviso per i casi in cui l&#39;attività richiede troppo tempo. Non influirà sul funzionamento del flusso di lavoro. Se l&#39;attività non viene completata al termine del **[!UICONTROL Max. execution period]**, nella pagina **[!UICONTROL Instance monitoring]** verrà visualizzato un avviso per questo flusso di lavoro. Questa pagina è accessibile tramite la scheda **[!UICONTROL Monitoring]** della home page.

## Comportamento {#behavior}

Questo campo consente di definire il comportamento da applicare per l’utilizzo di attività asincrone. Sono disponibili due opzioni possibili:

* **[!UICONTROL Several tasks authorized]**: è possibile eseguire più attività contemporaneamente, anche se la prima non è stata completata.
* **[!UICONTROL The current task has priority]**: le attività in corso hanno la priorità. Finché un’attività è in corso, non verrà eseguita nessun’altra attività.

## Fuso orario {#time-zone}

Questo campo ti consente di selezionare il fuso orario dell’attività. Per ulteriori informazioni: [Gestire i fusi orari](managing-time-zones.md).

## In caso di errori {#in-case-of-errors}

Questo campo ti consente di definire l’azione da eseguire in caso di errori dell’attività. Sono disponibili due opzioni possibili:

* **[!UICONTROL Suspend the process]**: il flusso di lavoro viene arrestato automaticamente. Lo stato cambia in **[!UICONTROL Failed]**. Una volta risolto il problema, riavvia il flusso di lavoro.
* **[!UICONTROL Ignore]**: questa attività e tutte le seguenti attività (nello stesso ramo) non vengono eseguite. Questa funzione può essere utile per le attività ricorrenti. Se il ramo ha un modulo di pianificazione posizionato a monte, questo inizierà come di consueto nella data di esecuzione successiva.
* **[!UICONTROL Abort on error]**: il flusso di lavoro viene interrotto automaticamente e non può essere riavviato. Lo stato cambia in **[!UICONTROL Failed]**.

## Script di inizializzazione {#initialization-script}

Questo campo consente di inizializzare le variabili o modificare le proprietà dell’attività. Per ulteriori informazioni, consulta: [Script e modelli di JavaScript](javascript-scripts-and-templates.md).

## Commento {#comment}

Il campo **[!UICONTROL Comment]** è un campo libero che consente di aggiungere una descrizione.
