---
product: campaign
title: Offerte su un canale in entrata
description: Offerte su un canale in entrata
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 90afced3-465d-4370-8a33-51a7e4356135
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 0%

---

# Offerte su un canale in entrata{#offers-on-an-inbound-channel}

![](../../assets/v7-only.svg)

## Presentare un’offerta a un visitatore anonimo {#presenting-an-offer-to-an-anonymous-visitor}

Il sito Neobank vuole presentare un&#39;offerta sul proprio sito web rivolta ai visitatori non identificati che navigano nella pagina.

Per impostare questa interazione, eseguiremo le seguenti operazioni:

1. [Creare un ambiente anonimo](#creating-an-anonymous-environment)
1. [Creare spazi di offerta anonimi](#creating-anonymous-offer-spaces)
1. [Creare una categoria di offerta e un tema](#creating-an-offer-category-and-a-theme)
1. [Creare offerte anonime.](#creating-anonymous-offers)
1. [Configurare gli spazi di offerta web sul sito web](#configure-the-web-offer-space-on-the-website)

### Creazione di un ambiente anonimo {#creating-an-anonymous-environment}

Seguire la procedura descritta in [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment) per creare un ambiente anonimo basato su **Visitatori**&#39; dimensioni.

Verrà visualizzata una struttura ad albero contenente il nuovo ambiente:

![](assets/offer_env_anonymous_003.png)

### Creazione di spazi di offerta anonimi {#creating-anonymous-offer-spaces}

1. Nel tuo ambiente anonimo (**Visitatori**) vai alla pagina **[!UICONTROL Administration]** > **[!UICONTROL Spaces]** nodo.
1. Fai clic su **[!UICONTROL New]** per creare canali di chiamata.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >Lo spazio viene automaticamente collegato all&#39;ambiente anonimo.

1. Modifica l’etichetta e seleziona la **[!UICONTROL Inbound Web]** canale. Devi anche controllare il **[!UICONTROL Enable unitary mode]** scatola.

   ![](assets/offer_inbound_anonymous_example_006.png)

1. Seleziona i campi del contenuto dell’offerta utilizzati per lo spazio e specificali come richiesto selezionando la casella corrispondente.

   In questo modo, tutte le offerte mancanti con uno dei seguenti elementi non saranno idonee per questo spazio:

   * Titolo
   * Contenuto HTML
   * URL immagine
   * URL di destinazione

   ![](assets/offer_inbound_anonymous_example_030.png)

1. Modificare la funzione di rendering di HTML, ad esempio come segue:

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
   >La funzione di rendering deve denominare i campi utilizzati per lo spazio nell’ordine in cui erano stati precedentemente selezionati in modo che le offerte vengano visualizzate correttamente.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. Salva lo spazio dell’offerta.

### Creazione di una categoria di offerta e di un tema {#creating-an-offer-category-and-a-theme}

1. Vai a **[!UICONTROL Offer catalog]** nell’ambiente appena creato.
1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL Offer catalog]** nodo e seleziona **[!UICONTROL Create a new 'Offer category' folder]**.

   Denomina la nuova categoria, **Prodotti finanziari** ad esempio.

1. Vai alla categoria **[!UICONTROL Eligibility]** e immetti **finanziamento** come tema, quindi salva le modifiche.

   ![](assets/offer_inbound_anonymous_example_023.png)

### Creazione di offerte anonime {#creating-anonymous-offers}

1. Passa alla categoria appena creata.
1. Fai clic su **[!UICONTROL New]**.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. Seleziona il modello di offerta anonima predefinito o un modello creato in precedenza.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. Modifica l’etichetta e salva l’offerta.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. Vai a **[!UICONTROL Eligibility]** e specifica il peso delle offerte in base ai relativi contesti di applicazione.

   In questo esempio, l’offerta è configurata per essere visualizzata sulla home page del sito come priorità fino alla fine dell’anno.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. Vai a **[!UICONTROL Content]** e definisci il contenuto dell’offerta.

   >[!NOTE]
   >
   >È possibile selezionare **[!UICONTROL Content definitions]** per visualizzare l’elenco degli elementi necessari per lo spazio web.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. Crea una seconda offerta.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. Vai a **[!UICONTROL Eligibility]** e applica lo stesso peso della prima offerta.
1. Esegui il ciclo di approvazione per ogni offerta al fine di renderle disponibili nell’ambiente online, così come i relativi spazi di offerta approvati.

### Configurare lo spazio di offerta web sul sito web {#configure-the-web-offer-space-on-the-website}

Per rendere visibili le offerte appena configurate sul sito web, inserisci un codice JavaScript nella pagina HTML del sito per richiamare il motore di interazione (per ulteriori informazioni, consulta [Informazioni sui canali in entrata](../../interaction/using/about-inbound-channels.md)).

1. Vai alla pagina HTML e inserisci un attributo @id con un valore corrispondente al nome interno dello spazio di offerta anonimo creato in precedenza (consulta [Creazione di spazi di offerta anonimi](#creating-anonymous-offer-spaces)), preceduta da **i_**.

   ![](assets/offer_inbound_anonymous_example_019.png)

1. Inserisci l’URL della chiamata.

   ![](assets/offer_inbound_anonymous_example_020.png)

   Le caselle blu URL sopra corrispondono al nome dell’istanza, al nome interno dell’ambiente (consulta [Creazione di un ambiente anonimo](#creating-an-anonymous-environment)) e il tema collegato alla categoria ([Creazione di una categoria di offerta e di un tema](#creating-an-offer-category-and-a-theme)). Quest&#39;ultimo è facoltativo.

Quando un visitatore accede alla home page del sito web, le offerte con **finanziamento** Il tema viene visualizzato come configurato nella pagina di HTML.

![](assets/offer_inbound_anonymous_example_022.png)

Un utente che visita la pagina più volte visualizzerà una o le altre offerte nella categoria, in quanto a entrambe è stato assegnato lo stesso peso.

## Passaggio a un ambiente anonimo in caso di contatti non identificati {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

L&#39;azienda Neobank vorrebbe creare offerte di marketing per due obiettivi diversi. Vuole mostrare offerte generiche per i suoi browser web anonimi. Se uno di questi utenti risulta essere un cliente con gli identificatori forniti da Neobank, l’azienda desidera che riceva offerte personalizzate non appena effettua l’accesso.

Questo caso di studio si basa sul seguente scenario:

1. Un visitatore naviga nel sito web Neobank senza effettuare l’accesso.

   ![](assets/offer_inbound_fallback_example_050.png)

   Nella pagina vengono visualizzate tre offerte anonime: due **Offerta migliore** offerte per prodotti Neobank e un&#39;offerta da un partner Neobank.

   ![](assets/offer_inbound_fallback_example_051.png)

1. L&#39;utente, un cliente Neobank, accede con le proprie credenziali.

   ![](assets/offer_inbound_fallback_example_052.png)

   Vengono visualizzate tre offerte personalizzate.

   ![](assets/offer_inbound_fallback_example_053.png)

Per implementare questo case study, è necessario disporre di due ambienti di offerta: uno per le interazioni anonime e uno con le offerte configurate soprattutto per i contatti identificati. L’ambiente di offerta identificato sarà configurato in modo da passare automaticamente all’ambiente di offerta anonimo se il contatto non è connesso e quindi non è identificato.

Applica i seguenti passaggi:

* Crea un catalogo di offerte specifiche per le interazioni in entrata anonime seguendo i passaggi seguenti:

   1. [Creazione di un ambiente per i contatti anonimi](#creating-an-environment-for-anonymous-contacts)
   1. [Configurazione degli spazi di offerta per l’ambiente anonimo](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [Creazione di categorie di offerte in un ambiente anonimo](#creating-offer-categories-in-an-anonymous-environment)
   1. [Creazione di offerte per visitatori anonimi](#creating-offers-for-anonymous-visitors)

* Crea un catalogo di offerte specifiche per le interazioni in entrata identificate utilizzando i seguenti passaggi:

   1. [Configurare gli spazi di offerta nell’ambiente identificato](#configure-the-offer-spaces-in-the-identified-environment)
   1. [Creazione di categorie di offerta in un ambiente identificato](#creating-offer-categories-in-an-identified-environment)
   1. [Creazione di offerte personalizzate](#creating-personalized-offers)

* Configura la chiamata al motore di offerta:

   1. [Configurazione degli spazi di offerta nella pagina web](#configuring-offer-spaces-on-the-web-page)
   1. [Specifica delle impostazioni avanzate degli spazi di offerta identificati](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### Creazione di un ambiente per i contatti anonimi {#creating-an-environment-for-anonymous-contacts}

1. Crea un ambiente di offerta per interazioni in entrata anonime tramite la procedura guidata di mappatura della consegna (**Visitatore** mappatura). Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

   ![](assets/offer_env_anonymous_003.png)

### Configurazione degli spazi di offerta per l’ambiente anonimo {#configuring-offer-spaces-for-the-anonymous-environment}

Le offerte che devono essere presentate sul sito web appartengono a due diverse categorie: **Offerta migliore** e **Partner**. In questo esempio, creeremo uno spazio di offerta specifico per ogni categoria.

Per creare uno spazio di offerta corrispondente al **Offerta migliore** , applica il seguente processo:

1. Nell’albero di Adobe Campaign, accedi all’ambiente anonimo appena creato e aggiungi uno spazio di offerta.

   ![](assets/offer_inbound_fallback_example_023.png)

1. Crea un nuovo **[!UICONTROL Inbound web]** digitare space.

   ![](assets/offer_inbound_fallback_example_024.png)

1. Immetti un’etichetta per la tua destinazione: **Migliore offerta anonima sul web** per esempio.
1. Aggiungi i campi del contenuto dell’offerta utilizzati per questo spazio di offerta e configura le funzioni di rendering.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!IMPORTANT]
   >
   >La funzione di rendering deve denominare i campi utilizzati per lo spazio nell’ordine in cui erano stati precedentemente selezionati in modo che le offerte vengano visualizzate correttamente.

1. Utilizza lo stesso processo per creare uno spazio di offerta del canale web in entrata che corrisponda al **Partner** categoria.

   ![](assets/offer_inbound_fallback_example_026.png)

### Creazione di categorie di offerte in un ambiente anonimo {#creating-offer-categories-in-an-anonymous-environment}

Inizia creando due categorie di offerta: la **Offerta migliore** la categoria e **Partner** categoria. Ogni categoria conterrà due offerte per contatti anonimi.

1. Vai a **[!UICONTROL Offer catalog]** nell’ambiente anonimo appena creato.
1. Aggiungi un **[!UICONTROL Offer category]** cartella con **Offerta migliore** come etichetta.

   ![](assets/offer_inbound_fallback_example_027.png)

1. Crea una seconda categoria con **Partner** come etichetta.

   ![](assets/offer_inbound_fallback_example_028.png)

### Creazione di offerte per visitatori anonimi {#creating-offers-for-anonymous-visitors}

Ora creeremo due offerte in ciascuna delle categorie create sopra.

1. Vai a **Offerta migliore** e crea un’offerta anonima.

   ![](assets/offer_inbound_fallback_example_029.png)

1. Vai a **[!UICONTROL Eligibility]** e specifica il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_030.png)

1. Vai a **[!UICONTROL Content]** e definisci il contenuto dell’offerta.

   ![](assets/offer_inbound_fallback_example_032.png)

1. Crea una seconda offerta nel **Offerta migliore** categoria.

   ![](assets/offer_inbound_fallback_example_031.png)

1. Vai a **Partner** e crea un’offerta anonima.
1. Vai a **[!UICONTROL Content]** e definisci il contenuto dell’offerta.

   ![](assets/offer_inbound_fallback_example_033.png)

1. Vai a **[!UICONTROL Eligibility]** e specifica il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_034.png)

1. Crea una seconda offerta per **Partner** categoria.

   ![](assets/offer_inbound_fallback_example_035.png)

1. Vai a **[!UICONTROL Eligibility]** applica lo stesso peso applicato alla prima offerta in questa categoria in modo che le offerte vengano visualizzate successivamente sul sito web.

   ![](assets/offer_inbound_fallback_example_036.png)

1. Esegui il ciclo di approvazione per ogni offerta per iniziare a renderli live. Quando approvi il contenuto, attiva il **Partner** o **Offerta migliore** spazio di offerta, in base all&#39;offerta.

### Configurare gli spazi di offerta nell’ambiente identificato {#configure-the-offer-spaces-in-the-identified-environment}

Le offerte che presenterete sul sito web sono state prese da due diverse categorie: **Offerta migliore** e **Partner**. In questo esempio, vogliamo creare uno spazio specifico per ogni categoria.

Per creare i due spazi di offerta, applica la stessa procedura utilizzata per gli spazi di offerta anonimi. Fai riferimento a [Configurazione degli spazi di offerta per l’ambiente anonimo](#configuring-offer-spaces-for-the-anonymous-environment).

1. Nella struttura di Adobe Campaign, passa all’ambiente appena creato e aggiungi **Offerta migliore** e **Partner** offrono spazi.
1. Applica il processo descritto in [Configurazione degli spazi di offerta per l’ambiente anonimo](#configuring-offer-spaces-for-the-anonymous-environment).

   ![](assets/offer_inbound_fallback_example_005.png)

1. Seleziona la **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** opzione .

   ![](assets/offer_inbound_fallback_example_006.png)

1. Dall’elenco a discesa, seleziona lo spazio di offerta web anonimo creato in precedenza (consulta [Configurazione degli spazi di offerta per l’ambiente anonimo](#configuring-offer-spaces-for-the-anonymous-environment)).

   ![](assets/offer_inbound_fallback_example_007.png)

### Specifica delle impostazioni avanzate degli spazi di offerta identificati {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

In questo esempio, l’identificazione del contatto avviene grazie all’indirizzo e-mail nel database Adobe Campaign. Per aggiungere l’e-mail del destinatario allo spazio, applica il seguente processo:

1. Nell’ambiente identificato, passa alla cartella spazio offerta.
1. Seleziona la **Offerta migliore** spazio di offerta e fai clic su **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. Nella scheda **[!UICONTROL Target identification]**, fai clic su **[!UICONTROL Add]**.

   ![](assets/offer_inbound_fallback_example_046.png)

1. Fai clic su **[!UICONTROL Edit expression]**, vai alla tabella dei destinatari e seleziona il **[!UICONTROL Email]** campo .

   ![](assets/offer_inbound_fallback_example_047.png)

1. Fai clic su **[!UICONTROL OK]** per chiudere **[!UICONTROL Advanced parameters]** finestra e completamento della configurazione **Offerta migliore** spazio disponibile.
1. Applica lo stesso processo per il **Partner** spazio disponibile.

   ![](assets/offer_inbound_fallback_example_048.png)

### Creazione di categorie di offerta in un ambiente identificato {#creating-offer-categories-in-an-identified-environment}

Creeremo due categorie separate: la **Offerta migliore** la categoria e **Partner** categoria , ciascuna con due offerte personalizzate.

1. Vai a **[!UICONTROL Offer catalogs]** nell&#39;ambiente identificato.
1. Come nell’ambiente anonimo, aggiungi due **[!UICONTROL Offer category]** cartelle con **Offerta migliore** e **Partner** come etichette.

   ![](assets/offer_inbound_fallback_example_009.png)

### Creazione di offerte personalizzate {#creating-personalized-offers}

Vogliamo creare due offerte personalizzate per ogni categoria, ovvero quattro offerte.

1. Vai a **Offerta migliore** e crea una prima offerta personalizzata.

   ![](assets/offer_inbound_fallback_example_011.png)

1. Vai a **[!UICONTROL Eligibility]** e specifica il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_012.png)

1. Vai a **[!UICONTROL Content]** e definisci il contenuto dell’offerta.

   ![](assets/offer_inbound_fallback_example_013.png)

1. Crea una seconda offerta nel **Offerta migliore** categoria.

   ![](assets/offer_inbound_fallback_example_014.png)

1. Vai a **Partner** e crea un’offerta personalizzata.

   ![](assets/offer_inbound_fallback_example_015.png)

1. Vai a **[!UICONTROL Eligibility]** e specifica il peso delle offerte in base ai relativi contesti di applicazione.

   ![](assets/offer_inbound_fallback_example_016.png)

1. Crea una seconda offerta per **Partner** categoria.

   ![](assets/offer_inbound_fallback_example_017.png)

1. Vai a **[!UICONTROL Eligibility]** applica lo stesso peso applicato alla prima offerta in questa categoria in modo che le offerte vengano visualizzate successivamente sul sito web.
1. Esegui il ciclo di approvazione per ogni offerta per iniziare ad aggiornarli. Durante l’approvazione del contenuto, attiva il **Partner** o **Offerta migliore** offrono spazi.

### Configurazione degli spazi di offerta nella pagina web {#configuring-offer-spaces-on-the-web-page}

Il sito web della società Neobank ha tre spazi per le offerte: due per le offerte bancarie dalla **Offerta migliore** e una per le offerte dal **Partner** categoria.

![](assets/offer_inbound_fallback_example_038.png)

Per configurare questi spazi di offerta nella pagina HTML del sito web, applica la seguente procedura:

1. Inserisci tre contenuti nella pagina HTML

   elementi con un attributo @id il cui valore ci consentirà di richiamare le offerte nei vari spazi di offerta del sito web.

   ![](assets/offer_inbound_fallback_example_039.png)

1. Quindi inserisci lo script per la definizione dei valori di attributo.

   ![](assets/offer_inbound_fallback_example_040.png)

   In questo esempio, **ContBO1** e **ContBO2** ricevere il valore **OsWebBestOfferIdentified**, vale a dire il nome interno del **Offerta migliore** spazio di offerta creato in precedenza nell&#39;ambiente identificato. La **CatBestOffer** e **CatBestOfferAnonym** i valori corrispondono al nome interno del **Offerta migliore** categorie per ambienti anonimi e identificati.

   ![](assets/offer_inbound_fallback_example_041.png)

   Analogamente, **ContPtn** riceve **OSWebPartnerIdentified** che corrisponde al nome interno del **Partner** spazio di offerta creato nell&#39;ambiente identificato. **CatPartner** e **CatPartnerAnonym** corrisponde al nome interno del **Partner** categorie per ambienti anonimi e identificati.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Assegna le informazioni che ti consentiranno di identificare la persona che accede al sito Neobank al **actionTarget** variabile.

   ![](assets/offer_inbound_fallback_example_043.png)

   L’identificazione della persona può essere basata su un cookie del browser, un parametro di lettura nell’URL, nell’e-mail o nell’identificatore della persona. Se si utilizza un campo della tabella dei destinatari diverso dalla chiave primaria, è necessario definirlo nei parametri avanzati dello spazio (consulta [Specifica delle impostazioni avanzate degli spazi di offerta identificati](#specifying-the-advanced-settings-of-the-identified-offer-spaces)).

1. Inserisci l’URL della chiamata.

   ![](assets/offer_inbound_fallback_example_049.png)

   L’URL contiene **EnvNeobankRecip**, il nome interno dell&#39;ambiente identificato.

Quando si apre la pagina Web; lo script ti consente di richiamare il motore di interazione per visualizzare il contenuto delle offerte negli spazi rilevanti della pagina web. In una singola chiamata al server Adobe Campaign, il motore determina l’ambiente, lo spazio di offerta e le categorie da selezionare.

In questo esempio, il motore riconosce l’ambiente identificato (**EnvNeobankIdnRecip**). Identifica lo spazio di offerta (**OSWebBestOfferIdentified**) e **Offerta migliore** categoria (**CatBestOffer**) per il primo e il secondo spazio di offerta sulla pagina web, nonché il (**OSWebPartnerIdentified**) e **Partner** categoria (**CatPartner**) per il terzo spazio di offerta sul sito.

Se il motore non è in grado di identificare il destinatario, passa agli spazi di offerta anonimi a cui si fa riferimento negli spazi di offerta identificati e verso le categorie anonime (**CatPartner** e **CatPartnerAnonym**) come specificato nello script.
