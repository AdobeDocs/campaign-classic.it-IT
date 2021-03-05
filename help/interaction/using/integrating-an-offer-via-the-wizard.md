---
solution: Campaign Classic
product: campaign
title: Integrazione di un’offerta tramite la procedura guidata
description: Integrazione di un’offerta tramite la procedura guidata
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 2%

---


# Integrazione di un’offerta tramite la procedura guidata{#integrating-an-offer-via-the-wizard}

Durante la creazione di una consegna, esistono due metodi possibili per integrare le offerte:

* Chiamata del motore di offerta nel corpo di una consegna.
* Riferimento alle offerte tramite i profili di consegna di una campagna. Questo metodo viene generalmente utilizzato per le campagne su carta.

## Consegna con una chiamata al motore di offerta {#delivering-with-a-call-to-the-offer-engine}

Per presentare un’offerta durante una campagna di marketing, è sufficiente creare un’azione di consegna classica in base al canale scelto. Il motore di offerta viene richiamato quando viene definito il contenuto della consegna, facendo clic sull’ icona **[!UICONTROL Offers]** disponibile nella barra degli strumenti.

![](assets/offer_delivery_009.png)

Ulteriori informazioni sulle consegne di direct mailing [in questa sezione](../../delivery/using/about-direct-mail-channel.md). Ulteriori informazioni sulle campagne di marketing [in questa sezione](../../campaign/using/setting-up-marketing-campaigns.md).

### Passaggi principali per l’inserimento di un’offerta in una consegna {#main-steps-for-inserting-an-offer-into-a-delivery}

Per inserire le proposte di offerta in una consegna, esegui i seguenti passaggi:

1. Nella finestra di consegna, fai clic sull’icona Offerte .

   ![](assets/offer_delivery_001.png)

1. Seleziona lo spazio che corrisponde all’ambiente delle offerte.

   ![](assets/offer_delivery_002.png)

1. Per perfezionare la scelta delle offerte da parte del motore, seleziona la categoria in cui le offerte da presentare fanno parte o uno o più temi. È consigliabile utilizzare solo uno di questi campi alla volta per evitare di sovraccaricare le restrizioni.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. Specifica il numero di offerte da inserire nel corpo della consegna.

   ![](assets/offer_delivery_005.png)

1. Se necessario, seleziona l’opzione **[!UICONTROL Exclude non-eligible recipients]** . Per ulteriori informazioni, consulta [Parametri per la chiamata al motore di offerta](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. Se necessario, seleziona l’opzione **[!UICONTROL Do not display anything if no offers are selected]** . Per ulteriori informazioni, consulta [Parametri per la chiamata al motore di offerta](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. Inserire le proprietà nel contenuto della consegna utilizzando i campi di unione. Il numero di proposte disponibili dipende dalla configurazione della chiamata del motore e dal loro ordine dipende dalla priorità delle offerte.

   ![](assets/offer_delivery_008.png)

1. Completare il contenuto e inviare la consegna come di consueto.

   ![](assets/offer_delivery_010.png)

### Parametri per la chiamata del motore di offerta {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** : spazio dell’ambiente dell’offerta che deve essere selezionato per attivare il motore di offerta.
* **[!UICONTROL Category]** : cartella specifica in cui vengono ordinate le offerte. Se non viene specificata alcuna categoria, tutte le offerte contenute nell’ambiente verranno prese in considerazione dal motore di offerta, a meno che non venga selezionato un tema.
* **[!UICONTROL Themes]** : parole chiave definite a monte nelle categorie. Questi fungono da filtro e consentono di perfezionare il numero di offerte da presentare selezionandole in un set di categorie.
* **[!UICONTROL Number of propositions]** : numero di offerte restituite dal motore che possono essere inserite nel corpo della consegna. Se non vengono inserite nel messaggio, le offerte verranno comunque generate ma non presentate.
* **[!UICONTROL Exclude non-eligible recipients]** : Questa opzione ti consente di attivare o disattivare l’esclusione dei destinatari per i quali non sono disponibili sufficienti offerte idonee. Il numero di proposte ammissibili può essere inferiore al numero di proposte richieste. Se questa casella è selezionata, i destinatari che non hanno abbastanza proposte verranno esclusi dalla consegna. Se non selezioni questa opzione, questi destinatari non verranno esclusi ma non avranno il numero di proposte richiesto.
* **[!UICONTROL Do not display anything if no offer is selected]** : questa opzione ti consente di scegliere come verrà elaborato il messaggio nel caso in cui una delle proposte non esista. Quando questa casella è selezionata, la rappresentazione della proposta mancante non viene visualizzata e nel messaggio per la proposta non verrà visualizzato alcun contenuto. Se la casella non è selezionata, il messaggio stesso viene annullato durante l’invio e i destinatari non riceveranno più messaggi.

### Inserimento di una proposta di offerta in una consegna {#inserting-an-offer-proposition-into-a-delivery}

La rappresentazione delle offerte da presentare viene inserita nel corpo della consegna tramite i campi di unione. Il numero di proposte è definito nei parametri della chiamata al motore di offerta.

La consegna può essere personalizzata utilizzando i campi dell’offerta o, nel caso di un’e-mail, le funzioni di rendering.

![](assets/offer_delivery_011.png)

## Distribuzione con profili di consegna {#delivering-with-delivery-outlines}

Puoi anche presentare offerte in una consegna utilizzando i contorni di consegna.

Per ulteriori informazioni sui profili di consegna, consulta la guida [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) .

1. Crea una nuova campagna o accedi a una campagna esistente.
1. Accedi ai profili di consegna tramite la scheda **[!UICONTROL Edit]** > **[!UICONTROL Documents]** della campagna.
1. Aggiungi una struttura e inserisci tutte le offerte che desideri al suo interno facendo clic con il pulsante destro del mouse sulla struttura e selezionando **[!UICONTROL New]** > **[!UICONTROL Offer]**, quindi salva la campagna.

   ![](assets/int_compo_offre1.png)

1. Crea una consegna a cui hai accesso (ad esempio, una consegna direct mailing).
1. Durante la modifica della consegna, fai clic su **[!UICONTROL Select a delivery outline]**.

   >[!NOTE]
   >
   >A seconda del tipo di consegna, questa opzione si trova nel menu **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** (ad esempio, per le consegne e-mail).

   ![](assets/int_compo_offre2.png)

1. Utilizzando il pulsante **[!UICONTROL Offers]** puoi quindi configurare lo spazio di offerta e il numero di offerte da presentare nella consegna.

   ![](assets/int_compo_offre3.png)

1. Aggiungi le proposte nel corpo della consegna utilizzando i campi di personalizzazione (per ulteriori informazioni, consulta la sezione [Inserimento di una proposta di offerta in una consegna](#inserting-an-offer-proposition-into-a-delivery) ) oppure, nel caso di una consegna direct mailing, modificando il formato del file di estrazione.

   Le proposte verranno selezionate tra le offerte a cui si fa riferimento nel profilo di consegna.

   >[!NOTE]
   >
   >Le informazioni relative alla classificazione e ai pesi delle offerte vengono salvate nella tabella delle proposte solo se queste vengono generate direttamente nella consegna.

