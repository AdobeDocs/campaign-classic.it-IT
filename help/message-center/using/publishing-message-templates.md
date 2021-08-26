---
product: campaign
title: 'Pubblicare modelli di messaggio '
description: Scopri la pubblicazione e l’annullamento della pubblicazione dei modelli di messaggio transazionali in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Pubblicare modelli di messaggio {#publishing-template-messages}

![](../../assets/v7-only.svg)

## Pubblicazione di modelli {#template-publication}

Quando il [modello di messaggio](../../message-center/using/creating-the-message-template.md) creato sull&#39;istanza di controllo è completo e una volta verificato [](../../message-center/using/testing-message-templates.md), puoi pubblicarlo. Questo processo lo pubblicherà anche su tutte le istanze di esecuzione.

La pubblicazione ti consente di creare automaticamente **due modelli di messaggio** sulle istanze di esecuzione, che ti consentono di inviare messaggi collegati a **eventi in tempo reale** e **eventi batch**.

>[!NOTE]
>
>Quando si pubblicano modelli di messaggi transazionali, anche le regole di tipologia vengono pubblicate automaticamente sulle istanze di esecuzione.

>[!IMPORTANT]
>
>Ogni volta che apporti modifiche a un modello, accertati di pubblicarlo nuovamente affinché queste modifiche siano effettive durante la consegna dei messaggi transazionali.

1. Nell&#39;istanza di controllo, passare alla cartella **[!UICONTROL Message Center > Transactional message templates]** della struttura ad albero.
1. Seleziona il modello da pubblicare sulle istanze di esecuzione.
1. Fai clic su **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Al termine della pubblicazione, nella struttura dell’istanza di produzione nella cartella **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** vengono creati entrambi i modelli di messaggio da applicare agli eventi batch e in tempo reale.

![](assets/messagecenter_deployed_model_001.png)

Una volta pubblicato un modello, se viene attivato l’evento corrispondente, l’istanza di esecuzione riceverà l’evento, lo collegherà al modello transazionale e invierà il messaggio transazionale corrispondente a ciascun destinatario. Per ulteriori informazioni, consulta [Elaborazione di eventi](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Se sostituisci un campo esistente del modello di messaggio transazionale, ad esempio l’indirizzo del mittente, con un valore vuoto, il campo corrispondente nelle istanze di esecuzione non verrà aggiornato una volta che il messaggio sulle transazioni viene pubblicato nuovamente. Conterrà ancora il valore precedente.
>
>Tuttavia, se aggiungi un valore non vuoto, il campo corrispondente verrà aggiornato come di consueto dopo la pubblicazione successiva.

## Annullamento della pubblicazione di modelli {#template-unpublication}

Una volta pubblicato un modello di messaggio sulle istanze di esecuzione, puoi annullarne la pubblicazione. Per ulteriori informazioni sul processo di pubblicazione dei modelli, consulta [questa sezione](#template-publication).

* In effetti, un modello pubblicato può ancora essere chiamato se viene attivato l’evento corrispondente: se non utilizzi più un modello di messaggio, è consigliabile annullarne la pubblicazione. In questo modo si evita di inviare per errore un messaggio sulle transazioni indesiderato.

   Ad esempio, hai pubblicato un modello di messaggio da utilizzare solo per le campagne di Natale. Puoi annullare la pubblicazione dopo la fine del periodo natalizio e pubblicarlo nuovamente l’anno prossimo.

* Inoltre, non puoi eliminare un modello di messaggio transazionale con lo stato **[!UICONTROL Published]** . Per prima cosa devi annullarla pubblicazione.

>[!NOTE]
>
>Questa funzionalità è disponibile a partire dalla versione 20.2 di Campaign.

Per annullare la pubblicazione di un modello di messaggio sulle transazioni, segui i passaggi riportati di seguito.

1. Nell&#39;istanza di controllo, passare alla cartella **[!UICONTROL Message Center > Transactional message templates]** della struttura ad albero.
1. Seleziona il modello da annullare la pubblicazione.
1. Fai clic su **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Fai clic su **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Lo stato del modello di messaggio transazionale cambia da **[!UICONTROL Published]** a **[!UICONTROL Being edited]**.

Al termine dell’annullamento della pubblicazione:

* Entrambi i modelli di messaggio (applicati a eventi di tipo batch e in tempo reale) vengono eliminati da ogni istanza di esecuzione.

   Non vengono più visualizzati nella cartella **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (consulta [questa sezione](#template-publication)).

* Una volta che un modello viene annullato, puoi eliminarlo dall’istanza di controllo.

   A tale scopo, selezionalo dall’elenco e fai clic sul pulsante **[!UICONTROL Delete]** in alto a destra dello schermo.
