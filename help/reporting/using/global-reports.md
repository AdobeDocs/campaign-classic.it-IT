---
product: campaign
title: Rapporti globali
description: Rapporti globali
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 1%

---

# Rapporti globali {#global-reports}

![](../../assets/common.svg)

Tali relazioni riguardano l&#39;attività dei dati nell&#39;intero database. Per visualizzare il dashboard dei rapporti, passa alla scheda **[!UICONTROL Reports]** .

![](assets/s_ncs_user_report_delivery_link.png)

Per visualizzare i rapporti, fare clic sui relativi nomi. Per impostazione predefinita sono disponibili i seguenti rapporti:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>Questa sezione mostra solo i rapporti collegati alle consegne.

* **[!UICONTROL Delivery throughput]** : fai riferimento a  [Velocità effettiva di consegna](#delivery-throughput).
* **[!UICONTROL Browsers]** : consulta  [Browser](#browsers).
* **[!UICONTROL Sharing to social networks]** : fare riferimento a  [Condivisione su social network](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** : fare riferimento a  [Statistiche sulle attività di condivisione](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** : fare riferimento a  [Sistemi operativi](#operating-systems).
* **[!UICONTROL URLs and click streams]** : fai riferimento agli  [URL e ai flussi di clic](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : fai riferimento agli indicatori  [di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** : fare riferimento a  [Non-deliverables e rimbalzi](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : consulta Attività  [utente](#user-activities).
* **[!UICONTROL Subscription tracking]** : consulta  [Tracciamento sottoscrizione](#subscription-tracking).
* **[!UICONTROL Delivery summary]** : consulta  [Riepilogo consegne](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : consulta Statistiche di  [consegna](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** : consulta  [Suddivisione delle aperture](#breakdown-of-opens).

## Velocità effettiva di consegna {#delivery-throughput}

Questo rapporto contiene informazioni sulla velocità effettiva di consegna dell’intera piattaforma per un determinato periodo di tempo. Per misurare la velocità con cui vengono inviati i messaggi, i criteri corrispondono al numero di messaggi inviati all’ora e alle dimensioni dei messaggi (in bit al secondo). Nell’esempio seguente, il primo grafico mostra le consegne riuscite in blu e il numero di consegne errate in arancione.

![](assets/s_ncs_user_report_toolbar.png)

Puoi configurare i valori visualizzati modificando la scala cronologica: Vista a 1 ora, visualizzazione a 3 ore, visualizzazione a 24 ore, ecc. Fai clic su **[!UICONTROL Refresh]** per confermare la selezione.

## Attività utente {#user-activities}

Questo rapporto mostra il raggruppamento di aperture, clic e transazioni per mezz&#39;ora, ora o giorno, sotto forma di grafico.

![](assets/s_ncs_user_user_report.png)

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Opens]** : Numero totale di messaggi aperti. Le e-mail in formato testo non vengono prese in considerazione. Per ulteriori informazioni sulle aperture di tracciamento, consulta [Aperture di tracciamento](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Numero totale di clic sui collegamenti nelle consegne. I clic sui collegamenti di annullamento all’abbonamento e sulle pagine mirror non vengono presi in considerazione.
* **[!UICONTROL Transactions]** : Numero totale di transazioni dopo la ricezione di un messaggio. Affinché una transazione possa essere presa in considerazione, è necessario inserire un tag di web tracking di tipo transazione nella pagina web corrispondente. La configurazione del web tracking è presentata in [questa sezione](../../configuration/using/about-web-tracking.md).

## Messaggi non recapitati e non trasferibili {#non-deliverables-and-bounces}

Questo rapporto mostra il raggruppamento dei non-deliverable e un raggruppamento dei mancati recapiti per dominio Internet.

Il **[!UICONTROL Number of messages processed]** rappresenta il numero totale di messaggi elaborati dal server di consegna. Questo valore è inferiore al numero di messaggi da consegnare quando alcune consegne sono state interrotte o messe in pausa (prima di essere elaborate dal server).

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>Gli errori mostrati in questo rapporto attivano il processo di quarantena. Per ulteriori informazioni sulla gestione della quarantena, consulta [Gestione della quarantena](../../delivery/using/understanding-quarantine-management.md).

La prima sezione di questo rapporto mostra la suddivisione dei non risultati finali sotto forma di tabella di valori e di grafico.

Per ogni tipo di errore:

* il numero di messaggi di errore di questo tipo,
* la percentuale di messaggi con errori di questo tipo rispetto al numero totale di messaggi con errori,
* la percentuale di messaggi di errore di questo tipo rispetto al numero totale di messaggi elaborati.

Vengono utilizzati i seguenti indicatori:

* **[!UICONTROL User unknown]** : Tipo di errore generato durante la consegna per indicare che l’indirizzo e-mail non è valido.
* **[!UICONTROL Invalid domain]** : Tipo di errore generato durante l’invio di una consegna per indicare che il dominio dell’indirizzo e-mail è errato o non esiste.
* **[!UICONTROL Inbox full]** : Tipo di errore generato dopo cinque tentativi di consegna per indicare che la casella in entrata dei destinatari contiene troppi messaggi.
* **[!UICONTROL Account disabled]** : Tipo di errore generato durante l’invio di una consegna per indicare che l’indirizzo non esiste più.
* **[!UICONTROL Rejected]** : Tipo di errore generato quando un indirizzo viene rifiutato dall&#39;IAP (Internet Access Provider), ad esempio in seguito all&#39;applicazione di una regola di sicurezza (software anti-spam).
* **[!UICONTROL Unreachable]** : Tipo di errore che si verifica nella stringa di distribuzione del messaggio: incidente sul relè SMTP, dominio temporaneamente irraggiungibile, ecc
* **[!UICONTROL Not connected]** : Tipo di errore per indicare che il telefono cellulare dei destinatari è spento o disconnesso dalla rete al momento dell&#39;invio.

   >[!NOTE]
   >
   >Questo indicatore riguarda solo le consegne sui canali mobili. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/sms-channel.md).

   Per aprire ciascuna riga della tabella dei valori, fai clic sul simbolo `[+]` . Per ogni tipo di errore, puoi visualizzare la suddivisione dei messaggi di errore per dominio.

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

La seconda sezione del rapporto mostra la suddivisione degli errori per dominio Internet sotto forma di tabella di valori e grafico.

Per ogni nome di dominio, abbiamo:

* il numero di messaggi con errori per questo dominio,
* la percentuale di messaggi con errori per questo dominio rispetto al numero totale di messaggi elaborati per questo dominio,
* la percentuale di messaggi di errore per questo dominio rispetto al numero totale di messaggi di errore.

Per aprire ciascuna riga della tabella dei valori, fai clic sul simbolo [+]. Per ogni tipo di dominio, puoi visualizzare la suddivisione dei messaggi di errore in base al tipo di errore.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>I nomi di dominio visualizzati in questo report vengono definiti a livello di cubo. Per modificare questi valori, modificare il cubo **[!UICONTROL Delivery logs (broadlogrcp)]**. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/about-cubes.md). La categoria **[!UICONTROL Others]** include nomi di dominio che non appartengono a una classe specifica.

## Browser {#browsers}

Questo rapporto mostra la suddivisione dei browser Internet utilizzati dai destinatari della consegna per il periodo in questione.

>[!NOTE]
>
>I valori indicati nel rapporto sono stime: verranno presi in considerazione solo i destinatari che hanno fatto clic su in una consegna.

**Statistiche globali**

Le statistiche globali sull&#39;uso del browser sono presentate sotto forma di tabella di valori e di grafico.

![](assets/dlv_explorers_report.png)

Vengono utilizzati i seguenti indicatori:

* **[!UICONTROL Visitors]** : Numero totale di destinatari interessati (per browser Internet) e che hanno fatto clic su una consegna almeno una volta.
* **[!UICONTROL Pages viewed]** : Numero totale di clic sui collegamenti in una consegna (per browser Internet) per tutte le consegne.
* **[!UICONTROL Usage rate]** : Questo tasso rappresenta la suddivisione dei visitatori (per browser Internet) in relazione al numero totale di visitatori.

**Statistiche per browser**

Nella tabella dei valori statistici globali, puoi fare clic sul nome di ciascun browser per visualizzarne le statistiche di utilizzo.

![](assets/s_ncs_user_explorers_report2.png)

Le statistiche sono presentate sotto forma di curva, grafico e tabella dei valori.

La curva **[!UICONTROL History]** rappresenta il tasso di frequenza giornaliera del browser. Il tasso è il rapporto tra il numero di visitatori al giorno (su questo browser) e il numero di visitatori misurato al giorno con il tasso di presenza più alto.

Il grafico **[!UICONTROL Breakdown per version]** rappresenta la suddivisione dei visitatori per versione rispetto al numero totale di visitatori (in questo browser).

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Global rate]** : Questo tasso rappresenta la suddivisione dei visitatori per versione rispetto al numero totale di visitatori (su tutti i browser).
* **[!UICONTROL Relative rate]** : Questo tasso rappresenta la suddivisione dei visitatori per versione rispetto al numero totale di visitatori (in questo browser).

### Condivisione sui social network {#sharing-to-social-networks}

Il marketing virale consente ai destinatari della consegna di condividere informazioni con la loro rete di contatti: possono aggiungere un collegamento al loro profilo (Facebook, Twitter, ecc.) o inviare un messaggio ad un amico. Ogni condivisione e ogni accesso alle informazioni condivise viene tracciato all&#39;interno della consegna. Per ulteriori informazioni sul marketing virale, consulta [questa sezione](../../delivery/using/viral-and-social-marketing.md).

Questo rapporto mostra la suddivisione dei messaggi condivisi e aperti per social network (Facebook, Twitter, ecc.) e/o per e-mail.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

Nelle statistiche di consegna e-mail vengono visualizzati due valori:

* **[!UICONTROL Number of messages to be delivered]** : Numero totale di messaggi elaborati durante l’analisi della consegna.
* **[!UICONTROL Number of successful deliveries]** : Numero di messaggi elaborati correttamente.

**[!UICONTROL Sharing activities and mail open statistics]**

La tabella centrale mostra le statistiche sulle condivisioni e-mail e si apre.

Nella colonna **[!UICONTROL Shares]** sono disponibili i seguenti indicatori:

* **[!UICONTROL No. of sharing activities]** : Numero totale di messaggi condivisi su ogni social network. Questo valore è uguale al numero totale di clic sull&#39;icona del blocco di personalizzazione **[!UICONTROL Links for sharing to social networks]** corrispondente.
* **[!UICONTROL Breakdown]** : Questo tasso rappresenta la disaggregazione delle azioni per rete sociale, in relazione al numero totale di azioni.
* **[!UICONTROL Sharing rate]** : Tale tasso corrisponde alla ripartizione delle azioni per rete sociale, in relazione al numero di messaggi da inviare.

Nella colonna **[!UICONTROL Opens]** sono disponibili i seguenti indicatori:

* **[!UICONTROL No. of opens]** : Numero totale di messaggi aperti dalle persone a cui è stato inoltrato il messaggio (tramite il blocco di  **[!UICONTROL Links for sharing to social networks]** personalizzazione). Questo valore è uguale al numero di volte in cui è stata visualizzata la pagina speculare. Le aperture da parte dei destinatari della consegna non vengono prese in considerazione.
* **[!UICONTROL Breakdown]** : Questo tasso rappresenta la disaggregazione delle aperture per rete sociale, in relazione al numero totale di aperture.
* **[!UICONTROL Rate of opens]** : Questo tasso rappresenta la disaggregazione delle aperture per rete sociale, in relazione al numero totale di azioni.

**[!UICONTROL Breakdown of sharing activities and opens]**

Questa sezione include due grafici che rappresentano la suddivisione delle attività di condivisione e si apre per ogni social network.

## Statistiche sulle attività di condivisione {#statistics-on-sharing-activities}

Questo rapporto mostra l&#39;evoluzione delle condivisioni sui social network (Facebook, Twitter, e-mail, ecc.) in tempo.

Per ulteriori informazioni sul marketing virale, consulta [questa sezione](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

Le statistiche sono presentate sotto forma di tabella di valori e di grafico.

Vengono utilizzati i seguenti indicatori:

* **[!UICONTROL New contacts]** : Numero di nuovi abbonamenti a seguito della ricezione di un messaggio condiviso via e-mail. Questo valore corrisponde al numero di persone che hanno ricevuto un messaggio condiviso tramite e-mail, hanno fatto clic su **[!UICONTROL Subscription link]** e hanno compilato il modulo di abbonamento.
* **[!UICONTROL Opens]** : Numero totale di messaggi aperti dalle persone a cui è stato trasferito il messaggio (tramite il blocco di  **[!UICONTROL Link for sharing to social networks]** personalizzazione). Questo valore è uguale al numero di volte in cui è stata visualizzata la pagina speculare. Le aperture da parte dei destinatari della consegna non vengono prese in considerazione.
* **[!UICONTROL Sharing activities]** : Numero totale di messaggi condivisi tramite i social network. Questo valore corrisponde al numero totale di clic sull&#39;icona del blocco di personalizzazione **[!UICONTROL Links for sharing to social networks]**.

## Sistemi operativi {#operating-systems}

Il rapporto mostra la ripartizione dei sistemi operativi utilizzati dai destinatari della consegna per il periodo in questione.

>[!NOTE]
>
>I valori indicati nel rapporto sono stime: verranno presi in considerazione solo i destinatari che hanno fatto clic su in una consegna.

**Statistiche globali**

Le statistiche di utilizzo globale dei sistemi operativi sono presentate sotto forma di tabella dei valori e di grafico.

![](assets/s_ncs_user_os_report.png)

Vengono utilizzati i seguenti indicatori:

* **[!UICONTROL Visitors]** : Media giornaliera del numero totale di destinatari (per sistema operativo) che hanno fatto clic su una consegna almeno una volta.
* **[!UICONTROL Pages viewed]** : Media giornaliera del numero totale di clic sui collegamenti di consegna (per sistema operativo) per tutte le consegne.
* **[!UICONTROL Rate of use]** : Questo tasso rappresenta la suddivisione dei visitatori (per sistema operativo) in relazione al numero totale di visitatori.

**Statistiche per sistema operativo**

Nella tabella dei valori delle statistiche globali, fare clic sul nome di ciascun sistema operativo per visualizzare le statistiche per sistema operativo.

![](assets/s_ncs_user_os_report2.png)

Le statistiche sono presentate sotto forma di curva, grafico e tabella dei valori.

La curva **[!UICONTROL History]** rappresenta il tasso di utilizzo di questo sistema operativo al giorno. Questo tasso è il rapporto tra il numero di visitatori al giorno (su questo sistema operativo) e il numero di visitatori misurato il giorno con la maggiore frequenza.

Il grafico **[!UICONTROL Breakdown by version]** rappresenta la suddivisione dei visitatori per versione in relazione al numero totale di visitatori in questo sistema operativo.

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Global rate]** : Questo tasso rappresenta la suddivisione dei visitatori (per versione) in relazione al numero totale di visitatori in tutti i sistemi operativi.
* **[!UICONTROL Relative rate]** : Questo tasso rappresenta la suddivisione dei visitatori (per versione) in relazione al numero totale di visitatori per questo sistema operativo.

## Tracciamento sottoscrizione {#subscription-tracking}

Questo rapporto ti consente di monitorare gli abbonamenti ai servizi di informazione. Mostra abbonamenti e annullamenti degli abbonamenti.

![](assets/s_ncs_user_services_report.png)

Può essere visualizzato per una sottoscrizione facendo clic sul nodo **[!UICONTROL Profiles and targets > Services and subscriptions]** della home page o dell&#39;explorer. Seleziona l’abbonamento desiderato, quindi fai clic sulla scheda **[!UICONTROL Reports]** . Il rapporto **[!UICONTROL Subscriptions tracking]** è disponibile per impostazione predefinita. Ti consente di visualizzare le tendenze di abbonamento e annullamento dell’abbonamento e il tasso di fedeltà in un periodo. Puoi configurare la rappresentazione di questi dati tramite l’elenco a discesa . Fai clic su **[!UICONTROL Refresh]** per convalidare la configurazione selezionata.

Per ulteriori informazioni, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).

Il **[!UICONTROL Number subscribed to date]** rappresenta il numero totale di persone attualmente abbonate.

**[!UICONTROL Overall evolution of subscriptions]**

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Subscribers]** : Numero totale di abbonati per il periodo in questione.
* **[!UICONTROL Subscriptions]** : Numero di abbonamenti per il periodo in questione.
* **[!UICONTROL Unsubscriptions]** : Numero di annullamenti per il periodo in questione.
* **[!UICONTROL Evolution]** : Numero di annullamenti di sottoscrizioni meno il numero di sottoscrizioni. Il tasso viene calcolato in base al numero totale di abbonati.
* **[!UICONTROL Loyalty]** : Tasso di fedeltà degli abbonati per il periodo in questione.

**[!UICONTROL Subscription evolution curves]**

Questo grafico mostra l’evoluzione degli abbonamenti e degli annullamenti degli abbonamenti per il periodo in questione.

## Statistiche di consegna {#delivery-statistics}

Questo rapporto mostra la suddivisione per dominio Internet di tutti i messaggi elaborati e inviati, di mancati recapiti rigidi e morbidi, aperture, clic e annullamenti dell’abbonamento.

![](assets/s_ncs_user_broadcast_report.png)

Vengono utilizzati i seguenti indicatori:

* **[!UICONTROL Emails processed]** : Numero totale di messaggi elaborati dal server di consegna.
* **[!UICONTROL Delivered]** : percentuale del numero di messaggi elaborati correttamente rispetto al numero totale di messaggi elaborati.
* **[!UICONTROL Hard bounces]** : percentuale del numero di messaggi non recapitati &quot;hard&quot; rispetto al numero totale di messaggi elaborati.
* **[!UICONTROL Soft bounces]** : percentuale del numero di messaggi non recapitati &quot;soft&quot; rispetto al numero totale di messaggi elaborati.

   >[!NOTE]
   >
   >Per ulteriori informazioni sui rimbalzi rigidi e morbidi, consulta [Gestione della quarantena](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : percentuale del numero di destinatari che hanno aperto un messaggio almeno una volta rispetto al numero di messaggi elaborati correttamente.
* **[!UICONTROL Clicks]** : percentuale del numero di persone che hanno fatto clic in una consegna almeno una volta rispetto al numero di messaggi elaborati correttamente.
* **[!UICONTROL Unsubscription]** : percentuale del numero di clic su un collegamento di annullamento dell’abbonamento rispetto al numero di messaggi elaborati correttamente.

## Suddivisione delle aperture {#breakdown-of-opens}

Questo rapporto mostra la suddivisione delle aperture per sistema operativo, dispositivo e browser per il periodo in questione. Per ogni categoria vengono utilizzati due grafici. Il primo visualizza le statistiche relative all&#39;apertura su un computer e dispositivi mobili. Il secondo visualizza le statistiche relative solo all’apertura su dispositivi mobili.

Il numero di aperture corrisponde al numero totale di messaggi aperti. Le e-mail in formato testo non vengono conteggiate. Per ulteriori informazioni sulle aperture di Tracking, consulta la sezione [Aperture di Tracking](../../reporting/using/indicator-calculation.md#tracking-opens-) .

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>I nomi dei browser e dei sistemi operativi costituiscono parte delle informazioni inviate dall&#39;agente utente del browser a cui il messaggio è stato aperto. Adobe Campaign deduce il tipo di dispositivo utilizzando le relative informazioni sul dispositivo.
