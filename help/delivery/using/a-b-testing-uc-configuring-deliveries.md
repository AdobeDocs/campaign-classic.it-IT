---
solution: Campaign Classic
product: campaign
title: Configurazione delle consegne
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Configurazione delle consegne nel flusso di lavoro {#step-4--configuring-the-deliveries-in-the-workflow}

Il passo successivo consiste nel configurare le consegne. Sono destinati alle tre popolazioni create nella fase precedente: [Passaggio 2: Configurazione dei campioni popolazione](#step-2--configuring-population-samples). Le prime due consegne consentono di inviare contenuti diversi alla popolazione A e B. La terza consegna è destinata alla popolazione che non ha ricevuto né A né B. Il contenuto verrà calcolato da uno script e sarà identico a A o B, a seconda di quale dei due avrà ottenuto il punteggio più alto. Dobbiamo configurare un periodo di attesa per la terza consegna, per conoscere il risultato delle consegne A e B. Questo è il motivo per cui il terzo invio include un&#39;attività **[!UICONTROL Wait]**.

1. Andate all&#39;attività **[!UICONTROL Split]** e collegate la transizione per la popolazione A a una delle consegne di e-mail già presenti nel flusso di lavoro.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Fate doppio clic sulla consegna per aprirla.
1. Utilizzando l&#39;elenco a discesa, selezionate il modello per la consegna A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Fare clic su **[!UICONTROL Continue]** per visualizzare la consegna, quindi salvarla.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Collegate la transizione dell&#39;attività **[!UICONTROL Split]** destinata alla popolazione B alla seconda consegna tramite e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Aprite la consegna e selezionate il modello nella consegna B, quindi salvate la consegna.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Collegare la transizione destinata alla popolazione rimanente all&#39;attività **[!UICONTROL Wait]**.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Aprite l&#39;attività **[!UICONTROL Wait]** e configurate un periodo di attesa di 5 giorni.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Collegate l&#39;attività **[!UICONTROL Wait]** all&#39;attività **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)
