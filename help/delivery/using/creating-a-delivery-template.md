---
solution: Campaign Classic
product: campaign
title: Creazione di un modello di consegna
description: Creazione di un modello di consegna
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 6335c1cd327a83dbc8c4d43c4ab795b84531c3e1
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 6%

---


# Creazione di un modello di consegna{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#delivery-template-video)

## Conversione di una consegna esistente in un modello {#converting-an-existing-delivery-to-a-template}

Una consegna può essere convertita in un modello per nuove azioni di consegna ripetute. Per convertire una consegna in un modello, selezionatela dall&#39;elenco di consegna, accessibile tramite il **[!UICONTROL Campaign management]** nodo della struttura.

Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Questa azione crea un modello di consegna dal recapito selezionato. È necessario immettere la cartella in cui viene salvato (nel **[!UICONTROL Folder]** campo) e la cartella in cui vengono create le consegne create in base a questo modello (nel **[!UICONTROL Execution folder]** campo).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Per ulteriori informazioni sulla modalità di configurazione, vedere [Collegamento del modello a una consegna](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Creazione di un nuovo modello {#creating-a-new-template}

Per configurare un modello di consegna, eseguite i seguenti passaggi:

1. Aprite Campaign Explorer.
1. Nella cartella **Risorse** , selezionate **Modelli** e quindi Modelli **di** consegna.

   ![](assets/delivery_template_1.png)

1. Fate clic su **Nuovo** nella barra degli strumenti per creare un nuovo modello di consegna.

   ![](assets/delivery_template_2.png)

1. Modificate l’ **etichetta** e il nome **** interno della cartella.
1. Salvate il modello e riapritelo.
1. Fate clic sul pulsante **Proprietà** , quindi modificate i valori in base alle vostre esigenze.

   ![](assets/delivery_template_3.png)

1. Nella scheda **Generale** , confermate o modificate le posizioni selezionate nei menu a discesa Cartella **** esecuzione, **Cartella** e **Ciclo** .

   ![](assets/delivery_template_4.png)

1. Completa la categoria dei parametri **** e-mail con l’oggetto e la popolazione dell’e-mail.
1. Aggiungete il contenuto **** HTML per personalizzare il modello, potete visualizzare un collegamento di pagina mirror e un collegamento di annullamento dell&#39;iscrizione.
1. Select the **Preview** tab. Nel menu a discesa **Personalizzazione** test, selezionate **Destinatario** per visualizzare in anteprima il modello come profilo scelto.

   ![](assets/delivery_template_5.png)

1. Fai clic su **Salva**. Il modello è ora pronto per essere utilizzato in una consegna.

>[!NOTE]
>
>Per evitare errori di configurazione, è consigliabile duplicare un modello nativo e modificarne le proprietà anziché creare un nuovo modello.

## Video tutorial {#delivery-template-video}

### Come configurare un modello di consegna

Il seguente video illustra come configurare un modello per una distribuzione ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### Come impostare le proprietà dei modelli di consegna

Il seguente video mostra come impostare le proprietà del modello di consegna e spiega in dettaglio ciascuna proprietà.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### Come distribuire un modello di consegna ad hoc

Questo video spiega come distribuire un modello di consegna e-mail ad hoc e spiega la differenza tra una consegna e-mail e un flusso di lavoro per la consegna.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Ulteriori video Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).