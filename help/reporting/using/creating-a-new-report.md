---
product: campaign
title: Creazione di un nuovo report
description: Scopri i passaggi chiave per creare un nuovo rapporto
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 4c2aad47-0e2d-4d0b-8898-b437f4a05e11
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# Creare un nuovo rapporto{#creating-a-new-report}

![](../../assets/common.svg)

Per creare un rapporto, effettua le seguenti operazioni:

1. Apri Adobe Campaign Explorer e dal nodo **[!UICONTROL Administration > Configuration]** , quindi seleziona la cartella **[!UICONTROL Reports]** .
1. Fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco dei rapporti.
1. Seleziona **[!UICONTROL Create a new report from a template]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. Seleziona il modello di rapporto nell’elenco a discesa.

   * Il **[!UICONTROL Extended report]** consente di creare un rapporto configurato utilizzando un grafico.
   * Il rapporto **[!UICONTROL Qualitative distribution]** ti consente di creare statistiche basate su tutti i tipi di dati (nome società, dominio e-mail, ecc.).
   * Il rapporto **[!UICONTROL Quantitative distribution]** ti consente di creare statistiche sui dati misurabili o conteggiabili (importo fattura, età destinatario, ecc.).

   Per ulteriori informazioni su questi modelli di report, consulta [questa sezione](../../reporting/using/about-descriptive-analysis.md).

1. Immetti il nome del rapporto e la relativa descrizione nei campi corrispondenti. Specifica il **[!UICONTROL schema]** in cui verrà applicato il rapporto.

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. Salva il rapporto.

## Modellazione del grafico {#modelizing-the-chart}

Dopo aver salvato il rapporto, questo verrà visualizzato. Ora puoi creare il grafico del rapporto.

![](assets/s_ncs_user_report_wizard_021.png)

Il grafico per la creazione del rapporto è costituito da una serie di attività.

![](assets/s_ncs_advuser_report_wizard_031.png)

Le attività sono collegate tramite transizioni, rappresentate da frecce.

![](assets/s_ncs_advuser_report_wizard_032.png)

Per creare un rapporto, a seconda della sua natura e del suo contesto, devi identificare gli elementi utili e modellare la loro sequenza logica.

1. Utilizza l’ attività **[!UICONTROL Start]** per materializzare il primo processo da eseguire per creare il rapporto. Puoi utilizzare solo una di queste attività per rapporto.

   È obbligatorio se il grafico include un ciclo.

1. Aggiungi una o più attività **[!UICONTROL Query]** per raccogliere i dati utili per la creazione del rapporto. I dati possono essere raccolti direttamente tramite una query su uno schema del database o tramite un elenco importato o un cubo esistente.

   Per ulteriori informazioni, consulta [Raccolta di dati da analizzare](../../reporting/using/collecting-data-to-analyze.md).

   Questi dati verranno visualizzati (o meno) nel rapporto a seconda della configurazione della pagina.

