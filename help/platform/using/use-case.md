---
product: campaign
title: Caso d’uso
description: Caso d’uso
feature: Subscriptions, Email, Data Management
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Caso d’uso{#use-case}



## Creare un filtro per il formato e-mail degli abbonati {#creating-a-filter-on-the-email-format-of-subscribers}

Questo caso d’uso illustra come creare un filtro per ordinare le iscrizioni alle newsletter in base al formato e-mail del destinatario.

A questo scopo, è necessario utilizzare un filtro predefinito: questi filtri sono collegati a un tipo di documento e sono accessibili tramite **[!UICONTROL Administration > Configuration > Predefined filters]** nodo. Questi filtri dati possono essere utilizzati per ogni tipo di editor (o documento) nell’applicazione.

I filtri dati vengono creati nello stesso modo dei filtri predefiniti, ma è disponibile un campo aggiuntivo per selezionare il tipo di documento a cui applicare il filtro.

Applica i seguenti passaggi:

1. Creare un nuovo filtro tramite **[!UICONTROL Administration > Configuration > Predefined filters]** nodo.
1. Fai clic su **[!UICONTROL Select link]** per selezionare il documento interessato:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Seleziona lo schema di abbonamento (nms:subscription) e fai clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Clic **[!UICONTROL Edit link]** per visualizzare i campi del documento selezionato.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   È quindi possibile visualizzare il contenuto del documento selezionato:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Puoi accedere a questi campi per definire le condizioni del filtro nel corpo dell’editor di filtri. Un filtro di applicazione viene definito esattamente nello stesso modo di un filtro avanzato. Consulta [Creare un filtro avanzato](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Crea un nuovo filtro per gli abbonamenti per visualizzare solo gli abbonamenti con un formato e-mail non definito:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Clic **[!UICONTROL Save]** per aggiungere un filtro ai filtri predefiniti per questo tipo di elenco.
1. Ora puoi utilizzare questo filtro nel **[!UICONTROL Subscriptions]** del profilo del destinatario; puoi accedere al filtro &quot;Formato e-mail sconosciuto&quot; facendo clic sul pulsante **[!UICONTROL Filters]** pulsante.

   ![](assets/s_ncs_user_filter_on_events.png)

   Il nome del filtro corrente viene visualizzato sopra l&#39;elenco. Per annullare il filtro, fai clic su **[!UICONTROL Delete this filter]** icona.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
