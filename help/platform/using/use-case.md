---
solution: Campaign Classic
product: campaign
title: Caso d’uso
description: Caso d’uso
audience: platform
content-type: reference
topic-tags: filtering-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 2%

---


# Caso d’uso{#use-case}

## Crea un filtro per il formato e-mail degli abbonati {#creating-a-filter-on-the-email-format-of-subscribers}

Questo caso d’uso illustra come creare un filtro per ordinare le iscrizioni a una newsletter in base al formato e-mail del destinatario.

A questo scopo, è necessario utilizzare un filtro predefinito: questi filtri sono collegati a un tipo di documento e sono accessibili tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]** . Questi filtri dati possono essere utilizzati per ogni tipo di editor (o documento) nell&#39;applicazione.

I filtri dati vengono creati allo stesso modo dei filtri predefiniti, ma è disponibile un campo aggiuntivo per selezionare il tipo di documento a cui applicare il filtro.

Applica i seguenti passaggi:

1. Crea un nuovo filtro tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]** .
1. Fare clic sull&#39;icona **[!UICONTROL Select link]** per selezionare il documento interessato:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Seleziona lo schema di sottoscrizione (nms:subscription) e fai clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Fare clic su **[!UICONTROL Edit link]** per visualizzare i campi del documento selezionato.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   È quindi possibile visualizzare il contenuto del documento selezionato:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Puoi accedere a questi campi per definire le condizioni di filtro nel corpo dell’editor di filtri. Un filtro applicazione è definito esattamente allo stesso modo di un filtro avanzato. Consulta [Creare un filtro avanzato](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crea un nuovo filtro per gli abbonamenti per visualizzare solo gli abbonamenti con un formato e-mail non definito:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Fai clic su **[!UICONTROL Save]** per aggiungere un filtro ai filtri predefiniti per questo tipo di elenco.
1. Ora puoi utilizzare questo filtro nella scheda **[!UICONTROL Subscriptions]** del profilo del destinatario; è possibile accedere al filtro &quot;Formato e-mail sconosciuto&quot; facendo clic sul pulsante **[!UICONTROL Filters]** .

   ![](assets/s_ncs_user_filter_on_events.png)

   Il nome del filtro corrente viene visualizzato sopra l’elenco. Per annullare il filtro, fai clic sull&#39;icona **[!UICONTROL Delete this filter]** .

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

