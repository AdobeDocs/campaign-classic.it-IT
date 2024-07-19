---
product: campaign
title: Configurare le consegne
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Test AB: configurare le consegne nel flusso di lavoro {#step-4--configuring-the-deliveries-in-the-workflow}

Una volta create [le popolazioni](a-b-testing-uc-population-samples.md), puoi configurare le consegne. In questo caso d’uso, le prime due consegne ti consentono di inviare contenuti diversi alla popolazione A e B. La terza consegna è la consegna di riserva: verrà inviata ai destinatari che non appartengono ad A né a B. Il suo contenuto verrà calcolato da uno script e sarà identico ad A o B, a seconda di quale ha ottenuto il punteggio più alto per il tasso di apertura. È necessario configurare un periodo di attesa per la terza consegna, per scoprire il risultato delle consegne A e B. Per questo motivo la terza consegna include un&#39;attività **[!UICONTROL Wait]**.

1. Vai all&#39;attività **[!UICONTROL Split]** e collega la transizione destinata alla popolazione A a una delle consegne e-mail già nel flusso di lavoro.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Fai doppio clic sulla consegna per aprirla.
1. Utilizzando l’elenco a discesa, seleziona il modello per la consegna A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Fai clic su **[!UICONTROL Continue]** per visualizzare la consegna, quindi salvala.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Collega la transizione dell&#39;attività **[!UICONTROL Split]** destinata alla popolazione B alla seconda consegna e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Apri la consegna e seleziona il modello nella consegna B, quindi salva la consegna.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Collega all&#39;attività **[!UICONTROL Wait]** la transizione destinata al gruppo rimanente.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Apri l&#39;attività **[!UICONTROL Wait]** e configura un periodo di attesa di 5 giorni.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Collega l&#39;attività **[!UICONTROL Wait]** all&#39;attività **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Ora puoi creare lo script. [Ulteriori informazioni](a-b-testing-uc-script.md).
