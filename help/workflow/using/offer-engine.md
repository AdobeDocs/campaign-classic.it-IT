---
title: Motore di offerta
seo-title: Motore di offerta
description: Motore di offerta
seo-description: null
page-status-flag: never-activated
uuid: a8f6056a-80e6-4f9f-81f5-563c98d11d28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 08987595-e80c-4197-ad1e-9aa7cfc7c3eb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 5%

---


# Motore di offerta{#offer-engine}

L&#39; **[!UICONTROL Offer engine]** attività consente di definire una chiamata al motore dell&#39;offerta prima della consegna.

Questa attività funziona sullo stesso principio dell&#39;attività di arricchimento con una chiamata al motore, arricchendo i dati della popolazione in entrata con un&#39;offerta calcolata dal motore, prima della consegna.

![](assets/int_offerengine_activity2.png)

Dopo aver configurato la query (consultare questa [sezione](../../workflow/using/query.md)):

1. Aggiungete e aprite un&#39; **[!UICONTROL Offer engine]** attività.
1. Completate i vari campi disponibili per specificare i parametri del motore di chiamata (spazio di offerta, categoria o tema/i, data di contatto, numero di offerte da mantenere). Il motore calcolerà automaticamente le offerte da aggiungere in base a questi parametri.

   >[!CAUTION]
   >
   >Se utilizzate questa attività, verranno memorizzate solo le proposte di offerta utilizzate nella consegna.

   ![](assets/int_offerengine_activity1.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Fare riferimento alle consegne [tra canali](../../workflow/using/cross-channel-deliveries.md).

