---
solution: Campaign Classic
product: campaign
title: Caso d’uso
description: Caso d’uso
audience: platform
content-type: reference
topic-tags: filtering-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 2%

---


# Caso d’uso{#use-case}

## Creazione di un filtro nel formato e-mail degli abbonati {#creating-a-filter-on-the-email-format-of-subscribers}

Questo caso di utilizzo illustra come creare un filtro per ordinare le iscrizioni alla newsletter in base al formato e-mail del destinatario.

A questo scopo, è necessario utilizzare un filtro predefinito: questi filtri sono collegati a un tipo di documento e sono accessibili tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]**. Questi filtri dati possono essere utilizzati per ogni tipo di editor (o documento) nell&#39;applicazione.

I filtri dati vengono creati allo stesso modo dei filtri predefiniti, ma è presente un campo aggiuntivo per selezionare il tipo di documento a cui verrà applicato il filtro.

Effettuate le seguenti operazioni:

1. Create un nuovo filtro tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Fare clic sull&#39;icona **[!UICONTROL Select link]** per selezionare il documento interessato:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selezionate lo schema di sottoscrizione (nms:subscription) e fate clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Fare clic su **[!UICONTROL Edit link]** per visualizzare i campi del documento selezionato.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   È quindi possibile visualizzare il contenuto del documento selezionato:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Potete accedere a questi campi per definire le condizioni del filtro nel corpo dell’editor di filtri. Un filtro applicazione è definito esattamente allo stesso modo di un filtro avanzato. Vedere [Creazione di un filtro avanzato](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Create un nuovo filtro per le iscrizioni per visualizzare solo le sottoscrizioni con un formato e-mail non definito:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Fare clic su **[!UICONTROL Save]** per aggiungere un filtro ai filtri predefiniti per questo tipo di elenco.
1. È ora possibile utilizzare questo filtro nella scheda **[!UICONTROL Subscriptions]** del profilo del destinatario; per accedere al filtro &quot;Formato e-mail sconosciuto&quot;, fare clic sul pulsante **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   Il nome del filtro corrente viene visualizzato sopra l&#39;elenco. Per annullare il filtro, fate clic sull&#39;icona **[!UICONTROL Delete this filter]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

