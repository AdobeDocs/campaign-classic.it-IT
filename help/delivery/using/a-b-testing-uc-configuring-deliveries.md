---
product: campaign
title: Configurare le consegne
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 1%

---

# Test AB: configurare le consegne nel flusso di lavoro {#step-4--configuring-the-deliveries-in-the-workflow}

Una volta [le popolazioni vengono create](a-b-testing-uc-population-samples.md), puoi configurare le consegne. In questo caso d’uso, le prime due consegne ti consentono di inviare contenuti diversi alla popolazione A e B. La terza consegna è la consegna di riserva: verrà inviata ai destinatari che non appartengono ad A né a B. Il suo contenuto verrà calcolato da uno script e sarà identico ad A o B, a seconda di quale ha ottenuto il punteggio più alto per il tasso di apertura. È necessario configurare un periodo di attesa per la terza consegna, per scoprire il risultato delle consegne A e B. Ecco perché la terza consegna include una **[!UICONTROL Wait]** attività.

1. Vai a **[!UICONTROL Split]** e collegare la transizione destinata alla popolazione A a una delle consegne e-mail già nel flusso di lavoro.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Fai doppio clic sulla consegna per aprirla.
1. Utilizzando l’elenco a discesa, seleziona il modello per la consegna A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Clic **[!UICONTROL Continue]** per visualizzare la consegna, quindi salvarla.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Collega la transizione del **[!UICONTROL Split]** attività destinata alla popolazione B alla seconda consegna e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Apri la consegna e seleziona il modello nella consegna B, quindi salva la consegna.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Collega la transizione destinata alla popolazione rimanente al **[!UICONTROL Wait]** attività.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Apri **[!UICONTROL Wait]** e configurare un periodo di attesa di 5 giorni.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Collega **[!UICONTROL Wait]** attività al **[!UICONTROL JavaScript code]** attività.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Ora puoi creare lo script. [Ulteriori informazioni](a-b-testing-uc-script.md).
