---
product: campaign
title: Caso d’uso
description: Caso d’uso
feature: Subscriptions, Email, Data Management
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
hidefromtoc: true
source-git-commit: 8817b485fd5b6d6aeb9d71c1106f16fbb6bc3c5b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---

# Caso d’uso{#use-case}



## Creare un filtro per il formato e-mail degli abbonati {#creating-a-filter-on-the-email-format-of-subscribers}

Questo caso d’uso illustra come creare un filtro per ordinare le iscrizioni alle newsletter in base al formato e-mail del destinatario.

A questo scopo, è necessario utilizzare un filtro predefinito: questi filtri sono collegati a un tipo di documento e sono accessibili tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]**. Questi filtri dati possono essere utilizzati per ogni tipo di editor (o documento) nell’applicazione.

I filtri dati vengono creati nello stesso modo dei filtri predefiniti, ma è disponibile un campo aggiuntivo per selezionare il tipo di documento a cui applicare il filtro.

Applica i seguenti passaggi:

1. Creare un nuovo filtro tramite il nodo **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Fare clic sull&#39;icona **[!UICONTROL Select link]** per selezionare il documento interessato:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selezionare lo schema di sottoscrizione (nms:subscription) e fare clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Fare clic su **[!UICONTROL Edit link]** per visualizzare i campi del documento selezionato.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   È quindi possibile visualizzare il contenuto del documento selezionato:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Puoi accedere a questi campi per definire le condizioni del filtro nel corpo dell’editor di filtri. Un filtro di applicazione viene definito esattamente nello stesso modo di un filtro avanzato. Per ulteriori informazioni sui filtri, consulta la [documentazione di Campaign v8 (console)](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.


1. Crea un nuovo filtro per gli abbonamenti per visualizzare solo gli abbonamenti con un formato e-mail non definito:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Fare clic su **[!UICONTROL Save]** per aggiungere un filtro ai filtri predefiniti per questo tipo di elenco.
1. È ora possibile utilizzare questo filtro nella scheda **[!UICONTROL Subscriptions]** del profilo del destinatario; è possibile accedere al filtro &quot;Formato e-mail sconosciuto&quot; facendo clic sul pulsante **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   Il nome del filtro corrente viene visualizzato sopra l&#39;elenco. Per annullare il filtro, fare clic sull&#39;icona **[!UICONTROL Delete this filter]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
