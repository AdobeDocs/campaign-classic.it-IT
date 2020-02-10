---
title: Utilizzo di un modello di contenuto
seo-title: Utilizzo di un modello di contenuto
description: Utilizzo di un modello di contenuto
seo-description: null
page-status-flag: never-activated
uuid: 893b9711-593f-4865-b61a-ef0fede9a2b0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 48f491b7-bf7b-457f-9cf2-db2bbf4eceea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Utilizzo di un modello di contenuto{#using-a-content-template}

## I modelli di contenuto {#about-content-templates}

È possibile fare riferimento ai modelli di contenuto e utilizzarli direttamente nelle consegne. Fare riferimento a [Creazione di una distribuzione tramite la gestione dei contenuti](#creating-a-delivery-via-content-management)

Possono anche essere utilizzati per creare istanze di contenuto. Una volta create, queste istanze sono pronte per essere distribuite (consultate [Distribuzione di un&#39;istanza](#delivering-a-content-instance)di contenuto) o esportate (consultate [Creazione di un&#39;istanza](#creating-a-content-instance)di contenuto).

## Creazione di una distribuzione tramite la gestione dei contenuti {#creating-a-delivery-via-content-management}

Potete fare riferimento a un modello di contenuto in una distribuzione per utilizzare i campi di input per immettere contenuto. Nella procedura guidata di consegna viene aggiunta una scheda aggiuntiva per la definizione del contenuto della consegna.

![](assets/s_ncs_content_deliver_a_content.png)

Il layout verrà applicato automaticamente in base alle impostazioni selezionate. Per visualizzarlo, fai clic sul **[!UICONTROL HTML preview]** (o **[!UICONTROL Text preview]** ) e seleziona un destinatario per testare gli elementi di personalizzazione.

![](assets/s_ncs_content_deliver_a_content_html.png)

Per ulteriori informazioni, consulta l’esempio completo di implementazione: [Creazione di contenuti nella procedura guidata](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard)di consegna.

## Creazione di un&#39;istanza di contenuto {#creating-a-content-instance}

Puoi creare contenuti direttamente nella struttura di Adobe Campaign da utilizzare nei flussi di lavoro, da esportare o da inserire direttamente nelle nuove consegne.

Effettuate le seguenti operazioni:

1. Selezionate il **[!UICONTROL Resources > Contents]** nodo della struttura ad albero, fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Selezionate i modelli di pubblicazione che saranno attivi per questa cartella.

   ![](assets/s_ncs_content_folder_templates.png)

1. È ora possibile creare nuovo contenuto utilizzando il **[!UICONTROL New]** pulsante situato sopra l&#39;elenco dei contenuti.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Immettere i campi nel modulo.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Fate clic sulla **[!UICONTROL HTML preview]** scheda per visualizzare il rendering. In questo caso, i campi di personalizzazione prelevati dal database non vengono inseriti.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Una volta creato, il contenuto viene aggiunto all’elenco dei contenuti disponibili. Fate clic sul **[!UICONTROL Properties]** collegamento per modificarne l’etichetta, lo stato o visualizzarne la cronologia.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Se necessario, una volta approvato il contenuto, questo può essere generato utilizzando il pulsante appropriato sulla barra degli strumenti.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Potete autorizzare la generazione di contenuti non approvati. A questo scopo, modificate l’opzione pertinente nel modello di pubblicazione. Per ulteriori informazioni, vedere [Creazione e configurazione del modello](../../delivery/using/publication-templates.md#creating-and-configuring-the-template).

   I contenuti HTML e di testo vengono generati per impostazione predefinita nella cartella di **pubblicazione** dell&#39;istanza Adobe Campaign. Potete modificare la cartella della pubblicazione tramite l’opzione **NcmPublishingDir** .

## Distribuzione di un&#39;istanza di contenuto {#delivering-a-content-instance}

Per creare un&#39;istanza di contenuto e distribuirla, è necessario collegare un modello di consegna al modello di pubblicazione utilizzato per generare il contenuto. Per ulteriori informazioni, consulta [Consegna](../../delivery/using/publication-templates.md#delivery).

Inoltre, la cartella di archiviazione dei contenuti deve essere dedicata ai contenuti tratti da questo modello di pubblicazione (quando una cartella di contenuti consente di generare diversi tipi di contenuto, non è possibile creare automaticamente le consegne).

Per creare la consegna automaticamente in base al contenuto selezionato, fate clic sull&#39; **[!UICONTROL Delivery]** icona e scegliete il modello.

![](assets/s_ncs_content_folder_create_the_delivery.png)

Il testo e il contenuto HTML vengono inseriti automaticamente.
