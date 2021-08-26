---
product: campaign
title: Offerte per cella
description: Offerte per cella
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 8%

---

# Offerte per cella{#offers-by-cell}

![](../../assets/common.svg)

L’attività **[!UICONTROL Offers by cell]** ti consente di distribuire il gruppo in entrata (da una query, ad esempio) in diversi segmenti e di specificare un’offerta da presentare per ciascuno di questi segmenti.

Questa attività può essere utilizzata solo con **Interazione**. Per ulteriori informazioni, consulta questa [sezione](../../interaction/using/about-outbound-channels.md).

Per eseguire questa operazione:

1. Aggiungi l’attività **[!UICONTROL Offers by cell]** una volta specificata la popolazione target, quindi aprila.
1. Nella scheda **[!UICONTROL General]** , seleziona lo spazio di offerta in cui desideri presentare le offerte.
1. Nella scheda **[!UICONTROL Cells]** , specifica i diversi sottoinsiemi utilizzando il pulsante **[!UICONTROL Add]** :

   * Specifica il gruppo di sottoinsiemi utilizzando le regole di filtraggio e limitazione disponibili.
   * Quindi, seleziona l’offerta da presentare al set secondario. Le offerte disponibili sono quelle idonee per lo spazio di offerta selezionato al passaggio precedente.

      ![](assets/int_offer_per_cell1.png)

1. Quindi configura un’attività di consegna corrispondente al canale scelto. Fai riferimento a [Consegne cross-channel](cross-channel-deliveries.md).
