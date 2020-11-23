---
solution: Campaign Classic
product: campaign
title: Layout degli elementi
description: Layout degli elementi
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---


# Layout degli elementi{#element-layout}

Oltre ai vari grafici qui descritti: [Tipi di grafico e varianti](../../reporting/using/creating-a-chart.md#chart-types-and-variants), è possibile adattare la visualizzazione e aggiungere elementi alle pagine del rapporto.

È possibile utilizzare i contenitori: questi consentono di collegare diversi elementi di una pagina e configurarne il layout in colonne e/o celle. Come utilizzarli è illustrato in [questa sezione](../../web/using/defining-web-forms-layout.md#creating-containers).

Puoi configurare il layout del rapporto nella parte principale della struttura e sovraccaricarlo per ogni contenitore. Le pagine sono ordinate in colonne. I contenitori sono anche ordinati in colonne. Solo gli elementi statici e grafici sono ordinati in celle.

## Definizione delle opzioni per ogni pagina {#defining-the-options-for-each-page}

Potete utilizzare le opzioni in ogni pagina del rapporto.

La **[!UICONTROL General]** scheda consente di modificare il titolo della pagina, nonché configurare le posizioni della legenda e spostarsi tra le pagine del rapporto.

![](assets/s_ncs_advuser_report_wizard_022.png)

Il **[!UICONTROL Title]** campo consente di personalizzare l’etichetta nell’intestazione della pagina del rapporto. Il titolo della finestra può essere configurato tramite la **[!UICONTROL Properties]** finestra del rapporto. Per ulteriori informazioni, vedere [Aggiunta di un&#39;intestazione e di un piè di pagina](#adding-a-header-and-a-footer).

Le **[!UICONTROL Display settings]** opzioni consentono di selezionare la posizione della didascalia di controllo all&#39;interno di una pagina del rapporto e di definire il numero di colonne nella pagina. Per ulteriori informazioni sul layout di pagina, fare riferimento alla sezione **Layout** elemento di [questa sezione](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Selezionate le varie opzioni nella **[!UICONTROL Browse]** sezione per autorizzare la navigazione da una pagina del rapporto all’altra. Se l&#39; **[!UICONTROL Disable next page]** opzione o l&#39; **[!UICONTROL Disable previous page]** opzione è selezionata, i pulsanti **[!UICONTROL Next]** e **[!UICONTROL Previous]** non vengono visualizzati nella pagina del rapporto.

## Aggiunta di un&#39;intestazione e di un piè di pagina {#adding-a-header-and-a-footer}

La finestra delle proprietà del rapporto consente inoltre di definire gli elementi di layout, ad esempio: il titolo della finestra, il contenuto HTML delle intestazioni e dei piè di pagina.

Per accedere alla finestra delle proprietà, fare clic sul **[!UICONTROL Properties]** pulsante del rapporto.

![](assets/reporting_properties.png)

La **[!UICONTROL Page]** scheda consente di personalizzare lo schermo.

![](assets/s_ncs_advuser_report_properties_04.png)

Il contenuto configurato in questa scheda sarà visibile su tutte le pagine del rapporto.

La **[!UICONTROL Texts]** sottoscheda consente di definire il contenuto variabile: sarà presa in considerazione durante il ciclo di traduzione se la relazione è destinata a essere utilizzata in più lingue.

Questo consente di creare un elenco di frammenti di testo e di collegarli a identificatori:

![](assets/s_ncs_advuser_report_properties_04a.png)

Quindi inserite questi identificatori nel contenuto HTML del rapporto:

![](assets/s_ncs_advuser_report_properties_04b.png)

Quando viene visualizzato il rapporto, verranno sostituiti automaticamente con il contenuto appropriato.

Come per i testi HTML, questa modalità operativa consente di centralizzare i testi utilizzati nel rapporto e di gestirne la traduzione. I testi creati in questa scheda vengono raccolti automaticamente dallo strumento di traduzione integrato  Adobe Campaign.
