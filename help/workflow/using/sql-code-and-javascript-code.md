---
solution: Campaign Classic
product: campaign
title: Codice SQL e codice JavaScript
description: Ulteriori informazioni sulle attività del flusso di lavoro relative ai codici SQL e JavaScript
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 8bcfc8826a66517e6a648dbc57b681778718c33c
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Codice SQL e codice JavaScript{#sql-code-and-javascript-code}

## Codice SQL {#sql-code}

Un&#39;attività **[!UICONTROL SQL code]** esegue uno script SQL. Lo script è un modello JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   L&#39;area centrale dell&#39;editor contiene lo script da eseguire. Questo script è un modello JST e può quindi essere configurato in base al contesto del flusso di lavoro.

* **[!UICONTROL Processing errors]**

   Fare riferimento a [Errori di elaborazione](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Codice JavaScript e codice JavaScript avanzato {#javascript-code}

**[!UICONTROL JavaScript code]** e  **[!UICONTROL Advanced JavaScript code]** le attività eseguono uno script JavaScript nel contesto di un flusso di lavoro. Per ulteriori informazioni sugli script, consultare la sezione [Script e modelli JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

### Ritardo di esecuzione {#exec-delay}

A partire dalla versione 20.2, alle attività **[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** è stato aggiunto un ritardo di esecuzione. Per impostazione predefinita, la fase di esecuzione non può superare 1 ora. Dopo questo ritardo, il processo verrà interrotto con un messaggio di errore e l&#39;esecuzione dell&#39;attività avrà esito negativo.

È possibile modificare questo ritardo nel campo **[!UICONTROL Stop execution after]** disponibile in queste attività.

Per ignorare questo limite, è necessario impostare il valore su **0**.

### Codice JavaScript {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: L&#39;area centrale dell&#39;editor contiene lo script da eseguire.

* **[!UICONTROL Process errors]**: Fare riferimento a Errori [ di ](../../workflow/using/monitoring-workflow-execution.md#processing-errors)elaborazione.

### Codice JavaScript avanzato {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: La prima area dell&#39;editor contiene lo script da eseguire durante la prima chiamata.
* **[!UICONTROL Next calls]**: La seconda area dell&#39;editor contiene lo script da eseguire durante le chiamate successive.
* **[!UICONTROL Transitions]**: Potete definire diverse transizioni di output dell&#39;attività.
* **[!UICONTROL Schedule]**: La  **[!UICONTROL Schedule]** scheda consente di pianificare quando attivare l&#39;attività.
