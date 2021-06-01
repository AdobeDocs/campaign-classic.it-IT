---
product: campaign
title: Pubblicazione su bacheche Facebook
description: Pubblicazione su bacheche Facebook
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 2%

---

# Pubblicazione su bacheche Facebook{#publishing-on-facebook-walls}

Affinché Adobe Campaign possa inviare pubblicazioni alle pareti Facebook, è necessario delegare l’accesso in scrittura per queste pagine ad Adobe Campaign. Sono previsti i seguenti passaggi di configurazione:

1. Crea un account Facebook con una o più pagine.
1. Crea una pagina Facebook di prova per l’invio di bozze.
1. Creare un’applicazione Facebook.
1. Immetti le impostazioni dell&#39;applicazione Facebook in Adobe Campaign, nell&#39;account esterno **[!UICONTROL Facebook routing]**.

## Prerequisiti {#prerequisites}

Inizia creando un account Facebook e diverse pagine: verranno utilizzati per l’invio di pubblicazioni.

* Per creare un account Facebook, utilizza il collegamento [https://www.facebook.com](https://www.facebook.com) .
* Per creare una pagina Facebook, utilizza il collegamento [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) .

   È consigliabile utilizzare lo stesso account Facebook per amministrare tutte le pagine. In questo modo, per scrivere su tutte le pagine dell’account sarà necessaria solo un’applicazione Facebook e un account esterno.

   ![](assets/social_diagram_fb_external_account.png)

## Creazione di una pagina Facebook di test {#creating-a-test-facebook-page}

È consigliabile creare una pagina Facebook privata per la distribuzione delle bozze di pubblicazione (per ulteriori informazioni, consulta [Invio della bozza](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Accedi all’account Facebook che utilizzi per amministrare le pagine.
1. Crea una nuova pagina Facebook.
1. Fai clic sul pulsante **[!UICONTROL Settings]** nell’angolo in alto a destra.
1. Nella scheda **[!UICONTROL General]** , modifica i parametri di visibilità della pagina: selezionare la casella **[!UICONTROL Page unpublished]**.
1. Fai clic sul pulsante **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Creazione di un’app Facebook {#creating-a-facebook-application}

Affinché Adobe Campaign possa pubblicare sulle pareti delle pagine, devi creare un’applicazione Facebook. A questo scopo, esegui i seguenti passaggi:

1. Accedi all’account Facebook utilizzato per amministrare le pagine.
1. Inserisci il seguente indirizzo nel browser: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >A seconda del tipo di account in uso, potrebbe essere necessaria una o più autorizzazioni.
   >
   >Per creare un&#39;applicazione Facebook, è necessario un account Facebook **verificato**.

1. Fai clic sul pulsante **[!UICONTROL Add a New App]** nell’angolo in alto a destra della pagina. Immetti un nome app e un messaggio e-mail di contatto, quindi passa il controllo di sicurezza.

   ![](assets/social_create_facebook_app_002.png)

1. In **[!UICONTROL Settings > Basic]**, fai clic su **[!UICONTROL Add a platform]** e seleziona il tipo **[!UICONTROL Facebook Web Games]**.

   ![](assets/social_create_facebook_app_003.png)

1. Nella sezione **[!UICONTROL Products]**, nel menu a sinistra, controlla di visualizzare il prodotto **[!UICONTROL Facebook Login]**. In caso contrario, aggiungi un nuovo prodotto e seleziona **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Una volta creata l&#39;applicazione, seleziona la scheda **[!UICONTROL App Review]** e pubblica l&#39;applicazione.

   ![](assets/social_create_facebook_app_004.png)

## Delega dell&#39;accesso in scrittura ad Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Per delegare l’accesso in scrittura ad Adobe Campaign per la pubblicazione sulle pareti delle pagine, è necessario immettere i parametri dell’applicazione Facebook creata in precedenza.

Questo passaggio richiede l’accesso sia alla console Adobe Campaign che a un browser Internet connesso all’account Facebook che utilizzi per l’amministrazione delle pagine:

>[!IMPORTANT]
>
>Per eseguire questa configurazione, l’operatore Adobe Campaign deve disporre dei diritti di amministrazione.

* **Facebook**: seleziona l’applicazione creata in precedenza (  [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e seleziona la  **[!UICONTROL Settings > Basic]** scheda .

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Se la sezione **[!UICONTROL Facebook Web Games]** non viene visualizzata, fare clic sul pulsante **[!UICONTROL Add Platform]** nella parte inferiore della pagina e selezionare **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vai al  **[!UICONTROL Administration > Platform > External Accounts]** nodo della struttura, seleziona l’account  **[!UICONTROL Facebook routing]** esterno e fai clic sulla  **[!UICONTROL Connector]** scheda .

   ![](assets/social_facebook_external_account_001.png)

1. Nella console Adobe Campaign, copia l’indirizzo contenuto nel campo **[!UICONTROL Secure Canvas URL]** e incollalo nel campo **[!UICONTROL Secure Web Games URL (https)]** di Facebook (nella sezione **[!UICONTROL Facebook Web Games]** ).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Non devi utilizzare l’URL non protetto in nessun caso.

   Copia e incolla questo URL anche in **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Per verificare la validità dell’URL, salva l’applicazione, copia e incolla l’URL nel campo **[!UICONTROL Redirect URI to Check]** , quindi fai clic su **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. In Facebook, copia il contenuto dei campi **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e incollalo nei campi corrispondenti della console.

   ![](assets/social_facebook_external_account_007.png)

1. In Facebook, fai clic sul pulsante **[!UICONTROL Save Changes]** in fondo alla pagina.
1. Vai alla console Adobe Campaign e salva l’account esterno.

   >[!NOTE]
   >
   >Il campo **[!UICONTROL Marketing URL]** è facoltativo.

1. Nella console Adobe Campaign, fai clic sul collegamento **[!UICONTROL Request the authorization from the application]** nella parte inferiore della scheda **[!UICONTROL Connector]** . Il flusso di lavoro **[!UICONTROL Synchronize Facebook pages]** viene attivato automaticamente e raccoglie tutte le pagine Facebook gestite dall’amministratore. Per ulteriori informazioni, consulta [Sincronizzazione delle pagine Facebook](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, le pagine vengono aggiunte alla cartella del servizio **[!UICONTROL Facebook]**, disponibile tramite il nodo **[!UICONTROL Profiles and Targets > Services and Subscriptions]** . Il campo **[!UICONTROL Folder]** della scheda **[!UICONTROL Connector]** consente di modificare la cartella del servizio in cui vengono create le pagine Facebook dopo la sincronizzazione. Puoi anche selezionare le pagine Facebook da sincronizzare in Adobe Campaign grazie al campo **[!UICONTROL Filter]** . Se si lascia vuoto questo campo, verranno sincronizzate tutte le pagine Facebook gestite dall’amministratore.

1. Viene visualizzata una finestra di dialogo con le varie impostazioni di autorizzazione di Facebook. Questi consentono ad Adobe Campaign di inviare pubblicazioni alle pagine dell&#39;account Facebook.

   Accetta le varie richieste di autorizzazione.

   ![](assets/social_facebook_external_account_003.png)

1. Ad Adobe Campaign è stato dato il diritto di pubblicare sulle pareti delle pagine dell&#39;account Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Se l’account Facebook amministra diverse pagine, è sufficiente configurare un account esterno da scrivere su qualsiasi pagina dell’account Facebook. Per ogni nuovo account Facebook, dovrai creare un nuovo account esterno di tipo **[!UICONTROL Routing]**.

Il flusso di lavoro **[!UICONTROL Synchronization of Facebook pages]** sincronizza tutte le pagine amministrate dall’account Facebook, per consentirti di postare direttamente sulla loro parete tramite Adobe Campaign. Per ulteriori informazioni, consulta [Sincronizzazione delle pagine Facebook](#synchronizing-facebook-pages).

## Sincronizzazione delle pagine Facebook {#synchronizing-facebook-pages}

Il flusso di lavoro **[!UICONTROL Synchronization of Facebook pages]**, accessibile tramite il nodo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, consente di sincronizzare (in Adobe Campaign) le pagine dell’account Facebook configurato in precedenza. Per impostazione predefinita, questo flusso di lavoro è configurato per l’esecuzione una volta al giorno o ogni volta che un amministratore fa clic sul collegamento **[!UICONTROL Request an authorization from the application]** nella schermata di configurazione del servizio (consulta [Delega dell’accesso in scrittura ad Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Una volta completata la sincronizzazione, le pagine raccolte vengono visualizzate nella cartella del servizio inserita nell&#39;account esterno (consulta [Delega dell&#39;accesso in scrittura ad Adobe Campaign](#delegating-write-access-to-adobe-campaign)). Per impostazione predefinita, le pagine vengono aggiunte alla directory principale della cartella del servizio **[!UICONTROL Facebook]** disponibile tramite il menu **[!UICONTROL Profiles and Targets > Services and subscriptions]** .

![](assets/social_facebook_service_002.png)

Ora puoi pubblicare direttamente sulle pareti delle pagine Facebook tramite Adobe Campaign. Per ulteriori informazioni, consulta [Pubblicazione su Facebook](#publishing-on-facebook-walls).
