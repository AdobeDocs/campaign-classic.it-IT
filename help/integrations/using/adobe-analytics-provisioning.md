---
product: campaign
title: Provisioning del connettore Adobe Analytics
description: Ulteriori informazioni sul provisioning dei connettori Adobe Analytics
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 84e6b2fad97f0ca5d6621cff4648e0be0bef7521
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---

# Provisioning del connettore Adobe Analytics {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Questi passaggi devono essere eseguiti solo da implementazioni ibride e locali.
>
>Per le implementazioni in hosting e Campaign Managed Services, contatta [Adobe Systems team dell&#39;Assistenza](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) clienti.

L&#39;integrazione tra autenticazione Adobe Campaign Classic e Adobe Analytics supporta Adobe Systems servizio Identity Management (IMS):

* Se gestisci un account esterno migrato, devi implementare Adobe Systems IMS e connetterti a Adobe Campaign tramite un Adobe ID.

  L&#39;utente che ha eseguito l&#39;accesso tramite Adobe ID IMS deve essere il proprietario dell&#39;account **Data Connector** in Adobe Analytics e disporre delle autorizzazioni per il **profilo di prodotto** menzionato [di seguito](#analytics-product-profile).

Il problema era che il proprietario del connettore dati era un utente diverso da quello che aveva effettuato l’accesso a Campaign e che stava tentando l’integrazione con Analytics.

* Se implementi un nuovo connettore, l’implementazione di Adobe IMS è facoltativa. Senza un utente Adobe ID, Adobe Campaign utilizzerà un utente tecnico per la sincronizzazione con Adobe Analytics.

Affinché questa integrazione funzioni, devi creare un profilo di prodotto Adobe Analytics che verrà utilizzato esclusivamente per il connettore Analytics. Quindi, devi creare un progetto Console sviluppatori.

>[!AVAILABILITY]
>
> Le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server OAuth. </br>
>
> * Se hai implementato integrazioni in entrata con Campaign, devi eseguire la migrazione del tuo account tecnico come descritto in [questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Le credenziali [dell&#39;account di servizio (JWT) esistenti](oauth-technical-account.md) continueranno a funzionare fino al 30 giugno 2025.</br>
>
> * Se hai implementato integrazioni in uscita, come l&#39;integrazione Campaign-Analytics o l&#39;integrazione Experience Cloud Triggers, continueranno a funzionare fino al 30 giugno 2025. Tuttavia, prima di tale data, è necessario aggiornare l&#39;ambiente Campaign alla versione 7.4.1 ed eseguire la migrazione dell&#39;account tecnico a OAuth.

## Crea un profilo di prodotto Adobe Analytics {#analytics-product-profile}

Il Profilo di prodotto determina il livello di accesso di un utente sui diversi componenti Analytics.

Se disponi già di un profilo di prodotto Analytics, devi comunque creare un nuovo profilo di prodotto Adobe Analytics utilizzato esclusivamente per il connettore Analytics. In questo modo il tuo profilo di prodotto sarà impostato con le autorizzazioni corrette per questa integrazione.

Per ulteriori informazioni sui profili di prodotto, consulta la [documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Da [Admin Console](https://adminconsole.adobe.com/), seleziona il tuo Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Fai clic su **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Aggiungere un **[!UICONTROL Product profile name]**. Si consiglia di utilizzare la sintassi seguente: `reserved_campaign_classic_<Company Name>`. Quindi fare clic su **[!UICONTROL Next]**.

   Deve **[!UICONTROL Product profile]** essere utilizzato esclusivamente per il connettore Analytics per evitare errori di configurazione.

1. Apri il nuovo creato **[!UICONTROL Product profile]** e seleziona il **[!UICONTROL Permissions]** scheda.

   ![](assets/do-not-localize/triggers_3.png)

1. Configura le diverse funzionalità cliccando **[!UICONTROL Edit]** e seleziona le autorizzazioni da assegnare cliccando **[!UICONTROL Product profile]** sull&#39;icona più (+).

   Per ulteriori informazioni su come gestire le autorizzazioni, consulta la documentazione[&#128279;](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html) di Admin Console.

1. Per la **[!UICONTROL Report Suites]** funzionalità, aggiungi la **[!UICONTROL Report Suites]** funzionalità che devi usare in seguito.

   Se non disponi di suite di rapporti, puoi crearle seguendo [questi passaggi](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. Per la funzionalità **[!UICONTROL Metrics]**, aggiungi **[!UICONTROL Metrics]** che dovrai configurare in seguito.

   Se necessario, puoi attivare l’opzione di inclusione automatica, che consente di aggiungere tutti gli elementi di autorizzazione all’elenco incluso e automaticamente quelli nuovi.

   ![](assets/do-not-localize/triggers_13.png)

1. Per la funzionalità **[!UICONTROL Dimensions]**, aggiungi **[!UICONTROL Dimensions]** necessario per la configurazione futura.

   Assicurati che le dimensioni scelte corrispondano a quelle da configurare nell’account esterno e siano allineate al numero eVar corrispondente di Adobe Analytics.

1. Per la funzionalità **[!UICONTROL Report Suite Tools]**, aggiungere le seguenti autorizzazioni:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Per la **[!UICONTROL Analytics Tools]** funzionalità, aggiungi le seguenti autorizzazioni:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Il profilo di prodotto è ora configurato. Devi quindi creare il progetto OAuth.

## Crea progetto OAuth {#create-adobe-io}

Per procedere con la configurazione del connettore Adobe Analytics, accesso la console Adobe Systems Developer e creare il progetto da server a server OAuth.

Per la documentazione dettagliata, consulta [questa pagina](oauth-technical-account.md#oauth-service).

## Configurazione e utilizzo {#adobe-analytics-connector-usage}

Scopri come utilizzare Adobe Campaign e Adobe Analytics nella [documentazione](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"} di Adobe Campaign v8.