---
product: campaign
title: Proprietà del rapporto
description: Ulteriori informazioni sulle impostazioni delle proprietà del report
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# Proprietà del rapporto{#properties-of-the-report}



Puoi personalizzare e configurare completamente il rapporto in base alle tue esigenze. A questo scopo, modificane le proprietà. Le proprietà del report sono accessibili tramite **[!UICONTROL Properties]** sopra il grafico della sequenza di attività.

![](assets/s_ncs_advuser_report_properties_01.png)

Le proprietà generali sono descritte di seguito. Funzionalità avanzate configurate in **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** e **[!UICONTROL Scripts]** le schede sono descritte [in questa sezione](../../reporting/using/advanced-functionalities.md).

## Proprietà generali {#overall-properties}

In **[!UICONTROL General]** della scheda delle proprietà del rapporto, puoi modificare le impostazioni elencate di seguito:

* L’etichetta e il nome interno del rapporto. Il **[!UICONTROL Internal name]** viene utilizzato nell’URL finale del rapporto. Non deve essere modificato dopo la creazione del rapporto.

* Il rapporto **Cartella** viene selezionato durante la creazione del rapporto. Si consiglia di creare una cartella dedicata per i rapporti personalizzati in modo che non vengano combinati con [rapporti incorporati](../../reporting/using/about-campaign-built-in-reports.md).

* Il **Storage** viene selezionato durante la creazione del rapporto. Per modificare la tabella dati del rapporto, fare clic su **[!UICONTROL Select link]** a destra del **[!UICONTROL Document type]** campo.

  ![](assets/s_ncs_advuser_report_properties_02.png)

* Il **Controllo degli accessi** parametri. Queste impostazioni sono descritte di seguito.

## Controllare l’accesso al rapporto {#report-accessibility}

È possibile accedere a un rapporto nella console Adobe Campaign o con un browser web. In questo caso, può essere necessario configurare il controllo di accesso ai rapporti come mostrato di seguito.

![](assets/s_ncs_advuser_report_properties_02b.png)

Le opzioni possibili sono:

* **[!UICONTROL Anonymous access]**: questa opzione consente l’accesso illimitato al rapporto. Tuttavia, non è possibile alcuna manipolazione.

  Le autorizzazioni dell’operatore tecnico &quot;webapp&quot; vengono utilizzate per visualizzare gli elementi del rapporto. Per ulteriori informazioni, consulta [questa sezione](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: questa opzione consente agli operatori Adobe Campaign di accedervi dopo aver effettuato l’accesso.
* **[!UICONTROL Specific account]**: questa opzione ti consente di eseguire il rapporto con i diritti dell’operatore selezionato nel **[!UICONTROL Operator]** campo.

## Tradurre il rapporto {#report-localization}

Puoi configurare le lingue in cui desideri tradurre il rapporto. A questo scopo, fai clic su **[!UICONTROL Localization]** scheda.

![](assets/s_ncs_advuser_report_properties_06.png)

La lingua di modifica è la lingua in cui si scrive. Quando aggiungi una lingua, la scheda secondaria viene visualizzata nella pagina di modifica del rapporto.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla localizzazione delle pagine web in Campaign, consulta [questa sezione](../../web/using/translating-a-web-form.md).

## Personalizzazione del rendering di HTML {#personalizing-html-rendering}

In **[!UICONTROL Rendering]** , puoi personalizzare la modalità di visualizzazione dei dati della pagina. Puoi selezionare:

* Il tipo di navigazione nel rapporto: tramite pulsanti o collegamenti.
* Posizione predefinita delle etichette per gli elementi del report. Questa posizione può essere sovraccaricata per ogni elemento.
* Modello o tema utilizzato per generare le pagine del rapporto.

![](assets/s_ncs_advuser_report_properties_08.png)

## Personalizzazione della pagina di errore {#personalizing-the-error-page}

Il **[!UICONTROL Error page]** La scheda ti consente di configurare il messaggio da visualizzare in caso di errore nella visualizzazione del rapporto.

Puoi definire i testi e collegarli a identificatori specifici per gestire la localizzazione dei rapporti. Per ulteriori informazioni, consulta [Aggiunta di un’intestazione e un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
