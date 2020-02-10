---
title: Avvio di Adobe Campaign
seo-title: Avvio di Adobe Campaign
description: Avvio di Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Avvio di Adobe Campaign{#launching-adobe-campaign}

## Avvio di Adobe Campaign {#starting-adobe-campaign}

Puoi avviare Adobe Campaign selezionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La finestra di connessione della console client consente di selezionare o configurare i database esistenti e di collegarli utilizzando un nome utente e una password:

![](assets/s_ncs_user_login.png)

## Connessione ad Adobe Campaign {#connecting-to-adobe-campaign}

Puoi connetterti ad Adobe Campaign utilizzando il tuo Adobe ID. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

È inoltre possibile connettersi con un login/password dedicato:

1. Immettete l&#39;identificatore dell&#39;account dell&#39;operatore nel **[!UICONTROL login]** campo.

   L&#39;identificatore viene fornito dall&#39;amministratore della piattaforma Adobe Campaign.

1. Immettere la password nel **[!UICONTROL Password]** campo.

   La prima volta che accedete al database, la password è quella fornita dall&#39;amministratore. Una volta connessi, potete cambiare la password tramite il **[!UICONTROL Tools > Change password...]** menu. I dettagli relativi agli operatori e alle connessioni sono disponibili in Gestione [](../../platform/using/access-management.md)accesso.

1. Fate clic **[!UICONTROL Log in]** per confermare.

Ora puoi accedere all&#39;area di lavoro [di](../../platform/using/adobe-campaign-workspace.md)Adobe Campaign.

## Configurazione delle connessioni {#setting-up-connections}

È possibile accedere alle impostazioni di connessione del server tramite il collegamento situato sopra la zona di input.

![](assets/s_ncs_user_connections_management.png)

Nella **[!UICONTROL Connections]** finestra, fate clic su **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

È quindi necessario definire le impostazioni di connessione. Per eseguire questa operazione:

* Immettete un nome **[!UICONTROL Label]** da assegnare alla connessione al database.
* Aggiungete l&#39;indirizzo del server applicazione nel **[!UICONTROL URL]** campo. Se non conoscete l’URL della connessione, rivolgetevi all’amministratore.
* Verificare **[!UICONTROL Connect with an Adobe ID]** che gli operatori possano connettersi alla console utilizzando il proprio Adobe ID. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).
* Fare clic **[!UICONTROL OK]** per eseguire la convalida.

>[!NOTE]
>
>Il **[!UICONTROL Add]** pulsante consente di creare **[!UICONTROL folders]** per organizzare tutte le connessioni. È sufficiente trascinare ogni connessione in una cartella.

## Operatori e autorizzazioni {#operators-and-permissions}

Gli identificatori e le password degli operatori che hanno accesso al software e alle rispettive autorizzazioni sono definiti dall&#39;amministratore di sistema di Adobe Campaign nel **[!UICONTROL Administration > Access management > Operators]** nodo della struttura ad albero di Adobe Campaign.

Questa funzionalità è descritta in dettaglio nella sezione Gestione [degli](../../platform/using/access-management.md) accessi.

## Disconnessione da Adobe Campaign {#disconnecting-from-adobe-campaign}

Per disconnettersi da Adobe Campaign, utilizza la prima icona nella barra delle icone.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>È inoltre possibile chiudere l&#39;applicazione senza prima disconnettersi.

## Ottenimento della versione di Campaign {#getting-your-campaign-version}

Il **[!UICONTROL Help > About...]** menu consente di accedere alle informazioni seguenti:

* **numero di versione** ,
* **numero build** ,
* un collegamento per contattare il supporto di Adobe Campaign.

   >[!CAUTION]
   >
   >Ogni volta che contattate il team di assistenza Adobe, dovete fornire il numero di versione e il numero di build della console client e del server applicazione di Campaign.

