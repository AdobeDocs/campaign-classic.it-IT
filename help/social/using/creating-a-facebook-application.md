---
product: campaign
title: Creazione di un’app Facebook
description: Creazione di un’app Facebook
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---

# Creazione di un’app Facebook{#creating-a-facebook-application}

Grazie alle applicazioni web, Social Marketing consente di visualizzare contenuti personalizzati nelle applicazioni Facebook, facilitando l&#39;acquisizione di potenziali clienti tramite questo social network. Per ulteriori esempi di applicazioni web di tipo Facebook, consulta [Esempi di app Facebook](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>È inoltre possibile integrare Adobe Campaign con un’applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare l’applicazione web Adobe Campaign per acquisire profili Facebook. Per ulteriori informazioni, consulta [Configurazione di account esterni](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Applica i seguenti passaggi di configurazione:

1. Crea una o più applicazioni Facebook. Per ulteriori informazioni, consulta: [Creazione di un&#39;applicazione Facebook](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).
1. Immetti i collegamenti **[!UICONTROL terms of service]** e **[!UICONTROL Privacy policy]** da visualizzare nella schermata di richiesta delle autorizzazioni di Facebook. Per ulteriori informazioni, consulta: [Inserimento dei termini del servizio e dei collegamenti all&#39;informativa sulla privacy](#entering-the-terms-of-service-and-privacy-policy-links).
1. Per ogni applicazione Facebook, crea un account esterno di tipo **[!UICONTROL Facebook Connect]**. Per ulteriori informazioni, consulta: [Configurazione di account esterni](#configuring-external-accounts).
1. Per ogni applicazione Facebook, crea un&#39;applicazione Web di tipo Facebook in Adobe Campaign. Per ulteriori informazioni, consulta: [Creazione di un&#39;applicazione Web di tipo Facebook](#creating-a-facebook-type-web-application).
1. Configura le applicazioni Facebook in modo che vengano visualizzate come schede nella pagina Facebook. Per ulteriori informazioni, consulta: [Configurazione delle schede Facebook](#configuring-facebook-tabs).

## Configurazione di account esterni {#configuring-external-accounts}

Per ogni applicazione Facebook, devi creare un account esterno di tipo **[!UICONTROL Facebook Connect]**.

Questo passaggio richiede l’accesso sia alla console Adobe Campaign che a un browser Internet connesso all’account Facebook che utilizzi per l’amministrazione delle pagine:

* **Facebook**: seleziona l’applicazione creata in precedenza (  [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e seleziona la scheda  **[!UICONTROL Settings]** >  **[!UICONTROL Basic]** .

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Se la sezione **[!UICONTROL Facebook Web Games]** non viene visualizzata, fare clic sul pulsante **[!UICONTROL Add Platform]** nella parte inferiore della pagina e selezionare **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vai al  **[!UICONTROL Administration > Platform > External accounts]** nodo della struttura ad albero e fai clic su  **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Immetti un’etichetta e un nome interno e seleziona il tipo **[!UICONTROL Facebook Connect]** .

   ![](assets/social_webapp_fb_006.png)

1. Seleziona una modalità di hosting per l&#39;applicazione: **[!UICONTROL hosted by a partner]** o **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Applicazione ospitata da un partner**

   È possibile integrare Adobe Campaign con un’applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare le applicazioni web Adobe Campaign per acquisire profili Facebook. Quando l’utente Facebook installa l’applicazione, viene generata una chiave (token di accesso). Il partner inoltra questo token di accesso ad Adobe Campaign richiamando un servizio Web. Adobe Campaign utilizza quindi questo token per accedere al database Facebook e raccogliere i dati condivisi dall’utente tramite l’applicazione.

   >[!NOTE]
   >
   >I parametri del servizio Web sono descritti nel file WSDL disponibile qui: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Per integrare l’applicazione di terze parti in Adobe Campaign, è necessario copiare il contenuto dei campi **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** Facebook e incollarlo nei campi **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** della console.

   ![](assets/social_facebook_external_account_013.png)

   **Applicazione ospitata da questa istanza**

   Se desideri ospitare l’applicazione in questa istanza (se non disponi di un’applicazione di terze parti), devi utilizzare le applicazioni web Adobe Campaign per acquisire i profili Facebook. Per ulteriori informazioni, consulta [Esempi di app Facebook](../../social/using/examples-of-facebook-apps.md).

   Nella console Adobe Campaign, copia l’indirizzo contenuto nel campo **[!UICONTROL Secure Canvas URL]** e incollalo nel campo **[!UICONTROL Facebook Web games (https)]** di Facebook (nella sezione **[!UICONTROL Facebook Web Games]** ).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >Non devi utilizzare l’URL non protetto in nessun caso.

   In Facebook, copia il contenuto dei campi **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e incollalo nei campi **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** della console.

   ![](assets/social_facebook_external_account_008.png)

1. In Facebook, fai clic sul pulsante **[!UICONTROL Save Changes]** in fondo alla pagina.
1. Nella console Adobe Campaign, fai clic sul pulsante **[!UICONTROL Subscribe]** per consentire ad Adobe Campaign di recuperare i dati in tempo reale ogni volta che una ventola effettua l’accesso tramite questa applicazione. Per ulteriori informazioni, consulta: [Esempi di app Facebook](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_fb_013.png)

## Inserimento dei termini del servizio e dei collegamenti all’informativa sulla privacy {#entering-the-terms-of-service-and-privacy-policy-links}

Si consiglia vivamente di aggiungere i collegamenti **[!UICONTROL Terms of service]** e **[!UICONTROL Privacy policy]** per visualizzarli nella schermata di richiesta delle autorizzazioni di Facebook.

![](assets/social_fb_terms_of_services_001.png)

Le fasi di configurazione sono le seguenti:

1. Inserisci il seguente indirizzo: [https://developers.facebook.com/apps](https://developers.facebook.com/apps), quindi seleziona l&#39;applicazione Facebook.
1. Seleziona la scheda **[!UICONTROL Settings > Basic]** e immetti i campi **[!UICONTROL Privacy Policy URL]** e **[!UICONTROL Terms of Service URL]** .

   ![](assets/social_fb_terms_of_services.png)

## Creazione di un&#39;applicazione Web di tipo Facebook {#creating-a-facebook-type-web-application}

L’applicazione Adobe Campaign Facebook consente di visualizzare contenuto personalizzato nell’applicazione Facebook. Per ogni applicazione Facebook, devi creare un’applicazione web in Adobe Campaign. Per creare un&#39;applicazione Web Facebook, procedere come segue:

1. Vai alla scheda **[!UICONTROL Social networks]** , fai clic sul collegamento **[!UICONTROL Applications]** , quindi sul pulsante **[!UICONTROL Create]** .

   ![](assets/social_webapp_001.png)

1. Seleziona un modello di applicazione web Facebook dall’elenco e immetti l’etichetta .

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Per impostazione predefinita sono disponibili quattro modelli di applicazione Web Facebook:
   >
   >* **[!UICONTROL New Facebook application]**: selezionare questo modello se si desidera iniziare da un&#39;applicazione vuota.
   >* **[!UICONTROL Pre-entered form]**: Applicazione facebook con un modulo e un pulsante &quot;Accesso Facebook&quot; che consente agli utenti di compilare automaticamente i campi del modulo utilizzando i dati del proprio profilo. Questo consente agli utenti di completare il modulo più rapidamente e ai marchi di ottenere informazioni di migliore qualità.
   >* **[!UICONTROL "Canvas page" competition]**: Applicazione facebook visualizzata sullo schermo per una migliore esperienza visiva per gli utenti.
   >* **[!UICONTROL "Page Tab" competition]**: Applicazione facebook completamente integrata nelle schede della pagina del brand.


1. Nel campo **[!UICONTROL Application]** , immetti l’account esterno collegato all’applicazione Facebook. Per ulteriori informazioni, consulta: [Configurazione di account esterni](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Seleziona la scheda **[!UICONTROL Edit]** , quindi modifica l’applicazione web. Per ulteriori informazioni, consulta: [Esempi di app Facebook](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_003.png)

1. Una volta completata l&#39;applicazione Web, seleziona la scheda **[!UICONTROL Dashboard]** , quindi fai clic su **[!UICONTROL Publish]** per pubblicare online.

   ![](assets/social_webapp_004.png)

## Configurazione delle schede Facebook {#configuring-facebook-tabs}

Puoi configurare le applicazioni Facebook in modo che vengano visualizzate come schede nella pagina Facebook. A questo scopo, esegui i seguenti passaggi:

1. Selezionare l&#39;applicazione Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selezionare la scheda **[!UICONTROL Settings > Basic]**.

   ![](assets/social_webapp_fb_008.png)

1. Nella parte inferiore della pagina fare clic sul pulsante **[!UICONTROL Add Platform]** e selezionare **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. Nel campo **[!UICONTROL Page Tab Name]** della sezione **[!UICONTROL Page Tab]** , immetti l’etichetta come desideri che appaia nella pagina Facebook.

   ![](assets/social_webapp_fb_001.png)

1. Nel campo **[!UICONTROL Secure Page Tab URL]** , immetti l’URL pubblico dell’applicazione web, accessibile tramite la scheda **[!UICONTROL Dashboard]** dell’applicazione web. Per ulteriori informazioni sulla creazione di applicazioni web di tipo Facebook, consulta [Creazione di un&#39;applicazione web di tipo Facebook](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. Fare clic sul collegamento **[!UICONTROL Dashboard]** dell&#39;applicazione Web.**[!UICONTROL Add a page tab]**

   ![](assets/social_webapp_fb_0010.png)

1. Seleziona la pagina Facebook a cui desideri aggiungere la scheda e fai clic su **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)
