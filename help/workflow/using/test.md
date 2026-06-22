---
product: campaign
title: Test
description: Ulteriori informazioni sull’attività del flusso di lavoro Test
feature: Workflows
hide: true
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
TQID: https://experienceleague.adobe.com/NaQuMb-U9z0U8QZZnmwgPdKaFacOduVvGWDl9P68qR4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: tm+mt
source-wordcount: 193
ht-degree: 4%

---

# Test{#test}



Un&#39;attività di tipo **Test** attiva la prima transizione che soddisfa la condizione associata. Se non viene soddisfatta alcuna condizione e se l&#39;opzione **[!UICONTROL Use the default fork]** è attivata, verrà attivata la transizione predefinita.

Una condizione è un’espressione JavaScript che deve essere valutata come &quot;true&quot; o &quot;false&quot;. Per immettere l&#39;espressione, fare clic sull&#39;icona a destra del nome della condizione, quindi selezionare **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Per ulteriori informazioni su tutte le funzioni JavaScript aggiuntive e i metodi SOAP del server applicativo accessibili tramite JavaScript del flusso di lavoro, fare riferimento alla [documentazione JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it).

Puoi anche inserire le variabili direttamente da questo editor. Per ulteriori informazioni su come utilizzare le variabili, consulta [questa sezione](javascript-scripts-and-templates.md#variables).

Le condizioni possono essere aggiunte, eliminate o ordinate dalla finestra di modifica delle proprietà dell’attività, ma possono anche essere modificate dalla transizione.

Se il risultato di un calcolo deve essere riutilizzato da condizioni diverse, è possibile calcolarlo nello script di inizializzazione dell’attività. Il risultato deve essere memorizzato in una variabile dell’attività a cui devono accedere gli script di condizione (task.vars.xxx).

