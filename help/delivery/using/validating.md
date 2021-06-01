---
product: campaign
title: Convalida
description: Convalida
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# Convalida{#validating}

I concetti globali durante la convalida di una consegna sono descritti in [questa sezione](../../delivery/using/steps-validating-the-delivery.md).

Il file di output di una consegna direct mailing viene generato durante l’analisi della consegna. Il contenuto del file dipende dalle colonne di output selezionate (fare riferimento a [File di estrazione](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La fase di analisi è descritta in [Analisi della consegna](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Durante la fase di analisi, il file viene generato ma le informazioni relative ai destinatari (ad esempio i registri di consegna) non vengono aggiornate. È quindi possibile annullare il processo senza correre rischi.

Prima di fare clic su **[!UICONTROL Confirm delivery]**, controlla il risultato dell’analisi e il contenuto del file di output. Un messaggio di conferma consente di avviare la consegna.

La conferma dell’invio avvia l’estrazione dei dati nel file specificato.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Puoi quindi chiudere la procedura guidata e guardare i registri di consegna tramite la scheda **[!UICONTROL Delivery]** , accessibile tramite i dettagli di consegna.

Puoi configurare la modalità di recupero dei registri di consegna dalla scheda **[!UICONTROL Analysis]** delle proprietà di consegna.

Sono disponibili due modalità:

* **[!UICONTROL Messages are considered sent after validation]** (modalità predefinita): in questa modalità di funzione, tutti i registri di trasmissione vengono aggiornati quando l’operatore conferma l’invio (il loro stato passa da &quot;Pending delivery&quot; a &quot;Sent&quot;) e la consegna viene automaticamente impostata su  **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : questa modalità consente di aggiornare i registri di trasmissione tramite un file esterno inviato dal provider di servizi. In questo caso, è necessario utilizzare un flusso di lavoro per elaborare queste informazioni per aggiornare lo stato del registro di trasmissione.

   >[!NOTE]
   >
   >In questo caso, anche lo stato della consegna deve essere modificato in **[!UICONTROL Finished]** dall’utente non appena i registri di trasmissione vengono aggiornati.
