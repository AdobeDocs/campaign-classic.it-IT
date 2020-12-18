---
solution: Campaign Classic
product: campaign
title: Integrazione di un’offerta tramite la procedura guidata
description: Integrazione di un’offerta tramite la procedura guidata
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 2%

---


# Integrazione di un’offerta tramite la procedura guidata{#integrating-an-offer-via-the-wizard}

Durante la creazione di una consegna, sono disponibili due metodi per integrare le offerte:

* Chiamata del motore di offerta nel corpo di una consegna.
* Fare riferimento alle offerte tramite i contorni di distribuzione di una campagna. Questo metodo viene generalmente utilizzato per le campagne cartacee.

## Distribuzione con una chiamata al motore delle offerte {#delivering-with-a-call-to-the-offer-engine}

Per presentare un&#39;offerta durante una campagna di marketing, create semplicemente un&#39;azione di consegna classica basata sul canale scelto. Il motore delle offerte viene richiamato quando il contenuto della distribuzione è definito, facendo clic sull&#39;icona **[!UICONTROL Offers]** disponibile nella barra degli strumenti.

![](assets/offer_delivery_009.png)

Per ulteriori informazioni sulle consegne e le campagne di marketing, fare riferimento a [Consegna](../../delivery/using/about-direct-mail-channel.md) e [Campagna](../../campaign/using/setting-up-marketing-campaigns.md).

### Passaggi principali per l&#39;inserimento di un&#39;offerta in una consegna {#main-steps-for-inserting-an-offer-into-a-delivery}

Per inserire le proposte di offerta in una consegna, effettuate le seguenti operazioni:

1. Nella finestra di consegna, fate clic sull&#39;icona Offerte.

   ![](assets/offer_delivery_001.png)

1. Selezionate lo spazio che corrisponde all&#39;ambiente delle offerte.

   ![](assets/offer_delivery_002.png)

1. Per perfezionare la scelta delle offerte del motore, selezionare la categoria tra le quali presentare le offerte fa parte o uno o più temi. È consigliabile utilizzare solo uno di questi campi alla volta per evitare di sovraccaricare le restrizioni.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. Specificate il numero di offerte che desiderate inserire nel corpo della consegna.

   ![](assets/offer_delivery_005.png)

1. Se necessario, selezionare l&#39;opzione **[!UICONTROL Exclude non-eligible recipients]**. Per ulteriori informazioni, vedere [Parametri per la chiamata del motore di offerta](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. Se necessario, selezionare l&#39;opzione **[!UICONTROL Do not display anything if no offers are selected]**. Per ulteriori informazioni, vedere [Parametri per la chiamata del motore di offerta](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. Inserite le proprietà nel contenuto della distribuzione utilizzando i campi di unione. Il numero di proposte disponibili dipende dalla configurazione della chiamata al motore e il loro ordine dipende dalla priorità delle offerte.

   ![](assets/offer_delivery_008.png)

1. Completate i contenuti e inviate la distribuzione come al solito.

   ![](assets/offer_delivery_010.png)

### Parametri per il motore di offerta chiamante {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** : spazio dell&#39;ambiente delle offerte che deve essere selezionato per attivare il motore delle offerte.
* **[!UICONTROL Category]** : cartella specifica in cui vengono ordinate le offerte. Se non viene specificata alcuna categoria, tutte le offerte contenute nell&#39;ambiente verranno prese in considerazione dal motore delle offerte, a meno che non sia selezionato un tema.
* **[!UICONTROL Themes]** : parole chiave definite a monte nelle categorie. che fungono da filtro e consentono di definire meglio il numero di offerte da presentare selezionandole in una serie di categorie.
* **[!UICONTROL Number of propositions]** : numero di offerte restituite dal motore che possono essere inserite nel corpo di consegna. Se non vengono inseriti nel messaggio, le offerte verranno comunque generate, ma non presentate.
* **[!UICONTROL Exclude non-eligible recipients]** : Questa opzione consente di attivare o disattivare l&#39;esclusione dei destinatari per i quali non esistono abbastanza offerte idonee. Il numero di proposte ammissibili può essere inferiore al numero richiesto di proposte. Se questa casella è selezionata, i destinatari che non dispongono di un numero sufficiente di proposte verranno esclusi dalla consegna. Se non selezionate questa opzione, questi destinatari non verranno esclusi ma non avranno il numero di proposte richiesto.
* **[!UICONTROL Do not display anything if no offer is selected]** : questa opzione consente di scegliere come verrà elaborato il messaggio nel caso in cui una delle proposte non esista. Quando questa casella è selezionata, la rappresentazione della proposizione mancante non viene visualizzata e nel messaggio per la proposta non viene visualizzato alcun contenuto. Se la casella non è selezionata, il messaggio stesso viene annullato durante l&#39;invio e i destinatari non riceveranno più alcun messaggio.

### Inserimento di una proposta di offerta in una consegna {#inserting-an-offer-proposition-into-a-delivery}

La rappresentazione delle offerte da presentare è inserita nel corpo della consegna attraverso i campi di unione. Il numero di proposizioni è definito nei parametri della chiamata del motore di offerta.

La consegna può essere personalizzata utilizzando i campi dell&#39;offerta o, nel caso di un&#39;e-mail, le funzioni di rendering.

![](assets/offer_delivery_011.png)

## Distribuzione con i contorni di consegna {#delivering-with-delivery-outlines}

Potete anche presentare le offerte in una consegna utilizzando i contorni di consegna.

Per ulteriori informazioni sui contorni di consegna, consultare la guida [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Create una nuova campagna o accedete a una campagna esistente.
1. Accedete ai contorni della distribuzione tramite la scheda **[!UICONTROL Edit]** > **[!UICONTROL Documents]** della campagna.
1. Aggiungete una struttura, quindi inserite tutte le offerte al suo interno facendo clic con il pulsante destro del mouse sulla struttura e selezionando **[!UICONTROL New]** > **[!UICONTROL Offer]**, quindi salvate la campagna.

   ![](assets/int_compo_offre1.png)

1. Create una consegna a cui avete accesso (ad esempio, una consegna diretta per posta).
1. Quando modificate la consegna, fate clic su **[!UICONTROL Select a delivery outline]**.

   >[!NOTE]
   >
   >A seconda del tipo di consegna, questa opzione si trova nel menu **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** (ad esempio per le consegne tramite e-mail).

   ![](assets/int_compo_offre2.png)

1. Utilizzando il pulsante **[!UICONTROL Offers]**, potete quindi configurare lo spazio delle offerte e il numero di offerte da presentare nella consegna.

   ![](assets/int_compo_offre3.png)

1. Aggiungete le proposte nel corpo di distribuzione utilizzando i campi di personalizzazione (per ulteriori informazioni, consultate la sezione [Inserimento di una proposta di offerta in una sezione consegna](#inserting-an-offer-proposition-into-a-delivery)), o nel caso di una consegna diretta per posta, modificando il formato del file di estrazione.

   Le proposte verranno selezionate tra le offerte a cui viene fatto riferimento nel profilo di consegna.

   >[!NOTE]
   >
   >Le informazioni relative alle classificazioni e ai pesi delle offerte vengono salvate nella tabella delle offerte solo se queste vengono generate direttamente nella consegna.

