---
title: Sincronizzazione dei pubblici
seo-title: Sincronizzazione dei pubblici
description: Sincronizzazione dei pubblici
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 1%

---


# Sincronizzazione dei pubblici{#synchronizing-audiences}

Potete creare un elenco sofisticato utilizzando le funzioni avanzate di Campaign v7 e condividere questo elenco come pubblico direttamente e in tempo reale con Campaign Standard (inclusi i dati aggiuntivi) in modo semplice. L&#39;utente Campaign Standard può quindi utilizzare il pubblico in  Adobe Campaign Standard.

Il targeting complesso che include dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo tramite Campaign v7.

È inoltre possibile condividere semplicemente elenchi di destinatari o dati provenienti da un connettore come Microsoft Dynamics con Campaign Standard.

Questo caso di utilizzo mostra come preparare la destinazione della consegna in Campaign v7 e come riutilizzare questa destinazione e i relativi dati aggiuntivi in una consegna creata e inviata con  Adobe Campaign Standard.

>[!NOTE]
>
>È inoltre possibile arricchire i dati utilizzando aggregati e raccolte in  Adobe Campaign Standard se tutti i dati necessari sono già replicati.

## Prerequisiti {#prerequisites}

A tal fine, è necessario:

* Destinatari memorizzati nel database Campaign v7 e sincronizzati con i Campaign Standard. Fare riferimento alla sezione [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md) .
* Dati aggiuntivi, ad esempio iscrizioni o transazioni memorizzate in tabelle correlate a nomi:destinatari nel database Campaign v7. Questi dati possono provenire da schemi OOB di Campaign v7 o da tabelle personalizzate. Per impostazione predefinita non sono disponibili in Campaign Standard poiché non sono sincronizzati.
* Diritto di eseguire flussi di lavoro sia in Campaign v7 che in Campaign Standard.
* Diritto di creare ed eseguire una consegna in Campaign Standard.

## Creare un flusso di lavoro di targeting con dati aggiuntivi in Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Il targeting complesso che include dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo tramite Campaign v7.

Una volta definiti la destinazione e i relativi dati aggiuntivi, è possibile salvarla come un elenco che può essere condiviso con Campaign Standard.

>[!NOTE]
>
>Questo è un esempio. A seconda delle esigenze, puoi semplicemente eseguire una query su un elenco di destinatari e condividerlo con ACS senza ulteriori elaborazioni. Potete inoltre utilizzare altre attività di gestione dei dati per preparare il target finale.

Per ottenere il pubblico finale e i relativi dati aggiuntivi:

1. Crea un nuovo flusso di lavoro da **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Aggiungete un&#39; **[!UICONTROL Query]** attività e selezionate i destinatari a cui desiderate inviare l&#39;e-mail finale. Ad esempio, tutti i beneficiari tra i 18 e i 30 anni che vivono in Francia.

   ![](assets/acs_connect_query1.png)

1. Aggiungere dati aggiuntivi dall&#39;interno della query. For more information, refer to the [Adding data](../../workflow/using/query.md#adding-data) section.

   Questo esempio mostra come aggiungere un aggregato per calcolare il numero di consegne ricevute da un destinatario in un anno.

   In the **[!UICONTROL Query]**, select **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Seleziona **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Scegliere **[!UICONTROL Data linked to the filtering dimension]** e quindi selezionare il **[!UICONTROL Recipient delivery logs]** nodo e fare clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Selezionare **[!UICONTROL Aggregates]** nel **[!UICONTROL Data collected]** campo e fare clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Aggiungete una condizione di filtro per tenere conto solo dei registri creati negli ultimi 365 giorni e fate clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Definire le colonne di output. In questo caso, l&#39;unica colonna necessaria è quella in cui viene conteggiato il numero di consegne. A tale scopo:

   * Selezionate **[!UICONTROL Add]** a destra della finestra.
   * From the **[!UICONTROL Select field]** window, click **[!UICONTROL Advanced selection]**.
   * Selezionate **[!UICONTROL Aggregate]**, quindi **[!UICONTROL Count]**. Selezionate l’ **[!UICONTROL Distinct]** opzione e fate clic su **[!UICONTROL Next]**.
   * Nell&#39;elenco dei campi, selezionare il campo utilizzato per la funzione **Count** . Scegliete un campo che verrà sempre popolato, ad esempio il **[!UICONTROL Primary key]** campo, e fate clic su **[!UICONTROL Finish]**.
   * Modificare l&#39;espressione nella **[!UICONTROL Alias]** colonna. Questo alias consente di recuperare facilmente la colonna aggiunta nella consegna finale. Ad esempio, **NBdelivery**.
   * Fate clic su **[!UICONTROL Finish]** e salvate la configurazione dell&#39; **[!UICONTROL Query]** attività.

   ![](assets/acs_connect_query7.png)

