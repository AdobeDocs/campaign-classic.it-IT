---
title: Canali di comunicazione
seo-title: Canali di comunicazione
description: Canali di comunicazione
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---


# Canali di comunicazione{#communication-channels}

Con Adobe Campaign, puoi inviare campagne tra canali, inclusi e-mail, SMS, messaggi LINE, notifiche push e e-mail dirette, e misurarne l&#39;efficacia utilizzando vari [rapporti](../../reporting/using/delivery-reports.md)dedicati. Questi messaggi sono progettati e inviati attraverso le consegne e possono essere personalizzati per ogni destinatario.

Le funzionalità principali includono il targeting, la definizione e la personalizzazione dei messaggi, l&#39;esecuzione delle comunicazioni e i relativi rapporti operativi. Il punto di accesso funzionale principale è la procedura guidata di consegna. Questo punto di accesso porta a diverse funzionalità coperte da Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign offre una serie di strumenti per monitorare la tua recapito e ottimizzare l&#39;invio delle e-mail. Per ulteriori informazioni, consulta la guida [Deliverability](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) and [Deliverability Management](../../delivery/using/about-deliverability.md)(Introduzione alla conformità e gestione della conformità).

L&#39;invio può essere automatizzato mediante la preparazione di una consegna e/o l&#39;invio nel processo di un flusso di lavoro. Per ulteriori informazioni sulle attività di tipo consegna nei flussi di lavoro, consulta [questa sezione](../../workflow/using/about-action-activities.md).

Adobe Campaign offre i seguenti canali di consegna:

1. **Canale** e-mail: le comunicazioni e-mail consentono di inviare e-mail personalizzate alla popolazione di destinazione. Fare riferimento a [Informazioni sul canale](../../delivery/using/about-email-channel.md)e-mail.
1. **Canale** di posta diretta: le consegne per posta diretta consentono di generare un file di estrazione contenente dati sulla popolazione di destinazione. Fare riferimento a [Informazioni sul canale](../../delivery/using/about-direct-mail-channel.md)di posta diretta.
1. **Canale** mobile: le consegne sui canali mobili ti consentono di inviare messaggi SMS o LINE personalizzati alla popolazione di destinazione. Fare riferimento al canale [](../../delivery/using/sms-channel.md)SMS.
1. **Canale** applicazione mobile: le consegne delle app mobili consentono di inviare notifiche ai sistemi iOS e Android. Fate riferimento al capitolo Canale [app](../../delivery/using/about-mobile-app-channel.md) mobile.

   Altri canali sono descritti in [questa pagina](../../delivery/using/other-channels.md).

   >[!NOTE]
   >
   >L’utilizzo di più canali dipende dal pacchetto. Controllare il contratto di licenza.

Le consegne possono essere effettuate **online** (tramite e-mail, uno dei canali mobili e notifiche push) e **offline** (canale di posta diretta).

A seconda del canale, le modalità di consegna possono essere:

* Distribuzione diretta di massa tramite Adobe Campaign (modalità predefinita per il canale e-mail).
* Distribuzione esterna tramite un operatore specializzato a cui viene assegnato il file di output generato dalla procedura guidata di consegna (modalità predefinita per il canale di posta diretta).

Gli account esterni sono configurati tramite il **[!UICONTROL Administration > Platform > External accounts]** nodo. Questa configurazione deve essere eseguita solo da utenti esperti.

## Consegne e-mail {#email-deliveries}

Il canale [e-](../../delivery/using/about-email-channel.md) mail è uno dei canali principali di Adobe Campaign e consente di pianificare e inviare e-mail personalizzate a target specifici.

Potete inviare diversi tipi di e-mail:

* E-mail per invio singolo: e-mail che potete inviare una volta a una destinazione definita. In genere vengono utilizzati per promuovere un contenuto specifico che verrebbe preparato e inviato una sola volta (newsletter, e-mail promozionali, ecc.).
* E-mail ricorrenti: in una campagna, invia regolarmente la stessa e-mail e aggrega ogni invio e i relativi rapporti su base periodica. La stessa e-mail viene inviata, ma in genere a una destinazione diversa, in base alla destinazione idonea per il giorno dell&#39;invio. Un esempio comune è rappresentato da un&#39;e-mail di compleanno. Per ulteriori informazioni, vedere Consegne [ricorrenti](../../workflow/using/recurring-delivery.md).
* E-mail transazionali: e-mail unitarie attivate in base al comportamento dei clienti. Fare riferimento a Messaggi [transazionali](../../message-center/using/about-transactional-messaging.md).

Per informazioni sull&#39;utilizzo della distribuzione e sulle raccomandazioni, consulta le procedure [consigliate per la](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)distribuzione delle campagne.

Per ulteriori informazioni sui diversi tipi di consegne, consulta [questa sezione](../../delivery/using/types-of-deliveries.md).

## Distribuzione per dispositivi mobili {#mobile-deliveries}

Adobe Campaign consente di inviare messaggi [SMS](../../delivery/using/sms-channel.md) e [LINE](../../delivery/using/line-channel.md) sui dispositivi mobili.

Per i messaggi SMS, potete creare, modificare e personalizzare i messaggi solo in formato testo. È inoltre possibile visualizzare l&#39;anteprima dei messaggi SMS prima dell&#39;invio.

Per i messaggi LINE, è possibile inviare testo o immagini e collegamenti.

Per inviare messaggi SMS o LINE a un cellulare è necessario:

* Account esterno configurato sul **[!UICONTROL Mobile (SMS)]** canale o sul **[!UICONTROL LINE]** canale.
* Un modello di consegna SMS o LINE correttamente collegato a questo account esterno.

## Notifiche push {#push-notifications}

Adobe Campaign consente di inviare notifiche [](../../delivery/using/about-mobile-app-channel.md) push personalizzate e segmentate su dispositivi mobili iOS e Android tramite app dedicate. Una volta eseguiti i passaggi di configurazione e integrazione, è possibile creare e inviare le consegne per iOS e Android. Potete anche progettare notifiche avanzate con immagini o video.

## Direct mail {#direct-mail}

[La posta](../../delivery/using/about-direct-mail-channel.md) diretta è un canale offline che consente di personalizzare e generare il file richiesto dai fornitori di posta diretta. Offre la possibilità di combinare canali online e offline nei viaggi dei clienti.

I canali online consentono di creare i messaggi (e-mail, SMS, distribuzione di app mobili, ecc.) e inviali al tuo pubblico direttamente da Adobe Campaign. Con i canali offline, è diverso. Quando prepari la consegna diretta per posta, Adobe Campaign genera un file contenente tutti i profili di destinazione e le informazioni di contatto scelte (ad esempio l&#39;indirizzo postale). Sarà quindi possibile inviare questo file al provider di posta diretta che si occuperà dell&#39;invio effettivo.
