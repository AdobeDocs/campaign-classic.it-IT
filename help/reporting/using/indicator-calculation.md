---
product: campaign
title: Calcolo indicatore
description: Calcolo indicatore
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3049'
ht-degree: 3%

---

# Calcolo indicatore {#indicator-calculation}



## Attività degli utenti {#user-activities-1}

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
   <td> Apertura di <br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somma di tutte le @totalClicks con una chiave primaria URL uguale a 1.<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Somma di tutte le @totalClicks con un tipo di URL uguale a "E-mail click".<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Somma di tutte le @totalClicks con un tipo di URL uguale a "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Questo report è basato sulla tabella **[!UICONTROL Consolidated tracking]** (nms:trackingStats). Questa tabella aggregata viene utilizzata per motivi di prestazioni durante la visualizzazione dei report al posto della tabella **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp) e non viene calcolata in tempo reale. La tabella viene generata pochi minuti dopo il recupero dei registri di tracciamento. Se gli indicatori sono aggiornati, i risultati saranno gli stessi degli indicatori del report **Tracking indicators**. L’indicatore @totalclicks esprime il numero totale di clic in un periodo di 5 minuti.

## Messaggi non recapitabili e mancati recapiti {#non-deliverables-and-bounces-1}

**Raggruppamento per tipo di errore**

