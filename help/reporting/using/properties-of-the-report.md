---
title: Proprietà del report
description: Ulteriori informazioni sulle impostazioni delle proprietà del report
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
translation-type: tm+mt
source-git-commit: b0b9a0714075474bf52c3eed78d45bcef25b44fc
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 1%

---


# Proprietà del report{#properties-of-the-report}

Puoi personalizzare e configurare il rapporto in base alle tue esigenze. A questo scopo, modificarne le proprietà. Le proprietà del report sono accessibili tramite il **[!UICONTROL Properties]** pulsante sopra il grafico della sequenza di attività.

![](assets/s_ncs_advuser_report_properties_01.png)

Le proprietà generali sono descritte di seguito. Le funzionalità avanzate configurate nelle **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** e **[!UICONTROL Scripts]** schede sono descritte [in questa sezione](../../reporting/using/advanced-functionalities.md).

## Proprietà generali {#overall-properties}

Nella **[!UICONTROL General]** scheda delle proprietà del rapporto puoi modificare le impostazioni elencate di seguito:

* Etichetta e nome interno del rapporto. L&#39;URL **[!UICONTROL Internal name]** viene utilizzato nell&#39;URL finale del report. Non deve essere modificato dopo la creazione del report.

* La **cartella** del report viene selezionata durante la creazione del report. È buona norma creare una cartella dedicata per i rapporti personalizzati in modo che non vengano mescolati ai rapporti [](../../reporting/using/about-campaign-built-in-reports.md)incorporati.

* Durante la creazione del rapporto viene selezionato **Archiviazione** . Per modificare la tabella dati del rapporto, fai clic sull&#39; **[!UICONTROL Select link]** icona a destra del **[!UICONTROL Document type]** campo.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* I parametri di controllo **di** Access. Queste impostazioni sono descritte di seguito.

## Controlling access to the report {#report-accessibility}

È possibile accedere a un rapporto dalla console  Adobe Campaign o da un browser Web. In questo caso, può essere necessario configurare il controllo di accesso al report come mostrato di seguito.

![](assets/s_ncs_advuser_report_properties_02b.png)

Le opzioni possibili sono:

* **[!UICONTROL Anonymous access]**: questa opzione consente l&#39;accesso illimitato al report. Tuttavia, non è possibile alcuna manipolazione.

   I diritti dell&#39;operatore tecnico &#39;webapp&#39; vengono utilizzati per visualizzare gli elementi del report. Ulteriori informazioni [in questa sezione](../../platform/using/access-management.md#default-operators).

* **[!UICONTROL Access control]**: questa opzione consente  operatori Adobe Campaign di accedervi una volta effettuato l&#39;accesso.
* **[!UICONTROL Specific account]**: questa opzione consente di eseguire il rapporto con i diritti dell&#39;operatore selezionato nel **[!UICONTROL Operator]** campo.

## Gestione della localizzazione dei report {#managing-report-localization}

Potete configurare le lingue in cui desiderate tradurre il rapporto. A tale scopo, fare clic sulla **[!UICONTROL Localization]** scheda.

![](assets/s_ncs_advuser_report_properties_06.png)

La lingua di modifica è la lingua in cui si scrive. Quando aggiungete una lingua, nella pagina di modifica del rapporto viene visualizzata la sottoscheda.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla localizzazione delle pagine Web in Campaign, consulta [questa sezione](../../web/using/translating-a-web-form.md).

## Personalizzazione del rendering HTML {#personalizing-html-rendering}

Nella **[!UICONTROL Rendering]** scheda, è possibile personalizzare la modalità di visualizzazione dei dati per la pagina. Potete selezionare:

* Il motore di rendering del grafico:  Adobe Campaign offre due diverse modalità per generare il rendering del grafico. Per impostazione predefinita, il motore di rendering è HTML 5. Se necessario, potete selezionare il rendering del Flash.
* Tipo di navigazione nel rapporto: tramite pulsanti o collegamenti.
* Posizione predefinita delle etichette per gli elementi del report. Questa posizione può essere sovraccaricata per ogni elemento.
* Modello o tema utilizzato per generare le pagine dei rapporti.

![](assets/s_ncs_advuser_report_properties_08.png)

## Personalizzazione della pagina di errore {#personalizing-the-error-page}

La **[!UICONTROL Error page]** scheda consente di configurare il messaggio che verrà visualizzato in caso di errore nella visualizzazione del rapporto.

Puoi definire testi e collegarli a identificatori specifici per gestire la localizzazione dei report. Per ulteriori informazioni, vedere [Aggiunta di un&#39;intestazione e di un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
