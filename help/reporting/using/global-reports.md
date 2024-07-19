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



Tali relazioni riguardano l&#39;attività dei dati nell&#39;intero database. Per visualizzare il dashboard dei report, passare alla scheda **[!UICONTROL Reports]**.

![](assets/s_ncs_user_report_delivery_link.png)

Per visualizzare i rapporti, fai clic sui relativi nomi. Per impostazione predefinita sono disponibili i seguenti rapporti:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>Questa sezione mostra solo i rapporti collegati alle consegne.

* **[!UICONTROL Delivery throughput]** : fai riferimento a [Velocità effettiva di consegna](#delivery-throughput).
* **[!UICONTROL Browsers]** : fai riferimento a [Browser](#browsers).
* **[!UICONTROL Sharing to social networks]**: fare riferimento a [Condivisione su social network](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** : fai riferimento a [Statistiche sulle attività di condivisione](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** : fare riferimento a [Sistemi operativi](#operating-systems).
* **[!UICONTROL URLs and click streams]** : fai riferimento a [URL e ai flussi di clic](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : fai riferimento a [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** : fai riferimento a [Messaggi non recapitati e non recapitati](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : fai riferimento a [Attività utente](#user-activities).
* **[!UICONTROL Subscription tracking]** : fai riferimento a [Tracciamento abbonamento](#subscription-tracking).
* **[!UICONTROL Delivery summary]** : fai riferimento a [Riepilogo consegna](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : fai riferimento a [Statistiche di consegna](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** : fai riferimento a [Raggruppamento di aperture](#breakdown-of-opens).

## Velocità di consegna {#delivery-throughput}

Questo rapporto contiene informazioni sulla velocità effettiva di consegna dell’intera piattaforma per un determinato periodo. I criteri utilizzati per misurare la velocità con cui vengono consegnati i messaggi comprendono il numero di messaggi inviati all’ora e le dimensioni dei messaggi (in bit al secondo). Nell’esempio seguente, il primo grafico mostra le consegne riuscite in blu e il numero di consegne con errori in arancione.

![](assets/s_ncs_user_report_toolbar.png)

Puoi configurare i valori visualizzati modificando la scala cronologica: visualizzazione a 1 ora, visualizzazione a 3 ore, visualizzazione a 24 ore, ecc. Fai clic su **[!UICONTROL Refresh]** per confermare la selezione.

>[!NOTE]
>
>Se l&#39;istanza è ospitata su AWS, puoi anche monitorare il numero di consegne inviate all&#39;ora utilizzando il Campaign Classic [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=it).
>
>Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
>
>Tieni presente che l&#39;istanza deve essere aggiornata con la build [Gold Standard](../../rn/using/gold-standard.md) più recente o con la build [GA più recente (21.1.3)](../../rn/using/latest-release.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Attività degli utenti {#user-activities}

Questo rapporto mostra il raggruppamento di aperture, clic e transazioni per mezz’ora, ora o giorno, sotto forma di un grafico.

![](assets/s_ncs_user_user_report.png)

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Opens]**: numero totale di messaggi aperti. Le e-mail in formato testo non vengono prese in considerazione. Per ulteriori informazioni sulle aperture di tracciamento, fare riferimento a [Aperture di tracciamento](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : numero totale di clic sui collegamenti nelle consegne. I clic sui collegamenti di annullamento dell’abbonamento e sulle pagine mirror non vengono presi in considerazione.
* **[!UICONTROL Transactions]**: numero totale di transazioni dopo la ricezione di un messaggio. Affinché una transazione possa essere presa in considerazione, è necessario inserire un tag di tracciamento web di tipo transazione nella pagina web corrispondente. La configurazione del tracciamento web è presentata in [questa sezione](../../configuration/using/about-web-tracking.md).

## Messaggi non recapitabili e mancati recapiti {#non-deliverables-and-bounces}

Questo rapporto mostra il raggruppamento dei messaggi non recapitati e dei messaggi non recapitati per dominio Internet.

**[!UICONTROL Number of messages processed]** rappresenta il numero totale di messaggi elaborati dal server di consegna. Questo valore è inferiore al numero di messaggi da consegnare quando alcune consegne sono state interrotte o sospese (prima di essere elaborate dal server).

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

* **[!UICONTROL User unknown]**: tipo di errore generato durante la consegna per indicare che l&#39;indirizzo e-mail non è valido.
* **[!UICONTROL Invalid domain]**: tipo di errore generato durante l&#39;invio di una consegna per indicare che il dominio dell&#39;indirizzo e-mail è errato o inesistente.
* **[!UICONTROL Inbox full]** : tipo di errore generato dopo cinque tentativi di consegna per indicare che la casella in entrata dei destinatari contiene troppi messaggi.
* **[!UICONTROL Account disabled]**: tipo di errore generato durante l&#39;invio di una consegna per indicare che l&#39;indirizzo non esiste più.
* **[!UICONTROL Rejected]**: tipo di errore generato quando un indirizzo viene rifiutato da IAP (Internet Access Provider), ad esempio in seguito all&#39;applicazione di una regola di sicurezza (software anti-spam).
* **[!UICONTROL Unreachable]**: tipo di errore che si verifica nella stringa di distribuzione del messaggio: problema nell&#39;inoltro SMTP, dominio temporaneamente non raggiungibile, ecc.
* **[!UICONTROL Not connected]**: tipo di errore per indicare che il telefono cellulare dei destinatari è spento o disconnesso dalla rete al momento dell&#39;invio.

  >[!NOTE]
  >
  >Questo indicatore riguarda solo le consegne sui canali mobili. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/sms-channel.md).

  È possibile aprire ogni riga della tabella dei valori facendo clic sul simbolo `[+]`. Per ogni tipo di errore, puoi visualizzare la suddivisione dei messaggi di errore per dominio.

  ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

La seconda sezione di questo rapporto mostra la suddivisione degli errori per dominio Internet sotto forma di tabella di valori e grafico.

Per ogni nome di dominio, abbiamo:

* il numero di messaggi con errori per questo dominio,
* la percentuale di messaggi con errori per questo dominio rispetto al numero totale di messaggi elaborati per questo dominio,
* la percentuale di messaggi di errore per questo dominio rispetto al numero totale di messaggi di errore.

Per aprire ogni riga della tabella dei valori, fare clic sul simbolo [+]. Per ogni tipo di dominio, puoi visualizzare la suddivisione dei messaggi di errore per tipo.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>I nomi di dominio visualizzati in questo report sono definiti a livello di cubo. Per modificare questi valori, modificare il cubo **[!UICONTROL Delivery logs (broadlogrcp)]**. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/ac-cubes.md). La categoria **[!UICONTROL Others]** include nomi di dominio che non appartengono a una classe specifica.

## Browser {#browsers}

Questo rapporto mostra il raggruppamento dei browser Internet utilizzati dai destinatari della consegna per il periodo in questione.

>[!NOTE]
>
>I valori mostrati in questo rapporto sono stime: verranno presi in considerazione solo i destinatari che hanno fatto clic in una consegna.

**Statistiche globali**

Le statistiche globali sull’utilizzo del browser sono presentate sotto forma di tabella di valori e di grafico.

![](assets/dlv_explorers_report.png)

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL Visitors]**: numero totale di destinatari di destinazione (per browser Internet) che hanno fatto clic almeno una volta su una consegna.
* **[!UICONTROL Pages viewed]** : numero totale di clic sui collegamenti in una consegna (per browser Internet) per tutte le consegne.
* **[!UICONTROL Usage rate]** : questo tasso rappresenta il raggruppamento dei visitatori (per browser Internet) in relazione al numero totale di visitatori.

**Statistiche per browser**

Nella tabella dei valori delle statistiche globali, puoi fare clic sul nome di ogni browser per visualizzarne le statistiche di utilizzo.

![](assets/s_ncs_user_explorers_report2.png)

Le statistiche sono presentate sotto forma di curva, grafico e tabella di valori.

La curva **[!UICONTROL History]** rappresenta la frequenza giornaliera di questo browser. Il tasso è il rapporto tra il numero di visitatori al giorno (in questo browser) e il numero di visitatori misurato nel giorno con il tasso di partecipazione più elevato.

Il grafico **[!UICONTROL Breakdown per version]** rappresenta il raggruppamento dei visitatori per versione rispetto al numero totale di visitatori (in questo browser).

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Global rate]** : questo tasso rappresenta il raggruppamento dei visitatori per versione rispetto al numero totale di visitatori (su tutti i browser).
* **[!UICONTROL Relative rate]** : questo tasso rappresenta il raggruppamento dei visitatori per versione rispetto al numero totale di visitatori (in questo browser).

### Condivisione sui social network {#sharing-to-social-networks}

Il marketing virale consente ai destinatari delle consegne di condividere informazioni con la loro rete di contatti: possono aggiungere un collegamento al loro profilo (Facebook, X, precedentemente noto come Twitter, ecc.) o inviare un messaggio a un amico. Ogni condivisione e ogni accesso alle informazioni condivise vengono tracciati all’interno della consegna. Per ulteriori informazioni sul marketing virale, consulta [questa sezione](../../delivery/using/viral-and-social-marketing.md).

Questo rapporto mostra il raggruppamento dei messaggi condivisi e aperti per social network (Facebook, X, ecc.) e/o per e-mail.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

Nelle statistiche della consegna e-mail, vengono visualizzati due valori:

* **[!UICONTROL Number of messages to be delivered]**: numero totale di messaggi elaborati durante l&#39;analisi della consegna.
* **[!UICONTROL Number of successful deliveries]**: numero di messaggi elaborati correttamente.

**[!UICONTROL Sharing activities and mail open statistics]**

La tabella centrale mostra le statistiche sulle condivisioni e-mail e sulle aperture.

Nella colonna **[!UICONTROL Shares]** sono presenti i seguenti indicatori:

* **[!UICONTROL No. of sharing activities]** : numero totale di messaggi condivisi su ciascun social network. Questo valore è uguale al numero totale di clic sull&#39;icona del blocco di personalizzazione **[!UICONTROL Links for sharing to social networks]** corrispondente.
* **[!UICONTROL Breakdown]** : questo tasso rappresenta la suddivisione delle condivisioni per social network, in relazione al numero totale di condivisioni.
* **[!UICONTROL Sharing rate]** : questo tasso rappresenta il raggruppamento delle condivisioni per social network, in relazione al numero di messaggi da consegnare.

Nella colonna **[!UICONTROL Opens]** sono presenti i seguenti indicatori:

* **[!UICONTROL No. of opens]**: numero totale di messaggi aperti da utenti a cui è stato inoltrato il messaggio (tramite il blocco di personalizzazione **[!UICONTROL Links for sharing to social networks]**). Questo valore è uguale al numero di volte in cui la pagina speculare è stata visualizzata. Le aperture da parte dei destinatari della consegna non vengono prese in considerazione.
* **[!UICONTROL Breakdown]** : questa tariffa rappresenta il raggruppamento delle aperture per social network, in relazione al numero totale di aperture.
* **[!UICONTROL Rate of opens]** : questa tariffa rappresenta il raggruppamento delle aperture per social network, in relazione al numero totale di condivisioni.

**[!UICONTROL Breakdown of sharing activities and opens]**

Questa sezione include due grafici che rappresentano il raggruppamento delle attività di condivisione e si aprono per social network.

## Statistiche sulla condivisione delle attività {#statistics-on-sharing-activities}

Questo rapporto mostra l’evoluzione delle condivisioni nei social network (Facebook, X - precedentemente noto come Twitter, e-mail, ecc.) nel tempo.

Per ulteriori informazioni sul marketing virale, consulta [questa sezione](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

Le statistiche sono presentate sotto forma di tabella di valori e di grafico.

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL New contacts]** : numero di nuovi abbonamenti in seguito alla ricezione di un messaggio condiviso tramite e-mail. Questo valore corrisponde al numero di persone che hanno ricevuto un messaggio condiviso tramite e-mail, hanno fatto clic su **[!UICONTROL Subscription link]** e compilato il modulo di abbonamento.
* **[!UICONTROL Opens]**: numero totale di messaggi aperti dalle persone a cui è stato trasferito il messaggio (tramite il blocco di personalizzazione **[!UICONTROL Link for sharing to social networks]**). Questo valore è uguale al numero di volte in cui la pagina speculare è stata visualizzata. Le aperture da parte dei destinatari della consegna non vengono prese in considerazione.
* **[!UICONTROL Sharing activities]**: numero totale di messaggi condivisi tramite i social network. Questo valore corrisponde al numero totale di clic sull&#39;icona del blocco di personalizzazione **[!UICONTROL Links for sharing to social networks]**.

## Sistemi operativi {#operating-systems}

Questo rapporto mostra la suddivisione dei sistemi operativi utilizzati dai destinatari delle consegne per il periodo in questione.

>[!NOTE]
>
>I valori mostrati in questo rapporto sono stime: verranno presi in considerazione solo i destinatari che hanno fatto clic in una consegna.

**Statistiche globali**

Le statistiche di utilizzo globali dei sistemi operativi vengono presentate sotto forma di tabella di valori e di grafico.

![](assets/s_ncs_user_os_report.png)

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL Visitors]**: media giornaliera del numero totale di destinatari di destinazione (per sistema operativo) che hanno fatto clic almeno una volta in una consegna.
* **[!UICONTROL Pages viewed]**: media giornaliera del numero totale di clic sui collegamenti di consegna (per sistema operativo) per tutte le consegne.
* **[!UICONTROL Rate of use]** : questo tasso rappresenta il raggruppamento dei visitatori (per sistema operativo) in relazione al numero totale di visitatori.

**Statistiche per sistema operativo**

Nella tabella dei valori delle statistiche globali fare clic sul nome di ogni sistema operativo per visualizzare le statistiche per sistema operativo.

![](assets/s_ncs_user_os_report2.png)

Le statistiche sono presentate sotto forma di curva, grafico e tabella di valori.

La curva **[!UICONTROL History]** rappresenta il tasso di utilizzo giornaliero del sistema operativo. Questo tasso è il rapporto tra il numero di visitatori al giorno (in questo sistema operativo) e il numero di visitatori misurato nel giorno con la partecipazione più elevata.

Il grafico **[!UICONTROL Breakdown by version]** rappresenta il raggruppamento dei visitatori per versione in relazione al numero totale di visitatori su questo sistema operativo.

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Global rate]** : questo tasso rappresenta il raggruppamento dei visitatori (per versione) in relazione al numero totale di visitatori in tutti i sistemi operativi.
* **[!UICONTROL Relative rate]** : questo tasso rappresenta il raggruppamento dei visitatori (per versione) in relazione al numero totale di visitatori per questo sistema operativo.

## Tracciamento abbonamento {#subscription-tracking}

Questo report consente di monitorare gli abbonamenti ai servizi di informazione. Mostra gli abbonamenti e il loro annullamento.

![](assets/s_ncs_user_services_report.png)

È possibile visualizzarlo per un abbonamento facendo clic sul nodo **[!UICONTROL Profiles and targets > Services and subscriptions]** della home page o dell&#39;Explorer. Selezionare la sottoscrizione desiderata, quindi fare clic sulla scheda **[!UICONTROL Reports]**. Il report **[!UICONTROL Subscriptions tracking]** è disponibile per impostazione predefinita. Ti consente di visualizzare le tendenze di abbonamento e annullamento dell’abbonamento e il tasso di fedeltà in un periodo. Puoi configurare la rappresentazione di questi dati tramite l’elenco a discesa. Fare clic su **[!UICONTROL Refresh]** per convalidare la configurazione selezionata.

Per ulteriori informazioni, consultare [questa pagina](../../delivery/using/managing-subscriptions.md).

**[!UICONTROL Number subscribed to date]** rappresenta il numero totale di persone attualmente abbonate.

**[!UICONTROL Overall evolution of subscriptions]**

La tabella dei valori utilizza i seguenti indicatori:

* **[!UICONTROL Subscribers]**: numero totale di abbonati per il periodo in questione.
* **[!UICONTROL Subscriptions]** : numero di abbonamenti per il periodo interessato.
* **[!UICONTROL Unsubscriptions]** : numero di annullamenti di abbonamenti per il periodo in questione.
* **[!UICONTROL Evolution]** : numero di annullamenti di abbonamenti meno il numero di abbonamenti. La tariffa viene calcolata in base al numero totale di abbonati.
* **[!UICONTROL Loyalty]**: tasso di fedeltà degli abbonati per il periodo in questione.

**[!UICONTROL Subscription evolution curves]**

Questo grafico mostra l’evoluzione degli abbonamenti e dei loro annullamenti per il periodo in questione.

## Statistiche consegna {#delivery-statistics}

Questo rapporto mostra la suddivisione per dominio Internet di tutti i messaggi elaborati e inviati, di mancati recapiti permanenti e non permanenti, aperture, clic e annullamenti di abbonamenti.

![](assets/s_ncs_user_broadcast_report.png)

Sono utilizzati i seguenti indicatori:

* **[!UICONTROL Emails processed]**: numero totale di messaggi elaborati dal server di consegna.
* **[!UICONTROL Delivered]** : percentuale del numero di messaggi elaborati correttamente rispetto al numero totale di messaggi elaborati.
* **[!UICONTROL Hard bounces]** : percentuale del numero di mancati recapiti &quot;permanenti&quot; rispetto al numero totale di messaggi elaborati.
* **[!UICONTROL Soft bounces]** : percentuale del numero di mancati recapiti &quot;non permanenti&quot; rispetto al numero totale di messaggi elaborati.

  >[!NOTE]
  >
  >Per ulteriori informazioni sui mancati recapiti permanenti e non permanenti, consulta [Gestione quarantena](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : percentuale del numero di destinatari di destinazione che hanno aperto un messaggio almeno una volta rispetto al numero di messaggi elaborati correttamente.
* **[!UICONTROL Clicks]** : percentuale di persone che hanno fatto clic su una consegna almeno una volta rispetto al numero di messaggi elaborati correttamente.
* **[!UICONTROL Unsubscription]** : percentuale del numero di clic su un collegamento di annullamento dell&#39;abbonamento rispetto al numero di messaggi elaborati correttamente.

## Raggruppamenti delle aperture {#breakdown-of-opens}

Raggruppamenti delle aperture: questo rapporto mostra le aperture raggruppate per sistema operativo, dispositivo e browser per il periodo in questione. Per ogni categoria vengono utilizzati due grafici. Il primo visualizza le statistiche relative all’apertura su un computer e dispositivi mobili. Il secondo visualizza le statistiche relative solo all’apertura su dispositivi mobili.

Il numero di aperture corrisponde al numero totale di messaggi aperti. Le e-mail in formato testo non vengono conteggiate. Per ulteriori informazioni sulle aperture di tracciamento, consulta la sezione [Aperture di tracciamento](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>I nomi del browser e del sistema operativo costituiscono parte delle informazioni inviate dall’agente utente del browser a cui è stato aperto il messaggio. Adobe Campaign deduce il tipo di dispositivo utilizzando le relative informazioni sul dispositivo.
