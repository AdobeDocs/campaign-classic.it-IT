---
product: campaign
title: Layout degli elementi
description: Layout degli elementi
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Layout degli elementi{#element-layout}



Oltre ai vari grafici dettagliati [qui](../../reporting/using/creating-a-chart.md#chart-types-and-variants), è possibile adattare la visualizzazione e aggiungere elementi alle pagine del rapporto.

Puoi utilizzare i contenitori: ti consentono di collegare diversi elementi di una pagina e configurarne il layout in colonne e/o celle. Come utilizzarli è descritto in [questa sezione](../../web/using/defining-web-forms-layout.md#creating-containers).

Puoi configurare il layout del rapporto nella directory principale della struttura e sovraccaricarlo per ogni contenitore. Le pagine sono ordinate in colonne. I contenitori vengono inoltre ordinati in colonne. Solo gli elementi statici e grafici vengono ordinati in celle.

## Definisci le opzioni per ogni pagina {#defining-the-options-for-each-page}

Puoi utilizzare le opzioni su ogni pagina del rapporto.

Il **[!UICONTROL General]** Questa scheda ti consente di modificare il titolo della pagina, nonché di configurare le posizioni della legenda e navigare tra le pagine del rapporto.

![](assets/s_ncs_advuser_report_wizard_022.png)

Il **[!UICONTROL Title]** consente di personalizzare l’etichetta nell’intestazione della pagina del rapporto. Il titolo della finestra può essere configurato tramite il **[!UICONTROL Properties]** finestra del report. Per ulteriori informazioni, consulta [Aggiunta di un’intestazione e un piè di pagina](#adding-a-header-and-a-footer).

Il **[!UICONTROL Display settings]** Le opzioni consentono di selezionare la posizione della didascalia del controllo all&#39;interno di una pagina di report e di definire il numero di colonne nella pagina. Per ulteriori informazioni sul layout di pagina, consulta **Layout elemento** sezione di [questa sezione](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Seleziona le varie opzioni nella sezione **[!UICONTROL Browse]** per autorizzare la navigazione da una pagina di report a un&#39;altra. Se il **[!UICONTROL Disable next page]** o **[!UICONTROL Disable previous page]** è selezionata, la **[!UICONTROL Next]** e **[!UICONTROL Previous]** i pulsanti scompaiono dalla pagina del report.

## Aggiungere un’intestazione e un piè di pagina {#adding-a-header-and-a-footer}

La finestra delle proprietà del rapporto consente inoltre di definire gli elementi di layout, ad esempio il titolo della finestra e il contenuto HTML delle intestazioni e dei piè di pagina.

Per accedere alla finestra delle proprietà, fare clic su **[!UICONTROL Properties]** del report.

![](assets/reporting_properties.png)

Il **[!UICONTROL Page]** consente di personalizzare la visualizzazione.

![](assets/s_ncs_advuser_report_properties_04.png)

Il contenuto configurato in questa scheda sarà visibile su tutte le pagine del rapporto.

Il **[!UICONTROL Texts]** scheda secondaria consente di definire il contenuto delle variabili: verrà preso in considerazione durante il ciclo di traduzione se il rapporto è progettato per l’utilizzo in più lingue.

Questo consente di creare un elenco di frammenti di testo e collegarli agli identificatori:

![](assets/s_ncs_advuser_report_properties_04a.png)

Quindi inserisci questi identificatori nel contenuto HTML del rapporto:

![](assets/s_ncs_advuser_report_properties_04b.png)

Vengono sostituiti automaticamente con il contenuto appropriato quando viene visualizzato il rapporto.

Come per i testi HTML, questa modalità operativa ti consente di centralizzare i testi utilizzati nel rapporto e di gestirne la traduzione. I testi creati in questa scheda vengono raccolti automaticamente dallo strumento di traduzione integrato Adobe Campaign.
