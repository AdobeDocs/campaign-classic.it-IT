---
product: campaign
title: Testare modelli di messaggi transazionali
description: Scopri come gestire gli indirizzi di seed nei messaggi transazionali per visualizzarli in anteprima e testarli in Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 3%

---

# Testare modelli di messaggi transazionali {#testing-message-templates}



Una volta [modello di messaggio](../../message-center/using/creating-the-message-template.md) è pronto, segui i passaggi seguenti per visualizzarlo in anteprima e testarlo.

## Gestire gli indirizzi seed nei messaggi transazionali {#managing-seed-addresses-in-transactional-messages}

Un indirizzo di seed ti consente di visualizzare un’anteprima del messaggio, inviare una bozza e testare la personalizzazione del messaggio prima della consegna e-mail o SMS. Gli indirizzi di seed sono collegati alla consegna e non possono essere utilizzati per altre consegne.

Per creare indirizzi di seed in un messaggio transazionale, segui i passaggi seguenti:

1. Nel modello per messaggi transazionali, fai clic su **[!UICONTROL Seed addresses]** scheda.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Assegna un’etichetta per facilitarne la selezione in un secondo momento.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Immetti l’indirizzo seed (e-mail o telefono cellulare a seconda del canale di comunicazione).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Immetti l’identificatore esterno: questo campo opzionale ti consente di immettere una chiave aziendale (ID univoco, nome + e-mail, ecc.) comune a tutte le applicazioni sul sito web, utilizzato per identificare i profili. Se questo campo è presente anche nel database di marketing di Adobe Campaign, puoi riconciliare un evento con un profilo nel database.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Inserire i dati di prova (fare riferimento a [Dati di personalizzazione](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Fai clic su **[!UICONTROL Add other seed addresses]** , quindi fare clic sul pulsante **[!UICONTROL Add]** pulsante.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Ripeti il processo per creare tutti gli indirizzi necessari.

   ![](assets/messagecenter_create_seedaddr_008.png)

Una volta creati gli indirizzi, puoi visualizzarne l’anteprima e la personalizzazione. Fai riferimento a [Anteprima di un messaggio transazionale](#transactional-message-preview).

## Dati di personalizzazione {#personalization-data}

È possibile utilizzare i dati nel modello del messaggio per testare la personalizzazione dei messaggi transazionali. Questa funzionalità viene utilizzata per generare un’anteprima o inviare una bozza. Puoi anche visualizzare il rendering del messaggio per vari provider di accesso a Internet. Per ulteriori informazioni, consulta [Rendering casella in entrata](../../delivery/using/inbox-rendering.md).

Lo scopo di questi dati è quello di testare i messaggi prima della loro consegna finale. Questi messaggi non coincidono con i dati effettivi da elaborare. Tuttavia, la struttura XML deve essere identica a quella dell’evento memorizzato nell’istanza di esecuzione, come illustrato di seguito:

![](assets/messagecenter_create_custo_006.png)

Queste informazioni ti consentono di personalizzare il contenuto dei messaggi utilizzando i tag di personalizzazione (per ulteriori informazioni, consulta [Creare il contenuto del messaggio](../../message-center/using/creating-the-message-template.md#creating-message-content)).

1. Seleziona il modello di messaggio transazionale.

1. Nel modello, fai clic su **[!UICONTROL Seed addresses]** scheda.

1. Nel contenuto dell&#39;evento, immettere le informazioni del test in formato XML.

   ![](assets/messagecenter_create_custo_001.png)

1. Fai clic su **[!UICONTROL Save]**.

## Anteprima di un messaggio transazionale {#transactional-message-preview}

Dopo aver creato uno o più indirizzi di seed e il corpo del messaggio, puoi visualizzare l’anteprima del messaggio e controllarne la personalizzazione.

1. Nel modello di messaggio, fai clic su **[!UICONTROL Preview]** scheda.

   ![](assets/messagecenter_preview_001.png)

1. Seleziona **[!UICONTROL A seed address]** nell’elenco a discesa.

   ![](assets/messagecenter_preview_002.png)

1. Seleziona l’indirizzo seed creato in precedenza per visualizzare il messaggio personalizzato.

   ![](assets/messagecenter_create_seedaddr_009.png)

Utilizzando gli indirizzi seed, puoi anche visualizzare il rendering del messaggio per vari provider di accesso a Internet. Per ulteriori informazioni, consulta [Rendering casella in entrata](../../delivery/using/inbox-rendering.md).

## Inviare una bozza {#sending-a-proof}

Puoi verificare la consegna dei messaggi inviando una bozza a un indirizzo seed creato in precedenza.

L’invio di una bozza prevede lo stesso processo di una [consegna regolare](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Tuttavia, con la messaggistica transazionale, devi eseguire in anticipo le seguenti operazioni:

* Crea uno o più [indirizzi seed](#managing-seed-addresses-in-transactional-messages) con [dati di personalizzazione](#personalization-data).
* [Creare il contenuto del messaggio](../../message-center/using/creating-the-message-template.md#creating-message-content).

Per inviare la bozza:

1. Fai clic su **[!UICONTROL Send a proof]** nella finestra di consegna.
1. Analizza la consegna.
1. Correggi eventuali errori e conferma la consegna.

   ![](assets/messagecenter_send_proof_001.png)

1. Verifica che il messaggio sia stato recapitato all’indirizzo di seed e che il suo contenuto sia conforme alla configurazione.

   ![](assets/messagecenter_send_proof_002.png)

Le bozze sono accessibili in ogni modello tramite **[!UICONTROL Audit]** scheda. Per maggiori dettagli, consulta [Inviare una bozza](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

![](assets/messagecenter_send_proof_003.png)

Il modello di messaggio è ora pronto per essere [pubblicato](../../message-center/using/publishing-message-templates.md).