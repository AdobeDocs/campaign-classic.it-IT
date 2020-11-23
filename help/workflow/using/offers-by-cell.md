---
solution: Campaign Classic
product: campaign
title: Offerte per cella
description: Offerte per cella
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 8%

---


# Offerte per cella{#offers-by-cell}

L&#39; **[!UICONTROL Offers by cell]** attività consente di distribuire la popolazione in entrata (ad esempio da una query) in diversi segmenti e di specificare un&#39;offerta da presentare per ciascuno di questi segmenti.

Questa attività può essere utilizzata solo con **Interazione**. For more information, refer to this [section](../../interaction/using/about-outbound-channels.md).

Per eseguire questa operazione:

1. Aggiungete l&#39; **[!UICONTROL Offers by cell]** attività una volta specificata la popolazione di destinazione, quindi apritela.
1. Nella **[!UICONTROL General]** scheda, selezionate lo spazio dell&#39;offerta sul quale desiderate presentare le offerte.
1. Nella **[!UICONTROL Cells]** scheda, specificate i diversi sottoinsiemi utilizzando il **[!UICONTROL Add]** pulsante:

   * Specificate la popolazione di sottoinsiemi utilizzando le regole di filtraggio e limitazione disponibili.
   * Selezionate quindi l’offerta da presentare al set secondario. Le offerte disponibili sono quelle idonee per lo spazio di offerta selezionato al passaggio precedente.

      ![](assets/int_offer_per_cell1.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Fare riferimento alle consegne [tra canali](../../workflow/using/cross-channel-deliveries.md).

