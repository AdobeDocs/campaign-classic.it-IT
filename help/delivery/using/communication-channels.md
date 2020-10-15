---
title: Canali di comunicazione
seo-title: Canali di comunicazione
description: Crea consegne per inviare messaggi personalizzati su canali diversi.
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 12%

---


# Canali di comunicazione{#communication-channels}

Con  Adobe Campaign, puoi inviare campagne tra canali, inclusi e-mail, SMS, messaggi LINE, notifiche push e indirizzi diretti, e misurarne l&#39;efficacia utilizzando vari [rapporti](../../reporting/using/delivery-reports.md)dedicati. Questi messaggi sono progettati e inviati tramite le consegne e possono essere personalizzati per ogni destinatario.

Le funzionalità principali includono il targeting, la definizione e la personalizzazione dei messaggi, l&#39;esecuzione delle comunicazioni e i relativi rapporti operativi. Il punto di accesso funzionale principale è la procedura guidata di consegna. Questo punto di accesso porta a diverse funzionalità coperte da  Adobe Campaign.

>[!NOTE]
>
> Adobe Campaign offre una serie di strumenti per monitorare la tua recapito e ottimizzare l&#39;invio delle e-mail. Per ulteriori informazioni, consulta la guida [Deliverability Getting Started](../../delivery/using/deliverability-key-points.md) and [Deliverability Management](../../delivery/using/about-deliverability.md)(Introduzione alla distribuzione).

L&#39;invio può essere automatizzato mediante la preparazione di una consegna e/o l&#39;invio nel processo di un flusso di lavoro. Per ulteriori informazioni sulle attività di tipo consegna nei flussi di lavoro, consulta [questa sezione](../../workflow/using/about-action-activities.md).

 Adobe Campaign offre i seguenti canali di distribuzione:

