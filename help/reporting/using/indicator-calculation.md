---
solution: Campaign Classic
product: campaign
title: Calcolo indicatore
description: Calcolo indicatore
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 1%

---


# Calcolo indicatore {#indicator-calculation}

## Attività utente {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somma di tutti @totalClicks con una chiave primaria URL uguale a 1.<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @clic<br /> </td> 
   <td> Somma di tutti i @totalClicks con un tipo di URL uguale a "Email click".<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Somma di tutti @totalClicks con un tipo URL uguale a "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Questo rapporto è basato sulla **[!UICONTROL Consolidated tracking]** tabella (nms:trackingStats). Questa tabella aggregata viene utilizzata per motivi di prestazioni durante la visualizzazione dei rapporti, al posto della **[!UICONTROL Recipient tracking logs]** tabella (nms:trackingLogRcp) e non viene calcolata in tempo reale. La tabella viene generata alcuni minuti dopo il recupero dei registri di tracciamento. Se gli indicatori sono aggiornati, i risultati saranno gli stessi degli indicatori del rapporto **degli indicatori** di tracciamento. L&#39;indicatore @totalclick esprime il numero totale di clic su un periodo di 5 minuti.

## Messaggi non recapitati e non trasferibili {#non-deliverables-and-bounces-1}

**Suddivisione per tipo di errore**

