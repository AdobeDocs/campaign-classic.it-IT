---
product: campaign
title: Creazione di un’app Facebook
description: Creazione di un’app Facebook
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 5%

---

# Creare un’applicazione Facebook{#creating-a-facebook-application}

![](../../assets/v7-only.svg)

Utilizzando le applicazioni web, il modulo Campaign Social Marketing consente di visualizzare contenuti personalizzati nelle applicazioni Facebook, semplificando l’acquisizione di potenziali clienti tramite questo social media. Per ulteriori esempi di applicazioni web di tipo Facebook, consulta [questa pagina](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>Puoi anche integrare Adobe Campaign con un’applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare l’applicazione web Adobe Campaign per acquisire profili Facebook. [Ulteriori informazioni](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

I passaggi di configurazione sono:

1. Crea una o più applicazioni Facebook.
1. Inserisci il **[!UICONTROL terms of service]** e **[!UICONTROL Privacy policy]** collegamenti da visualizzare nella schermata di richiesta delle autorizzazioni di Facebook. [Ulteriori informazioni](#entering-the-terms-of-service-and-privacy-policy-links)
1. Per ogni applicazione Facebook, crea un **[!UICONTROL Facebook Connect]** digitare account esterno. [Ulteriori informazioni](#configuring-external-accounts)
1. Per ogni applicazione Facebook, crea un&#39;applicazione Web di tipo Facebook in Adobe Campaign. [Ulteriori informazioni](#creating-a-facebook-type-web-application)
1. Configura le applicazioni Facebook in modo che vengano visualizzate come schede nella pagina Facebook. [Ulteriori informazioni](#configuring-facebook-tabs)

## Configurare account esterni {#configuring-external-accounts}

Per ogni applicazione Facebook, è necessario creare un **[!UICONTROL Facebook Connect]** digitare account esterno.

Questo passaggio richiede l’accesso alla console Adobe Campaign e all’account amministratore Facebook:

* On **Facebook**: seleziona l&#39;applicazione creata in precedenza ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e seleziona la **[!UICONTROL Settings]** > **[!UICONTROL Basic]** scheda .

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Se la **[!UICONTROL Facebook Web Games]** la sezione non viene visualizzata, fai clic sul pulsante **[!UICONTROL Add Platform]** nella parte inferiore della pagina e seleziona **[!UICONTROL Facebook Web Games]**.

* On **Adobe Campaign**: naviga a **[!UICONTROL Administration > Platform > External accounts]** e fai clic su **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Immetti un’etichetta e un nome interno, quindi seleziona la **[!UICONTROL Facebook Connect]** digitare.

   ![](assets/social_webapp_fb_006.png)

1. Seleziona la modalità di hosting dell&#39;applicazione: **[!UICONTROL hosted by a partner]** o **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Applicazione ospitata da un partner**

   È possibile integrare Adobe Campaign con un’applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare le applicazioni web Adobe Campaign per acquisire profili Facebook. Quando l’utente Facebook installa l’applicazione, viene generata una chiave (token di accesso). Il partner inoltra questo token di accesso ad Adobe Campaign richiamando un servizio Web. Adobe Campaign utilizza quindi questo token per accedere al database Facebook e raccogliere i dati condivisi dall’utente tramite l’applicazione.

   >[!NOTE]
   >
   >I parametri del servizio Web sono descritti nel file WSDL disponibile qui: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Per integrare l’applicazione di terze parti in Adobe Campaign, devi copiare il contenuto della **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** Campi facebook e incollarli nel **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** campi della console.

   ![](assets/social_facebook_external_account_013.png)

   **Applicazione ospitata da questa istanza**

   Se desideri ospitare l’applicazione in questa istanza (se non disponi di un’applicazione di terze parti), devi utilizzare le applicazioni web Adobe Campaign per acquisire i profili Facebook. Per ulteriori informazioni, consulta [questa pagina](../../social/using/examples-of-facebook-apps.md).

   Nella console Adobe Campaign, copia l’indirizzo contenuto in **[!UICONTROL Secure Canvas URL]** e incollalo nel **[!UICONTROL Facebook Web games (https)]** in Facebook (nel **[!UICONTROL Facebook Web Games]** sezione).

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >Non utilizzare URL non sicuri.

   Su Facebook, copia il contenuto del **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e incollalo nel **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** nella console.

   ![](assets/social_facebook_external_account_008.png)

1. In Facebook, fai clic sul pulsante **[!UICONTROL Save Changes]** nella parte inferiore della pagina.
1. Nella console Adobe Campaign, fai clic sul pulsante **[!UICONTROL Subscribe]** per consentire ad Adobe Campaign di recuperare i dati in tempo reale ogni volta che una ventola effettua l’accesso tramite questa applicazione.  [Ulteriori informazioni](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_fb_013.png)

## Inserisci i collegamenti alle Condizioni del servizio e all’informativa sulla privacy {#entering-the-terms-of-service-and-privacy-policy-links}

È vivamente consigliato aggiungere **[!UICONTROL Terms of service]** e **[!UICONTROL Privacy policy]** , da visualizzare nella schermata di richiesta delle autorizzazioni di Facebook.

![](assets/social_fb_terms_of_services_001.png)

Le fasi di configurazione sono le seguenti:

1. Inserisci il seguente indirizzo: [https://developers.facebook.com/apps](https://developers.facebook.com/apps), quindi seleziona l’applicazione Facebook.
1. Seleziona la **[!UICONTROL Settings > Basic]** e immetti **[!UICONTROL Privacy Policy URL]** e **[!UICONTROL Terms of Service URL]** campi.

   ![](assets/social_fb_terms_of_services.png)

## Creare un’applicazione Web di tipo Facebook {#creating-a-facebook-type-web-application}

L’applicazione Adobe Campaign Facebook consente di visualizzare contenuto personalizzato nell’applicazione Facebook. Per ogni applicazione Facebook, devi creare un’applicazione web in Adobe Campaign. Per creare un&#39;applicazione Web Facebook, procedere come segue:

1. Vai a **[!UICONTROL Social networks]** fai clic sulla scheda **[!UICONTROL Applications]** link, quindi il **[!UICONTROL Create]** pulsante .

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


1. In **[!UICONTROL Application]** , immetti l’account esterno collegato all’applicazione Facebook. [Ulteriori informazioni](#configuring-external-accounts)

   ![](assets/social_webapp_005.png)

1. Seleziona la **[!UICONTROL Edit]** , quindi modifica l&#39;applicazione Web. [Ulteriori informazioni](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_003.png)

1. Una volta completata l&#39;applicazione web, seleziona la **[!UICONTROL Dashboard]** scheda , quindi fai clic su **[!UICONTROL Publish]** per pubblicare online.

   ![](assets/social_webapp_004.png)

## Configurare le schede Facebook {#configuring-facebook-tabs}

Puoi configurare le applicazioni Facebook in modo che vengano visualizzate come schede nella pagina Facebook. A questo scopo, esegui i seguenti passaggi:

1. Seleziona l’applicazione Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e seleziona la **[!UICONTROL Settings > Basic]** scheda .

   ![](assets/social_webapp_fb_008.png)

1. Nella parte inferiore della pagina, fai clic sul pulsante **[!UICONTROL Add Platform]** e seleziona **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. In **[!UICONTROL Page Tab Name]** campo **[!UICONTROL Page Tab]** , immetti l’etichetta come desideri che appaia nella pagina Facebook.

   ![](assets/social_webapp_fb_001.png)

1. In **[!UICONTROL Secure Page Tab URL]** , immetti l’URL pubblico dell’applicazione web, accessibile tramite il **[!UICONTROL Dashboard]** scheda dell&#39;applicazione web. Per ulteriori informazioni sulla creazione di applicazioni web di tipo Facebook, consulta [questa sezione](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. Sulla **[!UICONTROL Dashboard]** dell&#39;applicazione web, fai clic sul pulsante **[!UICONTROL Add a page tab]** link.

   ![](assets/social_webapp_fb_0010.png)

1. Seleziona la pagina Facebook a cui desideri aggiungere la scheda e fai clic su **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)
