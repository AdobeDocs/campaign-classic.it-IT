---
product: campaign
title: Convalida
description: Convalida
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# Convalida{#validating}

![](../../assets/common.svg)

I concetti globali durante la convalida di una consegna sono descritti in [questa sezione](steps-validating-the-delivery.md).

Il file di output di una consegna direct mailing viene generato durante l’analisi della consegna. Il contenuto del file dipende dalle colonne di output selezionate (fare riferimento a [File di estrazione](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La fase di analisi è dettagliata in [Analisi della consegna](steps-validating-the-delivery.md#analyzing-the-delivery).

Durante la fase di analisi, il file viene generato ma le informazioni relative ai destinatari (ad esempio i registri di consegna) non vengono aggiornate. È quindi possibile annullare il processo senza correre rischi.

Controlla il risultato dell&#39;analisi e il contenuto del file di output prima di fare clic su **[!UICONTROL Confirm delivery]**. Un messaggio di conferma consente di avviare la consegna.

La conferma dell’invio avvia l’estrazione dei dati nel file specificato.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Puoi quindi chiudere la procedura guidata e esaminare i registri di consegna tramite il **[!UICONTROL Delivery]** , accessibile tramite i dettagli di consegna.

Puoi configurare la modalità di recupero dei registri di consegna dalla **[!UICONTROL Analysis]** scheda delle proprietà di consegna.

Sono disponibili due modalità:

* **[!UICONTROL Messages are considered sent after validation]** (modalità predefinita): in questa modalità di funzione, tutti i registri di trasmissione vengono aggiornati quando l’operatore conferma l’invio (il loro stato passa da &quot;Pending delivery&quot; a &quot;Sent&quot;) e la consegna viene automaticamente impostata su **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : questa modalità consente di aggiornare i registri di trasmissione tramite un file esterno inviato dal provider di servizi. In questo caso, è necessario utilizzare un flusso di lavoro per elaborare queste informazioni per aggiornare lo stato del registro di trasmissione.

   >[!NOTE]
   >
   >In questo caso, anche lo stato della consegna deve essere modificato in **[!UICONTROL Finished]** dall’utente non appena i log di trasmissione vengono aggiornati.