1. **Canale** e-mail: le comunicazioni e-mail consentono di inviare e-mail personalizzate alla popolazione di destinazione. Fare riferimento a [Informazioni sul canale](../../delivery/using/about-email-channel.md)e-mail.
1. **Canale** di posta diretta: le consegne per posta diretta consentono di generare un file di estrazione contenente dati sulla popolazione di destinazione. Fare riferimento a [Informazioni sul canale](../../delivery/using/about-direct-mail-channel.md)di posta diretta.
1. **Canale** mobile: le consegne sui canali mobili ti consentono di inviare messaggi SMS o LINE personalizzati alla popolazione di destinazione. Fare riferimento al canale [](../../delivery/using/sms-channel.md)SMS.
1. **Canale** applicazione mobile: le consegne delle app mobili consentono di inviare notifiche ai sistemi iOS e Android. Fate riferimento al capitolo Canale [app](../../delivery/using/about-mobile-app-channel.md) mobile.

   Altri canali sono descritti in [questa pagina](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >L’utilizzo di più canali dipende dal pacchetto. Controlla il contratto di licenza.

Le consegne possono essere effettuate **online** (tramite e-mail, uno dei canali mobili e notifiche push) e **offline** (canale di posta diretta).

A seconda del canale, le modalità di consegna possono essere:

* Distribuzione diretta di massa tramite  Adobe Campaign (modalità predefinita per il canale e-mail).
* Distribuzione esterna tramite un operatore specializzato a cui viene assegnato il file di output generato dalla procedura guidata di consegna (modalità predefinita per il canale di posta diretta).

Gli account esterni sono configurati tramite il **[!UICONTROL Administration > Platform > External accounts]** nodo. Questa configurazione deve essere eseguita solo da utenti esperti.

## Consegne e-mail {#email-deliveries}

Il canale [e-](../../delivery/using/about-email-channel.md) mail è uno dei canali principali di  Adobe Campaign, che consente di pianificare e inviare e-mail personalizzate a target specifici.

Potete inviare diversi tipi di e-mail:

* E-mail per invio singolo: e-mail che potete inviare una volta a una destinazione definita. In genere vengono utilizzati per promuovere un contenuto specifico che verrebbe preparato e inviato una sola volta (newsletter, e-mail promozionali, ecc.).
* E-mail ricorrenti: in una campagna, invia regolarmente la stessa e-mail e aggrega ogni invio e i relativi rapporti su base periodica. La stessa e-mail viene inviata, ma in genere a una destinazione diversa, in base alla destinazione idonea per il giorno dell&#39;invio. Un esempio comune è rappresentato da un&#39;e-mail di compleanno. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* E-mail transazionali: e-mail unitarie attivate in base al comportamento dei clienti. Fare riferimento a Messaggi [transazionali](../../message-center/using/about-transactional-messaging.md).

Per informazioni sull&#39;utilizzo della distribuzione e sulle raccomandazioni, consulta le procedure [consigliate per la](../../delivery/using/delivery-best-practices.md)distribuzione delle campagne.

Per ulteriori informazioni sui diversi tipi di consegne, consulta [questa sezione](#types-of-deliveries).

## Distribuzione per dispositivi mobili {#mobile-deliveries}

 Adobe Campaign consente di inviare messaggi [SMS](../../delivery/using/sms-channel.md) e [LINE](../../delivery/using/line-channel.md) su dispositivi mobili.

Per i messaggi SMS, potete creare, modificare e personalizzare i messaggi solo in formato testo. È inoltre possibile visualizzare l&#39;anteprima dei messaggi SMS prima dell&#39;invio.

Per i messaggi LINE, è possibile inviare testo o immagini e collegamenti.

Per inviare messaggi SMS o LINE a un cellulare è necessario:

* Account esterno configurato sul **[!UICONTROL Mobile (SMS)]** canale o sul **[!UICONTROL LINE]** canale.
* Un modello di consegna SMS o LINE correttamente collegato a questo account esterno.

## Notifiche push {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](../../delivery/using/about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Una volta eseguiti i passaggi di configurazione e integrazione, è possibile creare e inviare le consegne per iOS e Android. Potete anche progettare notifiche avanzate con immagini o video.

## Direct mailing {#direct-mail}

[La direct mailing è un canale offline che ti consente di personalizzare e generare il file richiesto dai provider di direct mailing. ](../../delivery/using/about-direct-mail-channel.md) Offre la possibilità di combinare i canali online e offline all’interno dei percorsi dei clienti.

I canali online ti consentono di creare i messaggi (e-mail, SMS, consegna su app mobili e così via) e di inviarli al tuo pubblico direttamente da Adobe Campaign. Con i canali offline, la situazione è diversa. Quando prepari una consegna di direct mailing, Adobe Campaign genera un file contenente tutti i profili target e le informazioni del contatto selezionato, ad esempio l’indirizzo postale. Potrai quindi inviare questo file al provider di direct mailing, che si occuperà dell’invio effettivo.

## Altri canali {#other-channels}

 Adobe Campaign offre modelli di consegna di agenzie o telefoni, che vengono utilizzati per creare consegne esterne. L&#39;utilizzo di questi canali implica la configurazione di metodologie dedicate per elaborare i file di output. I passaggi di configurazione sono gli stessi del canale [di posta](../../delivery/using/about-direct-mail-channel.md)diretta.

Inoltre, le consegne di tipo &quot;Altro&quot; utilizzano un modello tecnico specifico che non esegue un processo: questo consente loro di gestire le azioni di marketing eseguite al di fuori della piattaforma Adobe Campaign .

Questo canale non ha un meccanismo specifico. Si tratta di un canale generico che dispone di una propria opzione di routing dell&#39;account esterno, del tipo di modello di consegna e dell&#39;attività del flusso di lavoro della campagna, proprio come qualsiasi altro canale di comunicazione disponibile in  Adobe Campaign.

Questo canale è progettato solo per scopi descrittivi, ad esempio per definire le consegne per le quali si desidera mantenere traccia della destinazione di una campagna eseguita in uno strumento diverso da  Adobe Campaign.

## Tipi di consegne{#types-of-deliveries}

Campaign dispone di tre tipi di oggetti di consegna:

### Consegna singola {#single-delivery}

Un **recapito** è un oggetto di consegna standalone che viene eseguito una volta. Può essere duplicata, preparata di nuovo, ma finché è nello stato finale (annullato, interrotto, finito), non può essere riutilizzata.

Le consegne possono essere create dall&#39;elenco delle consegne o all&#39;interno di un flusso di lavoro tramite un&#39;attività [Consegna](../../workflow/using/delivery.md) .

I flussi di lavoro forniscono inoltre attività di consegna specifiche in base al tipo di canale che si desidera utilizzare. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Consegna ricorrente {#recurring-delivery}

Una consegna **** periodica consente di creare una nuova consegna ogni volta che l&#39;attività viene eseguita. In questo modo si evita di dover creare una nuova consegna per le attività ricorrenti.

Ad esempio, se esegui questo tipo di attività una volta al mese, alla fine avrai 12 consegne dopo un anno.

Le consegne ricorrenti vengono create all&#39;interno dei flussi di lavoro tramite l&#39;attività [di consegna](../../workflow/using/recurring-delivery.md)ricorrente. Un esempio di questa attività utilizzata è presentato in questa sezione: [Creazione di una distribuzione periodica in un flusso di lavoro](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)di targeting.

### Consegna continua {#continuous-delivery}

Una consegna **** continua consente di aggiungere nuovi destinatari a una consegna esistente, evitando di dover creare una nuova consegna ogni volta che viene eseguita.

Se un&#39;informazione nella consegna cambia (contenuto, nome, ecc.), viene creato un nuovo oggetto di consegna al momento dell&#39;esecuzione della consegna. Se non vengono modificate informazioni, lo stesso oggetto di consegna viene riutilizzato e i registri di consegna e tracciamento vengono aggiunti nello stesso oggetto.

Ad esempio, se esegui questo tipo di attività una volta al mese, finirai con un&#39;unica consegna dopo un anno (a condizione che non sia stata apportata alcuna modifica alla consegna).

Le consegne continue vengono create all&#39;interno dei flussi di lavoro tramite l&#39;attività [di consegna](../../workflow/using/continuous-delivery.md)continua.
