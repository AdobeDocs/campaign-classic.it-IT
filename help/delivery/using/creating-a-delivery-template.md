---
product: campaign
title: Creare un modello di consegna
description: Creare un modello di consegna
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Delivery Templates
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 7%

---

# Creazione di un modello di consegna{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#delivery-template-video)

## Conversione di una consegna esistente in un modello {#converting-an-existing-delivery-to-a-template}

Una consegna può essere convertita in un modello per nuove azioni di consegna ripetute. Per convertire una consegna in un modello, selezionala dall’elenco di consegna, accessibile tramite **[!UICONTROL Campaign management]** dell&#39;albero.

Fai clic con il pulsante destro del mouse e seleziona (Copia negli Appunti) **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Crea un modello di consegna dalla consegna selezionata. È necessario immettere la cartella in cui viene salvata (nel **[!UICONTROL Folder]** ) e la cartella in cui vengono create le consegne basate su questo modello (nel **[!UICONTROL Execution folder]** ).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Per ulteriori informazioni sulla modalità di configurazione, consulta [Collegamento del modello a una consegna](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Creazione di un nuovo modello {#creating-a-new-template}

>[!NOTE]
>
>Per evitare errori di configurazione, l’Adobe consiglia di duplicare un modello nativo e personalizzarne le impostazioni anziché crearne uno nuovo.

Per configurare un modello di consegna, effettua le seguenti operazioni:

1. Apri Campaign Explorer.
1. In **Risorse** cartella, seleziona **Modelli** allora **Modelli di consegna**.

   ![](assets/delivery_template_1.png)

1. Clic **Nuovo** nella barra degli strumenti per creare un nuovo modello di consegna, oppure **Duplica** un modello esistente.

   ![](assets/delivery_template_2.png)

1. Modifica il **Etichetta** e **Nome interno** della cartella.
1. Salva il modello e riaprilo.
1. Fai clic su **Proprietà** e quindi modificare i valori in base alle proprie esigenze.

   ![](assets/delivery_template_3.png)

1. In **Generale** , confermare o modificare le posizioni selezionate nella scheda **Cartella di esecuzione**, **Cartella**, e **Indirizzamento** menu a discesa.

   ![](assets/delivery_template_4.png)

1. Completa il **Parametri e-mail** categoria con l’oggetto dell’e-mail e la popolazione target.
1. Aggiungi il **Contenuto HTML** per personalizzare il modello, puoi visualizzare un collegamento a una pagina speculare e un collegamento per annullare l’abbonamento.
1. Seleziona la **Anteprima** scheda. In **Test personalizzazione** menu a discesa, seleziona **Destinatario** per visualizzare in anteprima il modello come profilo scelto.

   ![](assets/delivery_template_5.png)

1. Clic **Salva**. Il modello è ora pronto per essere utilizzato in una consegna.


## Video tutorial {#delivery-template-video}

### Come configurare un modello di consegna

Il video seguente illustra come configurare un modello per una consegna ad hoc.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### Impostare le proprietà dei modelli di consegna

Il video seguente mostra come impostare le proprietà del modello di consegna e spiega in dettaglio ciascuna proprietà.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### Come distribuire un modello di consegna ad hoc

Questo video spiega come distribuire un modello di consegna e-mail ad hoc e la differenza tra una consegna e-mail e un flusso di lavoro di consegna.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
