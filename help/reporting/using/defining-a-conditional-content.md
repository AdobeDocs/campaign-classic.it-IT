---
solution: Campaign Classic
product: campaign
title: Definizione di un contenuto condizionale
description: Definizione di un contenuto condizionale
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---


# Definizione di un contenuto condizionale{#defining-a-conditional-content}

È possibile condizionare la visualizzazione di elementi o pagine del rapporto specifici.

Per rendere specifici elementi condizionali, adattatene le impostazioni di visibilità. Per ulteriori informazioni, vedere [Visualizzazione dell&#39;elemento di condizionamento](#conditioning-item-display).

Per rendere condizionale la visualizzazione di una o più pagine, utilizzare un&#39;attività di tipo **[!UICONTROL Test]**. Per ulteriori informazioni, vedere [Visualizzazione pagina condizionale](#conditioning-page-display).

## Visualizzazione elemento condizionale {#conditioning-item-display}

Per rendere condizionale la visualizzazione di parte di un rapporto, è necessario definirne le condizioni di visibilità: se non sono soddisfatti, gli elementi non verranno visualizzati.

Le condizioni di visibilità possono dipendere dallo stato dell&#39;operatore, dagli elementi selezionati o inseriti nella pagina del rapporto.

Esempi che mostrano la visualizzazione condizionale degli elementi in una pagina sono forniti in [questa sezione](../../web/using/form-rendering.md#defining-fields-conditional-display).

Nell&#39;esempio seguente, la condizione di visualizzazione dipende dalla lingua:

![](assets/reporting_display_condition.png)

## Visualizzazione pagina condizionale {#conditioning-page-display}

Nel grafico di un report, l&#39;attività **[!UICONTROL Test]** consente di modificare la sequenza di pagine in base a una o più condizioni.

Questa attività si basa sul seguente principio operativo:

1. Inserite un elemento **[!UICONTROL Test]** in un grafico e modificatelo.
1. Fate clic sul pulsante **[!UICONTROL Add]** per creare i vari casi possibili.

   ![](assets/reporting_test_sample.png)

   Per ogni caso, una transizione di output viene aggiunta all&#39;attività **[!UICONTROL Test]**.

   ![](assets/reporting_test_transitions.png)

1. Selezionare **[!UICONTROL Enable default transition]** per aggiungere una transizione, nel caso in cui una delle condizioni configurate non sia soddisfatta.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Un&#39;attività **[!UICONTROL Test]** può essere posizionata all&#39;inizio del grafico per condizionare la visualizzazione a seconda del contesto o del profilo dell&#39;operatore, ad esempio.
