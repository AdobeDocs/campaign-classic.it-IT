---
product: campaign
title: Definire un contenuto condizionale
description: Definire un contenuto condizionale
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 7%

---

# Definire un contenuto condizionale{#defining-a-conditional-content}



Puoi condizionare la visualizzazione di pagine o elementi del rapporto specifici.

Per rendere condizionali elementi specifici, adattarne le impostazioni di visibilità. Per ulteriori informazioni, consulta [Visualizzazione elemento condizione](#conditioning-item-display).

Per rendere condizionale la visualizzazione di una o più pagine, utilizzare un&#39;attività di tipo **[!UICONTROL Test]**. Per ulteriori informazioni, consulta [Visualizzazione pagina condizione](#conditioning-page-display).

## Visualizzazione elemento condizione {#conditioning-item-display}

Per rendere condizionale la visualizzazione di una parte di un rapporto, è necessario definirne le condizioni di visibilità: se queste non vengono soddisfatte, gli elementi non verranno visualizzati.

Le condizioni di visibilità possono dipendere dallo stato dell’operatore, dagli elementi selezionati o immessi nella pagina del rapporto.

Esempi che mostrano la visualizzazione condizionale degli elementi in una pagina sono forniti in [questa sezione](../../web/using/form-rendering.md#defining-fields-conditional-display).

Nell’esempio seguente, la condizione di visualizzazione dipende dalla lingua:

![](assets/reporting_display_condition.png)

## Visualizzazione pagina condizione {#conditioning-page-display}

Nel grafico di un report, l&#39;attività **[!UICONTROL Test]** consente di modificare la sequenza di pagine a seconda di una o più condizioni.

Questa attività si basa sul seguente principio di funzionamento:

1. Inserire un **[!UICONTROL Test]** in un grafico e modificarlo.
1. Fare clic sul pulsante **[!UICONTROL Add]** per creare i vari casi possibili.

   ![](assets/reporting_test_sample.png)

   Per ogni caso, all&#39;attività **[!UICONTROL Test]** viene aggiunta una transizione di output.

   ![](assets/reporting_test_transitions.png)

1. Selezionare **[!UICONTROL Enable default transition]** per aggiungere una transizione, nel caso in cui una delle condizioni configurate non sia soddisfatta.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

È possibile inserire un&#39;attività **[!UICONTROL Test]** all&#39;inizio del grafico per condizionare la visualizzazione in base al contesto o al profilo dell&#39;operatore, ad esempio.
