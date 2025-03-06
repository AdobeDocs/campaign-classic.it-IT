---
title: Cambiare l’origine dati
description: Ulteriori informazioni sull’attività Modifica origine dati
feature: Workflows, Data Management, Federated Data Access
hide: true
hidefromtoc: true
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Cambiare l’origine dati {#change-data-source}

>[!NOTE]
>
> L&#39;attività **[!UICONTROL Change data source]** è disponibile solo con il pacchetto **[!UICONTROL Access to external data (Federated Data Access)]**. Per ulteriori informazioni sui pacchetti incorporati di Adobe Campaign Classic, consulta questa [pagina](../../installation/using/installing-campaign-standard-packages.md).

L&#39;attività **[!UICONTROL Change data source]** consente di modificare l&#39;origine dati di un flusso di lavoro **[!UICONTROL Working table]**. Questo offre maggiore flessibilità per gestire i dati tra diverse origini dati, come FDA, FFDA e database locale.

**[!UICONTROL Working table]** consente al flusso di lavoro Adobe Campaign Classic di gestire i dati e di condividerli con le attività del flusso di lavoro.
Per impostazione predefinita, **[!UICONTROL Working table]** viene creato nello stesso database dell&#39;origine dei dati su cui viene eseguita la query.

Ad esempio, quando si esegue una query sulla tabella **[!UICONTROL Profiles]**, memorizzata nel database Cloud, verrà creato un **[!UICONTROL Working table]** sullo stesso database Cloud.
Per modificare questa impostazione, è possibile aggiungere l&#39;attività **[!UICONTROL Change Data Source]** per scegliere un&#39;origine dati diversa per **[!UICONTROL Working table]**.

Quando si utilizza l&#39;attività **[!UICONTROL Change Data Source]**, è necessario tornare al database cloud per continuare l&#39;esecuzione del flusso di lavoro.

Per utilizzare l&#39;attività **[!UICONTROL Change Data Source]**:

1. Crea un flusso di lavoro.

1. Eseguire una query sui destinatari con un&#39;attività **[!UICONTROL Query]**.

   Per ulteriori informazioni sull&#39;attività **[!UICONTROL Query]**, vedere questa [pagina](../../workflow/using/query.md#creating-a-query).

1. Aggiungere un&#39;attività **[!UICONTROL Change data source]** dalla scheda **[!UICONTROL Targeting]**.

   ![](assets/change-data-source.png)

1. Fare doppio clic sull&#39;attività **[!UICONTROL Change data source]** per selezionare **[!UICONTROL Default data source]**.

   La tabella di lavoro, che contiene il risultato della query, viene quindi spostata nel database PostgreSQL predefinito.

   ![](assets/change-data-source_2.png)

1. Dalla scheda **[!UICONTROL Actions]**, trascina e rilascia un&#39;attività **[!UICONTROL JavaScript code]** per eseguire operazioni unitarie sulla tabella di lavoro.

   Per ulteriori informazioni sull&#39;attività **[!UICONTROL JavaScript code]**, fare riferimento alla pagina [Codice JavaScript e codice JavaScript avanzato](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

1. Aggiungi un&#39;altra attività **[!UICONTROL Change data source]** per tornare al database cloud.

1. Fai doppio clic sull&#39;attività e seleziona **[!UICONTROL Active FDA external account]**, quindi l&#39;account esterno **[!UICONTROL External database]** corrispondente.

   ![](assets/change-data-source_3.png)

1. Ora puoi avviare il flusso di lavoro.
