---
solution: Campaign Classic
product: campaign
title: Connettore Adobe Analytics
description: Ulteriori informazioni sul connettore Adobe Analytics provisioning
feature: Overview
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 671e29425e8962ced833c10303b6edce7afda462
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 4%

---

# Provisioning del connettore Adobe Analytics {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> Questi passaggi devono essere eseguiti solo da implementazioni ibride e on-premise.
>
>Per le implementazioni in hosting, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) squadra.

L’integrazione tra Adobe Campaign Classic e l’autenticazione Adobe Analytics supporta Adobe Identity Management Service (IMS):

* Se gestisci un account esterno migrato, devi implementare Adobe IMS e connetterti ad Adobe Campaign tramite un Adobe ID. L’utente che ha effettuato l’accesso tramite Adobe ID IMS deve essere il proprietario del **Connettore dati** in Adobe Analytics e dispongono di un set di autorizzazioni per **Profilo di prodotto** di seguito.

* Se stai implementando un nuovo connettore, l’implementazione di Adobe IMS è facoltativa. Senza un utente Adobe ID, Adobe Campaign utilizzerà un utente tecnico per la sincronizzazione con Adobe Analytics.

Affinché questa integrazione funzioni, devi creare un profilo di prodotto Adobe Analytics che verrà utilizzato esclusivamente per il connettore Analytics. Quindi, dovrai creare un progetto di Adobe I/O.

## Creare un profilo di prodotto Adobe Analytics {#analytics-product-profile}

Il profilo di prodotto determina il livello di accesso di un utente ai diversi componenti di Analytics.

Se disponi già di un profilo di prodotto Analytics, devi comunque creare un nuovo profilo di prodotto Adobe Analytics utilizzato esclusivamente per il connettore Analytics. In questo modo il profilo di prodotto sarà impostato con le autorizzazioni corrette per questa integrazione.

Per ulteriori informazioni sui profili di prodotto, consulta [Documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Da [Admin Console](https://adminconsole.adobe.com/), seleziona il tuo Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Fai clic su **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Aggiungi un **[!UICONTROL Product profile name]**, si consiglia di utilizzare la sintassi seguente: `reserved_campaign_classic_<Company Name>`. Quindi, fai clic su **[!UICONTROL Next]**.

   Questo **[!UICONTROL Product profile]** deve essere utilizzato esclusivamente per Analytics Connector per evitare errori di configurazione errata.

1. Apri la nuova **[!UICONTROL Product profile]** e seleziona la **[!UICONTROL Permissions]** scheda .

   ![](assets/do-not-localize/triggers_3.png)

1. Configura le diverse funzionalità facendo clic su **[!UICONTROL Edit]** e seleziona le autorizzazioni da assegnare al tuo **[!UICONTROL Product profile]** facendo clic sull’icona più (+).

   Per ulteriori informazioni su come gestire le autorizzazioni, consulta la [Documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Per **[!UICONTROL Report Suites]** aggiungi la funzionalità **[!UICONTROL Report Suites]** è necessario utilizzare in seguito.

   Se non disponi di suite di rapporti, puoi crearle come segue [questi passaggi](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. Per **[!UICONTROL Metrics]** aggiungi la funzionalità **[!UICONTROL Metrics]** dovrai effettuare la configurazione in un secondo momento.

   Se necessario, puoi attivare l’opzione di inclusione automatica che aggiungerà ogni elemento delle autorizzazioni nell’elenco incluso e aggiungerà automaticamente nuovi elementi delle autorizzazioni.

   ![](assets/do-not-localize/triggers_13.png)

1. Per **[!UICONTROL Dimensions]** aggiungi la funzionalità **[!UICONTROL Dimensions]** dovrai effettuare la configurazione in un secondo momento.

1. Per **[!UICONTROL Report Suite Tools]** , aggiungi le seguenti autorizzazioni:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Per **[!UICONTROL Analytics Tools]** , aggiungi le seguenti autorizzazioni:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Il tuo profilo di prodotto è ora configurato. Quindi devi creare il progetto di Adobe I/O.

## Crea progetto di Adobe I/O {#create-adobe-io}

1. Accedi all&#39;Adobe I/O e accedi come **Amministratore di sistema** dell&#39;Organizzazione IMS.

   Per ulteriori informazioni sui ruoli amministratore, consulta questo [page](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Fai clic su **[!UICONTROL Create a new project]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Fai clic su **[!UICONTROL Add to Project]** e seleziona **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Seleziona [!DNL Adobe Analytics] e fai clic su **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Scegli **[!UICONTROL Service Account (JWT)]** come tipo di autenticazione e fai clic su **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Seleziona la **[!UICONTROL Option 1: Generate a Key-Pair]** e fai clic su **[!UICONTROL Generate a Key-Pair]**.

   Il file config.zip viene quindi scaricato automaticamente.

   ![](assets/do-not-localize/triggers_9.png)

1. Fai clic su **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Seleziona la **[!UICONTROL Product profile]** creato nei passaggi precedenti descritti in questo [sezione](#analytics-product-profile).

1. Quindi, fai clic su **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Dal progetto, seleziona [!DNL Adobe Analytics] e copia le seguenti informazioni in **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. Incolla queste credenziali dell&#39;account di servizio nel server nlserver utilizzando il seguente comando:

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

Ora puoi iniziare a utilizzare il connettore Analytics e tenere traccia dei comportamenti dei clienti.
