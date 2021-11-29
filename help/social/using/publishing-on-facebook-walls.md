---
product: campaign
title: Pubblicare su bacheche Facebook
description: Pubblicare su bacheche Facebook
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 4%

---

# Pubblicare su bacheche Facebook{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

Affinché Adobe Campaign possa inviare pubblicazioni alle pareti Facebook, è necessario delegare l’accesso in scrittura per queste pagine ad Adobe Campaign. Sono previsti i seguenti passaggi di configurazione:

1. Crea un account Facebook con una o più pagine.
1. Crea una pagina Facebook di prova per l’invio di bozze.
1. Creare un’applicazione Facebook.
1. Immetti le impostazioni dell’applicazione Facebook in Adobe Campaign, nella **[!UICONTROL Facebook routing]** conto esterno.

## Prerequisiti {#prerequisites}

Inizia creando un account Facebook e diverse pagine: verranno utilizzati per l’invio di pubblicazioni.

* Per creare un account Facebook, utilizza le [https://www.facebook.com](https://www.facebook.com) link.
* Per creare una pagina Facebook, utilizza le [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) link.

   È consigliabile utilizzare lo stesso account Facebook per amministrare tutte le pagine. In questo modo, per scrivere su tutte le pagine dell’account sarà necessaria solo un’applicazione Facebook e un account esterno.

   ![](assets/social_diagram_fb_external_account.png)

## Creare una pagina Facebook di test {#creating-a-test-facebook-page}

È consigliabile creare una pagina Facebook privata per la distribuzione delle bozze di pubblicazione (per ulteriori informazioni, consulta [questa sezione](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Accedi all’account Facebook che utilizzi per amministrare le pagine.
1. Crea una nuova pagina Facebook.
1. Fai clic sul pulsante **[!UICONTROL Settings]** nell&#39;angolo in alto a destra.
1. In **[!UICONTROL General]** modifica i parametri di visibilità della pagina: controlla **[!UICONTROL Page unpublished]** scatola.
1. Fai clic sul pulsante **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Creare un’applicazione Facebook {#creating-a-facebook-application}

Affinché Adobe Campaign possa pubblicare sulle pareti delle pagine, devi creare un’applicazione Facebook. A questo scopo, esegui i seguenti passaggi:

1. Accedi all’account Facebook utilizzato per amministrare le pagine.
1. Inserisci il seguente indirizzo nel browser: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >A seconda del tipo di account in uso, potrebbe essere necessaria una o più autorizzazioni.
   >
   >Per creare un&#39;applicazione Facebook, è necessario un **verificato** Account facebook.

1. Fai clic sul pulsante **[!UICONTROL Add a New App]** nell’angolo in alto a destra della pagina. Immetti un nome app e un messaggio e-mail di contatto, quindi passa il controllo di sicurezza.

   ![](assets/social_create_facebook_app_002.png)

1. Sotto **[!UICONTROL Settings > Basic]**, fai clic su **[!UICONTROL Add a platform]** e seleziona la **[!UICONTROL Facebook Web Games]** digitare.

   ![](assets/social_create_facebook_app_003.png)

1. In **[!UICONTROL Products]** nel menu a sinistra, controlla di visualizzare il **[!UICONTROL Facebook Login]** prodotto. In caso contrario, aggiungi un nuovo prodotto e seleziona **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Una volta creata l&#39;applicazione, seleziona la **[!UICONTROL App Review]** e pubblica l&#39;applicazione.

   ![](assets/social_create_facebook_app_004.png)

## Delega dell’accesso in scrittura ad Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Per delegare l’accesso in scrittura ad Adobe Campaign per la pubblicazione sulle pareti delle pagine, è necessario immettere i parametri dell’applicazione Facebook creata in precedenza.

Questo passaggio richiede l’accesso sia alla console Adobe Campaign che a un browser Internet connesso all’account Facebook che utilizzi per l’amministrazione delle pagine:

>[!CAUTION]
>
>Per eseguire questa configurazione, l’operatore Adobe Campaign deve disporre dei diritti di amministrazione.

* **Facebook**: seleziona l&#39;applicazione creata in precedenza ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e seleziona la **[!UICONTROL Settings > Basic]** scheda .

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Se la **[!UICONTROL Facebook Web Games]** la sezione non viene visualizzata, fai clic sul pulsante **[!UICONTROL Add Platform]** nella parte inferiore della pagina e seleziona **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vai al **[!UICONTROL Administration > Platform > External Accounts]** nodo della struttura, selezionare il **[!UICONTROL Facebook routing]** account esterno e fai clic su **[!UICONTROL Connector]** scheda .

   ![](assets/social_facebook_external_account_001.png)

1. Nella console Adobe Campaign, copia l’indirizzo contenuto in **[!UICONTROL Secure Canvas URL]** e incollalo nel **[!UICONTROL Secure Web Games URL (https)]** in Facebook (nel **[!UICONTROL Facebook Web Games]** sezione).

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >Non devi utilizzare l’URL non protetto in nessun caso.

   Copia e incolla questo URL anche in **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Per verificare la validità dell’URL, salva l’applicazione, copia e incolla l’URL nel **[!UICONTROL Redirect URI to Check]** e fai clic su **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Su Facebook, copia il contenuto del **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e incollalo nei campi corrispondenti della console.

   ![](assets/social_facebook_external_account_007.png)

1. In Facebook, fai clic sul pulsante **[!UICONTROL Save Changes]** nella parte inferiore della pagina.
1. Vai alla console Adobe Campaign e salva l’account esterno.

   >[!NOTE]
   >
   >La **[!UICONTROL Marketing URL]** è facoltativo.

1. Nella console Adobe Campaign, fai clic sul pulsante **[!UICONTROL Request the authorization from the application]** link nella parte inferiore del **[!UICONTROL Connector]** scheda . La **[!UICONTROL Synchronize Facebook pages]** il flusso di lavoro viene attivato automaticamente e raccoglie tutte le pagine Facebook gestite dall’amministratore. [Ulteriori informazioni](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, le pagine vengono aggiunte al **[!UICONTROL Facebook]** cartella del servizio, disponibile tramite **[!UICONTROL Profiles and Targets > Services and Subscriptions]** nodo. La **[!UICONTROL Folder]** campo **[!UICONTROL Connector]** consente di modificare la cartella del servizio in cui vengono create le pagine Facebook dopo la sincronizzazione. Puoi anche selezionare le pagine Facebook da sincronizzare in Adobe Campaign grazie alla **[!UICONTROL Filter]** campo . Se si lascia vuoto questo campo, verranno sincronizzate tutte le pagine Facebook gestite dall’amministratore.

1. Viene visualizzata una finestra di dialogo con le varie impostazioni di autorizzazione di Facebook. Questi consentono ad Adobe Campaign di inviare pubblicazioni alle pagine dell&#39;account Facebook.

   Accetta le varie richieste di autorizzazione.

   ![](assets/social_facebook_external_account_003.png)

1. Ad Adobe Campaign è stato dato il diritto di pubblicare sulle pareti delle pagine dell&#39;account Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Se l’account Facebook amministra diverse pagine, è sufficiente configurare un account esterno da scrivere su qualsiasi pagina dell’account Facebook. Per ogni nuovo account Facebook, dovrai creare un nuovo **[!UICONTROL Routing]** digitare account esterno.

La **[!UICONTROL Synchronization of Facebook pages]** Il flusso di lavoro sincronizza tutte le pagine amministrate dall’account Facebook, per consentirti di pubblicare direttamente sul loro muro tramite Adobe Campaign. [Ulteriori informazioni](#synchronizing-facebook-pages).

## Sincronizzazione delle pagine Facebook {#synchronizing-facebook-pages}

La **[!UICONTROL Synchronization of Facebook pages]** , accessibile tramite il **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** node, consente di sincronizzare (in Adobe Campaign) le pagine dell’account Facebook configurate in precedenza. Per impostazione predefinita, questo flusso di lavoro è configurato per l’esecuzione una volta al giorno o ogni volta che un amministratore fa clic sul pulsante **[!UICONTROL Request an authorization from the application]** nella schermata di configurazione del servizio. [Ulteriori informazioni](#delegating-write-access-to-adobe-campaign).

Una volta completata la sincronizzazione, le pagine raccolte vengono visualizzate nella cartella del servizio immessa nell’account esterno. [Ulteriori informazioni](#delegating-write-access-to-adobe-campaign)).

Per impostazione predefinita, le pagine vengono aggiunte alla directory principale del **[!UICONTROL Facebook]** cartella del servizio disponibile tramite **[!UICONTROL Profiles and Targets > Services and subscriptions]** menu.

![](assets/social_facebook_service_002.png)

Ora puoi pubblicare direttamente sulle pareti delle pagine Facebook tramite Adobe Campaign. [Ulteriori informazioni](#publishing-on-facebook-walls).
