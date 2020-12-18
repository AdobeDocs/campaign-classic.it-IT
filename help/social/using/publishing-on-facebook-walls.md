---
solution: Campaign Classic
product: campaign
title: Pubblicazione su bacheche Facebook
description: Pubblicazione su bacheche Facebook
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 2%

---


# Pubblicazione su bacheche Facebook{#publishing-on-facebook-walls}

Affinché  Adobe Campaign possa inviare pubblicazioni alle mura di Facebook, è necessario delegare l&#39;accesso in scrittura per queste pagine a  Adobe Campaign. Sono previsti i seguenti passaggi di configurazione:

1. Create un account Facebook con una o più pagine.
1. Create una pagina Facebook di prova per l’invio delle prove.
1. Creare un’applicazione Facebook.
1. Immettete le impostazioni dell&#39;applicazione Facebook in  Adobe Campaign, nell&#39;account esterno **[!UICONTROL Facebook routing]**.

## Prerequisiti {#prerequisites}

Per iniziare, create un account Facebook e diverse pagine: verranno utilizzati per inviare pubblicazioni.

* Per creare un account Facebook, utilizzate il collegamento [https://www.facebook.com](https://www.facebook.com).
* Per creare una pagina Facebook, utilizzate il collegamento [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create).

   È consigliabile utilizzare lo stesso account Facebook per amministrare tutte le pagine. In questo modo, avrete bisogno solo di un&#39;applicazione Facebook e di un account esterno per scrivere su tutte le pagine dell&#39;account.

   ![](assets/social_diagram_fb_external_account.png)

## Creazione di una pagina Facebook di prova {#creating-a-test-facebook-page}

È consigliabile creare una pagina Facebook privata per la distribuzione delle prove di pubblicazione (per ulteriori informazioni, vedere [Invio delle prove](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Accedete all&#39;account Facebook che utilizzate per amministrare le pagine.
1. Create una nuova pagina Facebook.
1. Fare clic sul pulsante **[!UICONTROL Settings]** nell&#39;angolo in alto a destra.
1. Nella scheda **[!UICONTROL General]**, modificate i parametri di visibilità della pagina: selezionare la casella **[!UICONTROL Page unpublished]**.
1. Fai clic sul pulsante **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Creazione di un’app Facebook {#creating-a-facebook-application}

Affinché  Adobe Campaign possa pubblicare le pagine sui muri, è necessario creare un’applicazione Facebook. A questo scopo, eseguire i seguenti passaggi:

1. Accedete all’account Facebook che utilizzate per amministrare le pagine.
1. Inserite il seguente indirizzo nel browser: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >A seconda del tipo di account in uso, potrebbe essere necessaria una o più autorizzazioni.
   >
   >Per creare un&#39;applicazione Facebook, è necessario un account Facebook **verificato**.

1. Fare clic sul pulsante **[!UICONTROL Add a New App]** nell&#39;angolo superiore destro della pagina. Immettete un nome app e un messaggio e-mail di contatto, quindi passate il controllo di sicurezza.

   ![](assets/social_create_facebook_app_002.png)

1. In **[!UICONTROL Settings > Basic]**, fare clic su **[!UICONTROL Add a platform]** e selezionare il tipo **[!UICONTROL Facebook Web Games]**.

   ![](assets/social_create_facebook_app_003.png)

1. Nella sezione **[!UICONTROL Products]**, nel menu a sinistra, verificare di visualizzare il prodotto **[!UICONTROL Facebook Login]**. In caso contrario, aggiungete un nuovo prodotto e selezionate **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Una volta creata l&#39;applicazione, selezionate la scheda **[!UICONTROL App Review]** e pubblicate l&#39;applicazione.

   ![](assets/social_create_facebook_app_004.png)

## Delega dell&#39;accesso in scrittura a  Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Per delegare l&#39;accesso in scrittura a  Adobe Campaign per la pubblicazione sui muri delle pagine, è necessario immettere i parametri dell&#39;applicazione Facebook creata in precedenza.

Questo passaggio richiede l’accesso sia alla console Adobe Campaign  che a un browser Internet connesso all’account Facebook che utilizzate per l’amministrazione delle pagine:

>[!IMPORTANT]
>
>L&#39;operatore Adobe Campaign  deve disporre dei diritti di amministrazione per eseguire questa configurazione.

* **Facebook**: selezionate l’applicazione creata in precedenza (  [https://developers.facebook.com/apps](https://developers.facebook.com/apps)), quindi selezionate la  **[!UICONTROL Settings > Basic]** scheda.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Se la sezione **[!UICONTROL Facebook Web Games]** non viene visualizzata, fare clic sul pulsante **[!UICONTROL Add Platform]**, nella parte inferiore della pagina, quindi selezionare **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: andate al  **[!UICONTROL Administration > Platform > External Accounts]** nodo della struttura, selezionate l&#39;account  **[!UICONTROL Facebook routing]** esterno e fate clic sulla  **[!UICONTROL Connector]** scheda.

   ![](assets/social_facebook_external_account_001.png)

1. Nella console Adobe Campaign , copiate l&#39;indirizzo contenuto nel campo **[!UICONTROL Secure Canvas URL]** e incollatelo nel campo **[!UICONTROL Secure Web Games URL (https)]** su Facebook (nella sezione **[!UICONTROL Facebook Web Games]**).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Non è necessario utilizzare l&#39;URL non sicuro in nessun caso.

   Copiate e incollate questo URL anche in **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Per verificare la validità dell&#39;URL, salvate l&#39;applicazione, copiate e incollate l&#39;URL nel campo **[!UICONTROL Redirect URI to Check]**, quindi fate clic su **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Su Facebook, copiate il contenuto dei campi **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e incollatelo nei campi corrispondenti della console.

   ![](assets/social_facebook_external_account_007.png)

1. Su Facebook, fate clic sul pulsante **[!UICONTROL Save Changes]** in fondo alla pagina.
1. Passate alla  console Adobe Campaign e salvate l’account esterno.

   >[!NOTE]
   >
   >Il campo **[!UICONTROL Marketing URL]** è facoltativo.

1. Nella console Adobe Campaign , fate clic sul collegamento **[!UICONTROL Request the authorization from the application]** nella parte inferiore della scheda **[!UICONTROL Connector]**. Il flusso di lavoro **[!UICONTROL Synchronize Facebook pages]** viene attivato automaticamente e raccoglie tutte le pagine Facebook gestite dall&#39;amministratore. Per ulteriori informazioni, vedere [Sincronizzazione delle pagine Facebook](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, le pagine vengono aggiunte alla cartella **[!UICONTROL Facebook]** del servizio, disponibile tramite il nodo **[!UICONTROL Profiles and Targets > Services and Subscriptions]**. Il campo **[!UICONTROL Folder]** della scheda **[!UICONTROL Connector]** consente di modificare la cartella del servizio in cui vengono create le pagine Facebook dopo la sincronizzazione. È inoltre possibile selezionare le pagine Facebook da sincronizzare in  Adobe Campaign grazie al campo **[!UICONTROL Filter]**. Se lasciate vuoto questo campo, tutte le pagine Facebook gestite dall’amministratore verranno sincronizzate.

1. Viene visualizzata una finestra di dialogo con le varie impostazioni di autorizzazione di Facebook. Questi consentono  Adobe Campaign di inviare pubblicazioni alle pagine dell&#39;account Facebook.

   Accettate le varie richieste di autorizzazione.

   ![](assets/social_facebook_external_account_003.png)

1.  Adobe Campaign ha il diritto di pubblicare le pagine dell&#39;account Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Se l&#39;account Facebook gestisce diverse pagine, è sufficiente configurare un account esterno per scrivere su qualsiasi pagina dell&#39;account Facebook. Per ogni nuovo account Facebook, dovrete creare un nuovo account esterno di tipo **[!UICONTROL Routing]**.

Il flusso di lavoro **[!UICONTROL Synchronization of Facebook pages]** sincronizza tutte le pagine amministrate dall&#39;account Facebook, per consentirvi di pubblicare direttamente sulla loro bacheca tramite  Adobe Campaign. Per ulteriori informazioni, vedere [Sincronizzazione delle pagine Facebook](#synchronizing-facebook-pages).

## Sincronizzazione delle pagine Facebook {#synchronizing-facebook-pages}

Il flusso di lavoro **[!UICONTROL Synchronization of Facebook pages]**, a cui si accede tramite il nodo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, consente di sincronizzare (in  Adobe Campaign) le pagine dell&#39;account Facebook configurato in precedenza. Per impostazione predefinita, questo flusso di lavoro è configurato per essere eseguito una volta al giorno o ogni volta che un amministratore fa clic sul collegamento **[!UICONTROL Request an authorization from the application]** nella schermata di configurazione del servizio (fare riferimento a [Delegazione dell&#39;accesso in scrittura a  Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Una volta completata la sincronizzazione, le pagine raccolte vengono visualizzate nella cartella del servizio inserita nell&#39;account esterno (fare riferimento a [Delegare l&#39;accesso in scrittura a  Adobe Campaign](#delegating-write-access-to-adobe-campaign)). Per impostazione predefinita, le pagine vengono aggiunte alla radice della cartella **[!UICONTROL Facebook]** del servizio, disponibile tramite il menu **[!UICONTROL Profiles and Targets > Services and subscriptions]**.

![](assets/social_facebook_service_002.png)

È ora possibile pubblicare contenuti sulle pareti delle pagine Facebook direttamente tramite  Adobe Campaign. Per ulteriori informazioni, consultare [Pubblicazione su Facebook](#publishing-on-facebook-walls).