Questo rapporto è basato sulla **[!UICONTROL Delivery and tracking statistics]** tabella (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero totale di messaggi elaborati<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Somma di messaggi con stato uguale a "Pronto", "Inviato" o "Non riuscito".<br /> </td> 
   <td> @ready + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Conteggio di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Utente sconosciuto". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Non Raggiungibile <br /> </td> 
   <td> @non raggiungibile<br /> </td> 
   <td> Conteggio di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Non raggiungibile". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato<br /> </td> 
   <td> @rifiutato<br /> </td> 
   <td> Conteggio di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Rifiutato". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido<br /> </td> 
   <td> @InvalidDomain<br /> </td> 
   <td> Conteggio di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Dominio non valido". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Account disattivato<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Conteggio di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Account disabilitato".<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Casella in entrata piena<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Conteggio di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Posta in arrivo piena". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori<br /> </td> 
   <td> @value<br /> </td> 
   <td> Numero di messaggi non riusciti per questo tipo di errore.<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason="Valore del tipo di errore")<br /> </td> 
  </tr> 
  <tr> 
   <td> Contributo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di errori di questo tipo rispetto al numero totale di messaggi di errore.<br /> </td> 
   <td> percentuale(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di errori di questo tipo rispetto al numero totale di messaggi elaborati.<br /> </td> 
   <td> percentuale(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Suddivisione per dominio**

La seconda parte del rapporto descrive in dettaglio la suddivisione dei messaggi non riusciti per dominio Internet anziché per tipo di errore. La formula collegata all&#39;indicatore di **errore** (@value) in questo caso è: Count(@status=2 e @domain=&quot;Valore del nome di dominio&quot;), ovvero un conteggio di tutti i messaggi con uno stato non riuscito per questo dominio.

## Browser {#browsers-1}

Questo rapporto è basato sulla **[!UICONTROL Internet Browser Statistics]** tabella (nms:userAgentStats).

**Statistiche globali**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitatori<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Numero totale di destinatari con targeting per questo browser che hanno fatto clic almeno una volta in una consegna.<br /> </td> 
   <td> Sum(@visitatori)<br /> </td> 
  </tr> 
  <tr> 
   <td> Visualizzazioni pagina<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Numero totale di clic sui collegamenti di consegna che utilizzano questo browser, per tutte le consegne.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questo browser rispetto al numero totale di visitatori.<br /> </td> 
   <td> percentuale(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistiche per browser**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> @visitatori<br /> </td> 
   <td> Percentuale del numero di visitatori al giorno che utilizzano questo browser rispetto al numero di visitatori misurato nel giorno con il maggior numero di visite.<br /> </td> 
   <td> percentuale(sum(@visitatori),max(@visitatoriOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso globale<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questa versione rispetto al numero totale di visitatori che utilizzano tutti i browser.<br /> </td> 
   <td> percentuale(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Peso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questa versione rispetto al numero totale di visitatori che utilizzano questo browser.<br /> </td> 
   <td> percentuale(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Condivisione sui social network {#sharing-to-social-networks-1}

Questo rapporto è basato sulle tabelle **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Number of messages to deliver<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Numero totale di messaggi elaborati durante l'analisi di consegna.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Numero di consegne riuscite<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati correttamente <br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è uguale a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è uguale a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è uguale a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Delizioso<br /> </td> 
   <td> @delizioso<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è "deliziosa".<br /> </td> 
   <td> Sum(iIf([url/@category]='delizioso',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è uguale a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è uguale a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Azioni**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero di azioni<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Numero totale di messaggi condivisi in questo social network.<br /> </td> 
   <td> Sum(iIf([url/@category]="Valore del tipo di rete social",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Percentuale del numero di azioni su questo social network rispetto al numero totale di azioni.<br /> </td> 
   <td> percentuale(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità di condivisione<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Numero di condivisioni in questa rete rispetto al numero di messaggi da inviare.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Messaggi aperti**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero di aperture <br /> </td> 
   <td> @open<br /> </td> 
   <td> Numero totale di righe di tracciamento nella tabella di tracciamento Web.<br /> </td> 
   <td> Count<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Percentuale del numero di aperture in questo social network rispetto al numero totale di aperture.<br /> </td> 
   <td> percentuale(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Frequenza delle aperture<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Numero di aperture su questo social network rispetto al numero totale di messaggi da inviare.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiche sulle attività di condivisione {#statistics-on-sharing-activities-1}

Questo rapporto è basato sulle tabelle **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nuovi contatti<br /> </td> 
   <td> @newContatti<br /> </td> 
   <td> Conteggio del numero di visitatori collegati a un destinatario.<br /> </td> 
   <td> Formula: count(@id)<br /> Filtro: @receive-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @open<br /> </td> 
   <td> Conteggio di tutti gli @ids con un tipo URL uguale a "Open".<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Azioni<br /> </td> 
   <td> @shared<br /> </td> 
   <td> categoria URL inclusa in 'email' , 'facebook' , 'twitter' , 'delizioso' , 'digg' , 'google' , 'linkedin'<br /> Conteggio di tutti @totalClicks con una categoria URL uguale a "email", "facebook", "twitter", "delizioso", "digg", "google" o "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN (email) , 'facebook' , 'twitter' , 'delizioso' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sistemi operativi {#operating-systems-1}

Questo rapporto è basato sulla **[!UICONTROL Internet Browser Statistics]** tabella (nms:userAgentStats).

**Statistiche globali**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitatori<br /> </td> 
   <td> @totalVisitors / @Days<br /> </td> 
   <td> Media giornaliera del numero totale di destinatari a cui il sistema operativo ha fatto clic in una consegna almeno una volta.<br /> </td> 
   <td> Sum(@visitatori)<br /> </td> 
  </tr> 
  <tr> 
   <td> Pagine visualizzate<br /> </td> 
   <td> @totalPages / @Days<br /> </td> 
   <td> Media giornaliera del numero totale di clic sui collegamenti di consegna per ogni sistema operativo per tutte le consegne.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> -<br /> </td> 
   <td> Suddivisione dei visitatori per sistema operativo rispetto al numero totale di visitatori.<br /> </td> 
   <td> percentuale(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistiche per sistema operativo**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> @visitatori<br /> </td> 
   <td> Percentuale del numero di visitatori al giorno in questo sistema operativo rispetto al numero di visitatori misurati nel giorno con il maggior numero di visite.<br /> </td> 
   <td> percentuale(sum(@visitatori), max(@visitatoriOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso globale<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per versione rispetto al numero totale di visitatori per tutti i sistemi operativi.<br /> </td> 
   <td> percentuale(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per versione rispetto al numero totale di visitatori che utilizzano questo sistema operativo.<br /> </td> 
   <td> percentuale(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracciamento iscrizione {#subscription-tracking-1}

Questo rapporto è basato sulla **[!UICONTROL Services]** tabella (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Registrato<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Conteggio delle persone registrate il giorno precedente.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Iscrizioni<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> conteggio delle sottoscrizioni (@action = 1) nel giorno precedente.<br /> </td> 
   <td> sum(Iif(@action = 1 e @date &gt; addDays(getDate(), (-1)), 1, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Abbonamenti non riusciti<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> conteggio di sottoscrizioni (azione = 0) nel giorno precedente.<br /> </td> 
   <td> sum(Iif(@action = 0 e @date &gt; addDays(getDate(), (-1)), 1, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione<br /> </td> 
   <td> -<br /> </td> 
   <td> Numero di sottoscrizioni meno il numero di sottoscrizioni. Il tasso è calcolato in relazione al numero totale di abbonati.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percentuale(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.0 0')+ '%)',')<br /> </td> 
  </tr> 
  <tr> 
   <td> Fedeltà<br /> </td> 
   <td> -<br /> </td> 
   <td> Tasso di fedeltà dell’utente iscritto per il periodo correlato.<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indicatori di tracciamento {#tracking-indicators-1}

Questo rapporto è basato sulle tabelle **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messaggi da inviare<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Conteggio del numero di wideLogs dopo l’analisi di destinazione.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Successo<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Conteggio dei messaggi per i quali il campo "indirizzo" è uguale a "No" e con uno stato uguale a "Preso in considerazione dal provider di servizi" o "Inviato" o "Ricevuto sul cellulare".<br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Apertura distinta sulla popolazione raggiunta<br /> </td> 
   <td> @EstimalRecipientOpen<br /> </td> 
   <td> Estrapolazione del numero di aperture distinte per tutte le e-mail in base al numero di aperture distinte per le e-mail in formato html.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@RecipiOpen) * [@toDeliver] / ([@toDeliver] - [@text])<br /> </td> 
  </tr> 
  <tr> 
   <td> Somma di aperture sulla popolazione raggiunta<br /> </td> 
   <td> @EstimTotalRecipientOpen<br /> </td> 
   <td> Estrapolazione del numero totale di aperture per tutte le e-mail in base al numero totale di aperture di e-mail in formato html.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text])<br /> </td> 
  </tr> 
  <tr> 
   <td> Fate clic sul collegamento per annullare l’iscrizione<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Conteggio di tutti gli @ids con una categoria URL uguale a "Rifiuto".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic sul collegamento alla pagina mirror<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Conteggio di tutti gli @ids con una categoria URL uguale a "Mirror page".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Stima dei progressi<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Differenza tra il numero di persone distinte e il numero di destinatari distinti che hanno fatto clic sul messaggio almeno una volta.<br /> </td> 
   <td> @PersonaClick - @destinatarioClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Invio<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Conteggio dei messaggi per i quali il campo "indirizzo e-mail" è uguale a "No" e con uno stato uguale a "preso in considerazione dal destinatario" o "Inviato" o "Ricevuto su dispositivo mobile".<br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Reclami<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Conteggio di messaggi con stato uguale a "Non riuscito" e motivo uguale a "indirizzo sul elenco Bloccati".<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @receiveOpen<br /> </td> 
   <td> Conteggio di tutti gli @broadLog-ids in tutti i registri di tracciamento.<br /> </td> 
   <td> Countdistinto ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @destinatarioClick<br /> </td> 
   <td> Conteggio distinto di @broadLog-ids con un tipo URL uguale a "Clic e-mail". <br /> </td> 
   <td> Countdistinta(Iif([url/@type]=1, @wideLog-id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Reattività grezza<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale del numero di destinatari che hanno fatto clic in una consegna almeno una volta rispetto al numero di destinatari che hanno aperto una consegna almeno una volta.<br /> </td> 
   <td> percentuale(@destinatarioClick,@destinatarioOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic distinto sulla popolazione raggiunta<br /> </td> 
   <td> @PersonClick<br /> </td> 
   <td> Conteggio di tutti gli @source-ids con una categoria URL uguale a "E-mail click".<br /> </td> 
   <td> Countdistinta(Iif([url/@type]=1, @source-id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic cumulati<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Conteggio di tutti gli @ids con una categoria di URL che corrisponde a "Clic e-mail".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic del destinatario<br /> </td> 
   <td> @destinatarioClick<br /> </td> 
   <td> Conteggio distinto degli @broadLog-ids con un tipo di URL che corrisponde a "Clic e-mail".<br /> </td> 
   <td> Countdistinta(Iif([url/@type]=1, @wideLog-id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Reattività stimata<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra il numero di destinatari che hanno fatto clic in una consegna almeno una volta rispetto alla stima dei destinatari che hanno aperto la consegna almeno una volta.<br /> </td> 
   <td> percentuale(@RecipientClick, @EstimRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Pagine visitate<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Conteggio di tutti gli @ids con un tipo URL uguale a "Web" o "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=4 o [url/@type]=5, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Conteggio di tutti gli @ids con un tipo URL uguale a "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo totale<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Somma di webTrackingLog/@amount con un tipo URL uguale a "Transaction". <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo medio transazione<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra l'importo totale e il numero di transazioni.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Elementi<br /> </td> 
   <td> @article<br /> </td> 
   <td> Somma di articoli webTrackingLog/@con un tipo URL uguale a "Transaction".<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Numero medio di elementi per transazione<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra il numero di voci e il numero di transazioni.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo medio per messaggio<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra l'importo totale e il numero di messaggi da inviare.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL uguale a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL uguale a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL uguale a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Delizioso<br /> </td> 
   <td> @delizioso<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL uguale a "delizioso".<br /> </td> 
   <td> Sum(iIf([url/@category]='delizioso',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somma di tutti @totalClicks con una categoria URL uguale a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria di URL uguale a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somma di tutti @totalClicks con una categoria URL uguale a "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL e flussi di clic {#urls-and-click-streams-1}

Questo rapporto è basato sulla **[!UICONTROL Delivery]** tabella (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reattività<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Rapporto tra il numero di destinatari con targeting che hanno fatto clic in una consegna almeno una volta rispetto al numero stimato di destinatari con targeting che hanno aperto una consegna almeno una volta.<br /> </td> 
   <td> percentuale([indicatori/@destinatarioClick], [indicatori/@EstimRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic distinti<br /> </td> 
   <td> @distintaClicks<br /> </td> 
   <td> Rapporto tra il numero di persone distinte che hanno fatto clic in una consegna almeno una volta rispetto al numero di messaggi inviati con esito positivo.<br /> </td> 
   <td> percentuale([indicatori/@personaClic], [indicatori/@successo])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic cumulati<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Rapporto tra il numero totale di clic dei destinatari con targeting e il numero di messaggi inviati con esito positivo.<br /> </td> 
   <td> percentuale([indicatori/@totalRecipientClick], [indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Totale di tutti @totalClicks con una chiave primaria URL diversa da 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale del numero di clic rispetto al numero totale di clic cumulati.<br /> </td> 
   <td> percentuale(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Riepilogo consegne {#delivery-summary-1}

Questo rapporto è basato sulla **[!UICONTROL Delivery]** tabella (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Popolazione iniziale<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Numero totale di destinatari interessati dalla consegna.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi rifiutati dalla regola<br /> </td> 
   <td> @rifiutare<br /> </td> 
   <td> Numero di indirizzi ignorati durante l'analisi in conformità con le regole di tipologia: indirizzo non specificato, messo in quarantena, al elenco Bloccati, ecc.<br /> </td> 
   <td> sum([proprietà/@rifiuto])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi da inviare<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Numero totale di messaggi da inviare dopo l'analisi della consegna.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Successo<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati con esito positivo.<br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori<br /> </td> 
   <td> @error<br /> </td> 
   <td> Numero totale di errori cumulati durante le consegne e l'elaborazione automatica dei rimbalzi.<br /> </td> 
   <td> sum([indicatori/@errore])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuove quarantena<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Numero di indirizzi in quarantena dopo un errore di consegna (dominio utente sconosciuto, non valido).<br /> </td> 
   <td> sum([indicatori/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot click {#hot-clicks-1}

Questo rapporto è basato sulle tabelle Delivery(nms:delivery) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

Questo rapporto mostra il contenuto del messaggio (HTML e/o testo) con, su ogni collegamento, la percentuale di clic sui collegamenti. I blocchi di personalizzazione per i collegamenti di annullamento iscrizione e i collegamenti di pagina mirror vengono presi in considerazione nei clic totali cumulati, ma non vengono visualizzati nel rapporto.

## Tracciamento delle statistiche {#tracking-statistics-1}

Questo rapporto è basato sulla **[!UICONTROL Delivery]** tabella (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Somma di tutti @totalClicks con un tipo URL uguale a "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @clic<br /> </td> 
   <td> Somma di tutti @totalClicks con un tipo di URL che corrisponde a "Email click".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> Apri<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somma di tutti @totalClicks con una chiave primaria URL uguale a 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiche di consegna {#delivery-statistics-1}

Questo rapporto è basato sulla **[!UICONTROL Delivery and tracking statistics]** tabella (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> E-mail elaborate<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Numero totale di messaggi con stato uguale a "Pronto", "Inviato" o "Non riuscito".<br /> </td> 
   <td> @ready + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Consegnato<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati correttamente.<br /> </td> 
   <td> indicatori/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Rimbalzi netti<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Numero totale di messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Utente sconosciuto".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Rimbalzi morbidi<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Totale di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "non raggiungibile", "inbox completo", "dominio non valido", "account disabilitato", "non connesso" o "rifiutato"<br /> </td> 
   <td> @non raggiungibile + @mailBoxFull + @InvalidDomain + @disabled + @notConnected + @rifiutato<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @receiveOpen<br /> </td> 
   <td> Numero totale di @broadLog-ids nei registri di tracciamento.<br /> </td> 
   <td> Countdistinto ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @PersonClick<br /> </td> 
   <td> Numero totale di @source-ids per i quali la categoria URL è uguale a "Clic e-mail". <br /> </td> 
   <td> Countdistinta(Iif([url/@type]=1, @source-id, 0) <br /> </td> 
  </tr> 
  <tr> 
   <td> Abbonamenti non riusciti<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Numero totale di @ids per i quali la categoria URL è uguale a "Rifiuto".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Suddivisione delle aperture {#breakdown-of-opens-1}

Questo rapporto si basa sulle tabelle **Consegne** (nms:delivery) e **Registri** di tracciamento (nms:trackingLogRcp).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Somma di tutti gli @id con una chiave primaria URL uguale a 1 (aperta). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Altri indicatori {#other-indicators}

L&#39;indicatore **Inviato** (@sent), a cui si accede tramite il nodo **Consegne (nms:delivery) > Indicatori** corrisponde al numero totale di SMS inviati al provider di servizi. Questo indicatore è utilizzato solo per le consegne via SMS e non deve essere utilizzato per altri tipi di consegne (da non confondere con gli indicatori **@success** e **@processed** ).

## Sincronizzazione indicatori {#indicator-synchronization}

In caso di desincronizzazione o incoerenza per alcuni indicatori, selezionate la distribuzione interessata in  Adobe Campaign Explorer, fate clic con il pulsante destro del mouse e scegliete **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Fate clic **[!UICONTROL Next]**, quindi fate clic **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Aperture di tracciamento {#tracking-opens-}

Affinché  Adobe Campaign possa rilevare le aperture dei messaggi, il destinatario deve scaricare le immagini contenute nell&#39;e-mail. HTML e e e-mail multiparte/alternative includono un&#39;immagine di 0 pixel che consente di rilevare i messaggi aperti. Poiché i messaggi in formato testo non includono immagini, è impossibile rilevare se sono stati aperti o meno. I valori calcolati in base alle aperture dei messaggi sono sempre stime, a causa del margine di errore collegato alla visualizzazione delle immagini.

## Persone / destinatari interessati {#targeted-persons---recipients}

In alcuni rapporti,  Adobe Campaign distingue le persone mirate e i destinatari mirati.

I destinatari di destinazione sono tutti i destinatari a cui è stato inviato il recapito.

Il numero di persone include destinatari mirati più tutte le persone a cui è stato inviato il messaggio e-mail. Ogni volta che si apre o si fa clic in un nuovo browser (il messaggio non è ancora stato aperto), alle statistiche viene aggiunta un&#39;altra persona.

Ad esempio, se ricevi un&#39;e-mail (inviata da  Adobe Campaign) al lavoro e ti apri o fai clic su di essa, verrai conteggiato come destinatario (ad es. destinatario=1, persona=1). Se inviate questa e-mail a due amici, il numero di destinatari con targeting sarà ancora uguale a uno, mentre il numero di persone sarà uguale a tre. Il valore 3 coincide con ogni apertura o clic in un nuovo browser.
