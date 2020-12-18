---
solution: Campaign Classic
product: campaign
title: Utilizzo di un modello di contenuto
description: Utilizzo di un modello di contenuto
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---


# Utilizzo di un modello di contenuto{#using-a-content-template}

## Informazioni sui modelli di contenuto {#about-content-templates}

È possibile fare riferimento ai modelli di contenuto e utilizzarli direttamente nelle consegne. Fare riferimento a [Creazione di una distribuzione tramite la gestione dei contenuti](#creating-a-delivery-via-content-management)

Possono anche essere utilizzati per creare istanze di contenuto. Una volta create, queste istanze sono pronte per essere distribuite (fare riferimento a [Distribuzione di un&#39;istanza di contenuto](#delivering-a-content-instance)) o esportate (fare riferimento a [Creazione di un&#39;istanza di contenuto](#creating-a-content-instance)).

## Creazione di una distribuzione tramite la gestione dei contenuti {#creating-a-delivery-via-content-management}

Potete fare riferimento a un modello di contenuto in una distribuzione per utilizzare i campi di input per immettere contenuto. Alla procedura guidata di consegna viene aggiunta una scheda aggiuntiva per la definizione del contenuto della consegna.

![](assets/s_ncs_content_deliver_a_content.png)

Il layout verrà applicato automaticamente in base alle impostazioni selezionate. Per visualizzarlo, fai clic su **[!UICONTROL HTML preview]** (o **[!UICONTROL Text preview]** ) e seleziona un destinatario per testare gli elementi di personalizzazione.

![](assets/s_ncs_content_deliver_a_content_html.png)

Per ulteriori informazioni, consulta l’esempio completo di implementazione: [Creazione di contenuti nella procedura guidata di distribuzione](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Creazione di un&#39;istanza di contenuto {#creating-a-content-instance}

Potete creare contenuti direttamente nella struttura  di Adobe Campaign da usare nei flussi di lavoro, da esportare o da inserire direttamente nelle nuove consegne.

Effettuate le seguenti operazioni:

1. Selezionare il nodo **[!UICONTROL Resources > Contents]** della struttura ad albero, fare clic con il pulsante destro del mouse e scegliere **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Selezionate i modelli di pubblicazione che saranno attivi per questa cartella.

   ![](assets/s_ncs_content_folder_templates.png)

1. Ora potete creare nuovo contenuto utilizzando il pulsante **[!UICONTROL New]** sopra l&#39;elenco dei contenuti.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Immettere i campi nel modulo.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Fate clic sulla scheda **[!UICONTROL HTML preview]** per visualizzare il rendering. In questo caso, i campi di personalizzazione prelevati dal database non vengono inseriti.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Una volta creato, il contenuto viene aggiunto all’elenco dei contenuti disponibili. Fate clic sul collegamento **[!UICONTROL Properties]** per modificarne l&#39;etichetta, lo stato o visualizzarne la cronologia.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Se necessario, una volta approvato il contenuto, questo può essere generato utilizzando il pulsante appropriato sulla barra degli strumenti.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Potete autorizzare la generazione di contenuti non approvati. A questo scopo, modificate l’opzione pertinente nel modello di pubblicazione. Per ulteriori informazioni, vedere [Creazione e configurazione del modello](../../delivery/using/publication-templates.md#creating-and-configuring-the-template).

   I contenuti HTML e di testo vengono generati per impostazione predefinita nella cartella **publishing** dell&#39;istanza di Adobe Campaign . È possibile modificare la cartella della pubblicazione mediante l&#39;opzione **NcmPublishingDir**.

## Distribuzione di un&#39;istanza di contenuto {#delivering-a-content-instance}

Per creare un&#39;istanza di contenuto e distribuirla, è necessario collegare un modello di consegna al modello di pubblicazione utilizzato per generare il contenuto. Per ulteriori informazioni, vedere [Consegna](../../delivery/using/publication-templates.md#delivery).

Inoltre, la cartella di archiviazione dei contenuti deve essere dedicata ai contenuti tratti da questo modello di pubblicazione (quando una cartella di contenuti consente di generare diversi tipi di contenuto, non è possibile creare automaticamente le consegne).

Per creare la consegna automaticamente in base al contenuto selezionato, fate clic sull&#39;icona **[!UICONTROL Delivery]** e scegliete il modello.

![](assets/s_ncs_content_folder_create_the_delivery.png)

Il testo e il contenuto HTML vengono inseriti automaticamente.
