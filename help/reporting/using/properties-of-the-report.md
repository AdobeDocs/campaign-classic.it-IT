---
product: campaign
title: Proprietà del rapporto
description: Ulteriori informazioni sulle impostazioni delle proprietà del report
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 7fa8cea04fb4e25187c48ad19330815e9b522b37
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# Proprietà del rapporto{#properties-of-the-report}

![](../../assets/common.svg)

Puoi personalizzare e configurare completamente il rapporto in base alle tue esigenze. A questo scopo, modificane le proprietà. Le proprietà dei rapporti sono accessibili tramite la **[!UICONTROL Properties]** sopra il grafico a sequenza di attività.

![](assets/s_ncs_advuser_report_properties_01.png)

Le proprietà generali sono descritte di seguito. Funzionalità avanzate configurate nel **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** e **[!UICONTROL Scripts]** sono descritte le schede [in questa sezione](../../reporting/using/advanced-functionalities.md).

## Proprietà generali {#overall-properties}

In **[!UICONTROL General]** scheda delle proprietà del rapporto, puoi modificare le impostazioni elencate di seguito:

* Etichetta e nome interno del rapporto. La **[!UICONTROL Internal name]** viene utilizzato nell&#39;URL finale del report. Non deve essere modificato dopo la creazione del rapporto.

* Il rapporto **Cartella** viene selezionato durante la creazione del rapporto. È consigliabile creare una cartella dedicata per i rapporti personalizzati in modo che non vengano mescolati con [report incorporati](../../reporting/using/about-campaign-built-in-reports.md).

* La **Storage** viene selezionato durante la creazione del rapporto. Per modificare la tabella dati del rapporto, fai clic sul pulsante **[!UICONTROL Select link]** a destra della **[!UICONTROL Document type]** campo .

   ![](assets/s_ncs_advuser_report_properties_02.png)

* La **Controllo dell&#39;accesso** Parametri. Queste impostazioni sono descritte di seguito.

## Controllo dell’accesso al report {#report-accessibility}

Un rapporto è accessibile dalla console Adobe Campaign o da un browser web. In questo caso, può essere necessario configurare il controllo di accesso al report come mostrato di seguito.

![](assets/s_ncs_advuser_report_properties_02b.png)

Le opzioni possibili sono:

* **[!UICONTROL Anonymous access]**: questa opzione consente l’accesso illimitato al report. Tuttavia, non è possibile alcuna manipolazione.

   Le autorizzazioni dell’operatore tecnico &quot;webapp&quot; vengono utilizzate per visualizzare gli elementi del rapporto. Ulteriori informazioni [in questa sezione](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: questa opzione consente agli operatori Adobe Campaign di accedervi una volta connessi.
* **[!UICONTROL Specific account]**: questa opzione ti consente di eseguire il rapporto con i diritti dell’operatore selezionato in **[!UICONTROL Operator]** campo .

## Gestione della localizzazione dei report {#managing-report-localization}

Puoi configurare le lingue in cui desideri tradurre il rapporto. A questo scopo, fai clic sul pulsante **[!UICONTROL Localization]** scheda .

![](assets/s_ncs_advuser_report_properties_06.png)

Il linguaggio di modifica è la lingua in cui si scrive. Quando aggiungi una lingua, nella pagina di modifica del rapporto viene visualizzata la sottoscheda .

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla localizzazione delle pagine web in Campaign, consulta [questa sezione](../../web/using/translating-a-web-form.md).

## Personalizzazione del rendering di HTML {#personalizing-html-rendering}

In **[!UICONTROL Rendering]** è possibile personalizzare la modalità di visualizzazione dei dati per la pagina. Puoi selezionare:

* Tipo di navigazione nel rapporto: tramite pulsanti o collegamenti.
* Posizione predefinita delle etichette per gli elementi del report. Questa posizione può essere sovraccaricata per ogni elemento.
* Il modello o il tema utilizzato per generare le pagine dei rapporti.

![](assets/s_ncs_advuser_report_properties_08.png)

## Personalizzazione della pagina di errore {#personalizing-the-error-page}

La **[!UICONTROL Error page]** consente di configurare il messaggio che verrà visualizzato in caso di errore nella visualizzazione del rapporto.

Puoi definire i testi e collegarli a identificatori specifici per gestire la localizzazione dei report. Per ulteriori informazioni, consulta [Aggiunta di un’intestazione e di un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
