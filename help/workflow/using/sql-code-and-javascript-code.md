---
title: Codice SQL e codice JavaScript
seo-title: Codice SQL e codice JavaScript
description: Codice SQL e codice JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 9%

---


# Codice SQL e codice JavaScript{#sql-code-and-javascript-code}

## Codice SQL {#sql-code}

Un&#39; **[!UICONTROL SQL code]** attività esegue uno script SQL. Lo script è un modello JST.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   L&#39;area centrale dell&#39;editor contiene lo script da eseguire. Questo script è un modello JST e può quindi essere configurato in base al contesto del flusso di lavoro.

* **[!UICONTROL Processing errors]**

   Fare riferimento a Errori [di](../../workflow/using/monitoring-workflow-execution.md#processing-errors)elaborazione.

## Codice JavaScript e codice JavaScript avanzato {#javascript-code}

**[!UICONTROL JavaScript code]** e **[!UICONTROL Advanced JavaScript code]** le attività eseguono uno script JavaScript nel contesto di un flusso di lavoro. Per ulteriori informazioni sugli script, vedere la sezione relativa agli script e ai modelli [](../../workflow/using/javascript-scripts-and-templates.md) JavaScript.

>[!NOTE]
>
>Per impostazione predefinita, la fase di esecuzione delle **[!UICONTROL JavaScript code]** attività e delle **[!UICONTROL Advanced JavaScript code]** attività non può superare 1 ora. Dopo questo ritardo, il processo verrà interrotto con un messaggio di errore e l&#39;esecuzione dell&#39;attività avrà esito negativo.
>
>È possibile modificare questo ritardo nel **[!UICONTROL Stop execution after]** campo disponibile nelle proprietà delle attività.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: L&#39;area centrale dell&#39;editor contiene lo script da eseguire.
   * **[!UICONTROL Processing errors]**: Fare riferimento a Errori [di](../../workflow/using/monitoring-workflow-execution.md#processing-errors)elaborazione.

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: La prima area dell&#39;editor contiene lo script da eseguire durante la prima chiamata.
   * **[!UICONTROL Next calls]**: La seconda area dell&#39;editor contiene lo script da eseguire durante le chiamate successive.
   * **[!UICONTROL Transitions]**: Potete definire diverse transizioni di output dell&#39;attività.
   * **[!UICONTROL Schedule]**: La **[!UICONTROL Schedule]** scheda consente di pianificare quando attivare l&#39;attività.
