---
product: campaign
title: Configurazione dell’integrazione
description: Configurazione dell’integrazione
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---

# Monitoraggio della pipeline {#pipeline-monitoring}

![](../../assets/common.svg)

Il servizio Web di stato [!DNL pipelined] fornisce informazioni sullo stato del processo [!DNL pipelined].

È possibile accedervi manualmente utilizzando un browser o automaticamente con un&#39;applicazione di monitoraggio.

È in formato REST, come descritto di seguito.

![](assets/triggers_8.png)

## Indicatori {#indicators}

In questa sezione sono elencati gli indicatori nel servizio Web di stato.

Vengono evidenziati gli indicatori consigliati da monitorare.

* Consumatore: nome del client che esegue l&#39;estrazione dei trigger. Configurata nell’opzione pipeline.
* richiesta http
   * last-life-ms-ago: tempo in ms dall&#39;esecuzione di un controllo della connessione.
   * last-failed-cnx-ms-ago: tempo in ms dall&#39;ultima verifica della connessione non riuscita.
   * pipeline-host: nome dell’host da cui vengono estratti i dati della pipeline.
* puntatore
   * offset di corrente: valore del puntatore nella pipeline, per thread figlio.
   * last-flush-ms-ago: tempo in ms dal recupero di un batch di trigger.
   * next-offsets-flush: tempo di attesa del batch successivo, al termine.
   * elaborati-dall’ultimo scaricamento: numero di trigger elaborati nell’ultimo batch.
* ciclo
   * trigger: elenco dei trigger recuperati. Configurata nell&#39;opzione [!DNL pipelined].
* statistiche
   * tempo medio-di-flush-ms: tempo medio di elaborazione per un batch di trigger.
   * tempo medio di elaborazione-trigger-ms: tempo medio trascorso dall&#39;analisi dei dati dei trigger.
   * byte letti: numero di byte letti dalla coda dall&#39;avvio del processo.
   * messaggi correnti: numero corrente di messaggi in sospeso estratti dalla coda e in attesa di elaborazione. **Questo indicatore deve essere vicino a zero**.
   * tentativi correnti: numero corrente di messaggi con elaborazione non riuscita e in attesa di nuovo tentativo.
   * messaggi di picco: numero massimo di messaggi in sospeso gestiti dal processo dall&#39;avvio.
   * flush del puntatore: numero di batch di messaggi elaborati dall’inizio.
   * routing-JS-custom: numero di messaggi elaborati dal JS personalizzato.
   * attivatore scartato: numero di messaggi scartati dopo troppi tentativi a causa di errori di elaborazione.
   * elaborati dal trigger: numero di messaggi elaborati senza errore.
   * ricevuto dal trigger: numero di messaggi ricevuti dalla coda.

Queste statistiche vengono visualizzate per thread di elaborazione.

* tempo medio di elaborazione-trigger-ms: tempo medio trascorso dall&#39;analisi dei dati dei trigger.
* is-JS-processor: valore &quot;1&quot; se questo thread utilizza il JS personalizzato.
* attivatore scartato: numero di messaggi scartati dopo troppi tentativi a causa di errori di elaborazione. **Questo indicatore deve essere zero**.
* trigger-failed: numero di errori di elaborazione nel JS. **Questo indicatore deve essere zero**.
* ricevuto dal trigger: numero di messaggi ricevuti dalla coda.

* Impostazioni: sono impostati nei file di configurazione.
   * flush-puntatore-msg-count: numero di messaggi in un batch.
   * flush-puntatore-punto-ms: tempo tra due batch, in millisecondi.
   * processing-threads-JS: numero di thread di elaborazione che eseguono JS personalizzato.
   * nuovo-periodo-ms: tempo tra due tentativi quando si verifica un errore di elaborazione.
   * prova-validità-durata-ms: la durata dell&#39;elaborazione viene ritentata fino a quando il messaggio non viene eliminato.
   * Rapporto sui messaggi della pipeline

## Rapporto messaggi pipeline {#pipeline-report}

Questo rapporto visualizza il numero di messaggi all&#39;ora negli ultimi cinque giorni.

![](assets/triggers_9.png)
