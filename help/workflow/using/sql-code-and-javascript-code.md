---
product: campaign
title: Codice SQL e codice JavaScript
description: Ulteriori informazioni sulle attività del flusso di lavoro relative ai codici SQL e JavaScript
feature: Workflows
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 7%

---

# Codice SQL e codice JavaScript{#sql-code-and-javascript-code}

![](../../assets/common.svg)

## Codice SQL {#sql-code}

Un **[!UICONTROL SQL code]** L&#39;attività esegue uno script SQL. Lo script è un modello JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   L’area centrale dell’editor contiene lo script da eseguire. Questo script è un modello JST e può quindi essere configurato in base al contesto del flusso di lavoro.

* **[!UICONTROL Processing errors]**

   Fai riferimento a [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Codice JavaScript e codice JavaScript avanzato {#javascript-code}

**[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** le attività eseguono uno script JavaScript nel contesto di un flusso di lavoro. Per ulteriori informazioni sugli script, consulta le sezioni seguenti:

* [Script e modelli JavaScript](javascript-scripts-and-templates.md)
* [Esempi di codice JavaScript nei flussi di lavoro](javascript-in-workflows.md)

### Ritardo esecuzione {#exec-delay}

A partire dalla versione 20.2, è stato aggiunto un ritardo di esecuzione al **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** attività. Per impostazione predefinita, la fase di esecuzione non può superare 1 ora. Dopo questo ritardo, il processo verrà interrotto con un messaggio di errore e l’esecuzione dell’attività avrà esito negativo.

Puoi modificare questo ritardo nella **[!UICONTROL Stop execution after]** campo disponibile in queste attività.

Per ignorare questo limite, è necessario impostare il valore su **0**.

### Codice JavaScript {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: L’area centrale dell’editor contiene lo script da eseguire.

* **[!UICONTROL Process errors]**: Fai riferimento a [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

### Codice JavaScript avanzato {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: La prima zona dell’editor contiene lo script da eseguire durante la prima chiamata.
* **[!UICONTROL Next calls]**: La seconda zona dell’editor contiene lo script da eseguire durante le chiamate successive.
* **[!UICONTROL Transitions]**: Puoi definire diverse transizioni di output dell’attività.
* **[!UICONTROL Schedule]**: La **[!UICONTROL Schedule]** consente di pianificare quando attivare l’attività.

Advanced JavaScript è un’attività persistente e viene richiamato periodicamente se non è stato contrassegnato come completato. Per terminare l&#39;attività e evitare richiami futuri, è necessario utilizzare il **task.setCompleted()** nel **[!UICONTROL Next calls]** sezione:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
