---
product: campaign
title: Creazione di ipotesi
description: Scopri come creare ipotesi in Campaign Response Manager
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 3%

---

# Creare ipotesi{#creating-hypotheses}

![](../../assets/v7-only.svg)

Esistono varie possibilità per creare/collegare ipotesi a un’offerta o a una consegna di campagna:

* Tramite il **[!UICONTROL Measurement hypotheses]** creando una nuova ipotesi basata su un modello esistente e collegandolo a una consegna esistente.
* Tramite il **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** in una campagna.
* Tramite il **[!UICONTROL Measurement]** di una consegna creata da una campagna.

Le ipotesi possono essere calcolate solo dopo l’avvio della campagna di marketing e dopo che i destinatari hanno ricevuto la consegna. Se l&#39;ipotesi si basa su una proposta di offerta, quest&#39;ultima deve almeno essere presentata ed essere ancora attiva. Le ipotesi di offerta e consegna vengono create tramite il **[!UICONTROL Measurement hypotheses]** e si basano su un modello di ipotesi. Tuttavia, è possibile fare riferimento a un&#39;ipotesi direttamente nella consegna o nella campagna prima dell&#39;inizio della campagna. In questo caso, le ipotesi vengono calcolate automaticamente una volta avviata la campagna di marketing, in base alle impostazioni di esecuzione. [Ulteriori informazioni](hypothesis-templates.md#hypothesis-template-execution-settings)

## Crea un&#39;ipotesi al volo su una consegna {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Per creare un&#39;ipotesi su una consegna esistente, applica il seguente processo:

>[!NOTE]
>
>Questa operazione è possibile solo per le consegne in sospeso.

1. Nell’albero di Adobe Campaign, vai a **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Fai clic sul pulsante **[!UICONTROL New]** fare clic con il pulsante destro del mouse sull&#39;elenco delle ipotesi e selezionare **[!UICONTROL New]** nell’elenco a discesa.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. Nella finestra delle ipotesi, selezionare un modello creato in precedenza. [Ulteriori informazioni](hypothesis-templates.md)

   ![](assets/response_hypothesis_instance_creation_003.png)

   Il contesto dell&#39;ipotesi definito nel modello selezionato viene visualizzato nella finestra.

   >[!NOTE]
   >
   >Anche le impostazioni definite nel modello e non visibili in questo passaggio vengono memorizzate e riassegnate all&#39;ipotesi in corso.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Selezionare la consegna per la quale si desidera creare un&#39;ipotesi.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. Puoi personalizzare la tua ipotesi modificando il **[!UICONTROL General]**, **[!UICONTROL Transactions]** e **[!UICONTROL Scope]** schede. [Ulteriori informazioni](hypothesis-templates.md#creating-a-hypothesis-model)
1. Avvia l&#39;ipotesi facendo clic su **[!UICONTROL Start]**.

   Viene creato automaticamente un flusso di lavoro per eseguire la misurazione. Il nome viene definito automaticamente a seconda della configurazione dell&#39;ipotesi.

   >[!CAUTION]
   >
   >Puoi accedervi se hai selezionato la **[!UICONTROL Keep execution workflow]** scatola.\
   >Questa opzione deve essere attivata solo a scopo di debug, in caso di errore durante l&#39;esecuzione dell&#39;ipotesi. I flussi di lavoro generati automaticamente vengono salvati nel **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** in Adobe Campaign Explorer.
   > 
   >Inoltre, i flussi di lavoro generati automaticamente non devono essere modificati. Qualsiasi eventuale modifica non sarà presa in considerazione altrove per calcoli successivi.
   >
   >Se hai selezionato questa opzione, elimina il flusso di lavoro dopo l’esecuzione.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Una volta completato il calcolo, gli indicatori di misura vengono aggiornati automaticamente.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Se necessario, modificare le impostazioni e riavviare l&#39;ipotesi.

## Fai riferimento a un’ipotesi in una consegna della campagna {#referencing-a-hypothesis-in-a-campaign-delivery}

Puoi fare riferimento a un’ipotesi in una campagna di marketing prima di avviarla. In questo caso, l’ipotesi verrà avviata automaticamente una volta inviata la consegna, in base alle impostazioni di esecuzione definite nel modello di ipotesi. Per creare un&#39;ipotesi in una consegna, applica il seguente processo:

