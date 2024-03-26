---
product: campaign
title: Rapporti globali
description: Rapporti globali
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '2292'
ht-degree: 8%

---

# Rapporti globali {#global-reports}



Tali relazioni riguardano l&#39;attività dei dati nell&#39;intero database. Per visualizzare il dashboard dei rapporti, vai al **[!UICONTROL Reports]** scheda.

![](assets/s_ncs_user_report_delivery_link.png)

Per visualizzare i rapporti, fai clic sui relativi nomi. Per impostazione predefinita sono disponibili i seguenti rapporti:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>Questa sezione mostra solo i rapporti collegati alle consegne.

* **[!UICONTROL Delivery throughput]** : fai riferimento a [Velocità effettiva di consegna](#delivery-throughput).
* **[!UICONTROL Browsers]** : fai riferimento a [Browser](#browsers).
* **[!UICONTROL Sharing to social networks]** : fai riferimento a [Condivisione sui social network](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** : fai riferimento a [Statistiche sulla condivisione delle attività](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** : fai riferimento a [Sistemi operativi](#operating-systems).
* **[!UICONTROL URLs and click streams]** : fai riferimento a [URL e flussi di clic](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : fai riferimento a [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** : fai riferimento a [Non consegnabili e mancati recapiti](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : fai riferimento a [Attività degli utenti](#user-activities).
* **[!UICONTROL Subscription tracking]** : fai riferimento a [Tracciamento abbonamento](#subscription-tracking).
* **[!UICONTROL Delivery summary]** : fai riferimento a [Riepilogo delle consegne](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : fai riferimento a [Statistiche consegna](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** : fai riferimento a [Raggruppamento delle aperture](#breakdown-of-opens).

## Velocità di consegna {#delivery-throughput}

Questo rapporto contiene informazioni sulla velocità effettiva di consegna dell’intera piattaforma per un determinato periodo. I criteri utilizzati per misurare la velocità con cui vengono consegnati i messaggi comprendono il numero di messaggi inviati all’ora e le dimensioni dei messaggi (in bit al secondo). Nell’esempio seguente, il primo grafico mostra le consegne riuscite in blu e il numero di consegne con errori in arancione.

![](assets/s_ncs_user_report_toolbar.png)

Puoi configurare i valori visualizzati modificando la scala cronologica: visualizzazione a 1 ora, visualizzazione a 3 ore, visualizzazione a 24 ore, ecc. Clic **[!UICONTROL Refresh]** per confermare la selezione.

>[!NOTE]
>
>Se l’istanza è ospitata su AWS, puoi anche monitorare il numero di consegne inviate all’ora utilizzando il Campaign Classic [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=it).
>
>Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
>
>Tieni presente che l’istanza deve essere aggiornata con l’ultima versione [Gold Standard](../../rn/using/gold-standard.md) build o [build GA più recente (21.1.3)](../../rn/using/latest-release.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Attività degli utenti {#user-activities}

Questo rapporto mostra il raggruppamento di aperture, clic e transazioni per mezz’ora, ora o giorno, sotto forma di un grafico.

![](assets/s_ncs_user_user_report.png)

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Opens]** : numero totale di messaggi aperti. Le e-mail in formato testo non vengono prese in considerazione. Per ulteriori informazioni sulle aperture di tracciamento, consulta [Tracciamento delle aperture](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : numero totale di clic sui collegamenti nelle consegne. I clic sui collegamenti di annullamento dell’abbonamento e sulle pagine mirror non vengono presi in considerazione.
* **[!UICONTROL Transactions]** : numero totale di transazioni dopo la ricezione di un messaggio. Affinché una transazione possa essere presa in considerazione, è necessario inserire un tag di tracciamento web di tipo transazione nella pagina web corrispondente. La configurazione del tracciamento web è presentata in [questa sezione](../../configuration/using/about-web-tracking.md).

## Messaggi non recapitabili e mancati recapiti {#non-deliverables-and-bounces}

Questo rapporto mostra il raggruppamento dei messaggi non recapitati e dei messaggi non recapitati per dominio Internet.

Il **[!UICONTROL Number of messages processed]** rappresenta il numero totale di messaggi elaborati dal server di consegna. Questo valore è inferiore al numero di messaggi da consegnare quando alcune consegne sono state interrotte o sospese (prima di essere elaborate dal server).

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>Gli errori inclusi in questo rapporto attivano il processo di quarantena. Per ulteriori informazioni sulla gestione della quarantena, consulta [Gestione della quarantena](../../delivery/using/understanding-quarantine-management.md).

La prima sezione di questo rapporto mostra la suddivisione dei messaggi non recapitati sotto forma di tabella di valori e di grafico.

Per ogni tipo di errore, sono disponibili:

* il numero di messaggi di errore di questo tipo,
* la percentuale di messaggi con errori di questo tipo rispetto al numero totale di messaggi con errori,
* percentuale di messaggi di errore di questo tipo rispetto al numero totale di messaggi elaborati.

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL User unknown]** : tipo di errore generato durante la consegna per indicare che l’indirizzo e-mail non è valido.
* **[!UICONTROL Invalid domain]** : tipo di errore generato durante l’invio di una consegna per indicare che il dominio dell’indirizzo e-mail è errato o non esiste.
* **[!UICONTROL Inbox full]** : tipo di errore generato dopo cinque tentativi di consegna per indicare che la casella in entrata dei destinatari contiene troppi messaggi.
* **[!UICONTROL Account disabled]** : tipo di errore generato durante l’invio di una consegna per indicare che l’indirizzo non esiste più.
* **[!UICONTROL Rejected]** : tipo di errore generato quando un indirizzo viene rifiutato da IAP (Internet Access Provider), ad esempio in seguito all’applicazione di una regola di sicurezza (software anti-spam).
* **[!UICONTROL Unreachable]** : tipo di errore che si verifica nella stringa di distribuzione del messaggio: incidente sull’inoltro SMTP, dominio temporaneamente non raggiungibile, ecc.
* **[!UICONTROL Not connected]** : tipo di errore per indicare che il telefono cellulare del destinatario è spento o disconnesso dalla rete al momento dell’invio.

  >[!NOTE]
  >
  >Questo indicatore riguarda solo le consegne sui canali mobili. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/sms-channel.md).

  È possibile aprire ogni riga della tabella dei valori facendo clic sul pulsante `[+]` simbolo. Per ogni tipo di errore, puoi visualizzare la suddivisione dei messaggi di errore per dominio.

  ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

La seconda sezione di questo rapporto mostra la suddivisione degli errori per dominio Internet sotto forma di tabella di valori e grafico.

Per ogni nome di dominio, abbiamo:

* il numero di messaggi con errori per questo dominio,
* la percentuale di messaggi con errori per questo dominio rispetto al numero totale di messaggi elaborati per questo dominio,
* la percentuale di messaggi di errore per questo dominio rispetto al numero totale di messaggi di errore.

È possibile aprire ogni riga della tabella dei valori facendo clic sul pulsante [+] simbolo. Per ogni tipo di dominio, puoi visualizzare la suddivisione dei messaggi di errore per tipo.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>I nomi di dominio visualizzati in questo report sono definiti a livello di cubo. Per modificare questi valori, modificare il **[!UICONTROL Delivery logs (broadlogrcp)]** cubo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/ac-cubes.md). Il **[!UICONTROL Others]** categoria include i nomi di dominio che non appartengono a una classe specifica.

## Browser {#browsers}

Questo rapporto mostra il raggruppamento dei browser Internet utilizzati dai destinatari della consegna per il periodo in questione.

>[!NOTE]
>
>I valori mostrati in questo rapporto sono stime: verranno presi in considerazione solo i destinatari che hanno fatto clic in una consegna.

**Statistiche globali**

Le statistiche globali sull’utilizzo del browser sono presentate sotto forma di tabella di valori e di grafico.

![](assets/dlv_explorers_report.png)

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL Visitors]** : numero totale di destinatari target (per browser Internet) che hanno fatto clic almeno una volta su una consegna.
* **[!UICONTROL Pages viewed]** : numero totale di clic sui collegamenti in una consegna (per browser Internet) per tutte le consegne.
* **[!UICONTROL Usage rate]** : questo tasso rappresenta la suddivisione dei visitatori (per browser Internet) in relazione al numero totale di visitatori.

**Statistiche per browser**

Nella tabella dei valori delle statistiche globali, puoi fare clic sul nome di ogni browser per visualizzarne le statistiche di utilizzo.

![](assets/s_ncs_user_explorers_report2.png)

Le statistiche sono presentate sotto forma di curva, grafico e tabella di valori.

Il **[!UICONTROL History]** rappresenta la frequenza giornaliera di questo browser. Il tasso è il rapporto tra il numero di visitatori al giorno (in questo browser) e il numero di visitatori misurato nel giorno con il tasso di partecipazione più elevato.

Il **[!UICONTROL Breakdown per version]** il grafico rappresenta il raggruppamento dei visitatori per versione rispetto al numero totale di visitatori (in questo browser).

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Global rate]** : questo tasso rappresenta il raggruppamento dei visitatori per versione rispetto al numero totale di visitatori (su tutti i browser).
* **[!UICONTROL Relative rate]** : questo tasso rappresenta il raggruppamento dei visitatori per versione rispetto al numero totale di visitatori (in questo browser).

### Condivisione sui social network {#sharing-to-social-networks}

Il marketing virale consente ai destinatari delle consegne di condividere informazioni con la loro rete di contatti: possono aggiungere un collegamento al loro profilo (Facebook, X, precedentemente noto come Twitter, ecc.) o inviare un messaggio a un amico. Ogni condivisione e ogni accesso alle informazioni condivise vengono tracciati all’interno della consegna. Per ulteriori informazioni sul marketing virale, fare riferimento a [questa sezione](../../delivery/using/viral-and-social-marketing.md).

Questo rapporto mostra il raggruppamento dei messaggi condivisi e aperti per social network (Facebook, X, ecc.) e/o per e-mail.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

Nelle statistiche della consegna e-mail, vengono visualizzati due valori:

* **[!UICONTROL Number of messages to be delivered]** : numero totale di messaggi elaborati durante l’analisi della consegna.
* **[!UICONTROL Number of successful deliveries]** : numero di messaggi elaborati correttamente.

**[!UICONTROL Sharing activities and mail open statistics]**

La tabella centrale mostra le statistiche sulle condivisioni e-mail e sulle aperture.

In **[!UICONTROL Shares]** , sono disponibili i seguenti indicatori:

* **[!UICONTROL No. of sharing activities]** : numero totale di messaggi condivisi su ciascun social network. Questo valore è uguale al numero totale di clic sull’icona della corrispondenza **[!UICONTROL Links for sharing to social networks]** blocco di personalizzazione.
* **[!UICONTROL Breakdown]** : questo tasso rappresenta la ripartizione delle azioni per social network, in relazione al numero totale di azioni.
* **[!UICONTROL Sharing rate]** : questo tasso rappresenta il raggruppamento delle condivisioni per social network, in relazione al numero di messaggi da consegnare.

In **[!UICONTROL Opens]** , sono disponibili i seguenti indicatori:

* **[!UICONTROL No. of opens]** : numero totale di messaggi aperti dagli utenti a cui è stato inoltrato il messaggio (tramite il **[!UICONTROL Links for sharing to social networks]** blocco di personalizzazione). Questo valore è uguale al numero di volte in cui la pagina speculare è stata visualizzata. Le aperture da parte dei destinatari della consegna non vengono prese in considerazione.
* **[!UICONTROL Breakdown]** : questo tasso rappresenta il raggruppamento delle aperture per social network, in relazione al numero totale di aperture.
* **[!UICONTROL Rate of opens]** : questo tasso rappresenta il raggruppamento delle aperture per social network, in relazione al numero totale di azioni.

**[!UICONTROL Breakdown of sharing activities and opens]**

Questa sezione include due grafici che rappresentano il raggruppamento delle attività di condivisione e si aprono per social network.

## Statistiche sulla condivisione delle attività {#statistics-on-sharing-activities}

Questo rapporto mostra l’evoluzione delle condivisioni nei social network (Facebook, X - precedentemente noto come Twitter, e-mail, ecc.) nel tempo.

Per ulteriori informazioni sul marketing virale, fare riferimento a [questa sezione](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

Le statistiche sono presentate sotto forma di tabella di valori e di grafico.

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL New contacts]** : numero di nuovi abbonamenti in seguito alla ricezione di un messaggio condiviso tramite e-mail. Questo valore corrisponde al numero di persone che hanno ricevuto un messaggio condiviso tramite e-mail e su cui è stato fatto clic **[!UICONTROL Subscription link]** e compilato nel modulo di abbonamento.
* **[!UICONTROL Opens]** : numero totale di messaggi aperti dalle persone a cui è stato trasferito il messaggio (tramite il **[!UICONTROL Link for sharing to social networks]** blocco di personalizzazione). Questo valore è uguale al numero di volte in cui la pagina speculare è stata visualizzata. Le aperture da parte dei destinatari della consegna non vengono prese in considerazione.
* **[!UICONTROL Sharing activities]** : numero totale di messaggi condivisi tramite i social network. Questo valore corrisponde al numero totale di clic sull’icona del **[!UICONTROL Links for sharing to social networks]** blocco di personalizzazione.

## Sistemi operativi {#operating-systems}

Questo rapporto mostra la suddivisione dei sistemi operativi utilizzati dai destinatari delle consegne per il periodo in questione.

>[!NOTE]
>
>I valori mostrati in questo rapporto sono stime: verranno presi in considerazione solo i destinatari che hanno fatto clic in una consegna.

**Statistiche globali**

Le statistiche di utilizzo globali dei sistemi operativi vengono presentate sotto forma di tabella di valori e di grafico.

![](assets/s_ncs_user_os_report.png)

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL Visitors]** : media giornaliera del numero totale di destinatari target (per sistema operativo) che hanno fatto clic almeno una volta in una consegna.
* **[!UICONTROL Pages viewed]** : media giornaliera del numero totale di clic sui collegamenti di consegna (per sistema operativo) per tutte le consegne.
* **[!UICONTROL Rate of use]** : questo tasso rappresenta la suddivisione dei visitatori (per sistema operativo) in relazione al numero totale di visitatori.

**Statistiche per sistema operativo**

Nella tabella dei valori delle statistiche globali fare clic sul nome di ogni sistema operativo per visualizzare le statistiche per sistema operativo.

![](assets/s_ncs_user_os_report2.png)

Le statistiche sono presentate sotto forma di curva, grafico e tabella di valori.

Il **[!UICONTROL History]** La curva rappresenta il tasso di utilizzo giornaliero del sistema operativo. Questo tasso è il rapporto tra il numero di visitatori al giorno (in questo sistema operativo) e il numero di visitatori misurato nel giorno con la partecipazione più elevata.

Il **[!UICONTROL Breakdown by version]** il grafico rappresenta il raggruppamento dei visitatori per versione in relazione al numero totale di visitatori su questo sistema operativo.

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Global rate]** : questo tasso rappresenta la suddivisione dei visitatori (per versione) in relazione al numero totale di visitatori in tutti i sistemi operativi.
* **[!UICONTROL Relative rate]** : questo tasso rappresenta la suddivisione dei visitatori (per versione) in relazione al numero totale di visitatori per questo sistema operativo.

## Tracciamento abbonamento {#subscription-tracking}

Questo report consente di monitorare gli abbonamenti ai servizi di informazione. Mostra gli abbonamenti e il loro annullamento.

![](assets/s_ncs_user_services_report.png)

Per visualizzarlo per un abbonamento, fai clic sul pulsante **[!UICONTROL Profiles and targets > Services and subscriptions]** della home page o dell&#39;explorer. Selezionare l&#39;abbonamento desiderato, quindi fare clic su **[!UICONTROL Reports]** scheda. Il **[!UICONTROL Subscriptions tracking]** è disponibile per impostazione predefinita. Ti consente di visualizzare le tendenze di abbonamento e annullamento dell’abbonamento e il tasso di fedeltà in un periodo. Puoi configurare la rappresentazione di questi dati tramite l’elenco a discesa. Clic **[!UICONTROL Refresh]** per convalidare la configurazione selezionata.

Per ulteriori informazioni, fare riferimento a [questa pagina](../../delivery/using/managing-subscriptions.md).

Il **[!UICONTROL Number subscribed to date]** rappresenta il numero totale di persone attualmente abbonate.

**[!UICONTROL Overall evolution of subscriptions]**

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Subscribers]** : numero totale di abbonati per il periodo in questione.
* **[!UICONTROL Subscriptions]** : numero di abbonamenti per il periodo in questione.
* **[!UICONTROL Unsubscriptions]** : numero di annullamenti di abbonamenti per il periodo in questione.
* **[!UICONTROL Evolution]** : numero di annullamenti di abbonamenti meno il numero di abbonamenti. La tariffa viene calcolata in base al numero totale di abbonati.
* **[!UICONTROL Loyalty]** : tasso di fedeltà degli abbonati per il periodo in questione.

**[!UICONTROL Subscription evolution curves]**

Questo grafico mostra l’evoluzione degli abbonamenti e dei loro annullamenti per il periodo in questione.

## Statistiche consegna {#delivery-statistics}

Questo rapporto mostra la suddivisione per dominio Internet di tutti i messaggi elaborati e inviati, di mancati recapiti permanenti e non permanenti, aperture, clic e annullamenti di abbonamenti.

![](assets/s_ncs_user_broadcast_report.png)

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL Emails processed]** : numero totale di messaggi elaborati dal server di consegna.
* **[!UICONTROL Delivered]** : percentuale del numero di messaggi elaborati correttamente rispetto al numero totale di messaggi elaborati.
* **[!UICONTROL Hard bounces]** : percentuale del numero di mancati recapiti &quot;permanenti&quot; rispetto al numero totale di messaggi elaborati.
* **[!UICONTROL Soft bounces]** : percentuale del numero di mancati recapiti &quot;non permanenti&quot; rispetto al numero totale di messaggi elaborati.

  >[!NOTE]
  >
  >Per ulteriori informazioni sui mancati recapiti permanenti e non permanenti, consulta [Gestione della quarantena](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : percentuale del numero di destinatari che hanno aperto un messaggio almeno una volta rispetto al numero di messaggi elaborati correttamente.
* **[!UICONTROL Clicks]** : percentuale del numero di persone che hanno fatto clic su una consegna almeno una volta rispetto al numero di messaggi elaborati correttamente.
* **[!UICONTROL Unsubscription]** : percentuale del numero di clic su un collegamento di annullamento dell’abbonamento rispetto al numero di messaggi elaborati correttamente.

## Raggruppamenti delle aperture {#breakdown-of-opens}

Raggruppamenti delle aperture: questo rapporto mostra le aperture raggruppate per sistema operativo, dispositivo e browser per il periodo in questione. Per ogni categoria vengono utilizzati due grafici. Il primo visualizza le statistiche relative all’apertura su un computer e dispositivi mobili. Il secondo visualizza le statistiche relative solo all’apertura su dispositivi mobili.

Il numero di aperture corrisponde al numero totale di messaggi aperti. Le e-mail in formato testo non vengono conteggiate. Per ulteriori informazioni sulle aperture di tracciamento, consulta [Tracciamento delle aperture](../../reporting/using/indicator-calculation.md#tracking-opens-) sezione.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>I nomi del browser e del sistema operativo costituiscono parte delle informazioni inviate dall’agente utente del browser a cui è stato aperto il messaggio. Adobe Campaign deduce il tipo di dispositivo utilizzando le relative informazioni sul dispositivo.
