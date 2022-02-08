---
product: campaign
title: Configurare le consegne
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Configurare le consegne nel flusso di lavoro {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

Una volta [popolazioni create](a-b-testing-uc-population-samples.md), puoi configurare le consegne. In questo caso d’uso, le prime due consegne consentono di inviare contenuti diversi ai gruppi A e B. La terza consegna è la consegna di ritorno: verrà inviato ai destinatari che non appartengono a A né B. Il relativo contenuto verrà calcolato da uno script e sarà identico a A o B, a seconda di quale ha ottenuto il punteggio di apertura più alto. È necessario configurare un periodo di attesa per la terza consegna, per individuare il risultato delle consegne A e B. Per questo motivo la terza consegna include un **[!UICONTROL Wait]** attività.

1. Vai a **[!UICONTROL Split]** e collega la transizione destinata alla popolazione A a una delle consegne e-mail già presenti nel flusso di lavoro.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Fai doppio clic sulla consegna per aprirla.
1. Utilizzando l’elenco a discesa, seleziona il modello per la consegna A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Fai clic su **[!UICONTROL Continue]** per visualizzare la consegna, quindi salvarla.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Collega la transizione della **[!UICONTROL Split]** attività destinata alla popolazione B alla seconda consegna e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Apri la consegna e seleziona il modello nella consegna B, quindi salva la consegna.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Collegare la transizione destinata alla popolazione rimanente al **[!UICONTROL Wait]** attività.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Apri **[!UICONTROL Wait]** e configura un periodo di attesa di 5 giorni.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Collega **[!UICONTROL Wait]** attività **[!UICONTROL JavaScript code]** attività.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Ora puoi creare lo script. [Ulteriori informazioni](a-b-testing-uc-script.md).
