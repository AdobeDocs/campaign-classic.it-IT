---
product: campaign
title: Utilizzare un modello di contenuto
description: Utilizzare un modello di contenuto
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---

# Utilizzare un modello di contenuto{#using-a-content-template}

![](../../assets/common.svg)

## Informazioni sui modelli di contenuto {#about-content-templates}

Puoi fare riferimento ai modelli di contenuto e utilizzarli direttamente nelle consegne. Fai riferimento a [Creazione di una consegna tramite la gestione dei contenuti](#creating-a-delivery-via-content-management)

Possono anche essere utilizzati per creare istanze di contenuto. Una volta create, queste istanze sono pronte per essere distribuite (consulta [Distribuzione di un’istanza di contenuto](#delivering-a-content-instance)) o esportati (fare riferimento a [Creazione di un’istanza di contenuto](#creating-a-content-instance)).

## Creazione di una consegna tramite la gestione dei contenuti {#creating-a-delivery-via-content-management}

È possibile fare riferimento a un modello di contenuto in una consegna per utilizzare i campi di input per immettere il contenuto. Nella procedura guidata di consegna viene aggiunta una scheda aggiuntiva per la definizione del contenuto della consegna.

![](assets/s_ncs_content_deliver_a_content.png)

Il layout viene applicato automaticamente in base alle impostazioni selezionate. Per visualizzarlo, fai clic sul pulsante **[!UICONTROL HTML preview]** o **[!UICONTROL Text preview]** ) e seleziona un destinatario per testare gli elementi di personalizzazione.

![](assets/s_ncs_content_deliver_a_content_html.png)

Per ulteriori informazioni, consulta l’esempio di implementazione completo: [Creazione di contenuti nella procedura guidata di consegna](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Creazione di un’istanza di contenuto {#creating-a-content-instance}

Puoi creare contenuti direttamente nella struttura di Adobe Campaign da utilizzare nei flussi di lavoro, esportarli o inserirli direttamente nelle nuove consegne.

Applica i seguenti passaggi:

1. Seleziona la **[!UICONTROL Resources > Contents]** nodo della struttura, fare clic con il pulsante destro del mouse e scegliere **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Selezionare i modelli di pubblicazione che saranno attivi per questa cartella.

   ![](assets/s_ncs_content_folder_templates.png)

1. È ora possibile creare nuovi contenuti utilizzando **[!UICONTROL New]** sopra l’elenco dei contenuti.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Immettere i campi nel modulo.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Quindi fai clic sul pulsante **[!UICONTROL HTML preview]** per visualizzare il rendering. In questo caso, i campi di personalizzazione acquisiti dal database non vengono inseriti.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Una volta creato, il contenuto viene aggiunto all’elenco dei contenuti disponibili. Fai clic sul pulsante **[!UICONTROL Properties]** per modificare l’etichetta, lo stato o la cronologia.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Se necessario, una volta approvato il contenuto, è possibile generarlo utilizzando il pulsante appropriato sulla barra degli strumenti.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Puoi autorizzare la generazione di contenuti non approvati. A questo scopo, modifica l’opzione pertinente nel modello di pubblicazione. Per ulteriori informazioni, consulta [Creazione e configurazione del modello](publication-templates.md#creating-and-configuring-the-template).

   Il contenuto di HTML e Testo viene generato per impostazione predefinita nel **pubblicazione** della cartella dell’istanza Adobe Campaign. È possibile modificare la cartella della pubblicazione tramite la **NcmPublishingDir** opzione .

## Distribuzione di un’istanza di contenuto {#delivering-a-content-instance}

Per creare un’istanza di contenuto e consegnarla, è necessario collegare un modello di consegna al modello di pubblicazione utilizzato per generare il contenuto. Per ulteriori informazioni, consulta [Consegna](publication-templates.md#delivery).

Inoltre, la cartella di archiviazione dei contenuti deve essere dedicata ai contenuti estratti da questo modello di pubblicazione (quando una cartella di contenuto consente di generare diversi tipi di contenuto, le consegne non possono essere create automaticamente).

Per creare automaticamente la consegna in base al contenuto selezionato, fai clic sul pulsante **[!UICONTROL Delivery]** e scegli il modello.

![](assets/s_ncs_content_folder_create_the_delivery.png)

Il contenuto di testo e HTML viene immesso automaticamente.