Questo report è basato sulla tabella **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats).

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
   <td> Somma dei messaggi con uno stato uguale a "Pronto", "Inviato" o "Non riuscito".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Utente sconosciuto". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Non raggiungibile <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Non raggiungibile". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato<br /> </td> 
   <td> @refused<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Rifiutato". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Numero di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Dominio non valido". <br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Account disabilitato<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Conteggio di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Account disabilitato".<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Casella in entrata piena<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Casella in entrata piena". <br /> </td> 
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
   <td> Raggruppamento<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di errori di questo tipo rispetto al numero totale di messaggi elaborati.<br /> </td> 
   <td> percentuale(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Raggruppamento per dominio**

La seconda parte del rapporto descrive la suddivisione dei messaggi non riusciti per dominio Internet rispetto al tipo di errore. La formula collegata all&#39;indicatore **Errore** (@value) in questo caso è: Count(@status=2 and @domain=&quot;Value of the domain name&quot;), ovvero un conteggio di tutti i messaggi con uno stato di errore per questo dominio.

## Browser {#browsers-1}

Questo report è basato sulla tabella **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

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
   <td> Numero totale di destinatari di destinazione per questo browser che hanno fatto clic almeno una volta in una consegna.<br /> </td> 
   <td> Somma(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Visualizzazioni pagina<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Numero totale di clic sui collegamenti di consegna che utilizzano questo browser, per tutte le consegne.<br /> </td> 
   <td> Somma/@pages <br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questo browser rispetto al numero totale di visitatori.<br /> </td> 
   <td> percentuale(@totalVisitors, somma(@totalVisitors)) <br /> </td> 
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
   <td> @visitors<br /> </td> 
   <td> Percentuale del numero di visitatori al giorno che utilizzano questo browser rispetto al numero di visitatori misurato il giorno con il maggior numero di visite.<br /> </td> 
   <td> percentuale(somma(@visitors),max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tariffa globale<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questa versione rispetto al numero totale di visitatori che utilizzano tutti i browser.<br /> </td> 
   <td> percentuale(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Peso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questa versione rispetto al numero totale di visitatori che utilizzano questo browser.<br /> </td> 
   <td> percentuale(@totalVisitors, somma(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Condivisione sui social network {#sharing-to-social-networks-1}

Questo report è basato sulle tabelle **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** (nms:webTrackingLog).

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
   <td> Numero di messaggi da consegnare<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Numero totale di messaggi elaborati durante l'analisi della consegna.<br /> </td> 
   <td> sum([proprietà/@totalTarget])<br /> </td> 
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
   <td> Somma di tutte le @totalClicks per le quali la categoria URL è uguale a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somma di tutte le @totalClicks per le quali la categoria URL è uguale a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somma di tutte le @totalClicks per le quali la categoria URL è uguale a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delizioso<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Somma di tutte le @totalClicks per le quali la categoria URL è uguale a "delizioso".<br /> </td> 
   <td> Sum(iIf([url/@category]='delizioso',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somma di tutti i @totalClicks per i quali la categoria URL è uguale a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somma di tutte le @totalClicks per le quali la categoria URL è uguale a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somma di tutte le @totalClicks per le quali la categoria URL è uguale a "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**condivisioni**

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
   <td> Numero di condivisioni<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Numero totale di messaggi condivisi in questo social network.<br /> </td> 
   <td> Sum(iIf([url/@category]="Valore del tipo di social network",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Percentuale del numero di condivisioni su questo social network rispetto al numero totale di condivisioni.<br /> </td> 
   <td> percentuale(@forward, somma(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Percentuale di condivisione<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Numero di condivisioni della rete rispetto al numero di messaggi da recapitare.<br /> </td> 
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
   <td> Conteggio<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Percentuale del numero di aperture su questo social network rispetto al numero totale di aperture.<br /> </td> 
   <td> percentuale(@open, somma(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Frequenza di aperture<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Numero di aperture su questo social network rispetto al numero totale di messaggi da consegnare.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiche sulla condivisione delle attività {#statistics-on-sharing-activities-1}

Questo report è basato sulle tabelle **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** (nms:webTrackingLog).

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
   <td> @newContacts<br /> </td> 
   <td> Conteggio del numero di visitatori collegati a un destinatario.<br /> </td> 
   <td> Formula: count(@id)<br /> Filter: @recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Apertura di <br /> </td> 
   <td> @opened<br /> </td> 
   <td> Numero di tutti i @ids con tipo di URL uguale a "Open".<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisioni<br /> </td> 
   <td> @shared<br /> </td> 
   <td> Categoria URL inclusa in 'email' , 'facebook' , 'twitter' , 'delizioso' , 'digg' , 'google' , 'linkedin'<br /> Numero di tutti i @totalClicks con una categoria URL uguale a "email", "facebook", "twitter", "delizioso", "digg", "google" o "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN (e-mail' , "facebook" , "twitter" , "delizioso" , "digg" , "google" , "linkedin"), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sistemi operativi {#operating-systems-1}

Questo report è basato sulla tabella **[!UICONTROL Internet Browser Statistics]** (nms:userAgentsStats).

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
   <td> @totalVisitors / @days<br /> </td> 
   <td> Media giornaliera del numero totale di destinatari interessati dal sistema operativo che hanno fatto clic almeno una volta su una consegna.<br /> </td> 
   <td> Somma(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Pagine visualizzate<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Media giornaliera del numero totale di clic sui collegamenti di consegna per sistema operativo per tutte le consegne.<br /> </td> 
   <td> Somma(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> -<br /> </td> 
   <td> Raggruppamento dei visitatori per sistema operativo rispetto al numero totale di visitatori.<br /> </td> 
   <td> percentuale(@totalVisitors, somma(@totalVisitors))<br /> </td> 
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
   <td> @visitors<br /> </td> 
   <td> Percentuale del numero di visitatori al giorno in questo sistema operativo rispetto al numero di visitatori misurato il giorno con il maggior numero di visite.<br /> </td> 
   <td> percentuale(somma(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tariffa globale<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per versione rispetto al numero totale di visitatori su tutti i sistemi operativi.<br /> </td> 
   <td> percentuale(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Percentuale relativa<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per versione rispetto al numero totale di visitatori che utilizzano questo sistema operativo.<br /> </td> 
   <td> percentuale(@totalVisitors, somma(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracciamento abbonamento {#subscription-tracking-1}

Questo report è basato sulla tabella **[!UICONTROL Services]** (nms:service).

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
   <td> Numero di persone registrate il giorno precedente.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Sottoscrizioni<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> numero di sottoscrizioni (@action = 1) nel giorno precedente.<br /> </td> 
   <td> sum(Iif(@action = 1 e @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Annullamenti abbonamenti<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> numero di annullamenti di abbonamenti (azione = 0) nel giorno precedente.<br /> </td> 
   <td> sum(Iif(@action = 0 e @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione<br /> </td> 
   <td> -<br /> </td> 
   <td> Numero di abbonamenti meno il numero di annullamenti di abbonamenti. La tariffa viene calcolata in relazione al numero totale di sottoscrittori.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)',')<br /> </td> 
  </tr> 
  <tr> 
   <td> Fedeltà<br /> </td> 
   <td> -<br /> </td> 
   <td> Tasso di fedeltà del sottoscrittore per il periodo correlato.<br /> </td> 
   <td> 1 percento(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indicatori di tracciamento {#tracking-indicators-1}

Questo report è basato sulle tabelle **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

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
   <td> Messaggi da consegnare<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Conteggio del numero di broadLogs dopo l'analisi della destinazione.<br /> </td> 
   <td> sum([proprietà/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione completata<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Numero di messaggi per i quali il campo "Indirizzo seed" è uguale a "No" e con uno stato uguale a "Preso in considerazione dal provider di servizi" o "Inviato" o "Ricevuto sul dispositivo mobile".<br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Aperture distinte sulla popolazione raggiunta<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Estrapolazione del numero di messaggi aperti distinti per tutti i messaggi e-mail in base al numero di messaggi aperti distinti per i messaggi e-mail in formato html.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Somma delle aperture sulla popolazione raggiunta<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Estrapolazione del numero totale di aperture per tutte le e-mail in base al numero totale di aperture di e-mail in formato html.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Fai clic sul collegamento per annullare l'abbonamento<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Numero di tutti i @ids con una categoria URL uguale a "Rinuncia".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Fa clic sul collegamento alla pagina mirror<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Numero di tutti i @ids con una categoria URL uguale a "Mirror Page".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Stima degli inoltri<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Differenza tra il numero di persone distinte e il numero di destinatari distinti che hanno fatto clic almeno una volta nell'e-mail.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Invia <br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Numero di messaggi per i quali il campo "Indirizzo seed" è uguale a "No" e con uno stato uguale a "Preso in considerazione dal destinatario" o "Inviato" o "Ricevuto su dispositivo mobile".<br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Reclami<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Numero di messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "indirizzo in fase di inserisco nell'elenco Bloccati di".<br /> </td> 
   <td> Count(@status=2 e msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Apertura di <br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Numero di tutti i @broadLog-ids in tutti i registri di tracciamento.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Numero distinto di @broadLog-ids con tipo di URL uguale a "E-mail click". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reattività raw<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale del numero di destinatari che hanno fatto clic su una consegna almeno una volta rispetto al numero di destinatari che hanno aperto una consegna almeno una volta.<br /> </td> 
   <td> percentuale(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic distinti sulla popolazione raggiunta<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Numero di tutti i @source-ids con una categoria URL uguale a "E-mail click".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic cumulati<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Numero di tutti i @ids con una categoria URL uguale a "Email click".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic sul destinatario<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Conteggio distinto del @broadLog-ids con un tipo di URL uguale a "E-mail click".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reattività stimata<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra il numero di destinatari che hanno fatto clic su una consegna almeno una volta e la stima dei destinatari che hanno aperto la consegna almeno una volta.<br /> </td> 
   <td> percentuale(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Pagine visitate<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Numero di tutti i @ids con tipo di URL uguale a "Web" o "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=4 o [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Numero di tutti i @ids con tipo di URL uguale a "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo totale<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Somma di webTrackingLog/@amounts con un tipo di URL uguale a "Transaction". <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo medio delle transazioni<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra l'importo totale e il numero di transazioni.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Elementi<br /> </td> 
   <td> @article<br /> </td> 
   <td> Somma di webTrackingLog/@articles con un tipo di URL uguale a "Transaction".<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Numero medio di elementi per transazione<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra il numero di elementi e il numero di transazioni.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo medio per messaggio<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra la quantità totale e il numero di messaggi da consegnare.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delizioso<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "delizioso".<br /> </td> 
   <td> Sum(iIf([url/@category]='delizioso',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somma di tutte le @totalClicks con una categoria URL uguale a "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL e flussi di clic {#urls-and-click-streams-1}

Questo report è basato sulla tabella **[!UICONTROL Delivery]** (nms:delivery).

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
   <td> Rapporto tra il numero di destinatari che hanno fatto clic su una consegna almeno una volta e il numero stimato di destinatari che hanno aperto una consegna almeno una volta.<br /> </td> 
   <td> percent([indicatori/@recipientClick], [indicatori/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic distinti<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Rapporto tra il numero di persone distinte che hanno fatto clic su una consegna almeno una volta e il numero di messaggi consegnati con successo.<br /> </td> 
   <td> percent([indicatori/@personClick], [indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic cumulati<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Rapporto tra il numero totale di clic per destinatari di destinazione e il numero di messaggi consegnati con successo.<br /> </td> 
   <td> percent([indicatori/@totalRecipientClick], [indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Numero di tutti i @totalClicks con una chiave primaria URL diversa da 1<br /> </td> 
   <td> count(Iif([@url-id]!= 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale del numero di clic rispetto al numero totale di clic cumulativi.<br /> </td> 
   <td> percentuale(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Riepilogo della consegna {#delivery-summary-1}

Questo report è basato sulla tabella **[!UICONTROL Delivery]** (nms:delivery).

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
   <td> sum([proprietà/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi rifiutati dalla regola<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Numero di indirizzi ignorati durante l'analisi in conformità con le regole di tipologia: indirizzo non specificato, messo in quarantena, al inserisco nell'elenco Bloccati di, ecc.<br /> </td> 
   <td> sum([proprietà/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi da consegnare<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Numero totale di messaggi da consegnare dopo l'analisi della consegna.<br /> </td> 
   <td> sum([proprietà/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione completata<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati con successo.<br /> </td> 
   <td> sum([indicatori/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori<br /> </td> 
   <td> @error<br /> </td> 
   <td> Numero totale di errori accumulati durante le consegne e l'elaborazione automatica dei messaggi non recapitati.<br /> </td> 
   <td> sum([indicatori/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuove quarantene<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Numero di indirizzi messi in quarantena a seguito di un errore di consegna (utente sconosciuto, dominio non valido).<br /> </td> 
   <td> sum([indicatori/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot click {#hot-clicks-1}

Questo report è basato sulle tabelle Delivery(nms:delivery) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

Questo rapporto mostra il contenuto del messaggio (HTML e/o testo) e la percentuale di clic per ogni collegamento. La personalizzazione blocca i collegamenti di annullamento dell’abbonamento e i collegamenti alle pagine mirror che vengono presi in considerazione nel totale dei clic cumulativi, ma non vengono visualizzati nel rapporto.

## Statistiche di tracciamento {#tracking-statistics-1}

Questo report è basato sulla tabella **[!UICONTROL Delivery]** (nms:delivery).

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
   <td> @transactions<br /> </td> 
   <td> Somma di tutte le @totalClicks con un tipo di URL uguale a "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Somma di tutte le @totalClicks con un tipo di URL uguale a "E-mail click".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Apri<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somma di tutte le @totalClicks con una chiave primaria URL uguale a 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiche consegna {#delivery-statistics-1}

Questo report è basato sulla tabella **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats).

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
   <td> Numero totale di messaggi con stato "Pronto", "Inviato" o "Non riuscito".<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Consegnato<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati correttamente.<br /> </td> 
   <td> indicatori/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Mancati recapiti permanenti<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Numero totale di messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Utente sconosciuto".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Mancati recapiti non permanenti<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Totale di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "non raggiungibile", "casella in entrata piena", "dominio non valido", "account disabilitato", "non connesso" o "rifiutato"<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> Apertura di <br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Numero totale di @broadLog-ids nei registri di tracciamento.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Numero totale di @source-ids per i quali la categoria URL è uguale a "E-mail click". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Annullamenti abbonamenti<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Numero totale di @ids per cui la categoria URL è uguale a "Rinuncia".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Raggruppamenti delle aperture {#breakdown-of-opens-1}

Questo report è basato su **tabelle Deliveries** (nms:delivery) e **log di tracciamento** (nms:trackingLogRcp).

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
   <td> Apertura di <br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Somma di tutte le @id con una chiave primaria URL uguale a 1 (aperta). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Altri indicatori {#other-indicators}

L&#39;indicatore **Inviato** (@sent), a cui si accede tramite il nodo **Consegne (nms:delivery) > Indicatori**, corrisponde al numero totale di SMS inviati al provider di servizi. Questo indicatore viene utilizzato solo per le consegne SMS e non deve essere utilizzato per altri tipi di consegne (da non confondere con gli indicatori **@success** e **@processed**).

## Sincronizzazione indicatore {#indicator-synchronization}

Se per alcuni indicatori si verificano desincronizzazione o incoerenza, selezionare la consegna interessata in Adobe Campaign Explorer, fare clic con il pulsante destro del mouse e scegliere **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Tracciamento delle aperture {#tracking-opens-}

Affinché Adobe Campaign possa rilevare l’apertura di un messaggio, il destinatario deve scaricare le immagini nell’e-mail. Le e-mail HTML e Multipart/Alternative includono un’immagine a 0 pixel, che consente di rilevare quali messaggi sono stati aperti. Poiché i messaggi in formato di testo non includono immagini, è impossibile rilevare se sono stati aperti o meno. I valori calcolati in base alle aperture dei messaggi sono sempre delle stime, a causa del margine di errore legato alla visualizzazione delle immagini.

## Persone/destinatari interessati {#targeted-persons---recipients}

In alcuni rapporti, Adobe Campaign distingue le persone target dai destinatari target.

I destinatari di destinazione sono tutti i destinatari a cui è stata inviata la consegna.

Il numero di persone include i destinatari interessati e tutte le persone a cui è stata inoltrata l’e-mail. Ogni volta che si apre o si fa clic in un nuovo browser (in cui il messaggio non è ancora stato aperto), alle statistiche viene aggiunta un’altra persona.

Ad esempio, se ricevi un’e-mail (inviata da Adobe Campaign) al lavoro e apri o fai clic su di essa, verrai conteggiato come destinatario mirato (ovvero destinatario=1, persona=1). Se inoltri questa e-mail a due amici, il numero di destinatari target sarà ancora pari a uno, mentre il numero di persone sarà pari a tre. Il valore 3 coincide con ogni apertura o clic in un nuovo browser.
