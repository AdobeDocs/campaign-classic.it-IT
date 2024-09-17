---
product: campaign
title: Provisioning del connettore Adobe Analytics
description: Ulteriori informazioni sul provisioning dei connettori Adobe Analytics
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 1%

---

# Provisioning del connettore Adobe Analytics {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Questi passaggi devono essere eseguiti solo da implementazioni ibride e on-premise.
>
>Per le implementazioni Managed Services in hosting e Campaign, contatta il team [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

L’integrazione tra l’autenticazione di Adobe Campaign Classic e Adobe Analytics supporta Adobe Identity Management Service (IMS):

* Se gestisci un account esterno migrato, devi implementare Adobe IMS e connetterti ad Adobe Campaign tramite un Adobe ID.

  L&#39;utente che ha eseguito l&#39;accesso tramite Adobe ID IMS deve essere il proprietario dell&#39;account **Data Connector** in Adobe Analytics e disporre delle autorizzazioni per il **profilo di prodotto** menzionato [di seguito](#analytics-product-profile).

Il problema era che il proprietario del connettore dati era un utente diverso da quello che aveva effettuato l’accesso a Campaign e che stava tentando l’integrazione con Analytics.

* Se implementi un nuovo connettore, l’implementazione di Adobe IMS è facoltativa. Senza un utente Adobe ID, Adobe Campaign utilizzerà un utente tecnico per la sincronizzazione con Adobe Analytics.

Affinché questa integrazione funzioni, devi creare un profilo di prodotto Adobe Analytics che verrà utilizzato esclusivamente per il connettore Analytics. Quindi, devi creare un progetto Console sviluppatori.

>[!AVAILABILITY]
>
> Le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server OAuth. </br>
>
> * Se hai implementato integrazioni in entrata con Campaign, devi migrare l&#39;account tecnico come descritto in [questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Le credenziali [dell&#39;account di servizio (JWT) esistenti](oauth-technical-account.md) continueranno a funzionare fino al 27 gennaio 2025.</br>
>
> * Se hai implementato integrazioni in uscita, ad esempio l’integrazione Campaign-Analytics o l’integrazione Experience Cloud Triggers, queste continueranno a funzionare fino al 27 gennaio 2025. Tuttavia, prima di tale data, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a OAuth.

## Creare un profilo di prodotto Adobe Analytics {#analytics-product-profile}

Il profilo prodotto determina il livello di accesso di un utente ai diversi componenti di Analytics.

Se disponi già di un profilo di prodotto Analytics, devi comunque creare un nuovo profilo di prodotto Adobe Analytics utilizzato esclusivamente per il connettore Analytics. In questo modo il tuo profilo di prodotto sarà impostato con le autorizzazioni corrette per questa integrazione.

Per ulteriori informazioni sui profili di prodotto, consulta la [documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Da [Admin Console](https://adminconsole.adobe.com/), seleziona il tuo Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Fai clic su **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Aggiungere un **[!UICONTROL Product profile name]**. Si consiglia di utilizzare la sintassi seguente: `reserved_campaign_classic_<Company Name>`. Quindi fare clic su **[!UICONTROL Next]**.

   **[!UICONTROL Product profile]** deve essere utilizzato esclusivamente per il connettore Analytics per evitare errori di configurazione.

1. Apri **[!UICONTROL Product profile]** appena creato e seleziona la scheda **[!UICONTROL Permissions]**.

   ![](assets/do-not-localize/triggers_3.png)

1. Configurare le diverse funzionalità facendo clic su **[!UICONTROL Edit]** e selezionare le autorizzazioni da assegnare a **[!UICONTROL Product profile]** facendo clic sull&#39;icona più (+).

   Per ulteriori informazioni su come gestire le autorizzazioni, consulta la [documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Per la funzionalità **[!UICONTROL Report Suites]**, aggiungi **[!UICONTROL Report Suites]** da utilizzare in seguito.

   Se non disponi di suite di rapporti, puoi crearle seguendo [questi passaggi](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. Per la funzionalità **[!UICONTROL Metrics]**, aggiungi **[!UICONTROL Metrics]** che dovrai configurare in seguito.

   Se necessario, puoi attivare l’opzione di inclusione automatica, che consente di aggiungere tutti gli elementi di autorizzazione all’elenco incluso e automaticamente quelli nuovi.

   ![](assets/do-not-localize/triggers_13.png)

1. Per la funzionalità **[!UICONTROL Dimensions]**, aggiungi **[!UICONTROL Dimensions]** necessario per la configurazione futura.

   Assicurati che i Dimension scelti corrispondano a quelli da configurare nell’account esterno e allinearli al numero eVar corrispondente di Adobe Analytics.

1. Per la funzionalità **[!UICONTROL Report Suite Tools]**, aggiungere le seguenti autorizzazioni:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Per la funzionalità **[!UICONTROL Analytics Tools]**, aggiungere le seguenti autorizzazioni:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Il tuo profilo di prodotto è ora configurato. Quindi devi creare il progetto OAuth.

## Crea progetto OAuth {#create-adobe-io}

Per procedere con la configurazione del connettore Adobe Analytics, accedi alla console Adobe Developer e crea il progetto server-to-server OAuth.

Per la documentazione dettagliata, consulta [questa pagina](oauth-technical-account.md#oauth-service).

## Configurazione e utilizzo {#adobe-analytics-connector-usage}

Scopri come utilizzare Adobe Campaign e Adobe Analytics nella [documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.