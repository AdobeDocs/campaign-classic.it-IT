---
product: campaign
title: Provisioning del connettore Adobe Analytics
description: Ulteriori informazioni sul provisioning dei connettori Adobe Analytics
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 1%

---

# Provisioning del connettore Adobe Analytics {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Questi passaggi devono essere eseguiti solo da implementazioni ibride e on-premise.
>
>Per le implementazioni in hosting e Campaign Managed Services, contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team.

L’integrazione tra l’autenticazione di Adobe Campaign Classic e Adobe Analytics supporta Adobe Identity Management Service (IMS):

* Se gestisci un account esterno migrato, devi implementare Adobe IMS e connetterti ad Adobe Campaign tramite un Adobe ID.

  L’utente connesso tramite Adobe ID IMS deve essere il proprietario del **Connettore dati** in Adobe Analytics e di disporre delle autorizzazioni necessarie per **Profilo di prodotto** ha menzionato [sotto](#analytics-product-profile).

Il problema era che il proprietario del connettore dati era un utente diverso da quello che aveva effettuato l’accesso a Campaign e che stava tentando l’integrazione con Analytics.

* Se implementi un nuovo connettore, l’implementazione di Adobe IMS è facoltativa. Senza un utente Adobe ID, Adobe Campaign utilizzerà un utente tecnico per la sincronizzazione con Adobe Analytics.

Affinché questa integrazione funzioni, devi creare un profilo di prodotto Adobe Analytics che verrà utilizzato esclusivamente per il connettore Analytics. Quindi, devi creare un progetto Console sviluppatori.

>[!AVAILABILITY]
>
> Le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server OAuth. </br>
>
> * Se hai implementato le integrazioni in entrata con Campaign, devi migrare l’account tecnico come descritto in [questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Le credenziali dell’account di servizio (JWT) esistenti continueranno a funzionare fino al 27 gennaio 2025.</br>
>
> * Se hai implementato integrazioni in uscita, ad esempio l’integrazione Campaign-Analytics o l’integrazione Experience Cloud Triggers, queste continueranno a funzionare fino al 27 gennaio 2025. Tuttavia, prima di tale data, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a OAuth.

## Creare un profilo di prodotto Adobe Analytics {#analytics-product-profile}

Il profilo prodotto determina il livello di accesso di un utente ai diversi componenti di Analytics.

Se disponi già di un profilo di prodotto Analytics, devi comunque creare un nuovo profilo di prodotto Adobe Analytics utilizzato esclusivamente per il connettore Analytics. In questo modo il tuo profilo di prodotto sarà impostato con le autorizzazioni corrette per questa integrazione.

Per ulteriori informazioni sui profili di prodotto, consulta [Documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Dalla sezione [Admin Console](https://adminconsole.adobe.com/), seleziona il tuo Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Fai clic su **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Aggiungi un **[!UICONTROL Product profile name]**, si consiglia di utilizzare la sintassi seguente: `reserved_campaign_classic_<Company Name>`. Quindi, fai clic su **[!UICONTROL Next]**.

   Questo **[!UICONTROL Product profile]** deve essere utilizzato esclusivamente per il connettore Analytics per evitare errori di configurazione.

1. Apri il nuovo **[!UICONTROL Product profile]** e seleziona la **[!UICONTROL Permissions]** scheda.

   ![](assets/do-not-localize/triggers_3.png)

1. Configurare le diverse funzionalità facendo clic su **[!UICONTROL Edit]** e seleziona le autorizzazioni da assegnare al tuo **[!UICONTROL Product profile]** facendo clic sull&#39;icona più (+).

   Per ulteriori informazioni su come gestire le autorizzazioni, consulta [Documentazione di Admin Console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Per **[!UICONTROL Report Suites]** , aggiungi **[!UICONTROL Report Suites]** in seguito sarà necessario utilizzare.

   Se non disponi di suite di rapporti, puoi crearle come segue [questi passaggi](../../integrations/using/gs-aa.md).

   ![](assets/do-not-localize/triggers_4.png)

1. Per **[!UICONTROL Metrics]** , aggiungi **[!UICONTROL Metrics]** dovrai configurare in seguito.

   Se necessario, puoi attivare l’opzione di inclusione automatica, che consente di aggiungere tutti gli elementi di autorizzazione all’elenco incluso e automaticamente quelli nuovi.

   ![](assets/do-not-localize/triggers_13.png)

1. Per **[!UICONTROL Dimensions]** , aggiungi **[!UICONTROL Dimensions]** necessario per la configurazione futura.

   Assicurati che i Dimension scelti corrispondano a quelli da configurare nell’account esterno e allinearli al numero eVar corrispondente di Adobe Analytics.

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

Il tuo profilo di prodotto è ora configurato. Quindi devi creare il progetto OAuth.

## Crea progetto OAuth {#create-adobe-io}

Per procedere con la configurazione del connettore Adobe Analytics, accedi alla console Adobe Developer e crea il progetto server-to-server OAuth.

Fai riferimento a [questa pagina](oauth-technical-account.md#oauth-service) per la documentazione dettagliata.

## Configurazione e utilizzo {#adobe-analytics-connector-usage}

Scopri come utilizzare Adobe Campaign e Adobe Analytics in [Documentazione di Adobe Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.