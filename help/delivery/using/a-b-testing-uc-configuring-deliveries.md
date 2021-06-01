---
product: campaign
title: Configurazione delle consegne
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 1%

---

# Configurazione delle consegne nel flusso di lavoro {#step-4--configuring-the-deliveries-in-the-workflow}

Il passaggio successivo consiste nel configurare le consegne. Sono destinati alle tre popolazioni create nel corso della fase precedente: [Passaggio 2: Configurazione dei campioni di popolazione](#step-2--configuring-population-samples). Le prime due consegne consentono di inviare contenuti diversi alla popolazione A e B. La terza consegna è destinata alla popolazione che non ha ricevuto né A né B. Il relativo contenuto verrà calcolato da uno script e sarà identico a A o B, a seconda di quale ha ottenuto il più alto tasso di apertura. È necessario configurare un periodo di attesa per la terza consegna per individuare il risultato delle consegne A e B. Per questo motivo la terza consegna include un’attività **[!UICONTROL Wait]**.

1. Vai all’ attività **[!UICONTROL Split]** e collega la transizione destinata alla popolazione A a una delle consegne e-mail già presenti nel flusso di lavoro.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Fai doppio clic sulla consegna per aprirla.
1. Utilizzando l’elenco a discesa, seleziona il modello per la consegna A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Fai clic su **[!UICONTROL Continue]** per visualizzare la consegna, quindi salvala.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Collega la transizione dell’ attività **[!UICONTROL Split]** destinata alla popolazione B alla seconda consegna e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Apri la consegna e seleziona il modello nella consegna B, quindi salva la consegna.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Collega la transizione destinata alla popolazione rimanente all’attività **[!UICONTROL Wait]** .

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Apri l’attività **[!UICONTROL Wait]** e configura un periodo di attesa di 5 giorni.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Collega l’attività **[!UICONTROL Wait]** all’attività **[!UICONTROL JavaScript code]** .

   ![](assets/use_case_abtesting_createdeliveries_008.png)

È ora possibile creare lo script (vedere [Passaggio 5: Crea lo script](../../delivery/using/a-b-testing-uc-script.md)).
