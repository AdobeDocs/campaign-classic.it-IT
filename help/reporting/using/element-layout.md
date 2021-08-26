---
product: campaign
title: Layout degli elementi
description: Layout degli elementi
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---

# Layout degli elementi{#element-layout}

![](../../assets/common.svg)

Oltre ai vari grafici qui descritti: [Tipi di grafico e varianti](../../reporting/using/creating-a-chart.md#chart-types-and-variants), è possibile adattare la visualizzazione e aggiungere elementi alle pagine del rapporto.

Puoi utilizzare i contenitori: questi consentono di collegare diversi elementi di una pagina e configurarne il layout in colonne e/o celle. Come utilizzarli è descritto in [questa sezione](../../web/using/defining-web-forms-layout.md#creating-containers).

Puoi configurare il layout del rapporto nella directory principale della struttura e sovraccaricarlo per ogni contenitore. Le pagine sono ordinate in colonne. I contenitori vengono anche ordinati in colonne. Solo gli elementi statici e grafici vengono ordinati in celle.

## Definizione delle opzioni per ogni pagina {#defining-the-options-for-each-page}

Puoi utilizzare le opzioni su ogni pagina del rapporto.

La scheda **[!UICONTROL General]** ti consente di modificare il titolo della pagina, nonché configurare le posizioni della legenda e navigare tra le pagine del rapporto.

![](assets/s_ncs_advuser_report_wizard_022.png)

Il campo **[!UICONTROL Title]** ti consente di personalizzare l’etichetta nell’intestazione della pagina del rapporto. Il titolo della finestra può essere configurato tramite la finestra **[!UICONTROL Properties]** del rapporto. Per ulteriori informazioni, consulta [Aggiunta di un’intestazione e di un piè di pagina](#adding-a-header-and-a-footer).

Le opzioni **[!UICONTROL Display settings]** consentono di selezionare la posizione della didascalia di controllo all’interno di una pagina del rapporto e di definire il numero di colonne nella pagina. Per ulteriori informazioni sul layout di pagina, consulta la sezione **Layout elemento** di [questa sezione](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Seleziona le varie opzioni nella sezione **[!UICONTROL Browse]** per autorizzare la navigazione da una pagina del rapporto all’altra. Se è selezionata l’opzione **[!UICONTROL Disable next page]** o **[!UICONTROL Disable previous page]** , i pulsanti **[!UICONTROL Next]** e **[!UICONTROL Previous]** scompaiono dalla pagina del rapporto.

## Aggiunta di un’intestazione e di un piè di pagina {#adding-a-header-and-a-footer}

La finestra delle proprietà del report consente inoltre di definire gli elementi di layout, ad esempio: il titolo della finestra, il contenuto HTML delle intestazioni e dei piè di pagina.

Per accedere alla finestra delle proprietà, fai clic sul pulsante **[!UICONTROL Properties]** del rapporto.

![](assets/reporting_properties.png)

La scheda **[!UICONTROL Page]** ti consente di personalizzare la visualizzazione.

![](assets/s_ncs_advuser_report_properties_04.png)

Il contenuto configurato in questa scheda sarà visibile su tutte le pagine del rapporto.

La sottoscheda **[!UICONTROL Texts]** ti consente di definire il contenuto della variabile: sarà tenuto conto durante il ciclo di traduzione se il rapporto è destinato ad essere utilizzato in più lingue.

Consente di creare un elenco di frammenti di testo e di collegarli a identificatori:

![](assets/s_ncs_advuser_report_properties_04a.png)

Quindi inserisci questi identificatori nel contenuto HTML del rapporto:

![](assets/s_ncs_advuser_report_properties_04b.png)

Quando viene visualizzato il rapporto, questi verranno automaticamente sostituiti con il contenuto appropriato.

Come per i testi HTML, questa modalità operativa consente di centralizzare i testi utilizzati nel rapporto e di gestirne la traduzione. I testi creati in questa scheda vengono raccolti automaticamente dallo strumento di traduzione integrata di Adobe Campaign.
