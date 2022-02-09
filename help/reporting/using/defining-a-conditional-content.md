---
product: campaign
title: Definire un contenuto condizionale
description: Definire un contenuto condizionale
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Definire un contenuto condizionale{#defining-a-conditional-content}

![](../../assets/common.svg)

È possibile condizionare la visualizzazione di specifici elementi o pagine del rapporto.

Per rendere condizionali elementi specifici, adattane le impostazioni di visibilità. Per ulteriori informazioni, consulta [Visualizzazione dell&#39;elemento condizione](#conditioning-item-display).

Per rendere condizionale la visualizzazione di una o più pagine, utilizza un **[!UICONTROL Test]** digitare activity. Per ulteriori informazioni, consulta [Visualizzazione della pagina Condizione](#conditioning-page-display).

## Visualizzazione dell&#39;elemento condizione {#conditioning-item-display}

Per condizionare la visualizzazione di parte di un rapporto, è necessario definirne le condizioni di visibilità: se questi elementi non sono soddisfatti, gli elementi non verranno visualizzati.

Le condizioni di visibilità possono dipendere dallo stato dell’operatore, dagli elementi selezionati o inseriti nella pagina del rapporto.

Gli esempi che mostrano la visualizzazione condizionale degli elementi in una pagina sono forniti in [questa sezione](../../web/using/form-rendering.md#defining-fields-conditional-display).

Nell’esempio seguente, la condizione di visualizzazione dipende dalla lingua:

![](assets/reporting_display_condition.png)

## Visualizzazione della pagina Condizione {#conditioning-page-display}

Nel grafico di un rapporto, la **[!UICONTROL Test]** attività ti consente di modificare la sequenza di pagine a seconda di una o più condizioni.

Questa attività si basa sul seguente principio operativo:

1. Posiziona un **[!UICONTROL Test]** in un grafico e modificalo.
1. Fai clic sul pulsante **[!UICONTROL Add]** per creare i vari casi possibili.

   ![](assets/reporting_test_sample.png)

   Per ogni caso, viene aggiunta una transizione di output al **[!UICONTROL Test]** attività.

   ![](assets/reporting_test_transitions.png)

1. Seleziona la **[!UICONTROL Enable default transition]** per aggiungere una transizione, nel caso in cui una delle condizioni configurate non sia soddisfatta.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

A **[!UICONTROL Test]** l’attività può essere posizionata all’inizio del grafico per condizionare la visualizzazione in base al contesto o al profilo dell’operatore, ad esempio.
