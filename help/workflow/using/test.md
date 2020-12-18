---
solution: Campaign Classic
product: campaign
title: Test
description: Ulteriori informazioni sull'attività del flusso di lavoro Test
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---


# Test{#test}

Un&#39;attività di tipo **Test** attiva la prima transizione che soddisfa la condizione associata. Se nessuna condizione è soddisfatta e se l&#39;opzione **[!UICONTROL Use the default fork]** è attivata, la transizione predefinita verrà attivata.

Una condizione è un&#39;espressione JavaScript che deve essere valutata come &#39;true&#39; o &#39;false&#39;. Per immettere l&#39;espressione, fare clic sull&#39;icona a destra del nome della condizione, quindi selezionare **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Per ulteriori informazioni su tutte le funzioni e i metodi SOAP JavaScript aggiuntivi del server applicativo accessibili tramite il flusso di lavoro JavaScript, fare riferimento alla [documentazione JSAPI](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

È inoltre possibile inserire le variabili direttamente da questo editor. Per ulteriori informazioni sull&#39;utilizzo delle variabili, consultare [questa sezione](../../workflow/using/javascript-scripts-and-templates.md#variables).

Le condizioni possono essere aggiunte, eliminate o ordinate dalla finestra di modifica della proprietà dell&#39;attività, ma possono anche essere modificate dalla transizione.

Se il risultato di un calcolo deve essere riutilizzato da condizioni diverse, è possibile calcolarlo nello script di inizializzazione dell&#39;attività. Il risultato deve essere memorizzato in una variabile dell&#39;attività a cui devono accedere gli script di condizione (task.vars.xxx).
