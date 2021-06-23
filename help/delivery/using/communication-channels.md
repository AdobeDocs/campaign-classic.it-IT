---
product: campaign
title: Canali di comunicazione
description: Crea consegne per inviare messaggi personalizzati su canali diversi.
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 19%

---

# Canali di comunicazione{#communication-channels}

Con Adobe Campaign, puoi inviare campagne cross-channel tra cui e-mail, SMS, messaggi LINE, notifiche push e direct mailing e misurarne l’efficacia utilizzando vari [report](../../reporting/using/delivery-reports.md) dedicati. Questi messaggi sono progettati e inviati tramite consegna e possono essere personalizzati per ogni destinatario.

Le funzionalità di base includono il targeting, la definizione e la personalizzazione dei messaggi, l’esecuzione delle comunicazioni e i relativi rapporti operativi. Il punto di accesso funzionale principale è la procedura guidata di consegna. Permette di sfruttare diverse funzionalità incluse in Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign offre una serie di strumenti per monitorare il recapito messaggi e ottimizzare l’invio delle e-mail. Ulteriori informazioni in [questa sezione](about-deliverability.md).

L’invio della consegna può essere automatizzato preparando una consegna e/o inviandola nel processo di un flusso di lavoro. Per ulteriori informazioni sulle attività di tipo consegna nei flussi di lavoro, consulta [questa sezione](../../workflow/using/about-action-activities.md).

Adobe Campaign offre i seguenti canali di consegna:

