---
title: Offerte su un canale in entrata
seo-title: Offerte su un canale in entrata
description: Offerte su un canale in entrata
seo-description: null
page-status-flag: never-activated
uuid: 45cfc990-da38-451b-b65e-e9703e443a4d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 63245348-0402-4929-9c4f-71f01f97758e
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '2093'
ht-degree: 1%

---


# Offerte su un canale in entrata{#offers-on-an-inbound-channel}

## Presentazione di un&#39;offerta a un visitatore anonimo {#presenting-an-offer-to-an-anonymous-visitor}

Il sito Neobank vuole visualizzare un&#39;offerta sul suo sito Web rivolta ai visitatori non identificati che navigano nella pagina.

Per impostare questa interazione, stiamo per:

1. [Creare un ambiente anonimo](#creating-an-anonymous-environment)
1. [Creare spazi di offerta anonimi](#creating-anonymous-offer-spaces)
1. [Creare una categoria di offerte e un tema](#creating-an-offer-category-and-a-theme)
1. [Creare offerte anonime.](#creating-anonymous-offers)
1. [Configurare gli spazi di offerta Web nel sito Web](#configure-the-web-offer-space-on-the-website)

### Creazione di un ambiente anonimo {#creating-an-anonymous-environment}

Seguite la procedura descritta in [Creazione di un ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment) di offerte per creare un ambiente anonimo basato sulle dimensioni dei **visitatori**.

Verrà visualizzata una struttura ad albero contenente il nuovo ambiente:

![](assets/offer_env_anonymous_003.png)

### Creazione di spazi di offerta anonimi {#creating-anonymous-offer-spaces}

1. Nell’ambiente anonimo (**Visitatori**), passa al nodo **[!UICONTROL Administration]** > **[!UICONTROL Spaces]** .
1. Fai clic **[!UICONTROL New]** per creare canali di chiamata.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >Lo spazio viene collegato automaticamente all&#39;ambiente anonimo.

1. Modificate l’etichetta e selezionate il **[!UICONTROL Inbound Web]** canale. Dovete anche controllare la **[!UICONTROL Enable unitary mode]** casella.

   ![](assets/offer_inbound_anonymous_example_006.png)

1. Selezionate i campi di contenuto dell&#39;offerta utilizzati per lo spazio e specificateli come richiesto selezionando la casella corrispondente.

   In questo modo, eventuali offerte mancanti tra i seguenti elementi non saranno ammissibili per questo spazio:

   * Titolo
   * Contenuto HTML
   * URL immagine
   * URL di destinazione

   ![](assets/offer_inbound_anonymous_example_030.png)

1. Modificate la funzione di rendering HTML, ad esempio come segue:

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!IMPORTANT]
   >
   >La funzione di rendering deve denominare i campi utilizzati per lo spazio nell&#39;ordine in cui erano stati selezionati in precedenza, in modo che le offerte vengano visualizzate correttamente.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. Salvate lo spazio dell’offerta.

### Creazione di una categoria di offerte e di un tema {#creating-an-offer-category-and-a-theme}

1. Andate al **[!UICONTROL Offer catalog]** nodo all&#39;interno dell&#39;ambiente appena creato.
1. Fare clic con il pulsante destro del mouse sul **[!UICONTROL Offer catalog]** nodo e selezionare **[!UICONTROL Create a new 'Offer category' folder]**.

   Denominate la nuova categoria, ad esempio prodotti **finanziari** .

1. Vai alla **[!UICONTROL Eligibility]** scheda della categoria e inserisci il **finanziamento** come tema, quindi salva le modifiche.

   ![](assets/offer_inbound_anonymous_example_023.png)

### Creazione di offerte anonime {#creating-anonymous-offers}

1. Passate alla categoria appena creata.
1. Fai clic su **[!UICONTROL New]**.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. Selezionate il modello di offerta anonimo predefinito o un modello creato in precedenza.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. Modificate l’etichetta e salvate l’offerta.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e specificate il peso delle offerte in base ai relativi contesti di applicazione.

   In questo esempio, l&#39;offerta è configurata per essere visualizzata sulla home page del sito come priorità fino alla fine dell&#39;anno.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. Passate alla **[!UICONTROL Content]** scheda e definite il contenuto dell&#39;offerta.

   >[!NOTE]
   >
   >È possibile selezionare **[!UICONTROL Content definitions]** per visualizzare l&#39;elenco degli elementi richiesti per lo spazio Web.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. Create una seconda offerta.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e applicate lo stesso peso della prima offerta.
1. Eseguite il ciclo di approvazione per ogni offerta al fine di renderle disponibili nell&#39;ambiente online, così come i loro spazi di offerta approvati.

### Configurare lo spazio delle offerte Web nel sito Web {#configure-the-web-offer-space-on-the-website}

Per rendere le offerte configurate visibili sul sito Web, inserite un codice JavaScript nella pagina HTML del sito per richiamare il motore di interazione (per ulteriori informazioni, consultate [Informazioni sui canali](../../interaction/using/about-inbound-channels.md)in ingresso).

1. Passate alla pagina HTML e inserite un attributo @id con un valore corrispondente al nome interno dello spazio delle offerte anonimo creato in precedenza (consultate [Creazione di spazi](#creating-anonymous-offer-spaces)delle offerte anonimi), preceduto da **i_**.

   ![](assets/offer_inbound_anonymous_example_019.png)

1. Inserite l’URL della chiamata.

   ![](assets/offer_inbound_anonymous_example_020.png)

   Le caselle blu dell’URL sopra corrispondono al nome dell’istanza, al nome interno dell’ambiente (consultate [Creazione di un ambiente](#creating-an-anonymous-environment)anonimo) e al tema collegato alla categoria ([Creazione di una categoria di offerte e di un tema](#creating-an-offer-category-and-a-theme)). Il secondo è facoltativo.

Quando un visitatore accede alla home page del sito Web, le offerte con il tema di **finanziamento** vengono visualizzate come configurate sulla pagina HTML.

![](assets/offer_inbound_anonymous_example_022.png)

Un utente che visita più volte la pagina visualizzerà una o le altre offerte della categoria, in quanto a entrambe è stato assegnato lo stesso peso.

## Passaggio a un ambiente anonimo in caso di contatti non identificati {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

La società Neobank vorrebbe creare offerte di marketing per due target diversi. Vuole visualizzare offerte generiche per i suoi browser anonimi del sito web. Se uno di questi utenti risultasse essere un cliente con identificatori forniti da Neobank, l&#39;azienda vorrebbe che ricevessero offerte personalizzate non appena accedono.

Questo caso di studio si basa sul seguente scenario:

1. Un visitatore visita il sito Web di Neobank senza effettuare l’accesso.

   ![](assets/offer_inbound_fallback_example_050.png)

   Sulla pagina vengono visualizzate tre offerte anonime: due offerte **Best Offer** per i prodotti Neobank e una per Neobank.

   ![](assets/offer_inbound_fallback_example_051.png)

1. L&#39;utente, un cliente Neobank, accede con le sue credenziali.

   ![](assets/offer_inbound_fallback_example_052.png)

   Vengono visualizzate tre offerte personalizzate.

   ![](assets/offer_inbound_fallback_example_053.png)

Per implementare questo case study, è necessario disporre di due ambienti di offerta: uno per le interazioni anonime e uno con offerte configurate soprattutto per i contatti identificati. L&#39;ambiente delle offerte identificato sarà configurato per passare automaticamente all&#39;ambiente delle offerte anonimo se il contatto non è connesso e quindi non è identificato.

Effettuate le seguenti operazioni:

* Create un catalogo di offerte specifiche per le interazioni anonime in ingresso, utilizzando i seguenti passaggi:

   1. [Creazione di un ambiente per i contatti anonimi](#creating-an-environment-for-anonymous-contacts)
   1. [Configurazione degli spazi di offerta per l&#39;ambiente anonimo](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [Creazione di categorie di offerte in un ambiente anonimo](#creating-offer-categories-in-an-anonymous-environment)
   1. [Creazione di offerte per i visitatori anonimi](#creating-offers-for-anonymous-visitors)

* Create un catalogo di offerte specifiche per le interazioni in entrata identificate utilizzando i seguenti passaggi:

   1. [Configurare gli spazi di offerta nell&#39;ambiente identificato](#configure-the-offer-spaces-in-the-identified-environment)
   1. [Creazione di categorie di offerte in un ambiente identificato](#creating-offer-categories-in-an-identified-environment)
   1. [Creazione di offerte personalizzate](#creating-personalized-offers)

* Configura la chiamata al motore di offerte:

   1. [Configurazione degli spazi di offerta sulla pagina Web](#configuring-offer-spaces-on-the-web-page)
   1. [Specifica delle impostazioni avanzate degli spazi di offerta identificati](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### Creazione di un ambiente per i contatti anonimi {#creating-an-environment-for-anonymous-contacts}

1. Crea un ambiente di offerte per interazioni anonime in ingresso tramite la procedura guidata di mappatura della consegna (mappatura **visitatori** ). Per ulteriori informazioni, consultate [Creazione di un ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)di offerte.

   ![](assets/offer_env_anonymous_003.png)

### Configurazione degli spazi di offerta per l&#39;ambiente anonimo {#configuring-offer-spaces-for-the-anonymous-environment}

Le offerte che devono essere presentate sul sito web appartengono a due diverse categorie: **Migliore offerta** e **partner**. In questo esempio, creeremo uno spazio di offerta specifico per ciascuna categoria.

Per creare uno spazio di offerta che corrisponda alla categoria **Migliore offerta** , effettuate le seguenti operazioni:

1. Nella struttura  di Adobe Campaign, andate all’ambiente anonimo appena creato e aggiungete uno spazio per le offerte.

   ![](assets/offer_inbound_fallback_example_023.png)

1. Creare un nuovo spazio **[!UICONTROL Inbound web]** del tipo.

   ![](assets/offer_inbound_fallback_example_024.png)

1. Immettete un’etichetta: **Migliore offerta** anonima Web, per esempio.
1. Aggiungete i campi del contenuto dell&#39;offerta utilizzati per questo spazio e configurate le funzioni di rendering.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!IMPORTANT]
   >
   >La funzione di rendering deve denominare i campi utilizzati per lo spazio nell&#39;ordine in cui erano stati selezionati in precedenza, in modo che le offerte vengano visualizzate correttamente.

1. Utilizzate lo stesso processo per creare uno spazio di offerta per i canali Web in entrata che corrisponda alla categoria **Partner** .

   ![](assets/offer_inbound_fallback_example_026.png)

### Creazione di categorie di offerte in un ambiente anonimo {#creating-offer-categories-in-an-anonymous-environment}

Iniziate creando due categorie di offerte: la categoria **Migliore offerta** e la categoria **Partner** . Ogni categoria conterrà due offerte per contatti anonimi.

1. Andate all&#39; **[!UICONTROL Offer catalog]** ambiente anonimo che avete appena creato.
1. Aggiungete una **[!UICONTROL Offer category]** cartella con l’etichetta **Migliore offerta** .

   ![](assets/offer_inbound_fallback_example_027.png)

1. Crea una seconda categoria con **Partner** come etichetta.

   ![](assets/offer_inbound_fallback_example_028.png)

### Creazione di offerte per i visitatori anonimi {#creating-offers-for-anonymous-visitors}

Ora creeremo due offerte in ciascuna delle categorie create sopra.

1. Passate alla categoria **Migliore offerta** e create un&#39;offerta anonima.

   ![](assets/offer_inbound_fallback_example_029.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e specificate il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_030.png)

1. Passate alla **[!UICONTROL Content]** scheda e definite il contenuto dell&#39;offerta.

   ![](assets/offer_inbound_fallback_example_032.png)

1. Create una seconda offerta nella categoria **Migliore offerta** .

   ![](assets/offer_inbound_fallback_example_031.png)

1. Andate alla categoria **Partner** e create un&#39;offerta anonima.
1. Passate alla **[!UICONTROL Content]** scheda e definite il contenuto dell&#39;offerta.

   ![](assets/offer_inbound_fallback_example_033.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e specificate il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_034.png)

1. Crea una seconda offerta per la categoria **Partner** .

   ![](assets/offer_inbound_fallback_example_035.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e applicate lo stesso peso applicato alla prima offerta in questa categoria in modo che le offerte vengano visualizzate successivamente sul sito Web.

   ![](assets/offer_inbound_fallback_example_036.png)

1. Eseguite il ciclo di approvazione per ogni offerta per iniziare a renderle attive. Quando approvi il contenuto, attiva lo spazio di offerta **Partner** o **Migliore offerta** , in base all&#39;offerta.

### Configurare gli spazi di offerta nell&#39;ambiente identificato {#configure-the-offer-spaces-in-the-identified-environment}

Le offerte che state per presentare sul sito web sono prese da due diverse categorie: **Migliore offerta** e **partner**. In questo esempio, vogliamo creare uno spazio specifico per ciascuna categoria.

Per creare i due spazi di offerta, applicate la stessa procedura utilizzata per gli spazi di offerta anonimi. Consultate [Configurazione degli spazi di offerta per l’ambiente](#configuring-offer-spaces-for-the-anonymous-environment)anonimo.

1. Nella struttura  di Adobe Campaign, andate all&#39;ambiente appena creato e aggiungete gli spazi **Migliore offerta** e **Partner** .
1. Applicate il processo descritto in [Configurazione degli spazi di offerta per l&#39;ambiente](#configuring-offer-spaces-for-the-anonymous-environment)anonimo.

   ![](assets/offer_inbound_fallback_example_005.png)

1. Selezionate l’ **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** opzione.

   ![](assets/offer_inbound_fallback_example_006.png)

1. Dall’elenco a discesa, selezionate lo spazio delle offerte Web anonimo creato in precedenza (consultate [Configurazione degli spazi delle offerte per l’ambiente](#configuring-offer-spaces-for-the-anonymous-environment)anonimo).

   ![](assets/offer_inbound_fallback_example_007.png)

### Specifica delle impostazioni avanzate degli spazi di offerta identificati {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

In questo esempio, l&#39;identificazione dei contatti avviene grazie all&#39;indirizzo e-mail nel database Adobe Campaign . Per aggiungere l&#39;e-mail del destinatario allo spazio, eseguire la procedura seguente:

1. Nell’ambiente identificato, andate alla cartella dello spazio delle offerte.
1. Selezionate lo spazio **Migliore offerta** e fate clic su **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. Nella scheda **[!UICONTROL Target identification]**, fai clic su **[!UICONTROL Add]**.

   ![](assets/offer_inbound_fallback_example_046.png)

1. Fare clic **[!UICONTROL Edit expression]**, passare alla tabella dei destinatari e selezionare il **[!UICONTROL Email]** campo.

   ![](assets/offer_inbound_fallback_example_047.png)

1. Fate clic **[!UICONTROL OK]** per chiudere la **[!UICONTROL Advanced parameters]** finestra e completare la configurazione dello spazio **Migliore offerta** .
1. Applicate lo stesso processo allo spazio di offerta **Partner** .

   ![](assets/offer_inbound_fallback_example_048.png)

### Creazione di categorie di offerte in un ambiente identificato {#creating-offer-categories-in-an-identified-environment}

Verranno create due categorie separate: la categoria **Migliore offerta** e la categoria **Partner** , ciascuna con due offerte personalizzate.

1. Passare al **[!UICONTROL Offer catalogs]** nodo nell&#39;ambiente identificato.
1. Come nell&#39;ambiente anonimo, aggiungete due **[!UICONTROL Offer category]** cartelle con le etichette **Migliore offerta** e **Partner** .

   ![](assets/offer_inbound_fallback_example_009.png)

### Creazione di offerte personalizzate {#creating-personalized-offers}

Vogliamo creare due offerte personalizzate per ciascuna categoria, ossia quattro offerte.

1. Passate alla categoria **Migliore offerta** e create una prima offerta personalizzata.

   ![](assets/offer_inbound_fallback_example_011.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e specificate il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_012.png)

1. Passate alla **[!UICONTROL Content]** scheda e definite il contenuto dell&#39;offerta.

   ![](assets/offer_inbound_fallback_example_013.png)

1. Create una seconda offerta nella categoria **Migliore offerta** .

   ![](assets/offer_inbound_fallback_example_014.png)

1. Andate alla categoria **Partner** e create un&#39;offerta personalizzata.

   ![](assets/offer_inbound_fallback_example_015.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e specificate il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_016.png)

1. Crea una seconda offerta per la categoria **Partner** .

   ![](assets/offer_inbound_fallback_example_017.png)

1. Passate alla **[!UICONTROL Eligibility]** scheda e applicate lo stesso peso applicato alla prima offerta in questa categoria in modo che le offerte vengano visualizzate successivamente sul sito Web.
1. Eseguite il ciclo di approvazione per ogni offerta per iniziare ad aggiornarli. Durante l&#39;approvazione del contenuto, attivate gli spazi di offerta **Partner** o **Migliore offerta** .

### Configurazione degli spazi di offerta sulla pagina Web {#configuring-offer-spaces-on-the-web-page}

Il sito web della società Neobank ha tre spazi per le offerte: due per le offerte relative alla banca dalla categoria **Migliore offerta** e uno per le offerte dalla categoria **Partner** .

![](assets/offer_inbound_fallback_example_038.png)

Per configurare questi spazi di offerta sulla pagina HTML del sito Web, effettuate le seguenti operazioni:

1. Nel contenuto della pagina HTML, inseritene tre

   elementi con un attributo @id il cui valore ci consentirà di richiamare le offerte nei vari spazi di offerta del sito Web.

   ![](assets/offer_inbound_fallback_example_039.png)

1. Inserire quindi lo script per la definizione dei valori degli attributi.

   ![](assets/offer_inbound_fallback_example_040.png)

   In questo esempio, **ContBO1** e **ContBO2** ricevono il valore **OsWebBestOfferIdentified**, ovvero il nome interno dello spazio delle offerte **Best Offer** creato in precedenza nell&#39;ambiente identificato. I valori **CatBestOffer** e **CatBestOfferAnonym** corrispondono al nome interno delle categorie **Best Offer** per gli ambienti anonimi e identificati.

   ![](assets/offer_inbound_fallback_example_041.png)

   Analogamente, **ContPtn** riceve il valore **OSWebPartnerIdentified** , che corrisponde al nome interno dello spazio di offerta **Partner** creato nell&#39;ambiente identificato. **CatPartner** e **CatPartnerAnonym** corrispondono al nome interno delle categorie **Partner** per gli ambienti anonimi e identificati.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Assegnate le informazioni che vi consentiranno di identificare la persona che accede al sito Neobank sulla variabile **interactiveTarget** .

   ![](assets/offer_inbound_fallback_example_043.png)

   L&#39;identificazione della persona può essere basata su un cookie del browser, un parametro di lettura nell&#39;URL, nell&#39;e-mail o nell&#39;identificatore della persona. Se si utilizza un campo della tabella ricevente diverso dalla chiave primaria, è necessario definirlo nei parametri avanzati dello spazio (vedere [Specifica delle impostazioni avanzate degli spazi](#specifying-the-advanced-settings-of-the-identified-offer-spaces)di offerta identificati).

1. Inserite l’URL della chiamata.

   ![](assets/offer_inbound_fallback_example_049.png)

   L’URL contiene **EnvNeobankRecip**, il nome interno dell’ambiente identificato.

Quando si apre la pagina Web; lo script consente di richiamare il motore di interazione per visualizzare il contenuto delle offerte negli spazi pertinenti della pagina Web. In una singola chiamata al server Adobe Campaign , il motore determina l&#39;ambiente, lo spazio di offerta e le categorie da selezionare.

In questo esempio, il motore riconosce l&#39;ambiente identificato (**EnvNeobankIdnRecip**). Identifica lo spazio di offerta (**OSWebBestOfferIdentified**) e la categoria **Migliore offerta** (**CatBestOffer**) per il primo e il secondo spazio di offerta sulla pagina Web, nonché lo spazio di offerta (**OSWebPartnerIdentified**) e la categoria **Partner** (PAPACatPartner ****) per il terzo) offre spazio sul sito.

Se il motore non riesce a identificare il destinatario, passa agli spazi di offerta anonimi a cui fanno riferimento gli spazi di offerta identificati e verso le categorie anonime (**CatPartner** e **CatPartnerAnonym**) come specificato nello script.
