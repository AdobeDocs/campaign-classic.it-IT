---
product: campaign
title: Calcolo indicatore
description: Calcolo indicatore
feature: Reporting
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 6%

---

# Calcolo indicatore {#indicator-calculation}

![](../../assets/common.svg)

## Attività utente {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
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
   <td> @click<br /> </td> 
   <td> Somma di tutti i @totalClicks con un tipo di URL uguale a "Email click".<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transazioni<br /> </td> 
   <td> Somma di tutti i @totalClicks con un tipo di URL uguale a "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Questo rapporto si basa sul **[!UICONTROL Consolidated tracking]** tabella (nms:trackingStats). Questa tabella aggregata viene utilizzata per motivi di prestazioni durante la visualizzazione dei rapporti, al posto della **[!UICONTROL Recipient tracking logs]** tabella (nms:trackingLogRcp) e non viene calcolata in tempo reale. La tabella viene generata alcuni minuti dopo il recupero dei log di tracciamento. Se gli indicatori sono aggiornati, i risultati saranno gli stessi degli indicatori del **Indicatori di tracciamento** rapporto. L&#39;indicatore @totalclick esprime il numero totale di clic su un periodo di 5 minuti.

## Messaggi non recapitati e non trasferibili {#non-deliverables-and-bounces-1}

**Suddivisione per tipo di errore**

