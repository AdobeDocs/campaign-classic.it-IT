---
solution: Campaign Classic
product: campaign
title: Motore di offerta
description: Motore di offerta
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 4%

---


# Motore di offerta{#offer-engine}

L&#39;attività **[!UICONTROL Offer engine]** consente di definire una chiamata al motore delle offerte prima della consegna.

Questa attività funziona sullo stesso principio dell&#39;attività di arricchimento con una chiamata al motore, arricchendo i dati della popolazione in entrata con un&#39;offerta calcolata dal motore, prima della consegna.

![](assets/int_offerengine_activity2.png)

Dopo aver configurato la query (consultare la sezione [sezione](../../workflow/using/query.md)):

1. Aggiungete e aprite un&#39;attività **[!UICONTROL Offer engine]**.
1. Completate i vari campi disponibili per specificare i parametri del motore di chiamata (spazio di offerta, categoria o tema/i, data di contatto, numero di offerte da mantenere). Il motore calcolerà automaticamente le offerte da aggiungere in base a questi parametri.

   >[!CAUTION]
   >
   >Se utilizzate questa attività, verranno memorizzate solo le proposte di offerta utilizzate nella consegna.

   ![](assets/int_offerengine_activity1.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Fare riferimento a [Consegne tra canali](../../workflow/using/cross-channel-deliveries.md).

