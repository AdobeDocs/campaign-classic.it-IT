---
title: Caso d’uso
seo-title: Caso d’uso
description: Caso d’uso
seo-description: null
page-status-flag: never-activated
uuid: d4c76fdf-d562-4151-93ec-08b4f6563440
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: fbc38e33-60a6-4d21-a598-312293d168fb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 3%

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

