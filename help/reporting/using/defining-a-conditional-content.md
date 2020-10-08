---
title: Definizione di un contenuto condizionale
seo-title: Definizione di un contenuto condizionale
description: Definizione di un contenuto condizionale
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 9%

---


# Definizione di un contenuto condizionale{#defining-a-conditional-content}

È possibile condizionare la visualizzazione di elementi o pagine del rapporto specifici.

Per rendere specifici elementi condizionali, adattatene le impostazioni di visibilità. Per ulteriori informazioni, vedere Visualizzazione [degli elementi](#conditioning-item-display)Condizionati.

Per rendere condizionale la visualizzazione di una o più pagine, utilizzare un&#39;attività **[!UICONTROL Test]** tipo. For more on this, refer to [Conditioning page display](#conditioning-page-display).

## Visualizzazione dell&#39;elemento di condizionamento {#conditioning-item-display}

Per rendere condizionale la visualizzazione di parte di un rapporto, è necessario definirne le condizioni di visibilità: se non sono soddisfatti, gli elementi non verranno visualizzati.

Le condizioni di visibilità possono dipendere dallo stato dell&#39;operatore, dagli elementi selezionati o inseriti nella pagina del rapporto.

In [questa sezione](../../web/using/form-rendering.md#defining-fields-conditional-display)sono disponibili esempi che mostrano la visualizzazione condizionale degli elementi su una pagina.

Nell&#39;esempio seguente, la condizione di visualizzazione dipende dalla lingua:

![](assets/reporting_display_condition.png)

## Visualizzazione della pagina con condizioni {#conditioning-page-display}

Nel grafico di un rapporto, l&#39; **[!UICONTROL Test]** attività consente di modificare la sequenza di pagine in base a una o più condizioni.

Questa attività si basa sul seguente principio operativo:

1. Inserite un grafico **[!UICONTROL Test]** e modificatelo.
1. Fate clic sul **[!UICONTROL Add]** pulsante per creare i vari casi possibili.

   ![](assets/reporting_test_sample.png)

   Per ogni caso, all&#39; **[!UICONTROL Test]** attività viene aggiunta una transizione di output.

   ![](assets/reporting_test_transitions.png)

1. Selezionare l&#39;opzione **[!UICONTROL Enable default transition]** per aggiungere una transizione, nel caso in cui una delle condizioni configurate non sia soddisfatta.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Un&#39; **[!UICONTROL Test]** attività può essere posizionata all&#39;inizio del grafico per condizionare la visualizzazione in base al contesto o al profilo dell&#39;operatore, ad esempio.
