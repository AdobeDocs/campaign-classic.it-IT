---
title: Test
seo-title: Test
description: Test
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 6%

---


# Test{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

Una condizione è un&#39;espressione JavaScript che deve essere valutata come &#39;true&#39; o &#39;false&#39;. Per immettere l&#39;espressione, fate clic sull&#39;icona a destra del nome della condizione, quindi selezionate **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Per ulteriori informazioni su tutte le funzioni e i metodi SOAP JavaScript aggiuntivi del server applicativo accessibili tramite il flusso di lavoro JavaScript, consultare la documentazione [](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)JSAPI.

È inoltre possibile inserire le variabili direttamente da questo editor. Per ulteriori informazioni sull&#39;utilizzo delle variabili, consultare [questa sezione](../../workflow/using/javascript-scripts-and-templates.md#variables).

Le condizioni possono essere aggiunte, eliminate o ordinate dalla finestra di modifica della proprietà dell&#39;attività, ma possono anche essere modificate dalla transizione.

Se il risultato di un calcolo deve essere riutilizzato da condizioni diverse, è possibile calcolarlo nello script di inizializzazione dell&#39;attività. Il risultato deve essere memorizzato in una variabile dell&#39;attività a cui devono accedere gli script di condizione (task.vars.xxx).
