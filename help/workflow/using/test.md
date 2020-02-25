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
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a

---


# Test{#test}

Un&#39;attività di tipo **Test** attiva la prima transizione che soddisfa la condizione associata. Se non viene soddisfatta alcuna condizione e se l&#39; **[!UICONTROL Use the default fork]** opzione è attivata, verrà attivata la transizione predefinita.

Una condizione è un&#39;espressione JavaScript che deve essere valutata come &#39;true&#39; o &#39;false&#39;. Per immettere l&#39;espressione, fate clic sull&#39;icona a destra del nome della condizione, quindi selezionate **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Per ulteriori informazioni su tutte le funzioni e i metodi SOAP JavaScript aggiuntivi del server applicativo accessibili tramite il flusso di lavoro JavaScript, consultare la documentazione [](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)JSAPI.

È inoltre possibile inserire le variabili direttamente da questo editor.

Le condizioni possono essere aggiunte, eliminate o ordinate dalla finestra di modifica della proprietà dell&#39;attività, ma possono anche essere modificate dalla transizione.

Se il risultato di un calcolo deve essere riutilizzato da condizioni diverse, è possibile calcolarlo nello script di inizializzazione dell&#39;attività. Il risultato deve essere memorizzato in una variabile dell&#39;attività a cui devono accedere gli script di condizione (task.vars.xxx).
