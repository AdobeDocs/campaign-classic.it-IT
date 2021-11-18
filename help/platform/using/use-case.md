---
product: campaign
title: Caso d’uso
description: Caso d’uso
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 2%

---

# Caso d’uso{#use-case}

![](../../assets/common.svg)

## Crea un filtro per il formato e-mail degli abbonati {#creating-a-filter-on-the-email-format-of-subscribers}

Questo caso d’uso illustra come creare un filtro per ordinare le iscrizioni a una newsletter in base al formato e-mail del destinatario.

A questo scopo, è necessario utilizzare un filtro predefinito: questi filtri sono collegati a un tipo di documento e sono accessibili tramite **[!UICONTROL Administration > Configuration > Predefined filters]** nodo. Questi filtri dati possono essere utilizzati per ogni tipo di editor (o documento) nell&#39;applicazione.

I filtri dati vengono creati allo stesso modo dei filtri predefiniti, ma è disponibile un campo aggiuntivo per selezionare il tipo di documento a cui applicare il filtro.

Applica i seguenti passaggi:

1. Crea un nuovo filtro tramite **[!UICONTROL Administration > Configuration > Predefined filters]** nodo.
1. Fai clic sul pulsante **[!UICONTROL Select link]** icona per selezionare il documento interessato:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Seleziona lo schema di sottoscrizione (nms:subscription) e fai clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Fai clic su **[!UICONTROL Edit link]** per visualizzare i campi del documento selezionato.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   È quindi possibile visualizzare il contenuto del documento selezionato:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Puoi accedere a questi campi per definire le condizioni di filtro nel corpo dell’editor di filtri. Un filtro applicazione è definito esattamente allo stesso modo di un filtro avanzato. Vedi [Creare un filtro avanzato](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crea un nuovo filtro per gli abbonamenti per visualizzare solo gli abbonamenti con un formato e-mail non definito:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Fai clic su **[!UICONTROL Save]** per aggiungere un filtro ai filtri predefiniti per questo tipo di elenco.
1. Ora puoi utilizzare questo filtro nella **[!UICONTROL Subscriptions]** scheda del profilo destinatario; puoi accedere al filtro &quot;Formato e-mail sconosciuto&quot; facendo clic sul pulsante **[!UICONTROL Filters]** pulsante .

   ![](assets/s_ncs_user_filter_on_events.png)

   Il nome del filtro corrente viene visualizzato sopra l’elenco. Per annullare il filtro, fai clic sul pulsante **[!UICONTROL Delete this filter]** icona.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