1. Posiziona una o più attività **[!UICONTROL Page]** per definire la rappresentazione grafica dei dati raccolti. È possibile inserire tabelle, grafici, campi di input e condizionare la visualizzazione di una o più pagine o elementi della pagina. Il contenuto visualizzato è completamente configurabile.

   Per ulteriori informazioni, consulta [Elementi statici](#static-elements).

1. Utilizza un’attività **[!UICONTROL Test]** per definire le condizioni per la visualizzazione o l’accesso ai dati.

   Per ulteriori informazioni, consulta [Visualizzazione pagina di condizionamento](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display).

1. Se necessario, aggiungi script personalizzati tramite l’attività **[!UICONTROL Script]** , ad esempio per calcolare il nome di un rapporto, per filtrare la visualizzazione del risultato all’interno di un contesto specifico, ecc.

   Per ulteriori informazioni, consulta [Attività script](../../reporting/using/advanced-functionalities.md#script-activity).

1. Infine, per semplificare la lettura dei rapporti complessi, puoi inserire una o più attività di tipo **[!UICONTROL Jump]**. Ciò ti consente di passare da un’attività all’altra senza materializzare la transizione nel rapporto. L’attività **[!UICONTROL Jump]** può essere utilizzata anche per visualizzare un altro rapporto.

   Per ulteriori informazioni, consulta [Attività Jump](../../reporting/using/advanced-functionalities.md#jump-activity).

Non è possibile eseguire più rami contemporaneamente. Ciò significa che un report costruito in questo modo non funzionerà:

![](assets/reporting_graph_sample_ko.png)

Tuttavia, è possibile posizionare diversi rami. Verrà eseguito solo uno di questi:

![](assets/reporting_graph_sample_ok.png)

## Creazione di una pagina {#creating-a-page}

Il contenuto viene configurato tramite le attività inserite nel grafico. Per ulteriori informazioni, consulta [Modellazione del grafico](#modelizing-the-chart).

Per configurare un’attività, fai doppio clic sulla relativa icona.

Il contenuto visualizzato è definito nelle attività di tipo **Pagina** .

Un rapporto può includere una o più pagine. Le pagine vengono create tramite un editor dedicato che consente di inserire, in una struttura ad albero, campi di input, campi di selezione, elementi statici, grafici o tabelle. I contenitori consentono di definire il layout. Per ulteriori informazioni, consulta [Layout degli elementi](../../reporting/using/element-layout.md).

Per aggiungere un componente alla pagina, utilizza le icone nella sezione in alto a sinistra della barra degli strumenti.

![](assets/reporting_add_component_in_page.png)

Puoi anche fare clic con il pulsante destro del mouse sul nodo in cui desideri aggiungere il componente e selezionarlo dall’elenco.

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>Se il rapporto è destinato all’esportazione in formato Excel, si consiglia di non utilizzare una formattazione HTML complessa. Per ulteriori informazioni, consulta [Esportazione di un report](../../reporting/using/actions-on-reports.md#exporting-a-report).

Un elemento **[!UICONTROL Page]** può includere i seguenti elementi:

* Barre, torta, tipo di curva **[!UICONTROL charts]**, ecc.
* Pivot; Elenco con gruppo o raggruppamento **[!UICONTROL tables]**.
* Testo o tipo di numero **[!UICONTROL Input controls]**.
* Elenco a discesa, casella di controllo, pulsante di scelta, scelta multipla, data o tipo di matrice **[!UICONTROL Selection controls]**.
* Editor collegamenti, Costante, Tipo di selezione cartelle **[!UICONTROL Advanced controls]**.
* Valore, Collegamento, HTML, Immagine, ecc. **[!UICONTROL Static elements]**.
* **[!UICONTROL Containers]** che consentono di controllare il layout del componente.

La modalità di configurazione di una pagina e dei relativi componenti è descritta in [questa sezione](../../web/using/about-web-forms.md).

La barra degli strumenti consente di aggiungere o rimuovere controlli e di organizzarne la sequenza nelle pagine del rapporto.

![](assets/s_ncs_advuser_report_wizard_08.png)

### Elementi statici {#static-elements}

Gli elementi statici consentono di visualizzare nel rapporto informazioni quali elementi grafici o script con cui l’utente non interagisce. Per ulteriori informazioni, consulta [questa sezione](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) .

![](assets/s_advuser_report_page_activity_03.png)

### Filtrare le informazioni in un rapporto {#filtering-information-in-a-report}

I controlli di input e selezione consentono di filtrare le informazioni visualizzate nel rapporto. Per ulteriori informazioni sull&#39;implementazione di questo tipo di filtro, consulta [Opzioni di filtro nelle query](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries).

Per ulteriori informazioni sulla creazione e la configurazione di campi di input e campi di selezione, consulta [questa sezione](../../web/using/about-web-forms.md).

Puoi integrare uno o più controlli di input nei rapporti. Questo tipo di controllo consente di filtrare le informazioni visualizzate in base a un valore inserito.

![](assets/reporting_control_text.png)

Puoi anche integrare uno o più controlli di selezione nei rapporti. Questo tipo di controllo consente di filtrare le informazioni contenute nel rapporto in base ai valori selezionati, ad esempio:

* tramite pulsanti di scelta o caselle di controllo:

   ![](assets/reporting_radio_buttons.png)

* tramite un elenco a discesa:

   ![](assets/reporting_control_list.png)

* tramite un calendario:

   ![](assets/reporting_control_date.png)

Infine, puoi integrare uno o più controlli avanzati nei rapporti. Questo tipo di controllo consente di inserire un collegamento, una costante o selezionare una cartella.

Qui puoi filtrare i dati nel rapporto per visualizzare solo le informazioni contenute in una delle cartelle della struttura:

![](assets/reporting_control_folder.png)