1. A seconda delle tue esigenze, puoi crearne una o più **[!UICONTROL Delivery]** modelli di tipo , come descritto in [questa sezione](hypothesis-templates.md#creating-a-hypothesis-model)
1. Crea una campagna di marketing e flussi di lavoro di targeting.
1. Nella finestra di consegna, fai clic sul pulsante **[!UICONTROL Delivery measurement]** icona.
1. Selezionare il modello di ipotesi (la query configurata nel modello viene visualizzata nella finestra di ipotesi).

   L’ipotesi viene calcolata automaticamente al termine della campagna, in base alle date configurate nel modello. [Ulteriori informazioni](hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## Aggiungere un’ipotesi predefinita alle consegne per una campagna {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

È possibile fare riferimento direttamente a un&#39;ipotesi a livello di campagna. In questo caso, l’ipotesi verrà automaticamente collegata a tutte le consegne create nella campagna. Per eseguire questa operazione:

1. Vai a **[!UICONTROL Edit]** scheda della campagna.
1. Nella sezione di misurazione, fai clic sul pulsante **[!UICONTROL Default hypotheses]** scheda .

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Fai clic su **[!UICONTROL Add]** e selezionare un modello di ipotesi.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Per impostazione predefinita, in ogni nuova consegna per la campagna viene ora fatto riferimento a un’ipotesi basata su questo modello.

   ![](assets/response_hypothesis_instance_creation_012.png)

I risultati dell&#39;ipotesi possono essere visualizzati nel **[!UICONTROL General]** e **[!UICONTROL Reactions]** schede dell&#39;ipotesi. [Ulteriori informazioni](hypothesis-tracking.md)

Per ulteriori informazioni, puoi anche fare riferimento a [questo campione](#example--creating-a-hypothesis-linked-to-a-delivery).

## Creare un’ipotesi su un’offerta {#creating-a-hypothesis-on-an-offer}

La creazione di un&#39;ipotesi su una proposta di offerta è simile alla creazione di un&#39;ipotesi di consegna rapida. L’ipotesi può essere eseguita finché l’offerta è attiva. Il periodo di calcolo si basa sulla data della proposta di offerta. Quando l’ipotesi ti consente di collegare un destinatario a un acquisto, lo stato della proposta di offerta che probabilmente verrà accettata può essere modificato automaticamente. [Ulteriori informazioni](hypothesis-templates.md#transactions)

1. Crea uno o più **[!UICONTROL Offer]** modelli di tipo descritti in [questa sezione](hypothesis-templates.md#creating-a-hypothesis-model).
1. Vai a **[!UICONTROL Campaign management > Measurement hypotheses]** nodo.
1. Crea un **[!UICONTROL Offers]** digitate ipotesi selezionando il modello creato in precedenza.

   ![](assets/response_hypothesis_instance_offer_001.png)

   La query creata nel modello viene visualizzata nella finestra.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Scegli l’offerta per la quale desideri creare un’ipotesi.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Se necessario, perfeziona la query.
1. Fai clic su **[!UICONTROL Start]** per fare l&#39;ipotesi.
1. I risultati dell&#39;ipotesi possono essere visualizzati nella sua **[!UICONTROL General]** e **[!UICONTROL Reactions]** schede. [Ulteriori informazioni](hypothesis-tracking.md)

   Le ipotesi effettuate su un’offerta sono riportate nella variabile **[!UICONTROL Measurement]** scheda .

   ![](assets/response_hypothesis_instance_offer_007.png)

   Se la **[!UICONTROL Update offer proposition status]** opzione abilitata nel modello di ipotesi, lo stato della proposta di offerta viene modificato automaticamente, fornendo così un feedback sull’impatto della campagna (per ulteriori informazioni, consulta [Transazioni](hypothesis-templates.md#transactions)).

## Esempio: creare un&#39;ipotesi collegata a una consegna {#example--creating-a-hypothesis-linked-to-a-delivery}

In questo esempio, vogliamo creare un&#39;ipotesi collegata a una consegna. Questa ipotesi sarà basata sul modello creato in precedenza. [Ulteriori informazioni](hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)

Quindi perfezioneremo la query ereditata dal modello per fare un&#39;ipotesi su un articolo specifico della tabella di acquisto.

1. Creare una campagna e una consegna. [Ulteriori informazioni](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)

   Nel nostro esempio, utilizzeremo una consegna di tipo direct mailing.

1. Configura un indirizzo di seed: il modello di ipotesi creato in precedenza è stato configurato per tenere conto di un gruppo di controllo nei risultati della reazione.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni, consulta [questa sezione](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

1. Apri **[!UICONTROL Direct mail delivery]** e fai clic su **[!UICONTROL Delivery measurement]** icona, quindi fai clic su **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Scegli il modello di ipotesi creato in precedenza dall’elenco a discesa.

   ![](assets/response_hypothesis_delivery_example_004.png)

   Viene visualizzata la query creata nel modello.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Fai clic su **[!UICONTROL Edit query...]** e affina la query inserendo il prodotto che l&#39;ipotesi riguarda.

   ![](assets/response_hypothesis_delivery_example_006.png)

   Puoi verificare che l’ipotesi sia collegata alla consegna nel **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** scheda della campagna.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Avvia il flusso di lavoro di targeting ed esegui i controlli necessari fino al termine della campagna. [Ulteriori informazioni](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Nell’albero di Adobe Campaign, vai alla pagina **[!UICONTROL Campaign management > Measurement hypotheses]** nodo per controllare gli indicatori calcolati dall&#39;ipotesi.

   ![](assets/response_hypothesis_delivery_example_010.png)