1. Salva il flusso di lavoro. La sezione successiva mostra come condividere la popolazione con ACS.

## Condivisione della destinazione con Campaign Standard {#share-the-target-with-campaign-standard}

Una volta definita la popolazione di destinazione, potete condividerla con ACS attraverso un&#39; **[!UICONTROL List update]** attività.

1. Nel flusso di lavoro creato in precedenza, aggiungete un&#39; **[!UICONTROL List update]** attività e specificate l&#39;elenco da aggiornare o creare.

   Specificate la cartella in cui salvare l&#39;elenco in Campaign v7. Gli elenchi sono soggetti alla mappatura delle cartelle definita durante l&#39;implementazione, che può avere un impatto sulla loro visibilità una volta condivisa in Campaign Standard. Fate riferimento alla sezione [Conversione](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) diritti.

1. Accertatevi che l’ **[!UICONTROL Share with ACS]** opzione sia selezionata. È selezionato per impostazione predefinita.

   ![](assets/acs_connect_listupdate1.png)

1. Salvate ed eseguite il flusso di lavoro.

   La destinazione e i relativi dati aggiuntivi vengono salvati in un elenco in Campaign v7 e condivisi immediatamente come pubblico di elenchi in Campaign Standard. Solo i profili replicati vengono condivisi con ACS.

Se si verifica un errore nell&#39; **[!UICONTROL List update]** attività, significa che la sincronizzazione con Campaign Standard potrebbe non essere riuscita. Per visualizzare maggiori dettagli su cosa è andato storto, vai a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene i flussi di lavoro di sincronizzazione attivati dall&#39;esecuzione dell&#39; **[!UICONTROL List update]** attività. Fare riferimento alla sezione [Risoluzione dei problemi del connettore](../../integrations/using/troubleshooting-the-acs-connector.md) ACS.

## Recuperare i dati in Campaign Standard e utilizzarli in una consegna {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Una volta eseguito il flusso di lavoro di targeting in Campaign v7, potete trovare l&#39;audience dell&#39;elenco in modalità di sola lettura dal **[!UICONTROL Audiences]** menu dei Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Creando un flusso di lavoro di distribuzione in Campaign Standard, è possibile utilizzare questa audience e i dati aggiuntivi che contiene in una distribuzione.

1. Crea un nuovo flusso di lavoro dal **[!UICONTROL Marketing activities]** menu.
1. Aggiungete un&#39; **[!UICONTROL Read audience]** attività e selezionate l&#39;audience precedentemente condivisa da Campaign v7.

   Questa attività viene utilizzata per recuperare i dati dell&#39;audience selezionata. Potete anche applicare un&#39;ulteriore applicazione **[!UICONTROL Source Filtering]** se necessario utilizzando la scheda in base a questa attività.

1. Aggiungete un&#39; **[!UICONTROL Email delivery]** attività e configuratela come qualsiasi altra attività [di distribuzione](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)e-mail.
1. Aprite il contenuto della distribuzione.
1. Aggiungi un campo di personalizzazione. Dalla finestra a comparsa, individuare il **[!UICONTROL Additional data (targetData)]** nodo. Questo nodo contiene i dati aggiuntivi dell&#39;audience calcolati nel flusso di lavoro di targeting iniziale. Puoi usarli come qualsiasi altro campo di personalizzazione.

   In questo esempio, i dati aggiuntivi provenienti dal flusso di lavoro di targeting originale corrispondono al numero di consegne inviate a ciascun destinatario negli ultimi 365 giorni. L&#39;alias NBdelivery specificato nel flusso di lavoro di targeting è visibile qui.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Salvate la consegna e il flusso di lavoro.

   Il flusso di lavoro è ora pronto per essere eseguito. La consegna verrà analizzata e pronta per essere inviata.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Invio e monitoraggio della consegna {#send-and-monitor-your-delivery}

Una volta pronti la consegna e il relativo contenuto, inviate la consegna, come descritto con maggiori dettagli in [questa sezione](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html):

1. Esegui il flusso di lavoro di consegna. Questo passaggio prepara l’e-mail per l’invio.
1. Dal dashboard di consegna, verificate manualmente che la consegna possa essere inviata.
1. Controlla i rapporti e i registri della consegna:

   * **In Campaign Standard**: Accedi a [rapporti](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) e [registri](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) relativi alla consegna come per qualsiasi consegna.
   * **in Campaign v7 e Campaign Standard**: Gli ID di distribuzione, i registri di indirizzi e-mail ampi e i registri di tracciamento delle e-mail vengono sincronizzati su Campaign v7. Potete quindi visualizzare a 360° le campagne di marketing da Campaign v7.

      Le quarantena vengono sincronizzate automaticamente su Campaign v7. Questo consente di tenere conto delle informazioni non consegnabili per il targeting successivo eseguito in Campaign v7.

      Per ulteriori informazioni sulla gestione della quarantena, consulta [questa sezione](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

