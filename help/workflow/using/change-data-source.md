---
title: Modificare l’origine dati
description: Ulteriori informazioni sull’attività Cambia origine dati
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 31483bdd2e0a2dd0676ef391c5484e4b778317c1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# Modificare l’origine dati {#change-data-source}

>[!NOTE]
>
> La **[!UICONTROL Change data source]** l’attività è disponibile solo con **[!UICONTROL Access to external data (Federated Data Access)]** pacchetto. Per ulteriori informazioni sui pacchetti incorporati Adobe Campaign Classic, consulta questo [page](../../installation/using/installing-campaign-standard-packages.md).

La **[!UICONTROL Change data source]** consente di modificare l’origine dati di un flusso di lavoro **[!UICONTROL Working table]**. Questo offre maggiore flessibilità per gestire i dati tra diverse origini dati, come FDA, FFDA e database locale.

La **[!UICONTROL Working table]** consente al flusso di lavoro Adobe Campaign Classic di gestire i dati e condividerli con le attività del flusso di lavoro.
Per impostazione predefinita, la **[!UICONTROL Working table]** viene creato nello stesso database dell&#39;origine dei dati su cui eseguiamo la query.

Ad esempio, quando si esegue una query sul **[!UICONTROL Profiles]** nella tabella, memorizzata nel database Cloud, verrà creato un **[!UICONTROL Working table]** sullo stesso database Cloud.
Per modificare questa impostazione, puoi aggiungere la **[!UICONTROL Change Data Source]** per scegliere un’origine dati diversa per la **[!UICONTROL Working table]**.

Tieni presente che quando utilizzi **[!UICONTROL Change Data Source]** per continuare l’esecuzione del flusso di lavoro, dovrai tornare al database Cloud .

Per utilizzare **[!UICONTROL Change Data Source]** attività:

1. Creare un flusso di lavoro.

1. Invia una query ai destinatari con un **[!UICONTROL Query]** attività.

   Per ulteriori informazioni sulla **[!UICONTROL Query]** attività, fai riferimento a [page](../../workflow/using/query.md#creating-a-query).

1. Da **[!UICONTROL Targeting]** aggiungi una scheda **[!UICONTROL Change data source]** attività.

   ![](assets/change-data-source.png)

1. Fai doppio clic sul **[!UICONTROL Change data source]** attività da selezionare **[!UICONTROL Default data source]**.

   La tabella di lavoro, che contiene il risultato della query, viene quindi spostata nel database PostgreSQL predefinito.

   ![](assets/change-data-source_2.png)

1. Da **[!UICONTROL Actions]** trascinare un **[!UICONTROL JavaScript code]** attività per eseguire operazioni unitarie sul tavolo di lavoro.

   Per ulteriori informazioni sulla **[!UICONTROL JavaScript code]** attività, fai riferimento alla [Codice JavaScript e codice JavaScript avanzato](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) pagina.

1. Aggiungi un altro **[!UICONTROL Change data source]** attività per tornare al database Cloud.

1. Fai doppio clic sull’attività e seleziona **[!UICONTROL Active FDA external account]** quindi il corrispondente **[!UICONTROL External database]** conto esterno.

   ![](assets/change-data-source_3.png)

1. Ora puoi avviare il flusso di lavoro.
