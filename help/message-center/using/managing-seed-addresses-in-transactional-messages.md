---
solution: Campaign Classic
product: campaign
title: Gestione degli indirizzi di seed nei messaggi transazionali
description: Gestione degli indirizzi di seed nei messaggi transazionali
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 11%

---


# Gestione degli indirizzi di seed nei messaggi transazionali{#managing-seed-addresses-in-transactional-messages}

L&#39;indirizzo seed consente di visualizzare un&#39;anteprima del messaggio, inviare una prova e testare la personalizzazione dei messaggi prima dell&#39;invio tramite e-mail o SMS. Gli indirizzi dei semi sono collegati alla consegna e non possono essere utilizzati per altre consegne.

## Creazione di indirizzi di seed {#creating-a-seed-address}

1. In the transactional message template, click the **[!UICONTROL Seed addresses]** tab.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Assegnate un’etichetta per facilitarne la selezione in un secondo momento.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Inserite l’indirizzo e-mail (e-mail o telefono cellulare a seconda del canale di comunicazione).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Immettere l&#39;identificatore esterno: questo campo facoltativo consente di inserire una chiave aziendale (ID univoco, nome + e-mail, ecc.) comune a tutte le applicazioni presenti sul sito Web, utilizzate per identificare i profili. Se questo campo è presente anche nel  database di marketing di Adobe Campaign, potete quindi riconciliare un evento con un profilo presente nel database.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Inserire i dati di prova (fare riferimento a Dati [di](../../message-center/using/personalization-data.md)personalizzazione).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Fate clic sul **[!UICONTROL Add other seed addresses]** collegamento, quindi fate clic sul **[!UICONTROL Add]** pulsante.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Ripetete il processo per creare tutti gli indirizzi necessari.

   ![](assets/messagecenter_create_seedaddr_008.png)

Una volta creati gli indirizzi, potete visualizzarne l’anteprima e la personalizzazione. Consultare [Anteprima](../../message-center/using/transactional-message-preview.md)messaggi transazionali.
