---
title: Modificare l’origine dati
description: Ulteriori informazioni sull’attività Modifica origine dati
feature: Workflows, Data Management, Federated Data Access
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Modificare l’origine dati {#change-data-source}

>[!NOTE]
>
> Il **[!UICONTROL Change data source]** l&#39;attività è disponibile solo con **[!UICONTROL Access to external data (Federated Data Access)]** pacchetto. Per ulteriori informazioni sui pacchetti incorporati di Adobe Campaign Classic, consulta [pagina](../../installation/using/installing-campaign-standard-packages.md).

Il **[!UICONTROL Change data source]** attività ti consente di modificare l’origine dati di un flusso di lavoro **[!UICONTROL Working table]**. Questo offre maggiore flessibilità per gestire i dati tra diverse origini dati, come FDA, FFDA e database locale.

Il **[!UICONTROL Working table]** consente al flusso di lavoro Adobe Campaign Classic di gestire i dati e condividerli con le attività del flusso di lavoro.
Per impostazione predefinita, il **[!UICONTROL Working table]** viene creato nello stesso database dell’origine dei dati su cui eseguiamo le query.

Ad esempio, quando si esegue una query su **[!UICONTROL Profiles]** , memorizzata nel database Cloud, creerai un&#39; **[!UICONTROL Working table]** sullo stesso database cloud.
Per modificare questa impostazione, puoi aggiungere **[!UICONTROL Change Data Source]** attività per scegliere un’origine dati diversa per il **[!UICONTROL Working table]**.

Tieni presente che quando utilizzi **[!UICONTROL Change Data Source]** attività, dovrai tornare al database Cloud per continuare l’esecuzione del flusso di lavoro.

Per utilizzare **[!UICONTROL Change Data Source]** attività:

1. Crea un flusso di lavoro.

1. Effettua query sui destinatari target con una **[!UICONTROL Query]** attività.

   Per ulteriori informazioni su **[!UICONTROL Query]** attività, fai riferimento a questo [pagina](../../workflow/using/query.md#creating-a-query).

1. Dalla sezione **[!UICONTROL Targeting]** , aggiungi un **[!UICONTROL Change data source]** attività.

   ![](assets/change-data-source.png)

1. Fai doppio clic sul tuo **[!UICONTROL Change data source]** attività da selezionare **[!UICONTROL Default data source]**.

   La tabella di lavoro, che contiene il risultato della query, viene quindi spostata nel database PostgreSQL predefinito.

   ![](assets/change-data-source_2.png)

1. Dalla sezione **[!UICONTROL Actions]** , trascina e rilascia una **[!UICONTROL JavaScript code]** attività per eseguire operazioni unitarie sulla tabella di lavoro.

   Per ulteriori informazioni su **[!UICONTROL JavaScript code]** attività, fai riferimento alla [Codice JavaScript e codice JavaScript avanzato](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) pagina.

1. Aggiungi un altro **[!UICONTROL Change data source]** per tornare al database Cloud.

1. Fai doppio clic sull’attività e seleziona **[!UICONTROL Active FDA external account]** quindi il corrispondente **[!UICONTROL External database]** account esterno.

   ![](assets/change-data-source_3.png)

1. Ora puoi avviare il flusso di lavoro.
