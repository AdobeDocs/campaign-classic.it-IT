---
product: campaign
title: Attività Test
description: Ulteriori informazioni sull’attività del flusso di lavoro Test
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---

# Attività Test{#test}

![](../../assets/common.svg)

Un&#39;attività di tipo **Test** attiva la prima transizione che soddisfa la condizione associata. Se non viene soddisfatta alcuna condizione e se l&#39;opzione **[!UICONTROL Use the default fork]** è attivata, la transizione predefinita verrà attivata.

Una condizione è un&#39;espressione JavaScript che deve essere valutata come &#39;true&#39; o &#39;false&#39;. Per immettere l’espressione, fai clic sull’icona a destra del nome della condizione, quindi seleziona **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Per ulteriori informazioni su tutte le funzioni JavaScript aggiuntive e i metodi SOAP del server applicativo accessibili tramite il flusso di lavoro JavaScript, consulta la [documentazione JSAPI](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Puoi anche inserire le variabili direttamente da questo editor. Per ulteriori informazioni su come lavorare con le variabili, consulta [questa sezione](javascript-scripts-and-templates.md#variables).

Le condizioni possono essere aggiunte, eliminate o ordinate dalla finestra di modifica della proprietà dell’attività, ma possono anche essere modificate dalla transizione.

Se il risultato di un calcolo deve essere riutilizzato da condizioni diverse, è possibile calcolarlo nello script di inizializzazione dell&#39;attività. Il risultato deve essere memorizzato in una variabile dell&#39;attività a cui devono accedere gli script di condizione (task.vars.xxx).