Questo rapporto si basa sul **[!UICONTROL Delivery and tracking statistics]** tabella (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero totale di messaggi elaborati<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Somma dei messaggi con stato uguale a "Ready", "Sent" o "Failed" (Pronto).<br /> </td> 
   <td> @ready + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Utente sconosciuto". <br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Non raggiungibile <br /> </td> 
   <td> @irraggiungibile<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Non raggiungibile". <br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato<br /> </td> 
   <td> @@rifiutato<br /> </td> 
   <td> Numero di tutti i messaggi con stato uguale a "Non riuscito" e motivo uguale a "Rifiutato". <br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido<br /> </td> 
   <td> @validDomain<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Dominio non valido". <br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Account disabilitato<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Numero di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Account disabilitato".<br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Casella in entrata piena<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Conteggio di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Casella in entrata piena". <br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori<br /> </td> 
   <td> @valore<br /> </td> 
   <td> Numero di messaggi non riusciti per questo tipo di errore.<br /> </td> 
   <td> Count(@status=2 e msg/@failedReason="Valore del tipo di errore")<br /> </td> 
  </tr> 
  <tr> 
   <td> Contributo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di errori di questo tipo rispetto al numero totale di messaggi di errore.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di errori di questo tipo rispetto al numero totale di messaggi elaborati.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Suddivisione per dominio**

La seconda parte del rapporto descrive la suddivisione dei messaggi non riusciti per dominio Internet anziché per tipo di errore. La formula collegata al **Errore** indicatore (@value) in questo caso è: Count(@status=2 e @domain=&quot;Value of the domain name&quot;), cioè un conteggio di tutti i messaggi con uno stato non riuscito per questo dominio.

## Browser {#browsers-1}

Questo rapporto si basa sul **[!UICONTROL Internet Browser Statistics]** tabella (nms:userAgentsStats).

**Statistiche globali**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitatori<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Numero totale di destinatari per il browser che ha fatto clic su in una consegna almeno una volta.<br /> </td> 
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
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
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
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> @visitatori<br /> </td> 
   <td> Percentuale del numero di visitatori al giorno che utilizzano questo browser rispetto al numero di visitatori misurato nel giorno con il maggior numero di visite.<br /> </td> 
   <td> percent(sum(@visitatori),max(@visitatoriOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso globale<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questa versione rispetto al numero totale di visitatori che utilizzano tutti i browser.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Peso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per questa versione rispetto al numero totale di visitatori che utilizzano questo browser.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Condivisione sui social network {#sharing-to-social-networks-1}

Questo rapporto si basa sul **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** tabelle (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero di messaggi da inviare<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Numero totale di messaggi elaborati durante l’analisi della consegna.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Numero di consegne riuscite<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati correttamente <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @e-mail<br /> </td> 
   <td> Somma di tutti i @totalClicks per i quali la categoria URL è uguale a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somma di tutti i @totalClicks per i quali la categoria URL è uguale a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somma di tutti i @totalClicks per i quali la categoria URL è uguale a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delizioso<br /> </td> 
   <td> @delizioso<br /> </td> 
   <td> Somma di tutti @totalClicks per i quali la categoria URL è uguale a "delizioso".<br /> </td> 
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
   <td> Somma di tutti i @totalClicks per i quali la categoria URL è uguale a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somma di tutti i @totalClicks per i quali la categoria URL è uguale a "linkedin".<br /> </td> 
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
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero di azioni<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Numero totale di messaggi condivisi nel social network.<br /> </td> 
   <td> Sum(iIf([url/@category]="Valore del tipo di social network",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Percentuale del numero di azioni di questo social network rispetto al numero totale di azioni.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
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
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Numero di aperture <br /> </td> 
   <td> @open<br /> </td> 
   <td> Numero totale di righe di tracciamento nella tabella di tracciamento web.<br /> </td> 
   <td> Conteggio<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Percentuale del numero di aperture su questo social network rispetto al numero totale di aperture.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di apertura<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Numero di aperture su questo social network rispetto al numero totale di messaggi da inviare.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiche sulle attività di condivisione {#statistics-on-sharing-activities-1}

Questo rapporto si basa sul **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) e **[!UICONTROL Web tracking]** tabelle (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nuovi contatti<br /> </td> 
   <td> @newContatti<br /> </td> 
   <td> Numero di visitatori collegati a un destinatario.<br /> </td> 
   <td> Formula: count(@id)<br /> Filtro: @recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @open<br /> </td> 
   <td> Numero di tutti gli @ids con un tipo di URL uguale a "Open".<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Azioni<br /> </td> 
   <td> @shared<br /> </td> 
   <td> Categoria URL inclusa in "email" , "facebook" , "twitter" , "delizioso" , "digg" , "google" , "linkedin"<br /> Numero di tutti @totalClicks con una categoria URL che è uguale a "email", "facebook", "twitter", "delizioso", "digg", "google" o "linkedin".<br /> </td> 
   <td> count (Iif([url/@category] IN (e-mail' , 'facebook' , 'twitter' , 'delizioso' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sistemi operativi {#operating-systems-1}

Questo rapporto si basa sul **[!UICONTROL Internet Browser Statistics]** tabella (nms:userAgentsStats).

**Statistiche globali**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Visitatori<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Media giornaliera del numero totale di destinatari interessati dal sistema operativo che hanno fatto clic su una consegna almeno una volta.<br /> </td> 
   <td> Sum(@visitatori)<br /> </td> 
  </tr> 
  <tr> 
   <td> Pagine visualizzate<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Media giornaliera del numero totale di clic sui collegamenti di consegna per sistema operativo per tutte le consegne.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> -<br /> </td> 
   <td> Suddivisione dei visitatori per sistema operativo rispetto al numero totale di visitatori.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
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
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Tasso di utilizzo<br /> </td> 
   <td> @visitatori<br /> </td> 
   <td> Percentuale del numero di visitatori al giorno in questo sistema operativo rispetto al numero di visitatori misurato nel giorno con il maggior numero di visite.<br /> </td> 
   <td> percent(sum(@visitatori), max(@visitatoriOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso globale<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per versione rispetto al numero totale di visitatori per tutti i sistemi operativi.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso relativo<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale di visitatori per versione rispetto al numero totale di visitatori che utilizzano questo sistema operativo.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracciamento sottoscrizione {#subscription-tracking-1}

Questo rapporto si basa sul **[!UICONTROL Services]** tabella (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
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
   <td> Abbonamenti<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> conteggio degli abbonamenti (@action = 1) il giorno precedente.<br /> </td> 
   <td> sum(Iif(@action = 1 e @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Abbonamenti annullati<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> numero di annullamenti di abbonamenti (azione = 0) il giorno precedente.<br /> </td> 
   <td> sum(Iif(@action = 0 e @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione<br /> </td> 
   <td> -<br /> </td> 
   <td> Numero di sottoscrizioni meno il numero di annullamenti di sottoscrizioni. Il tasso è calcolato in relazione al numero totale di abbonati.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.0 0')+ '%)',')<br /> </td> 
  </tr> 
  <tr> 
   <td> Fedeltà<br /> </td> 
   <td> -<br /> </td> 
   <td> Tasso fedeltà sottoscrittore per il periodo correlato.<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Indicatori di tracciamento {#tracking-indicators-1}

Questo rapporto si basa sul **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats) tabelle.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messaggi da consegnare<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Numero di wideLogs dopo l’analisi del target.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione riuscita<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Numero di messaggi per i quali il campo "indirizzo di seed" è uguale a "No" e con uno stato uguale a "Preso in considerazione dal fornitore di servizi" o "Inviato" o "Ricevuto sul cellulare".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Si apre una distinta sulla popolazione raggiunta<br /> </td> 
   <td> @EstimatedRecipientOpen<br /> </td> 
   <td> Estrapolazione del numero di aperture distinte per tutte le e-mail in base al numero di aperture distinte per le e-mail in formato html.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Somma delle aperture sulla popolazione raggiunta<br /> </td> 
   <td> @EstimTotalRecipientOpen<br /> </td> 
   <td> Estrapolazione del numero totale di aperture per tutte le e-mail in base al numero totale di aperture di e-mail in formato html.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic sul collegamento per annullare l’abbonamento<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Numero di tutti gli @ids con una categoria URL uguale a "Rinuncia".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic sul collegamento alla pagina speculare<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Numero di tutti gli @ids con una categoria URL uguale a "Pagina speculare".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Stima degli inoltri<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Differenza tra il numero di persone distinte e il numero di destinatari distinti che hanno fatto clic almeno una volta nell’e-mail.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Invio<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Conteggio dei messaggi per i quali il campo "indirizzo di seed" è uguale a "No" e con uno stato uguale a "preso in considerazione dal destinatario" o "Inviato" o "Ricevuto su cellulare".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Reclami<br /> </td> 
   <td> @reclami<br /> </td> 
   <td> Numero di messaggi con stato uguale a "Non riuscito" e motivo uguale a "indirizzo al elenco Bloccati".<br /> </td> 
   <td> Count(@status=2 e msg/@failedReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Numero di tutti gli @wideLog-id in tutti i log di tracciamento.<br /> </td> 
   <td> Countdistinct ([@wideLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Conteggio distinto di @wideLog-ids con un tipo di URL uguale a "Clic su e-mail". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @wideLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reattività grezza<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentuale del numero di destinatari che hanno fatto clic in una consegna almeno una volta rispetto al numero di destinatari che hanno aperto una consegna almeno una volta.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic distinto sulla popolazione raggiunta<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Numero di tutti gli @source-ids con una categoria URL uguale a "Clic su e-mail".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic cumulativo<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Numero di tutti gli @id con una categoria URL che è uguale a "Clic su e-mail".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic del destinatario<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Conteggio distinto degli @wideLog-ids con un tipo di URL che è uguale a "Email click".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @wideLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Reattività stimata<br /> </td> 
   <td> -<br /> </td> 
   <td> Rapporto tra il numero di destinatari che hanno fatto clic su in una consegna almeno una volta rispetto alla stima dei destinatari che hanno aperto la consegna almeno una volta.<br /> </td> 
   <td> percent(@recipientClick, @EstimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Pagine visitate<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Numero di tutti gli @ids con un tipo di URL uguale a "Web" o "Transaction".<br /> </td> 
   <td> count(Iif([url/@type]=4 o [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transazione<br /> </td> 
   <td> Numero di tutti gli @ids con un tipo di URL uguale a "Transazione".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Importo totale<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Somma di webTrackingLog/@amount con un tipo di URL uguale a "Transaction". <br /> </td> 
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
   <td> Somma di webTrackingLog/@articoli con un tipo di URL che è uguale a "Transaction".<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
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
   <td> Rapporto tra l’importo totale e il numero di messaggi da consegnare.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @e-mail<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "email".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delizioso<br /> </td> 
   <td> @delizioso<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "delizioso".<br /> </td> 
   <td> Sum(iIf([url/@category]='delizioso',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Somma di tutti i @totalClicks con una categoria URL che è uguale a "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL e flussi di clic {#urls-and-click-streams-1}

Questo rapporto si basa sul **[!UICONTROL Delivery]** tabella (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reattività<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Rapporto tra il numero di destinatari con cui hai fatto clic su una consegna almeno una volta rispetto al numero stimato di destinatari con cui hai aperto una consegna almeno una volta.<br /> </td> 
   <td> percentuale([indicatori/@destinatariClick], [indicatori/@stimatoRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic distinto<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Rapporto tra il numero di persone distinte che hanno fatto clic su in una consegna almeno una volta rispetto al numero di messaggi consegnati con successo.<br /> </td> 
   <td> percentuale([indicatori/@personaClic], [indicatori/@successo])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic cumulativo<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Rapporto tra il numero totale di clic dei destinatari con targeting e il numero di messaggi consegnati con successo.<br /> </td> 
   <td> percentuale([indicatori/@totalRecipientClick], [indicatori/@successo])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Numero di tutti @totalClicks con una chiave primaria URL diversa da 1<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
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

Questo rapporto si basa sul **[!UICONTROL Delivery]** tabella (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
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
   <td> @rifiuto<br /> </td> 
   <td> Numero di indirizzi ignorati durante l’analisi in linea con le regole di tipologia: indirizzo non specificato, messo in quarantena, al elenco Bloccati, ecc.<br /> </td> 
   <td> sum([proprietà/@rifiuto])<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi da consegnare<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Numero totale di messaggi da consegnare dopo l’analisi della consegna.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Operazione riuscita<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati con successo.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori<br /> </td> 
   <td> @error<br /> </td> 
   <td> Numero totale di errori cumulati durante le consegne e l’elaborazione automatica dei messaggi non recapitati.<br /> </td> 
   <td> sum([indicators/@errore])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nuove quarantene<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Numero di indirizzi messi in quarantena dopo un errore di consegna (dominio sconosciuto, dominio non valido).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot click {#hot-clicks-1}

Questo rapporto si basa sulla consegna (nms:delivery) e **[!UICONTROL Consolidated tracking]** (nms:trackingStats) tabelle.

Questo rapporto mostra il contenuto del messaggio (HTML e/o testo) e la percentuale di clic per ogni collegamento. I blocchi di personalizzazione per i collegamenti di annullamento dell’abbonamento e i collegamenti alle pagine mirror vengono presi in considerazione nei clic cumulati totali, ma non vengono visualizzati nel rapporto.

## Tracking delle statistiche {#tracking-statistics-1}

Questo rapporto si basa sul **[!UICONTROL Delivery]** tabella (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transazioni<br /> </td> 
   <td> @transazioni<br /> </td> 
   <td> Somma di tutti i @totalClicks con un tipo di URL che è uguale a "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @click<br /> </td> 
   <td> Somma di tutti i @totalClicks con un tipo di URL che è uguale a "Email click".<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Apri<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Somma di tutti @totalClicks con una chiave primaria URL uguale a 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiche consegna {#delivery-statistics-1}

Questo rapporto si basa sul **[!UICONTROL Delivery and tracking statistics]** tabella (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> E-mail elaborate<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Numero totale di messaggi con stato uguale a "Ready", "Sent" o "Failed" (Pronto).<br /> </td> 
   <td> @ready + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Consegnato<br /> </td> 
   <td> @success<br /> </td> 
   <td> Numero di messaggi elaborati correttamente.<br /> </td> 
   <td> indicators/@success<br /> </td> 
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
   <td> Totale di tutti i messaggi con uno stato uguale a "Non riuscito" e un motivo uguale a "Non raggiungibile", "Posta in arrivo piena", "dominio non valido", "account disabilitato", "non connesso" o "rifiutato"<br /> </td> 
   <td> @unreachable + @mailBoxFull + @InvalidDomain + @disabled + @notConnected + @rifiutato<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Numero totale di @wideLog-ids nei log di tracciamento.<br /> </td> 
   <td> Countdistinct ([@wideLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Numero totale di @source-ids per i quali la categoria URL è uguale a "Clic su e-mail". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Abbonamenti annullati<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Numero totale di @id per i quali la categoria URL è uguale a "Rinuncia".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Breakdown delle aperture {#breakdown-of-opens-1}

Questo rapporto si basa su **Consegne** (nms:delivery) e **Registri di tracciamento** (nms:trackingLogRcp) tabelle.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Etichetta</strong> <br /> </th> 
   <th> <strong>Nome campo</strong> <br /> </th> 
   <th> <strong>Descrizione indicatore</strong> <br /> </th> 
   <th> <strong>Formula di calcolo dell'indicatore</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Messaggi aperti<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Somma di tutti gli @id con una chiave primaria URL uguale a 1 (aperta). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Altri indicatori {#other-indicators}

La **Inviato** indicatore (@sent), accessibile tramite **Consegne (nms:delivery) > Indicatori** nodo corrisponde al numero totale di SMS inviati al provider di servizi. Questo indicatore viene utilizzato solo per le consegne SMS e non deve essere utilizzato per altri tipi di consegne (da non confondere con il **@success** e **@elaborati** indicatori).

## Sincronizzazione indicatore {#indicator-synchronization}

Se si verifica una desincronizzazione o un’incoerenza per determinati indicatori, seleziona la consegna interessata nell’explorer di Adobe Campaign, fai clic con il pulsante destro del mouse e scegli **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Fai clic su **[!UICONTROL Next]**, quindi fai clic su **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Aperture di tracciamento {#tracking-opens-}

Affinché Adobe Campaign possa rilevare l’apertura dei messaggi, il destinatario deve scaricare le immagini nell’e-mail. Le e-mail HTML e Multipart/Alternative includono un’immagine a 0 pixel, che consente di rilevare i messaggi aperti. Poiché i messaggi in formato testo non includono immagini, è impossibile rilevare se sono stati aperti o meno. I valori calcolati in base all&#39;apertura dei messaggi sono sempre stime, a causa del margine di errore collegato alla visualizzazione dell&#39;immagine.

## Persone/destinatari interessati {#targeted-persons---recipients}

In alcuni rapporti, Adobe Campaign distingue le persone mirate e i destinatari mirati.

I destinatari di destinazione sono tutti i destinatari a cui è stata inviata la consegna.

Il numero di persone include destinatari con targeting e tutte le persone a cui è stato inoltrato il messaggio e-mail. Ogni volta che si apre o si fa clic in un nuovo browser (in cui il messaggio non è ancora stato aperto), alle statistiche viene aggiunta un’altra persona.

Ad esempio, se ricevi un’e-mail (inviata da Adobe Campaign) sul posto di lavoro e la apri o fai clic su di essa, verrai conteggiato come destinatario con targeting (ad esempio, destinatario=1, persona=1). Se invii questa e-mail a due amici, il numero di destinatari target sarà ancora uguale a uno, mentre il numero di persone sarà uguale a tre. Il valore 3 coincide con ogni apertura/clic in un nuovo browser.