1. **Canale e-mail**: le consegne e-mail ti consentono di inviare e-mail personalizzate alla popolazione target. Fai riferimento a [Informazioni sul canale e-mail](about-email-channel.md).
1. **Canale direct mailing**: le consegne tramite direct mailing ti consentono di generare un file di estrazione che contiene dati sulla popolazione target. Fai riferimento a [Informazioni sul canale direct mailing](about-direct-mail-channel.md).
1. **Canale** mobile: le consegne sui canali mobili ti consentono di inviare messaggi SMS o LINE personalizzati alla popolazione target. Fai riferimento a [Canale SMS](sms-channel.md).
1. **Canale dell’app mobile**: le consegne tramite app mobile ti consentono di inviare notifiche ai sistemi iOS e Android. Fai riferimento al capitolo [Canale app mobile](about-mobile-app-channel.md) .

   Altri canali sono descritti in [questa pagina](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >Il numero di canali disponibili dipende dal contratto. Controlla il contratto di licenza.

Le consegne possono essere eseguite **online** (tramite e-mail, uno dei canali mobili e notifiche push) e **offline** (canale direct mail).

A seconda del canale, le modalità di consegna possono essere:

* Consegna di massa diretta tramite Adobe Campaign (modalità predefinita per il canale e-mail).
* Consegna esterna tramite un operatore specializzato a cui viene assegnato il file di output generato dalla procedura guidata di consegna (modalità predefinita per il canale direct mailing).

Gli account esterni sono configurati tramite il nodo **[!UICONTROL Administration > Platform > External accounts]** . Questa configurazione deve essere eseguita solo da utenti esperti.

## Consegne e-mail {#email-deliveries}

Il [canale e-mail](about-email-channel.md) è uno dei canali principali di Adobe Campaign, che consente di pianificare e inviare e-mail personalizzate a destinazioni specifiche.

Puoi inviare diversi tipi di e-mail:

* E-mail a invio singolo: e-mail che puoi inviare una volta a un target definito. In genere vengono utilizzati per promuovere un contenuto specifico che verrebbe preparato e inviato una sola volta (newsletter, e-mail promozionale, ecc.).
* E-mail ricorrenti: in una campagna, invia regolarmente la stessa e-mail e aggrega ogni invio e i relativi rapporti su base periodica. La stessa e-mail viene inviata, ma di solito a un target diverso, in base al target idoneo per il giorno dell’invio. Un esempio comune è rappresentato da un’e-mail di compleanno. Per ulteriori informazioni, consulta [Consegne ricorrenti](../../workflow/using/recurring-delivery.md).
* E-mail transazionali: e-mail unitarie attivate in base al comportamento dei clienti. Fai riferimento a [Messaggistica transazionale](../../message-center/using/about-transactional-messaging.md).

Per informazioni sull’utilizzo della consegna e sui consigli, consulta le best practice per la consegna [Campaign](delivery-best-practices.md).

Per ulteriori informazioni sui diversi tipi di consegne, consulta [questa sezione](#types-of-deliveries).

## Consegne mobile {#mobile-deliveries}

Adobe Campaign consente di inviare messaggi [SMS](sms-channel.md) e [LINE](line-channel.md) sui dispositivi mobili.

Per i messaggi SMS, puoi creare, modificare e personalizzare i messaggi solo in formato testo. Puoi anche visualizzare in anteprima i messaggi SMS prima di inviarli.

Per i messaggi LINE, è possibile inviare testo o immagini e collegamenti.

Per inviare messaggi SMS o LINE a un cellulare è necessario:

* Un account esterno configurato sul canale **[!UICONTROL Mobile (SMS)]** o sul canale **[!UICONTROL LINE]**.
* Un modello di consegna SMS o LINE correttamente collegato a questo account esterno.

## Notifiche push {#push-notifications}

Adobe Campaign ti consente di inviare notifiche push personalizzate e segmentate [su dispositivi mobili iOS e Android, tramite app dedicate. ](about-mobile-app-channel.md) Una volta eseguiti i passaggi di configurazione e integrazione, è possibile creare e inviare le consegne iOS e Android. Puoi anche progettare notifiche avanzate con immagini o video.

## Direct mail {#direct-mail}

[La direct mailing è un canale offline che ti consente di personalizzare e generare il file richiesto dai provider di direct mailing. ](about-direct-mail-channel.md) Offre la possibilità di combinare i canali online e offline all’interno dei percorsi dei clienti.

I canali online ti consentono di creare i messaggi (e-mail, SMS, consegna su app mobili e così via) e di inviarli al tuo pubblico direttamente da Adobe Campaign. Con i canali offline, la situazione è diversa. Quando prepari una consegna di direct mailing, Adobe Campaign genera un file contenente tutti i profili target e le informazioni del contatto selezionato, ad esempio l’indirizzo postale. Potrai quindi inviare questo file al provider di direct mailing, che si occuperà dell’invio effettivo.

## Altri canali {#other-channels}

Adobe Campaign offre il modello di consegna telefonica, utilizzato per creare consegne esterne. L&#39;utilizzo di questo canale implica la configurazione di metodologie dedicate per elaborare i file di output. I passaggi di configurazione sono gli stessi del [Canale direct mailing](about-direct-mail-channel.md).

>[!NOTE]
>
>Il canale telefonico non è disponibile come standard. La sua implementazione richiede il coinvolgimento di Consulenza Adobe o di un Partner Adobe. Per ulteriori informazioni, contatta il tuo rappresentante di Adobe.

Inoltre, le consegne di tipo &quot;Altro&quot; utilizzano un modello tecnico specifico che non esegue un processo: questo consente loro di gestire le azioni di marketing eseguite al di fuori della piattaforma Adobe Campaign.

Questo canale non ha un meccanismo specifico. Si tratta di un canale generico che dispone della propria opzione di indirizzamento account esterno, del tipo di modello di consegna e dell’attività del flusso di lavoro della campagna, proprio come qualsiasi altro canale di comunicazione disponibile in Adobe Campaign.

Questo canale è progettato solo a scopo descrittivo, ad esempio per definire le consegne per le quali desideri mantenere una traccia del target di una campagna eseguita in uno strumento diverso da Adobe Campaign.

## Tipi di consegne{#types-of-deliveries}

In Campaign sono disponibili tre tipi di oggetti di consegna:

### Consegna singola {#single-delivery}

Un **delivery** è un oggetto di consegna autonomo che viene eseguito una volta. Può essere duplicato, preparato di nuovo, ma finché è nello stato finale (annullato, interrotto, finito) non può essere riutilizzato.

Le consegne possono essere create dall’elenco delle consegne o all’interno di un flusso di lavoro tramite un’attività [Consegna](../../workflow/using/delivery.md) .

I flussi di lavoro forniscono anche attività di consegna specifiche in base al tipo di canale che desideri utilizzare. Per ulteriori informazioni su queste attività, consulta [questa sezione](../../workflow/using/cross-channel-deliveries.md).

### Consegna ricorrente {#recurring-delivery}

Una **consegna ricorrente** consente di creare una nuova consegna ogni volta che l&#39;attività viene eseguita. In questo modo si evita la necessità di creare una nuova consegna per le attività ricorrenti.

Ad esempio, se esegui questo tipo di attività una volta al mese, finirai con 12 consegne dopo un anno.

Le consegne ricorrenti vengono create all’interno dei flussi di lavoro tramite l’ [Attività di consegna ricorrente](../../workflow/using/recurring-delivery.md). Un esempio di questa attività in uso è presentato in questa sezione: [Creazione di una consegna ricorrente in un flusso di lavoro di targeting](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Consegna continua {#continuous-delivery}

Una **consegna continua** consente di aggiungere nuovi destinatari a una consegna esistente, evitando di dover creare una nuova consegna ogni volta che viene eseguita.

Se vengono modificate delle informazioni nella consegna (contenuto, nome, ecc.), all’esecuzione della consegna viene creato un nuovo oggetto di consegna. Se non sono state modificate informazioni, lo stesso oggetto di consegna viene riutilizzato e i registri di consegna e di tracciamento vengono aggiunti nello stesso oggetto.

Ad esempio, se esegui questo tipo di attività una volta al mese, finirai con una singola consegna dopo un anno (purché non sia stata apportata alcuna modifica alla consegna).

Le consegne continue vengono create all’interno dei flussi di lavoro tramite l’ [attività di consegna continua](../../workflow/using/continuous-delivery.md).
