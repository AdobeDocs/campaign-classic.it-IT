---
title: Configurazione dell’integrazione
seo-title: Configurazione dell’integrazione
description: Configurazione dell’integrazione
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 2%

---


# Monitoraggio della pipeline {#pipeline-monitoring}

Il servizio Web [!DNL pipelined] status fornisce informazioni sullo stato del [!DNL pipelined] processo.

È possibile accedervi manualmente utilizzando un browser o automaticamente con un&#39;applicazione di monitoraggio.

È in formato REST, come descritto di seguito.

![](assets/triggers_8.png)

## Indicatori {#indicators}

In questa sezione sono elencati gli indicatori nel servizio Web dello stato.

Gli indicatori raccomandati da monitorare sono evidenziati.

* Consumatore: nome del client che esegue il pulling dei trigger. Configurato nell&#39;opzione di pipeline.
* http-request
   * last-live-ms-ago: tempo in millisecondi trascorso il controllo della connessione.
   * last-fail-cnx-ms-ago: tempo in ms dall&#39;ultima volta che il controllo della connessione non è riuscito.
   * pipeline-host: nome dell&#39;host da cui vengono estratti i dati della pipeline.
* puntatore
   * current-off: valore del puntatore nella pipeline, per thread figlio.
   * last-flush-ms-ago: tempo in ms dal recupero di un batch di attivatori.
   * next-offsets-flush: tempo di attesa per il batch successivo, al termine.
   * processed-from-last-flush: numero di attivatori elaborati nell&#39;ultimo batch.
* routing
   * trigger: elenco di trigger recuperati. Configurata nell’ [!DNL pipelined] opzione.
* statistiche
   * tempo medio-rosso-rosso-ms: tempo di elaborazione medio per un batch di attivatori.
   * tempo medio di elaborazione-trigger-ms: tempo medio impiegato per l&#39;analisi dei dati dei trigger.
   * byte-read: numero di byte letti dalla coda dall&#39;avvio del processo.
   * current-messages: numero corrente di messaggi in sospeso estratti dalla coda e in attesa di elaborazione. **Questo indicatore deve essere vicino a zero**.
   * current-retries: numero corrente di messaggi con elaborazione non riuscita e in attesa di nuovo tentativo.
   * picco di messaggi: numero massimo di messaggi in sospeso gestiti dal processo dall&#39;avvio.
   * pennelli: numero di batch di messaggi elaborati dall&#39;inizio.
   * routing-JS-custom: numero di messaggi elaborati dal JS personalizzato.
   * con trigger-away: numero di messaggi che sono stati eliminati dopo troppi tentativi a causa di errori di elaborazione.
   * elaborato dall&#39;attivatore: numero di messaggi elaborati senza errore.
   * trigger-Received: numero di messaggi ricevuti dalla coda.

Tali stati vengono visualizzati per ciascun thread di elaborazione.

* tempo medio di elaborazione-trigger-ms: tempo medio impiegato per l&#39;analisi dei dati dei trigger.
* is-JS-processor: &quot;1&quot; se questo thread utilizza il JS personalizzato.
* con trigger-away: numero di messaggi che sono stati eliminati dopo troppi tentativi a causa di errori di elaborazione. **Questo indicatore deve essere zero**.
* trigger-failures: numero di errori di elaborazione nel JS. **Questo indicatore deve essere zero**.
* trigger-Received: numero di messaggi ricevuti dalla coda.

* Impostazioni: sono impostati nei file di configurazione.
   * flush-puntatore-msg-count: numero di messaggi in un batch.
   * flush-puntatore-punto-ms: tempo tra due batch, in millisecondi.
   * processing-thread-JS: numero di thread di elaborazione che eseguono il JS personalizzato.
   * periodo-tentativi-ms: intervallo tra due tentativi in caso di errore di elaborazione.
   * try-validation-Duration-ms: la durata dell&#39;elaborazione viene riprovata fino a quando il messaggio non viene eliminato.
   * Report messaggi pipeline

## Report messaggi pipeline {#pipeline-report}

Questo rapporto mostra il numero di messaggi orari negli ultimi cinque giorni.

![](assets/triggers_9.png)
