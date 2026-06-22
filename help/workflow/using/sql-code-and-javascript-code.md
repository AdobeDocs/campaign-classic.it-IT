---
product: campaign
title: Codice SQL e codice JavaScript
description: Ulteriori informazioni sulle attività del flusso di lavoro dei codici SQL e JavaScript
feature: Workflows
hide: true
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
TQID: https://experienceleague.adobe.com/B-OWeBTtXSxSD1k-qgRq06ymp00LvVH2U7k9yRAN3YE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 13%

---

# Codice SQL e codice JavaScript{#sql-code-and-javascript-code}



## Codice SQL {#sql-code}

Un&#39;attività **[!UICONTROL SQL code]** esegue uno script SQL. Lo script è un modello JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

  L’area centrale dell’editor contiene lo script da eseguire. Questo script è un modello JST e può quindi essere configurato in base al contesto del flusso di lavoro.

* **[!UICONTROL Processing errors]**

  Consulta [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Codice JavaScript e codice JavaScript avanzato {#javascript-code}

Le attività **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** eseguono uno script JavaScript nel contesto di un flusso di lavoro. Per ulteriori informazioni sugli script, consulta le sezioni seguenti:

* [Script e modelli JavaScript](javascript-scripts-and-templates.md)
* [Esempi di codice JavaScript nei flussi di lavoro](javascript-in-workflows.md)

### Ritardo di esecuzione {#exec-delay}

A partire dalla versione 20.2, è stato aggiunto un ritardo di esecuzione alle attività **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]**. Per impostazione predefinita, la fase di esecuzione non può superare 1 ora. Dopo questo ritardo, il processo verrà interrotto con un messaggio di errore e l’esecuzione dell’attività avrà esito negativo.

È possibile modificare questo ritardo nel campo **[!UICONTROL Stop execution after]** disponibile in queste attività.

Per ignorare questo limite, è necessario impostare il valore su **0**.

### Codice JavaScript {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: l&#39;area centrale dell&#39;editor contiene lo script da eseguire.

* **[!UICONTROL Process errors]**: consultare [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

### Codice JavaScript avanzato {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: la prima zona dell&#39;editor contiene lo script da eseguire durante la prima chiamata.
* **[!UICONTROL Next calls]**: la seconda zona dell&#39;editor contiene lo script da eseguire durante le chiamate successive.
* **[!UICONTROL Transitions]**: è possibile definire diverse transizioni di output attività.
* **[!UICONTROL Schedule]**: la scheda **[!UICONTROL Schedule]** consente di pianificare quando attivare l&#39;attività.

Advanced JavaScript è un&#39;attività persistente che viene periodicamente richiamata se non è stata contrassegnata come completata. Per terminare l&#39;attività ed evitare richiami futuri, è necessario utilizzare il metodo **task.setCompleted()** nella sezione **[!UICONTROL Next calls]**:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```

