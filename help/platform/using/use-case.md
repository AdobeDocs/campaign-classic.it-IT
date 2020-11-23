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

## Creazione di un filtro per il formato e-mail degli abbonati {#creating-a-filter-on-the-email-format-of-subscribers}

Questo caso di utilizzo illustra come creare un filtro per ordinare le iscrizioni alla newsletter in base al formato e-mail del destinatario.

A questo scopo, è necessario utilizzare un filtro predefinito: questi filtri sono collegati a un tipo di documento e sono accessibili tramite il **[!UICONTROL Administration > Configuration > Predefined filters]** nodo. Questi filtri dati possono essere utilizzati per ogni tipo di editor (o documento) nell&#39;applicazione.

I filtri dati vengono creati allo stesso modo dei filtri predefiniti, ma è presente un campo aggiuntivo per selezionare il tipo di documento a cui verrà applicato il filtro.

Effettuate le seguenti operazioni:

1. Crea un nuovo filtro tramite il **[!UICONTROL Administration > Configuration > Predefined filters]** nodo.
1. Fare clic sull&#39; **[!UICONTROL Select link]** icona per selezionare il documento interessato:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selezionate lo schema di sottoscrizione (nms:subscription) e fate clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Fare clic **[!UICONTROL Edit link]** per visualizzare i campi del documento selezionato.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   È quindi possibile visualizzare il contenuto del documento selezionato:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Potete accedere a questi campi per definire le condizioni del filtro nel corpo dell’editor di filtri. Un filtro applicazione è definito esattamente allo stesso modo di un filtro avanzato. Consultate [Creazione di un filtro](../../platform/using/creating-filters.md#creating-an-advanced-filter)avanzato.

1. Create un nuovo filtro per le iscrizioni per visualizzare solo le sottoscrizioni con un formato e-mail non definito:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Fate clic **[!UICONTROL Save]** per aggiungere un filtro ai filtri predefiniti per questo tipo di elenco.
1. Ora puoi usare questo filtro nella **[!UICONTROL Subscriptions]** scheda del profilo del destinatario; potete accedere al filtro &quot;Formato e-mail sconosciuto&quot; facendo clic sul **[!UICONTROL Filters]** pulsante.

   ![](assets/s_ncs_user_filter_on_events.png)

   Il nome del filtro corrente viene visualizzato sopra l&#39;elenco. Per annullare il filtro, fate clic sull’ **[!UICONTROL Delete this filter]** icona .

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

