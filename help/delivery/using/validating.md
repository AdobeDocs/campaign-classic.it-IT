---
product: campaign
title: Convalida
description: Convalida
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 1%

---

# Convalida{#validating}



I concetti globali durante la convalida di una consegna sono presentati in [questa sezione](steps-validating-the-delivery.md).

Il file di output di una consegna direct mailing viene generato durante l’analisi della consegna. Il contenuto del file dipende dalle colonne di output selezionate (fare riferimento a [File di estrazione](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>La fase di analisi è descritta in [Analisi della consegna](steps-validating-the-delivery.md#analyzing-the-delivery).

Durante la fase di analisi, viene generato il file ma le informazioni relative ai destinatari (ovvero i registri di consegna) non vengono aggiornate. È quindi possibile annullare questo processo senza correre rischi.

Controllare il risultato dell&#39;analisi e il contenuto del file di output prima di fare clic su **[!UICONTROL Confirm delivery]**. Un messaggio di conferma ti consente di avviare la consegna.

La conferma di invio avvia l’estrazione dei dati nel file specificato.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

È quindi possibile chiudere l&#39;assistente e visualizzare i registri di consegna tramite la scheda **[!UICONTROL Delivery]**, accessibile tramite i dettagli di consegna.

Puoi configurare la modalità di recupero dei registri di consegna dalla scheda **[!UICONTROL Analysis]** delle proprietà di consegna.

Esistono due modalità:

* **[!UICONTROL Messages are considered sent after validation]** (modalità predefinita): in questa modalità funzione, tutti i broadLog vengono aggiornati quando l&#39;operatore conferma l&#39;invio (il loro stato passa da &quot;Consegna in sospeso&quot; a &quot;Inviato&quot;) e la consegna viene impostata automaticamente su **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : questa modalità consente di aggiornare i broadLog tramite un file esterno inviato dal provider di servizi. In questo caso, è necessario utilizzare un flusso di lavoro per elaborare queste informazioni al fine di aggiornare lo stato del registro di trasmissione.

  >[!NOTE]
  >
  >In questo caso, non appena i broadLog vengono aggiornati, anche lo stato della consegna deve essere modificato in **[!UICONTROL Finished]** dall&#39;utente.
