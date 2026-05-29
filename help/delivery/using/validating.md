---
product: campaign
title: Convalida
description: Convalida
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Direct Mail
hide: true
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
TQID: https://experienceleague.adobe.com/I31u-kAqMRpzti-bOtfYjrGbwvmsfeEPwWU7kCFLzcQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 250
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
