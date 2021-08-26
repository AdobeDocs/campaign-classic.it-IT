---
product: campaign
title: Codice SQL e codice JavaScript
description: Ulteriori informazioni sulle attività del flusso di lavoro relative ai codici SQL e JavaScript
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---

# Codice SQL e codice JavaScript{#sql-code-and-javascript-code}

![](../../assets/common.svg)

## Codice SQL {#sql-code}

Un&#39;attività **[!UICONTROL SQL code]** esegue uno script SQL. Lo script è un modello JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   L’area centrale dell’editor contiene lo script da eseguire. Questo script è un modello JST e può quindi essere configurato in base al contesto del flusso di lavoro.

* **[!UICONTROL Processing errors]**

   Fare riferimento a [Errori di elaborazione](monitoring-workflow-execution.md#processing-errors).

## Codice JavaScript e codice JavaScript avanzato {#javascript-code}

**[!UICONTROL JavaScript code]** e  **[!UICONTROL Advanced JavaScript code]** le attività eseguono uno script JavaScript nel contesto di un flusso di lavoro. Per ulteriori informazioni sugli script, consulta la sezione [Script e modelli JavaScript](javascript-scripts-and-templates.md) .

### Ritardo esecuzione {#exec-delay}

A partire dalla versione 20.2, alle attività **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** è stato aggiunto un ritardo di esecuzione. Per impostazione predefinita, la fase di esecuzione non può superare 1 ora. Dopo questo ritardo, il processo verrà interrotto con un messaggio di errore e l’esecuzione dell’attività avrà esito negativo.

Puoi modificare questo ritardo nel campo **[!UICONTROL Stop execution after]** disponibile in queste attività.

Per ignorare questo limite, è necessario impostare il valore su **0**.

### Codice JavaScript {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: L’area centrale dell’editor contiene lo script da eseguire.

* **[!UICONTROL Process errors]**: Fai riferimento agli errori  [di elaborazione](monitoring-workflow-execution.md#processing-errors).

### Codice JavaScript avanzato {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: La prima zona dell’editor contiene lo script da eseguire durante la prima chiamata.
* **[!UICONTROL Next calls]**: La seconda zona dell’editor contiene lo script da eseguire durante le chiamate successive.
* **[!UICONTROL Transitions]**: Puoi definire diverse transizioni di output dell’attività.
* **[!UICONTROL Schedule]**: La  **[!UICONTROL Schedule]** scheda ti consente di pianificare quando attivare l’attività.

Advanced JavaScript è un’attività persistente e viene richiamato periodicamente se non è stato contrassegnato come completato. Per terminare l&#39;attività ed evitare richiami futuri, è necessario utilizzare il metodo **task.setCompleted()** nella sezione **[!UICONTROL Next calls]** :

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
