---
title: Creazione di ipotesi
seo-title: Creazione di ipotesi
description: Creazione di ipotesi
seo-description: null
page-status-flag: never-activated
uuid: 48b74772-473f-4fbc-a228-ce8e35a7b9ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 0f73de0e-e589-4e39-9895-209dad75db75
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 1%

---


# Creazione di ipotesi{#creating-hypotheses}

Esistono varie possibilità per creare/collegare ipotesi a un&#39;offerta o una consegna di campagna:

* Tramite la **[!UICONTROL Measurement hypotheses]** cartella, potete creare una nuova ipotesi basata su un modello esistente e collegarla a una consegna esistente.
* Tramite la scheda **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** in una campagna.
* Tramite l&#39; **[!UICONTROL Measurement]** opzione di consegna creata da una campagna.

Le ipotesi possono essere calcolate solo dopo che la campagna di marketing è stata avviata e che i destinatari hanno ricevuto la consegna. Se l&#39;ipotesi si basa su una proposta di offerta, quest&#39;ultima deve essere almeno presentata e deve essere ancora attiva. Le ipotesi di offerta e di consegna vengono create tramite la **[!UICONTROL Measurement hypotheses]** cartella e si basano su un modello di ipotesi. Tuttavia, è possibile fare riferimento a un&#39;ipotesi direttamente nella consegna o nella campagna prima dell&#39;inizio della campagna. In questo caso, le ipotesi verranno calcolate automaticamente dopo l&#39;avvio della campagna di marketing, in base alle impostazioni di esecuzione (per ulteriori informazioni, vedere Impostazioni [di esecuzione dei modelli di](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)ipotesi).

## Creazione di un&#39;ipotesi al volo su una consegna {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Per creare un&#39;ipotesi su una consegna esistente, eseguite il seguente processo:

>[!NOTE]
>
>Questa operazione è possibile solo per le consegne in sospeso.

1. Nella  albero di Adobe Campaign, andate a **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Fare clic sul **[!UICONTROL New]** pulsante o fare clic con il pulsante destro del mouse sull&#39;elenco delle ipotesi e selezionare **[!UICONTROL New]** nell&#39;elenco a discesa.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. Nella finestra dell&#39;ipotesi, selezionare un modello creato in precedenza (fare riferimento a Modelli [di](../../campaign/using/hypothesis-templates.md)ipotesi).

   ![](assets/response_hypothesis_instance_creation_003.png)

   Il contesto dell&#39;ipotesi definito nel modello selezionato viene visualizzato nella finestra.

   >[!NOTE]
   >
   >Le impostazioni definite nel modello e non visibili in questo passaggio vengono anche memorizzate e riassegnate all&#39;ipotesi in corso.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Selezionare la consegna per la quale si desidera creare un&#39;ipotesi.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. Potete personalizzare l&#39;ipotesi modificando le **[!UICONTROL General]**, **[!UICONTROL Transactions]** e **[!UICONTROL Scope]** le schede. Per ulteriori informazioni, vedere [Creazione di un modello](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)di ipotesi.
1. Iniziate l&#39;ipotesi facendo clic **[!UICONTROL Start]**.

   Viene creato automaticamente un flusso di lavoro per eseguire la misurazione. Il nome viene definito automaticamente in base alla configurazione dell&#39;ipotesi.

   >[!CAUTION]
   >
   >È possibile accedervi se avete selezionato la **[!UICONTROL Keep execution workflow]** casella.\
   >Questa opzione deve essere attivata solo a scopo di debug, in caso di errore durante l&#39;esecuzione dell&#39;ipotesi. I flussi di lavoro generati automaticamente vengono salvati nella cartella **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** di  Adobe Campaign Explorer.
   > 
   >Inoltre, i flussi di lavoro generati automaticamente non devono essere modificati. Eventuali modifiche non saranno prese in considerazione altrove per ulteriori calcoli.
   >
   >Se avete selezionato questa opzione, eliminate il flusso di lavoro dopo che è stato eseguito.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Una volta completato il calcolo, gli indicatori di misura vengono aggiornati automaticamente.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Se necessario, modificate le impostazioni e riavviate l’ipotesi.

## Riferimento a un&#39;ipotesi nella distribuzione di una campagna {#referencing-a-hypothesis-in-a-campaign-delivery}

Potete fare riferimento a un&#39;ipotesi in una campagna di marketing prima di avviarla. In questo caso, l&#39;ipotesi verrà avviata automaticamente dopo l&#39;invio della consegna, in base alle impostazioni di esecuzione definite nel modello di ipotesi. Per creare un&#39;ipotesi in una consegna, eseguite il seguente processo:

1. A seconda delle esigenze, potete creare uno o più modelli di **[!UICONTROL Delivery]** tipo, come descritto in [Creazione di un modello di ipotesi](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. Crea una campagna di marketing e flussi di lavoro di targeting.
1. Nella finestra consegna, fate clic sull&#39; **[!UICONTROL Delivery measurement]** icona.
1. Selezionate il modello di ipotesi (la query configurata nel modello viene visualizzata nella finestra di ipotesi).

   L&#39;ipotesi verrà calcolata automaticamente al termine della campagna, in base alle date configurate nel modello (consultate le impostazioni [di esecuzione dei modelli di](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)ipotesi).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Aggiunta di un&#39;ipotesi predefinita alle consegne per una campagna {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Potete fare riferimento direttamente a un&#39;ipotesi a livello di campagna. In questo caso, l&#39;ipotesi sarà automaticamente collegata a tutte le consegne create nella campagna. Per eseguire questa operazione:

1. Passate alla **[!UICONTROL Edit]** scheda della campagna.
1. Nella sezione relativa alla misura, fare clic sulla **[!UICONTROL Default hypotheses]** scheda.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Fate clic su **[!UICONTROL Add]** e selezionate un modello di ipotesi.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Per impostazione predefinita, a un&#39;ipotesi basata su questo modello viene fatto riferimento in ogni nuova consegna per la campagna.

   ![](assets/response_hypothesis_instance_creation_012.png)

I risultati dell&#39;ipotesi possono essere visualizzati nelle **[!UICONTROL General]** e **[!UICONTROL Reactions]** nelle schede dell&#39;ipotesi (fare riferimento al tracciamento [dell&#39;](../../campaign/using/hypothesis-tracking.md)ipotesi)

Per ulteriori informazioni, potete fare riferimento anche a [Esempio: creazione di un&#39;ipotesi collegata a una consegna](#example--creating-a-hypothesis-linked-to-a-delivery).

## Creazione di un&#39;ipotesi su un&#39;offerta {#creating-a-hypothesis-on-an-offer}

Creare un&#39;ipotesi su una proposta di offerta è simile a creare un&#39;ipotesi di consegna al volo. L&#39;ipotesi può essere eseguita finché l&#39;offerta è attiva. Il periodo di calcolo è basato sulla data di proposta dell&#39;offerta. Quando l&#39;ipotesi consente di collegare un destinatario a un acquisto, lo stato dell&#39;offerta che potrebbe essere accettata può essere modificato automaticamente (per ulteriori informazioni, fare riferimento a [Transazioni](../../campaign/using/hypothesis-templates.md#transactions)).

1. Creare uno o più modelli di **[!UICONTROL Offer]** tipo come descritto in [Creazione di un modello](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)di ipotesi.
1. Go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node.
1. Per creare un&#39;ipotesi di **[!UICONTROL Offers]** tipo, selezionate il modello creato in precedenza.

   ![](assets/response_hypothesis_instance_offer_001.png)

   La query creata nel modello viene visualizzata nella finestra.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Scegliete l&#39;offerta per la quale desiderate creare un&#39;ipotesi.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Se necessario, perfezionate la query.
1. Fare clic **[!UICONTROL Start]** per eseguire l&#39;ipotesi.
1. I risultati dell&#39;ipotesi possono essere visualizzati nelle relative **[!UICONTROL General]** e **[!UICONTROL Reactions]** schede (fare riferimento al tracciamento [dell&#39;](../../campaign/using/hypothesis-tracking.md)ipotesi).

   Le ipotesi effettuate su un&#39;offerta sono indicate nella **[!UICONTROL Measurement]** scheda.

   ![](assets/response_hypothesis_instance_offer_007.png)

   Se l&#39; **[!UICONTROL Update offer proposition status]** opzione è stata attivata nel modello di ipotesi, lo stato della proposta di offerta viene modificato automaticamente, fornendo così un feedback sull&#39;impatto della campagna (per ulteriori informazioni, fare riferimento a [Transazioni](../../campaign/using/hypothesis-templates.md#transactions)).

## Esempio: creazione di un&#39;ipotesi collegata a una consegna {#example--creating-a-hypothesis-linked-to-a-delivery}

In questo esempio, vogliamo creare un&#39;ipotesi collegata a una consegna. Questa ipotesi si basa sul modello creato in precedenza (fare riferimento a [Esempio: creazione di un modello di ipotesi su una consegna](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). La query ereditata dal modello verrà quindi perfezionata per effettuare un&#39;ipotesi su un articolo specifico della tabella di acquisto.

1. Create una campagna e una consegna (per ulteriori informazioni, consultate [Creazione di una campagna](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   Nel nostro esempio, utilizzeremo una consegna diretta per tipo di posta.

1. Configurare un indirizzo e-mail: il modello di ipotesi creato in precedenza è stato configurato per tenere conto di un gruppo di controllo nei risultati della reazione.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni, vedere [Definizione di un gruppo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)di controllo.

1. Aprite l&#39;icona **[!UICONTROL Direct mail delivery]** e fate clic sull&#39; **[!UICONTROL Delivery measurement]** icona, quindi fate clic su **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Scegliete il modello di ipotesi creato in precedenza dall’elenco a discesa.

   ![](assets/response_hypothesis_delivery_example_004.png)

   Viene visualizzata la query creata nel modello.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Fare clic **[!UICONTROL Edit query...]** e affinare la query immettendo il prodotto che l&#39;ipotesi riguarderà.

   ![](assets/response_hypothesis_delivery_example_006.png)

   Potete verificare che l&#39;ipotesi sia collegata alla distribuzione nella scheda **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** della campagna.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Avviate il flusso di lavoro di targeting ed eseguite i controlli necessari fino al completamento della campagna (per ulteriori informazioni, consultate [Avvio di una distribuzione](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Nella struttura  Adobe Campaign, andare al **[!UICONTROL Campaign management > Measurement hypotheses]** nodo per verificare gli indicatori calcolati dall&#39;ipotesi.

   ![](assets/response_hypothesis_delivery_example_010.png)

