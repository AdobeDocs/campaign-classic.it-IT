---
title: Monitoraggio della recapito in Adobe Campaign Classic
description: Scopri gli strumenti e le linee guida sul monitoraggio della recapito in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a30c4a2d31c3f674ac4a7bb4827a6951b36014ab
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---


# Monitoraggio del recapito messaggi{#monitoring-deliverability}

Di seguito troverai informazioni dettagliate sui diversi strumenti di monitoraggio forniti da Adobe Campaign, nonché alcune linee guida aggiuntive sul monitoraggio della recapito.

## Strumenti di monitoraggio {#monitoring-tools}

Utilizza le funzionalità offerte da Adobe Campaign per monitorare la recapito della tua piattaforma.

Il pacchetto Deliverability consente di accedere a:

* Rapporto di monitoraggio tecnico per le prestazioni quotidiane di recapito (monitoraggio tecnico). Questo rapporto, disponibile su richiesta, consente di ricevere un rapporto giornaliero via e-mail all&#39;indirizzo specificato. Per ulteriori informazioni, contatta il team di assistenza clienti di Adobe.
* Il rapporto [di rendering della](../../delivery/using/inbox-rendering.md) casella in entrata consente di visualizzare in anteprima i messaggi sui principali client e-mail al fine di acquisire il contenuto e la reputazione.
* Panoramica della qualità del messaggio (inbox, spam).

Potete anche usare i seguenti strumenti:

* Il **[!UICONTROL Delivery throughput]** rapporto fornisce una panoramica dell&#39;intero throughput della piattaforma per un determinato periodo di tempo. Per ulteriori informazioni, consulta [questa sezione](../../reporting/using/global-reports.md#delivery-throughput).
* Il **[!UICONTROL Technical deliverability monitoring]** rapporto include una serie di indicatori di qualità della distribuzione per la piattaforma. Per ulteriori informazioni, consulta [questa sezione](#technical-deliverability-monitoring).
* Il dashboard [](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) consegna consente di accedere al riepilogo [](../../delivery/using/monitoring-a-delivery.md#delivery-summary)Consegna, ai registri e alla cronologia [delle](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) consegne e ai registri [di](../../delivery/using/monitoring-a-delivery.md#tracking-logs)tracciamento. Mostra i dettagli dell’invio, quale destinazione è stata esclusa e perché, nonché le informazioni di tracciamento come aperture e clic. <!--For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).-->
* Puoi anche controllare il numero di messaggi da inviare, elaborare e inviare con esito positivo. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent)
   <!--[SpamAssassin](../../installation/using/configuring-spamassassin.md)?-->

## Linee guida per il monitoraggio {#monitoring-guidelines}

Seguono alcune linee guida aggiuntive sul monitoraggio della recapito:

* Controllate regolarmente il throughput [di](../../reporting/using/global-reports.md#delivery-throughput) consegna per l&#39;intera piattaforma per verificare se è coerente con la configurazione originale.
* Verificate che [i tentativi](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) siano impostati correttamente (30 minuti per il periodo di tentativi e più di 20 tentativi) nei modelli di consegna.
* Verifica regolarmente che la cassetta postale [di rimbalzo](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) sia accessibile e che l&#39;account non stia per scadere.
* Controllate ogni throughput di distribuzione per assicurarvi che sia coerente con la validità del contenuto di distribuzione (ad es. Le vendite flash devono essere consegnate in minuti, non in giorni).
* Quando si utilizzano [le onde](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verificare che ogni onda disponga di tempo sufficiente per terminare prima che venga attivata la successiva.
* Verificate che il numero di errori e di nuove [quarantena](../../delivery/using/understanding-quarantine-management.md) siano coerenti con altre consegne.
* Consultate attentamente i registri [di](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) consegna per verificare il tipo di errori evidenziati (lista grigia o nera, problemi DNS, regole anti-spam, ecc.).

## Spam segnale {#signal-spam}

Signal Spam è un servizio francese che offre un report anonimo sul loop di feedback per gli ISP francesi (Orange, SFR).

* Questo servizio consente di seguire la reputazione degli ISP francesi e di monitorare l&#39;evoluzione dell&#39;attività dei clienti.

* Il segnale Spam fornisce inoltre reclami diretti che gli utenti finali accedono attraverso un&#39;interfaccia dedicata. Tali reclami vengono quindi messi in quarantena dal database degli indirizzi e-mail.

## 250 ok {#deliverability-250ok}

[250ok](https://250ok.com/) è una soluzione di monitoraggio complementare agli strumenti interni di Adobe per la distribuzione, che fornisce informazioni su IP, elenchi di dominio e indicatori di reputazione.

Le informazioni fornite sono in tempo reale, il che consente un&#39;assistenza proattiva.

## Rapporto di monitoraggio sulla realizzazione tecnica {#technical-deliverability-monitoring}

Il rapporto di monitoraggio della recapito tecnico viene aggiornato ogni giorno e disponibile accedendo a **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** e facendo clic sul **[!UICONTROL Technical monitoring]** collegamento dalla scheda Adobe Campaign **[!UICONTROL Home]** . Include una serie di indicatori di qualità della distribuzione per la piattaforma.

Questi indicatori vengono aggiornati ogni giorno alle 9.

>[!NOTE]
>
>Inoltre, potete ricevere un rapporto giornaliero via e-mail all&#39;indirizzo specificato. Inviaci l&#39;indirizzo e-mail richiesto tramite e-mail o tramite Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

Nella relazione sono utilizzati i seguenti indicatori:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign verifica se per un indirizzo IP è stato specificato un DNS inverso e che questo indichi correttamente l&#39;IP.

* **[!UICONTROL SPF]** (Framework per i criteri di invio): Meccanismo di autenticazione che consente agli ISP e ai fornitori di cassette postali di verificare se il mittente e-mail è autorizzato nel dominio di invio.

* **[!UICONTROL DomainKeys]** : Un servizio sviluppato da Yahoo e destinato a certificare l&#39;identità di un mittente di posta elettronica.

* **[!UICONTROL IP and RBL domain]** (Elenco buchi neri in tempo reale): Un elenco di indirizzi IP e domini contrassegnati da organizzazioni blocklist per cattiva reputazione. Questi elenchi sono gestiti da organizzazioni dedicate come Spamhaus, Spampoliziotto, SURBL/URIBL, ecc. Adobe Campaign elabora attualmente controlli rispetto agli URL che hanno un impatto significativo sulla recapito. Questi URL riflettono la reputazione dell&#39;invio e possono essere citati dagli ISP prima di accettare di ricevere le tue e-mail.

* **[!UICONTROL SNDS]** (Smart Network Data Services): Un servizio [Windows Live Hotmail anti-spam](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail è l&#39;unico ISP che fornisce questo tipo di informazioni. I punteggi di riferimento sono un risultato di filtro verde, un tasso di reclamo inferiore allo 0,1% e zero spam trap.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
