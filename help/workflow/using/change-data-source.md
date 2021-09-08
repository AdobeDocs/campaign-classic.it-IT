---
title: Modificare l’origine dati
description: Ulteriori informazioni sull’attività Cambia origine dati
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Modificare l’origine dati {#change-data-source}

>[!NOTE]
>
> L’attività **[!UICONTROL Change data source]** è disponibile solo con il pacchetto **[!UICONTROL Access to external data (Federated Data Access)]** . Per ulteriori informazioni sui pacchetti incorporati Adobe Campaign Classic, consulta questa [pagina](../../installation/using/installing-campaign-standard-packages.md).

L’attività **[!UICONTROL Change data source]** ti consente di modificare l’origine dati di un flusso di lavoro **[!UICONTROL Working table]**. Questo offre maggiore flessibilità per gestire i dati tra diverse origini dati, come FDA, FFDA e database locale.

Il **[!UICONTROL Working table]** consente al flusso di lavoro Adobe Campaign Classic di gestire i dati e condividerli con le attività del flusso di lavoro.
Per impostazione predefinita, il **[!UICONTROL Working table]** viene creato nello stesso database dell&#39;origine dei dati su cui eseguiamo la query.

Ad esempio, quando esegui una query sulla tabella **[!UICONTROL Profiles]** memorizzata nel database Cloud, creerai un elemento **[!UICONTROL Working table]** nello stesso database Cloud.
Per modificare questa impostazione, puoi aggiungere l’attività **[!UICONTROL Change Data Source]** per scegliere una diversa origine dati per il tuo **[!UICONTROL Working table]**.

Tieni presente che quando utilizzi l’attività **[!UICONTROL Change Data Source]** , dovrai tornare al database Cloud per continuare l’esecuzione del flusso di lavoro.

Per utilizzare l&#39;attività **[!UICONTROL Change Data Source]**:

1. Creazione di un flusso di lavoro.

1. Esegui una query sui destinatari con un’attività **[!UICONTROL Query]** .

   Per ulteriori informazioni sull&#39;attività **[!UICONTROL Query]**, consulta questa [pagina](../../workflow/using/query.md#creating-a-query).

1. Aggiungi un’attività **[!UICONTROL Change data source]** dalla scheda **[!UICONTROL Targeting]** .

   ![](assets/change-data-source.png)

1. Fai doppio clic sull’attività **[!UICONTROL Change data source]** per selezionare **[!UICONTROL Default data source]**.

   La tabella di lavoro, che contiene il risultato della query, viene quindi spostata nel database PostgreSQL predefinito.

   ![](assets/change-data-source_2.png)

1. Dalla scheda **[!UICONTROL Actions]** , trascina e rilascia un’attività **[!UICONTROL JavaScript code]** per eseguire operazioni unitarie sulla tabella di lavoro.

   Per ulteriori informazioni sull&#39;attività **[!UICONTROL JavaScript code]**, consulta la pagina [Codice JavaScript e Codice JavaScript avanzato](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) .

1. Aggiungi un’altra attività **[!UICONTROL Change data source]** per tornare al database Cloud.

1. Fai doppio clic sull’attività e seleziona **[!UICONTROL Active FDA external account]** , quindi l’account esterno corrispondente **[!UICONTROL External database]**.

   ![](assets/change-data-source_3.png)

1. Ora puoi avviare il flusso di lavoro.
