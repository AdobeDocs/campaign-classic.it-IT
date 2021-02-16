---
solution: Campaign Classic
product: campaign
title: Tracciamento della risoluzione dei problemi
description: Questa sezione contiene le domande comuni relative al tracciamento della configurazione e dell’implementazione in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Tracciamento della risoluzione dei problemi {#tracking-troubleshooting}

In questa sezione troverai le domande più frequenti sul tracciamento della configurazione e dell’implementazione in Adobe Campaign Classic.

## Il flusso di lavoro di tracciamento non riesce {#tracking-workflow-failing}

Il mio flusso di lavoro di tracciamento non riesce. Come posso rilevare le righe danneggiate nel file di tracciamento?

>[!NOTE]
>
>Disponibile solo per Windows

Il file di registro di tracciamento danneggiato .../nl6/var/&lt;nome_istanza>/redir/log/0x0000 log può arrestare il flusso di lavoro di tracciamento. Per rilevare facilmente le linee danneggiate e rimuoverle per riprendere il flusso di lavoro di tracciamento, potete utilizzare i comandi riportati di seguito.

### So in quale file la linea danneggiata è

In tal caso, le righe danneggiate possono essere trovate nel file 0x000000000A0000.log, ma lo stesso processo può essere applicato a un set di file, uno per uno.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Potete quindi interrompere il flusso di lavoro di tracciamento, eliminare le righe danneggiate e riavviare il flusso di lavoro.

### Non ora in quale file la linea danneggiata è

1. utilizzate la seguente riga di comando per archiviare tutti i file di tracciamento.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. Il comando elenca tutte le righe danneggiate. Ad esempio:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Il ritorno a capo è stato aggiunto prima dell&#39;agente utente per consentire una migliore lettura e non riflette il rendering efficace.

1. Eseguite un comando grep per trovare il file corrispondente.

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. Individuare il registro difettoso con il nome del file e il numero di riga. Ad esempio:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >È stato aggiunto un ritorno a capo prima dell&#39;agente utente per consentire una lettura migliore e non riflette il rendering efficace.

Potete quindi interrompere il flusso di lavoro di tracciamento, eliminare le righe danneggiate e riavviare il flusso di lavoro.

## I collegamenti di tracciamento non vanno a buon fine {#tracking-links-fail-intermittently}

Quando si tenta di accedere ai collegamenti di tracciamento, viene visualizzato il messaggio seguente:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. Accedete a &lt;redirection_server>/r/test URL e verificate che il numero di build e localhost siano stati restituiti dalla richiesta.

1. Controlla la configurazione di spareServer nel file serverConf.xml per il server di tracciamento. Questa configurazione deve essere in modalità di reindirizzamento.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Verificare manualmente se il file &lt;deliveryID>.xml esiste nel computer in ...directory /nl6/var/&lt;nome_istanza>/redir/url/&lt;AAAA> (AAAA rappresenta l&#39;anno di consegna).

1. Controllate manualmente se è possibile trovare &lt;trackingUrlId> nel file &lt;deliveryID>.xml.

1. Verifica manualmente l’esistenza di broadlogID nella relativa consegna dell’ID di distribuzione.

1. Controlla le autorizzazioni per i file &lt;deliveryID>.xml in .../nl6/var/&lt;nome_istanza>/redir/url/anno.

   Devono disporre di almeno 644 autorizzazioni in modo che Apache possa leggere gli URL di tracciamento per reindirizzare il collegamento richiesto.

## Aggiornare l&#39;opzione NmsTracking_Pointer? {#updating-option}

Per aggiornare l’opzione NmsTracking_Pointer, effettuate le seguenti operazioni:

1. Arrestate il flusso di lavoro di tracciamento.

1. Arrestate il servizio trackinglogd.

1. Aggiornare l&#39;opzione NmsTracking_Pointer al valore desiderato.

1. Riavviate il servizio trackinglogd.

1. Riavviate il flusso di lavoro di tracciamento.

## Il monitoraggio non sembra funzionare con WebMail {#webmail}

Potete personalizzare la formula di tracciamento dei clic e specificare una formula di tracciamento Adobe Analytics  personalizzata.

Questo tipo di personalizzazione deve essere effettuato con cautela per evitare di aggiungere caratteri di avanzamento riga aggiuntivi. Tutti i caratteri linefeed presenti al di fuori dell&#39;espressione javascript saranno presenti nella formula finale.

Questo tipo di carattere di avanzamento riga aggiuntivo nell&#39;URL di tracciamento causerà un problema in alcuni WebMail (AOL, GMail, ecc.).

**Primo esempio:**

* Sintassi errata

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* Sintassi corretta

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

Per capire dove si trova il feed di linea aggiuntivo, è possibile sostituire l&#39;espressione javascript con una stringa fissa STRING.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Secondo esempio**

* Sintassi errata

   ```
   <%@ include option='NmsTracking_ClickFormula' %>
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* Sintassi corretta

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

Per capire dove si trova il feed di linea aggiuntivo, è possibile sostituire l&#39;espressione javascript con una stringa fissa STRING.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## Il recupero dei log di monitoraggio è troppo lento {#slow-retrieval}

Quando l’istanza non recupera direttamente i registri di tracciamento ma da un server Adobe Campaign Classic remoto, i registri vengono recuperati tramite la chiamata SOAP GetTrackingLogs definita nello schema remoteTracking.

Un&#39;opzione nel file serverConf.xml consente di impostare il numero di file di registro recuperati contemporaneamente tramite questo metodo: logCountPerRequest.

Il valore predefinito di logCountPerRequest è 1000. In alcuni casi potrebbe risultare troppo piccolo. I valori accettati devono essere compresi tra 0 e 10.000.

## Impossibile collegare i registri di tracciamento ai destinatari {#link-recipients}

In Adobe Campaign Classic, una mappatura di destinazione dovrebbe essere univoca in termini di schema destinatario rispetto agli schemi di trasmissione/tracciamento.

![](assets/tracking-troubleshooting.png)

Non è possibile utilizzare più schemi di targeting con lo stesso schema di trackinglog, poiché il flusso di lavoro di tracciamento non sarà in grado di riconciliare i dati con l&#39;ID di targeting.

Se non desiderate utilizzare la mappatura di destinazione out-of-the-box con nms:Recipients, consigliamo i seguenti approcci:

* Se desiderate utilizzare la dimensione di targeting personalizzata, dovete creare uno schema wideLog/trackingLog personalizzato utilizzando nms:broadcast come modello (ad esempio, nms:wideLogRcp, nms:wideLogSvc, ecc.).

* Se si desidera utilizzare OOB trackingLogRcp/broadLogRcp, la dimensione di targeting deve essere nms:destinatario e la dimensione di filtro potrebbe essere uno schema personalizzato.
