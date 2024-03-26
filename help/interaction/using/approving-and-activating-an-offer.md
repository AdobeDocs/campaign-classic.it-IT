---
product: campaign
title: Approvazione e attivazione di un’offerta
description: Approvazione e attivazione di un’offerta
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Approvazione e attivazione di un’offerta{#approving-and-activating-an-offer}



Una volta completato il contenuto dell’offerta, devi approvarlo affinché possa essere duplicato nell’ambiente live e consegnato. L’approvazione riguarda il contenuto dell’offerta e la sua idoneità.

Il banner sul dashboard delle offerte indica se l’offerta deve o meno superare il ciclo di approvazione.

![](assets/offer_validate_001.png)

## Approvazione del contenuto delle offerte {#approving-offer-content}

Approvando il contenuto dell’offerta si selezionano le rappresentazioni da rendere disponibili nell’ambiente live.

Il contenuto di un’offerta ha una rappresentazione per spazio. Poiché ogni spazio dell’offerta ha la propria struttura e le proprie funzioni di rendering, la rappresentazione dell’offerta può variare.

Puoi scegliere di approvare il contenuto dell’offerta in alcuni spazi disponibili e rifiutarlo in altri.

>[!IMPORTANT]
>
>Una volta approvati il contenuto e l’idoneità di un’offerta, il flusso di lavoro di pubblicazione (notifica di offerta) viene eseguito automaticamente e l’offerta viene resa live e disponibile su tutti gli spazi attivati.

Per approvare il contenuto dell’offerta, effettua le seguenti operazioni:

1. Fai clic su **[!UICONTROL Approval]** e seleziona **[!UICONTROL Approve content]** nel popup.

   ![](assets/offer_validate_002.png)

1. Dall’elenco a discesa, seleziona le rappresentazioni da continuare a modificare o quelle da pubblicare nell’ambiente live, quindi fai clic su **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   Una volta approvato il contenuto dell’offerta, le informazioni vengono aggiornate nella tabella del dashboard delle offerte.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >Il **[!UICONTROL Content approved]** la menzione non significa che tutte le rappresentazioni di offerta siano state abilitate e approvate. Indica che il processo di approvazione del contenuto è stato completato, indipendentemente dal fatto che tutte le offerte siano state abilitate/approvate o meno.

## Approvazione idoneità offerta {#approving-offer-eligibility}

L’approvazione dell’idoneità per l’offerta comporta l’accettazione o il rifiuto dei pesi dell’offerta e delle regole di idoneità configurate anche nell’offerta o ereditate dalle regole create nella categoria principale.

>[!IMPORTANT]
>
>Una volta approvati il contenuto e l’idoneità di un’offerta, il flusso di lavoro di pubblicazione (notifica di offerta) viene eseguito automaticamente e l’offerta viene resa live e disponibile su tutti gli spazi attivati.

* Per visualizzare l’elenco completo delle regole, fai clic su **[!UICONTROL Schedule and eligibility rules]**.

  ![](assets/offer_validate_005.png)

* Per modificare le regole di idoneità, fai clic su **[!UICONTROL Reject]**, quindi fai clic su **[!UICONTROL Eligibility approval]**.

  ![](assets/offer_validate_007.png)

  I vari stati vengono aggiornati nel dashboard delle offerte.

  ![](assets/offer_validate_006.png)

* Per accettare l’idoneità dell’offerta, fai clic su **[!UICONTROL Approve eligibility]**.

  ![](assets/offer_validate_008.png)

  Approva l’idoneità, aggiungi un commento se necessario, quindi fai clic su **[!UICONTROL Eligibility approval]**.

  ![](assets/offer_validate_009.png)

  I vari stati vengono aggiornati nel dashboard delle offerte.

  ![](assets/offer_validate_010.png)

## Tracciamento approvazione {#approval-tracking}

Il tracciamento delle approvazioni è disponibile nel dashboard delle offerte. Clic **[!UICONTROL Hide/display logs]** per accedervi.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Il tracciamento è disponibile anche nel **[!UICONTROL Audit]** dell’offerta, con i dettagli dei commenti dei revisori.

## Riavvia l’approvazione {#restart-the-approval}

Una volta avviata, l’approvazione può essere riavviata. A questo scopo, segui queste istruzioni:

1. Clic **[!UICONTROL Content approved]** nel dashboard delle offerte.
1. In **[!UICONTROL Edit]** visualizzata, seleziona l’approvazione da riavviare, quindi fai clic su **[!UICONTROL Re-initialize approval to submit it again]**.
1. Conferma facendo clic su **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## Pubblicazione dell’offerta {#publishing-the-offer}

Dopo aver approvato sia il contenuto che l’idoneità di un’offerta, l’offerta viene pubblicata da un flusso di lavoro che viene eseguito automaticamente per ogni offerta il cui ciclo di approvazione è stato completato. Il **[!UICONTROL Offer notification]** il flusso di lavoro viene inoltre eseguito ogni ora per sincronizzare (se necessario) gli spazi e le categorie contenuti nel catalogo delle offerte dall’ambiente di progettazione all’ambiente live.

Il dashboard dell’offerta disponibile nell’ambiente di progettazione contiene informazioni relative alla pubblicazione, tra cui il nome dell’offerta corrispondente nell’ambiente live.

![](assets/offer_golive_001.png)

Per visualizzare l’offerta disponibile nell’ambiente live, fai clic sull’etichetta dell’offerta: l’offerta live presenta una dashboard contenente tutte le informazioni rilevanti.

![](assets/offer_golive_002.png)

## Disabilitazione di un’offerta {#disabling-an-offer}

Una volta approvata l’offerta, puoi disattivarla.

A questo scopo, vai alla dashboard per un’offerta online o un’offerta in attesa di essere online, quindi fai clic su **[!UICONTROL Disable offer]**.

Puoi anche disabilitare direttamente una categoria accedendo al **[!UICONTROL Eligibility]** e selezionando la **[!UICONTROL Enabled]** casella.

>[!NOTE]
>
>Quando un’offerta viene eliminata in un ambiente di progettazione, viene disattivata automaticamente nell’ambiente online collegato. Dopo un periodo di conservazione della proposta, le offerte disattivate vengono eliminate dall’ambiente online.

![](assets/offer_preview_deactivate.png)
