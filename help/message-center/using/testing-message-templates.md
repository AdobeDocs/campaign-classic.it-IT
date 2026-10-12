---
product: campaign
title: Testare modelli di messaggi transazionali
description: Scopri come gestire gli indirizzi di seed nei messaggi transazionali per visualizzarli in anteprima e testarli in Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%
---
# Testare modelli di messaggi transazionali {#testing-message-templates}

Una volta che il [modello di messaggio](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentazione di Campaign v8) è pronto, segui i passaggi seguenti per visualizzarlo in anteprima e testarlo.

Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per informazioni su come aggiungere indirizzi di seed, visualizzare in anteprima un messaggio transazionale e inviare una bozza, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## Dati di personalizzazione {#personalization-data}

È possibile utilizzare i dati nel modello del messaggio per testare la personalizzazione dei messaggi transazionali. Questa funzionalità viene utilizzata per generare un’anteprima o inviare una bozza. Puoi anche visualizzare il rendering del messaggio per vari provider di accesso a Internet. Per ulteriori informazioni, consulta [Rendering in entrata](../../delivery/using/inbox-rendering.md).

Lo scopo di questi dati è quello di testare i messaggi prima della loro consegna finale. Questi messaggi non coincidono con i dati effettivi da elaborare. Tuttavia, la struttura XML deve essere identica a quella dell’evento memorizzato nell’istanza di esecuzione, come illustrato di seguito:

![](assets/messagecenter_create_custo_006.png)

Queste informazioni ti consentono di personalizzare il contenuto dei messaggi utilizzando tag di personalizzazione (per ulteriori informazioni, consulta [Creare il contenuto del messaggio](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"} (documentazione di Campaign v8).

1. Seleziona il modello di messaggio transazionale.

1. Nel modello, fare clic sulla scheda **[!UICONTROL Seed addresses]**.

1. Nel contenuto dell&#39;evento, immettere le informazioni del test in formato XML.

   ![](assets/messagecenter_create_custo_001.png)

1. Fai clic su **[!UICONTROL Save]**.
