---
product: campaign
title: Modificare i moduli
description: Modificare i moduli
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

---


# Modificare i moduli{#editing-forms}

![](../../assets/common.svg)

## Panoramica

Gli addetti al marketing e gli operatori utilizzano moduli di input per creare, modificare e visualizzare in anteprima i record. Forms mostra una rappresentazione visiva delle informazioni.

È possibile creare e modificare i moduli di input:

* È possibile modificare i moduli di input di fabbrica consegnati per impostazione predefinita. I moduli di input di fabbrica si basano sugli schemi di dati di fabbrica.
* È possibile creare moduli di input personalizzati in base agli schemi di dati definiti dall’utente.

Forms è entità di `xtk:form` digitare. È possibile visualizzare la struttura del modulo di input nel `xtk:form` schema. Per visualizzare questo schema, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** dal menu. Ulteriori informazioni [struttura del modulo](form-structure.md).

Per accedere ai moduli di input, scegli **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** dal menu:

![](assets/d_ncs_integration_form_arbo.png)

Per progettare i moduli, modificare il contenuto XML nell’editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Leggi tutto](form-structure.md#formatting).

Per visualizzare l’anteprima di un modulo, fare clic sul pulsante **[!UICONTROL Preview]** scheda:

![](assets/d_ncs_integration_form_preview.png)

## Tipi di modulo

È possibile creare diversi tipi di moduli di input. Il tipo di modulo determina il modo in cui gli utenti navigano nel modulo:

* Schermata della console

   Questo è il tipo di modulo predefinito. Il modulo comprende una singola pagina.

   ![](assets/console_screen_form.png)

* Gestione dei contenuti

   Utilizzare questo tipo di modulo per la gestione del contenuto. Vedi questo [caso d&#39;uso](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Creazione guidata

   Questo modulo comprende più schermate mobili ordinate in sequenze specifiche. Gli utenti passano da una schermata all’altra. [Leggi tutto](form-structure.md#wizards).

* Iconbox

   Questo modulo comprende più pagine. Per spostarsi nel modulo, gli utenti selezionano le icone a sinistra del modulo.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Questo modulo comprende più pagine. Per spostarsi nel modulo, gli utenti selezionano le schede nella parte superiore del modulo.

   ![](assets/notebook_form_preview.png)

* Riquadro verticale

   Questo modulo mostra una struttura di navigazione.

* Riquadro orizzontale

   Questo modulo mostra un elenco di elementi.

