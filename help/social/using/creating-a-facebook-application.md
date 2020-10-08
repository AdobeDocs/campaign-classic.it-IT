---
title: Creazione di un’app Facebook
seo-title: Creazione di un’app Facebook
description: Creazione di un’app Facebook
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 1%

---


# Creazione di un’app Facebook{#creating-a-facebook-application}

Grazie alle applicazioni Web, Social Marketing consente di visualizzare contenuti personalizzati nelle applicazioni Facebook, semplificando l&#39;acquisizione di potenziali clienti tramite questo social network. Per ulteriori esempi di applicazioni Web di tipo Facebook, consultate [Esempi di app](../../social/using/examples-of-facebook-apps.md)Facebook.

>[!NOTE]
>
>È inoltre possibile integrare  Adobe Campaign con un&#39;applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare l&#39;applicazione Web  Adobe Campaign per acquisire i profili Facebook. Per ulteriori informazioni, consulta [Configurazione di account](#configuring-external-accounts)esterni.

![](assets/social_webapp_fb_000.png)

Effettuate le seguenti operazioni di configurazione:

1. Create una o più applicazioni Facebook. Per ulteriori informazioni, consulta: [Creazione di un’applicazione](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)Facebook.
1. Immettete i **[!UICONTROL terms of service]** collegamenti e i **[!UICONTROL Privacy policy]** collegamenti da visualizzare nella schermata di richiesta delle autorizzazioni di Facebook. Per ulteriori informazioni, consulta: [Inserimento dei collegamenti](#entering-the-terms-of-service-and-privacy-policy-links)alle Condizioni di servizio e all&#39;Informativa sulla privacy.
1. Per ogni applicazione Facebook, create un account esterno di tipo **[!UICONTROL Facebook Connect]** type. Per ulteriori informazioni, consulta: [Configurazione di account](#configuring-external-accounts)esterni.
1. Per ogni applicazione Facebook, create un’applicazione Web di tipo Facebook in  Adobe Campaign. Per ulteriori informazioni, consulta: [Creazione di un’applicazione](#creating-a-facebook-type-web-application)Web di tipo Facebook.
1. Configurate le applicazioni Facebook in modo che vengano visualizzate come schede sulla pagina Facebook. Per ulteriori informazioni, consulta: [Configurazione delle schede](#configuring-facebook-tabs)Facebook.

## Configurazione di account esterni {#configuring-external-accounts}

Per ogni applicazione Facebook, è necessario creare un account esterno di tipo **[!UICONTROL Facebook Connect]** type.

Questo passaggio richiede l’accesso sia alla console Adobe Campaign  che a un browser Internet connesso all’account Facebook che utilizzate per l’amministrazione delle pagine:

* **Facebook**: selezionate l&#39;applicazione creata in precedenza ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)), quindi selezionate la **[!UICONTROL Settings]** > **[!UICONTROL Basic]** scheda.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Se la **[!UICONTROL Facebook Web Games]** sezione non viene visualizzata, fate clic sul **[!UICONTROL Add Platform]** pulsante, nella parte inferiore della pagina, quindi selezionate **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: andare al **[!UICONTROL Administration > Platform > External accounts]** nodo della struttura ad albero e fare clic su **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Immettete un&#39;etichetta e un nome interno e selezionate il **[!UICONTROL Facebook Connect]** tipo.

   ![](assets/social_webapp_fb_006.png)

1. Selezionate una modalità di hosting per l&#39;applicazione: **[!UICONTROL hosted by a partner]** o **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Applicazione ospitata da un partner**

   È possibile integrare  Adobe Campaign con un&#39;applicazione Facebook sviluppata da un partner. In questo caso, non è necessario utilizzare le applicazioni Web Adobe Campaign  per acquisire i profili Facebook. Quando l&#39;utente Facebook installa l&#39;applicazione, viene generata una chiave (token di accesso). Il partner inoltra questo token di accesso a  Adobe Campaign chiamando un servizio Web.  Adobe Campaign utilizza quindi questo token per accedere al database di Facebook e raccogliere i dati condivisi dall&#39;utente tramite l&#39;applicazione.

   >[!NOTE]
   >
   >I parametri del servizio Web sono descritti nel file WSDL disponibile qui: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Per integrare l’applicazione di terze parti in  Adobe Campaign, è necessario copiare il contenuto dei campi **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** Facebook e incollarlo nei campi **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** nella console.

   ![](assets/social_facebook_external_account_013.png)

   **Applicazione ospitata da questa istanza**

   Se desiderate ospitare l&#39;applicazione in questa istanza (se non disponete di un&#39;applicazione di terze parti), dovete utilizzare le applicazioni Web Adobe Campaign  per acquisire i profili Facebook. Per ulteriori informazioni, consultate [Esempi di app](../../social/using/examples-of-facebook-apps.md)Facebook.

   Nella console Adobe Campaign , copiate l’indirizzo contenuto nel **[!UICONTROL Secure Canvas URL]** campo e incollatelo nel **[!UICONTROL Facebook Web games (https)]** campo su Facebook (nella **[!UICONTROL Facebook Web Games]** sezione).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >Non è necessario utilizzare l&#39;URL non sicuro in nessun caso.

   In Facebook, copiate il contenuto dei **[!UICONTROL App ID]** campi e **[!UICONTROL App Secret]** incollatelo nei campi **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** nella console.

   ![](assets/social_facebook_external_account_008.png)

1. Su Facebook, fate clic sul **[!UICONTROL Save Changes]** pulsante in fondo alla pagina.
1. Nella  console Adobe Campaign, fare clic sul **[!UICONTROL Subscribe]** pulsante per abilitare  Adobe Campaign a recuperare i dati in tempo reale ogni volta che una ventola effettua l&#39;accesso tramite questa applicazione. Per ulteriori informazioni, consulta: [Esempi di app](../../social/using/examples-of-facebook-apps.md)Facebook.

   ![](assets/social_webapp_fb_013.png)

## Inserimento dei collegamenti ai termini di servizio e all&#39;informativa sulla privacy {#entering-the-terms-of-service-and-privacy-policy-links}

È consigliabile aggiungere i **[!UICONTROL Terms of service]** collegamenti e **[!UICONTROL Privacy policy]** i collegamenti, da visualizzare nella schermata di richiesta delle autorizzazioni di Facebook.

![](assets/social_fb_terms_of_services_001.png)

Le fasi di configurazione sono le seguenti:

1. Inserite il seguente indirizzo: [https://developers.facebook.com/apps](https://developers.facebook.com/apps), quindi selezionate l’applicazione Facebook.
1. Selezionate la **[!UICONTROL Settings > Basic]** scheda e immettete i **[!UICONTROL Privacy Policy URL]** campi e **[!UICONTROL Terms of Service URL]** .

   ![](assets/social_fb_terms_of_services.png)

## Creazione di un’applicazione Web di tipo Facebook {#creating-a-facebook-type-web-application}

L’applicazione Adobe Campaign Facebook  consente di visualizzare contenuto personalizzato nell’applicazione Facebook. Per ogni applicazione Facebook, è necessario creare un&#39;applicazione Web in  Adobe Campaign. Per creare un’applicazione Web Facebook, effettuate le seguenti operazioni:

1. Vai all&#39; **[!UICONTROL Social networks]** universo, fai clic sul **[!UICONTROL Applications]** collegamento, poi sul **[!UICONTROL Create]** pulsante.

   ![](assets/social_webapp_001.png)

1. Selezionate un modello di applicazione Web Facebook dall’elenco e immettete l’etichetta.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, sono disponibili quattro modelli di applicazione Web per Facebook:
   >
   >* **[!UICONTROL New Facebook application]**: selezionate questo modello se desiderate iniziare da un’applicazione vuota.
   >* **[!UICONTROL Pre-entered form]**: Applicazione Facebook con un modulo e un pulsante di accesso Facebook che consente agli utenti di compilare automaticamente i campi del modulo utilizzando i dati del proprio profilo. Questo consente agli utenti di compilare il modulo più rapidamente e ai marchi di ottenere informazioni di qualità migliore.
   >* **[!UICONTROL "Canvas page" competition]**: Applicazione Facebook visualizzata sullo schermo per una migliore esperienza visiva per gli utenti.
   >* **[!UICONTROL "Page Tab" competition]**: Applicazione Facebook completamente integrata nelle schede delle marche.


1. Nel **[!UICONTROL Application]** campo, immettete l’account esterno collegato all’applicazione Facebook. Per ulteriori informazioni, consulta: [Configurazione di account](#configuring-external-accounts)esterni.

   ![](assets/social_webapp_005.png)

1. Selezionate la **[!UICONTROL Edit]** scheda, quindi modificate l&#39;applicazione Web. Per ulteriori informazioni, consulta: [Esempi di app](../../social/using/examples-of-facebook-apps.md)Facebook.

   ![](assets/social_webapp_003.png)

1. Una volta completata l&#39;applicazione Web, selezionate la **[!UICONTROL Dashboard]** scheda, quindi fate clic **[!UICONTROL Publish]** per pubblicare online.

   ![](assets/social_webapp_004.png)

## Configurazione delle schede Facebook {#configuring-facebook-tabs}

Potete configurare le applicazioni Facebook in modo che vengano visualizzate come schede sulla pagina Facebook. A questo scopo, eseguire i seguenti passaggi:

1. Selezionate l’applicazione Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)), quindi selezionate la **[!UICONTROL Settings > Basic]** scheda.

   ![](assets/social_webapp_fb_008.png)

1. Nella parte inferiore della pagina, fare clic sul **[!UICONTROL Add Platform]** pulsante e selezionare **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. Nel **[!UICONTROL Page Tab Name]** campo della **[!UICONTROL Page Tab]** sezione, immettete l’etichetta come desiderate venga visualizzata sulla pagina Facebook.

   ![](assets/social_webapp_fb_001.png)

1. Nel **[!UICONTROL Secure Page Tab URL]** campo, immettete l’URL pubblico dell’applicazione Web, accessibile tramite la **[!UICONTROL Dashboard]** scheda dell’applicazione Web. Per ulteriori informazioni sulla creazione di applicazioni Web di tipo Facebook, vedere [Creazione di un&#39;applicazione](#creating-a-facebook-type-web-application)Web di tipo Facebook.

   ![](assets/social_webapp_fb_002.png)

1. Sul **[!UICONTROL Dashboard]** sito dell&#39;applicazione Web, fare clic sul **[!UICONTROL Add a page tab]** collegamento.

   ![](assets/social_webapp_fb_0010.png)

1. Selezionate la pagina Facebook a cui desiderate aggiungere la scheda e fate clic su **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

