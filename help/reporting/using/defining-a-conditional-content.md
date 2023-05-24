---
product: campaign
title: Definire un contenuto condizionale
description: Definire un contenuto condizionale
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---

# Definire un contenuto condizionale{#defining-a-conditional-content}



Puoi condizionare la visualizzazione di pagine o elementi del rapporto specifici.

Per rendere condizionali elementi specifici, adattarne le impostazioni di visibilità. Per ulteriori informazioni, consulta [Visualizzazione elemento condizione](#conditioning-item-display).

Per rendere condizionale la visualizzazione di una o più pagine, utilizzare una **[!UICONTROL Test]** attività di tipo. Per ulteriori informazioni, consulta [Visualizzazione pagina condizione](#conditioning-page-display).

## Visualizzazione elemento condizione {#conditioning-item-display}

Per rendere condizionale la visualizzazione di una parte di un rapporto, è necessario definirne le condizioni di visibilità: se queste non vengono soddisfatte, gli elementi non verranno visualizzati.

Le condizioni di visibilità possono dipendere dallo stato dell’operatore, dagli elementi selezionati o immessi nella pagina del rapporto.

Esempi che mostrano la visualizzazione condizionale degli elementi su una pagina sono forniti in [questa sezione](../../web/using/form-rendering.md#defining-fields-conditional-display).

Nell’esempio seguente, la condizione di visualizzazione dipende dalla lingua:

![](assets/reporting_display_condition.png)

## Visualizzazione pagina condizione {#conditioning-page-display}

Nel grafico di un report, il **[!UICONTROL Test]** attività consente di modificare la sequenza di pagine a seconda di una o più condizioni.

Questa attività si basa sul seguente principio di funzionamento:

1. Inserisci un **[!UICONTROL Test]** in un grafico e modificarlo.
1. Fai clic su **[!UICONTROL Add]** per creare i vari casi possibili.

   ![](assets/reporting_test_sample.png)

   Per ogni caso, viene aggiunta una transizione di output al **[!UICONTROL Test]** attività.

   ![](assets/reporting_test_transitions.png)

1. Seleziona la **[!UICONTROL Enable default transition]** per aggiungere una transizione, nel caso in cui una delle condizioni configurate non sia soddisfatta.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

A **[!UICONTROL Test]** L’attività può essere posizionata all’inizio del grafico per condizionare la visualizzazione in base al contesto o al profilo dell’operatore, ad esempio.
