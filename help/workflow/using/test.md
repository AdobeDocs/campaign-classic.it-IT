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
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Test{#test}

Un&#39;attività di tipo **Test** attiva la prima transizione che soddisfa la condizione associata. Se non viene soddisfatta alcuna condizione e se l&#39; **[!UICONTROL Use the default fork]** opzione è attivata, verrà attivata la transizione predefinita.

Una condizione è un&#39;espressione JavaScript che deve essere valutata come &#39;true&#39; o &#39;false&#39;. Per immettere l&#39;espressione, fate clic sull&#39;icona a destra del nome della condizione, quindi selezionate **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Per ulteriori informazioni su tutte le funzioni e i metodi SOAP JavaScript aggiuntivi del server applicativo accessibili tramite il flusso di lavoro JavaScript, consultare la documentazione [](http://docs.campaign.adobe.com/doc/AC/en/jsapi/p-1.html)JSAPI.

È inoltre possibile inserire le variabili direttamente da questo editor.

Le condizioni possono essere aggiunte, eliminate o ordinate dalla finestra di modifica della proprietà dell&#39;attività, ma possono anche essere modificate dalla transizione.

Se il risultato di un calcolo deve essere riutilizzato da condizioni diverse, è possibile calcolarlo nello script di inizializzazione dell&#39;attività. Il risultato deve essere memorizzato in una variabile dell&#39;attività a cui devono accedere gli script di condizione (task.vars.xxx).
