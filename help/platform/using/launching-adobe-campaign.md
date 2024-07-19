---
product: campaign
title: Avvio di Adobe Campaign
description: Avvio di Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 9%

---

# Avviare Adobe Campaign{#launching-adobe-campaign}



La console client di Campaign è un client avanzato che consente di connettersi ai server applicazioni di Campaign. Scopri come scaricare e configurare la console client in [questa pagina](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Verifica la compatibilità del sistema e degli strumenti con Adobe Campaign Client Console nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Avvia Adobe Campaign {#starting-adobe-campaign}

È possibile avviare Adobe Campaign selezionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

La finestra di connessione della console client consente di selezionare o configurare i database esistenti e di connettersi ad essi utilizzando un nome utente e una password:

![](assets/acc-logon.png)

## Connessione ad Adobe Campaign {#connecting-to-adobe-campaign}

Puoi connetterti ad Adobe Campaign utilizzando il tuo Adobe ID. Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

Puoi anche connetterti con un login/password dedicato:

1. Immettere l&#39;identificatore dell&#39;account operatore nel campo **[!UICONTROL Login]**.

   L’identificatore viene fornito dall’amministratore della piattaforma Adobe Campaign.

1. Immettere la password nel campo **[!UICONTROL Password]**.

   La prima volta che si accede al database, la password è quella fornita dall&#39;amministratore. Una volta effettuata la connessione, è possibile modificare la password tramite il menu **[!UICONTROL Tools > Change password...]**. I dettagli sugli operatori e sulle connessioni sono disponibili in [Gestione degli accessi](../../platform/using/access-management.md).

1. Fai clic su **[!UICONTROL LOG IN]** per confermare.<!--You can also press the **Enter** key to launch connection.-->

È ora possibile accedere all&#39;[area di lavoro Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

Alcune scelte rapide da tastiera sono disponibili in **[!UICONTROL Sign in screen]**:
* Tutti gli elementi utilizzabili sono selezionabili tramite il tasto **Tab** (dall&#39;alto verso il basso) o i tasti **Tab** + **Shift** (dal basso verso l&#39;alto).
* Per avviare la connessione, puoi anche premere il tasto **Invio**.
* È possibile utilizzare la chiave **Escape** per ripristinare i campi **[!UICONTROL Login]** e **[!UICONTROL Password]** agli ultimi valori di connessione completati.

## Configurare le connessioni {#setting-up-connections}

È possibile accedere alle impostazioni di connessione al server tramite il collegamento sopra l&#39;area di input.

![](assets/s_ncs_user_connections_management.png)

Nella finestra **[!UICONTROL Connections]**, fare clic su **[!UICONTROL Add > Connection]**.

È quindi necessario definire le impostazioni di connessione. Per eseguire questa operazione:

1. Immetti **[!UICONTROL Label]** per assegnare un nome alla connessione al database.

1. Aggiungere l&#39;indirizzo del server applicazioni nel campo **[!UICONTROL URL]**. Se non conosci l’URL di connessione, contatta l’amministratore.

1. Selezionare **[!UICONTROL Connect with an Adobe ID]** per consentire agli operatori di connettersi alla console utilizzando il proprio Adobe ID. Per ulteriori informazioni, consulta [questa pagina](../../integrations/using/about-adobe-id.md).

1. Fai clic su **[!UICONTROL OK]** per confermare.

## Operatori e autorizzazioni {#operators-and-permissions}

Gli identificatori e le password degli operatori con accesso al software e le rispettive autorizzazioni sono definiti dall&#39;amministratore di sistema Adobe Campaign nel nodo **[!UICONTROL Administration > Access management > Operators]** della struttura Adobe Campaign.

Questa funzionalità è descritta nella sezione [Gestione degli accessi](../../platform/using/access-management.md).

## Disconnetti da Adobe Campaign {#disconnecting-from-adobe-campaign}

Per disconnettersi da Adobe Campaign, utilizza la prima icona nella barra delle icone.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>È inoltre possibile chiudere l&#39;applicazione senza disconnettersi.

## Scarica la versione Adobe Campaign {#getting-your-campaign-version}

Il menu **[!UICONTROL Help > About...]** consente di accedere alle seguenti informazioni:

* Numero **versione** per la console client di Campaign e il server applicazioni
* Numero **build** per la console client di Campaign e il server applicazioni
* un collegamento per contattare l’Assistenza clienti di Adobe
* collegamenti alla Policy per i cookie, alle Condizioni d’uso e all’Informativa sulla privacy di Adobe

![](assets/about-acc.png)

Quando ti rivolgi al team di assistenza clienti Adobe, devi fornire il numero di versione e di build della console client e del server applicazioni Adobe Campaign.

**Argomenti correlati**:

* [Opzioni di assistenza e supporto per Adobe Campaign](../../support.md)
* [Distribuzione software Adobe Campaign](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)
* [Sessioni Adobe Experience Cloud Support ed Expert](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
