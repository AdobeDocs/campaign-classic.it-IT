---
solution: Campaign Classic
product: campaign
title: Convalida
description: Convalida
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# Convalida{#validating}

I concetti globali per la convalida di una consegna sono descritti in [questa sezione](../../delivery/using/steps-validating-the-delivery.md).

Il file di output di una consegna diretta viene generato durante l&#39;analisi della consegna. Il contenuto del file dipende dalle colonne di output selezionate (fare riferimento al file [](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)Estrazione).

>[!NOTE]
>
>La fase di analisi è dettagliata nell&#39; [analisi della consegna](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Durante la fase di analisi, il file viene generato, ma le informazioni relative ai destinatari (cioè i registri di consegna) non vengono aggiornate. È quindi possibile annullare il processo senza correre rischi.

Verificare il risultato dell&#39;analisi e il contenuto del file di output prima di fare clic **[!UICONTROL Confirm delivery]**. Un messaggio di conferma consente di avviare la consegna.

La conferma di invio avvia l&#39;estrazione dei dati nel file specificato.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

È quindi possibile chiudere la procedura guidata ed esaminare i registri di consegna tramite la **[!UICONTROL Delivery]** scheda, accessibile tramite i dettagli di consegna.

Puoi configurare la modalità di recupero dei registri di consegna dalla **[!UICONTROL Analysis]** scheda delle proprietà di consegna.

Sono disponibili due modalità:

* **[!UICONTROL Messages are considered sent after validation]** (modalità predefinita): in questa modalità di funzione, tutti i log di trasmissione vengono aggiornati quando l&#39;operatore conferma l&#39;invio (il loro stato passa da &quot;In attesa di consegna&quot; a &quot;Inviato&quot;) e la consegna viene automaticamente impostata su **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : questa modalità consente di aggiornare i log di trasmissione tramite un file esterno inviato dal provider di servizi. In questo caso, per elaborare queste informazioni è necessario utilizzare un flusso di lavoro per aggiornare lo stato del registro di trasmissione.

   >[!NOTE]
   >
   >In questo caso, lo stato della consegna deve essere modificato **[!UICONTROL Finished]** dall&#39;utente non appena i log di trasmissione vengono aggiornati.
