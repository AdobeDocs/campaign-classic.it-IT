---
solution: Campaign Classic
product: campaign
title: Canali di comunicazione
description: Crea consegne per inviare messaggi personalizzati su canali diversi.
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 44f2aed49a12d51bb3b38f304e6b922f0faf68cc
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 12%

---


# Canali di comunicazione{#communication-channels}

Con  Adobe Campaign, puoi inviare campagne tra canali, inclusi e-mail, SMS, messaggi LINE, notifiche push e indirizzi diretti, e misurarne l&#39;efficacia utilizzando vari [report](../../reporting/using/delivery-reports.md) dedicati. Questi messaggi sono progettati e inviati attraverso le consegne e possono essere personalizzati per ogni destinatario.

Le funzionalità principali includono il targeting, la definizione e la personalizzazione dei messaggi, l&#39;esecuzione delle comunicazioni e i relativi rapporti operativi. Il punto di accesso funzionale principale è la procedura guidata di consegna. Questo punto di accesso porta a molteplici funzionalità coperte da  Adobe Campaign.

>[!NOTE]
>
> Adobe Campaign offre una serie di strumenti per monitorare la tua recapito e ottimizzare l&#39;invio delle e-mail. Per ulteriori informazioni, consultare la sezione [Guida introduttiva all&#39;implementazione](../../delivery/using/deliverability-key-points.md) e [Gestione dell&#39;accessibilità](../../delivery/using/about-deliverability.md).

L&#39;invio può essere automatizzato mediante la preparazione di una consegna e/o l&#39;invio nel processo di un flusso di lavoro. Per ulteriori informazioni sulle attività di tipo consegna nei flussi di lavoro, consultare [questa sezione](../../workflow/using/about-action-activities.md).

 Adobe Campaign offre i seguenti canali di distribuzione:

1. **Canale** e-mail: le comunicazioni e-mail consentono di inviare e-mail personalizzate alla popolazione di destinazione. Fare riferimento a [Informazioni sul canale e-mail](../../delivery/using/about-email-channel.md).
1. **Canale** di posta diretta: le consegne per posta diretta consentono di generare un file di estrazione contenente dati sulla popolazione di destinazione. Fare riferimento a [Informazioni sul canale di posta diretta](../../delivery/using/about-direct-mail-channel.md).
1. **Canale** mobile: le consegne sui canali mobili ti consentono di inviare messaggi SMS o LINE personalizzati alla popolazione di destinazione. Fare riferimento a [canale SMS](../../delivery/using/sms-channel.md).
1. **Canale** applicazione mobile: le consegne delle app mobili consentono di inviare notifiche ai sistemi iOS e Android. Fare riferimento al capitolo [Canale app mobile](../../delivery/using/about-mobile-app-channel.md).

   Altri canali sono descritti in [questa pagina](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >Il numero di canali disponibili dipende dal contratto. Controlla il contratto di licenza.

Le consegne possono essere eseguite **online** (tramite e-mail, uno dei canali mobili e notifiche push), e **offline** (canale di posta diretta).

A seconda del canale, le modalità di consegna possono essere:

* Distribuzione diretta di massa tramite  Adobe Campaign (modalità predefinita per il canale e-mail).
* Distribuzione esterna tramite un operatore specializzato a cui viene assegnato il file di output generato dalla procedura guidata di consegna (modalità predefinita per il canale di posta diretta).

Gli account esterni sono configurati tramite il nodo **[!UICONTROL Administration > Platform > External accounts]**. Questa configurazione deve essere eseguita solo da utenti esperti.

## Consegne e-mail {#email-deliveries}

Il [canale e-mail](../../delivery/using/about-email-channel.md) è uno dei canali principali di  Adobe Campaign, che consente di pianificare e inviare e-mail personalizzate a target specifici.

Potete inviare diversi tipi di e-mail:

* E-mail per invio singolo: e-mail che potete inviare una volta a una destinazione definita. In genere vengono utilizzati per promuovere un contenuto specifico che verrebbe preparato e inviato una sola volta (newsletter, e-mail promozionali, ecc.).
* E-mail ricorrenti: in una campagna, invia regolarmente la stessa e-mail e aggrega ogni invio e i relativi rapporti su base periodica. La stessa e-mail viene inviata, ma in genere a una destinazione diversa, in base alla destinazione idonea per il giorno dell&#39;invio. Un esempio comune è rappresentato da un&#39;e-mail di compleanno. Per ulteriori informazioni, consultare [Consegne ricorrenti](../../workflow/using/recurring-delivery.md).
* E-mail transazionali: e-mail unitarie attivate in base al comportamento dei clienti. Fare riferimento a [Messaggi transazionali](../../message-center/using/about-transactional-messaging.md).

Per informazioni sull&#39;utilizzo della distribuzione e sulle raccomandazioni, consulta le procedure ottimali per la distribuzione di Campaign [Consegna](../../delivery/using/delivery-best-practices.md).

Per ulteriori informazioni sui diversi tipi di consegne, consultare [questa sezione](#types-of-deliveries).

## Distribuzione per dispositivi mobili {#mobile-deliveries}

 Adobe Campaign consente di inviare messaggi [SMS](../../delivery/using/sms-channel.md) e [LINE](../../delivery/using/line-channel.md) sui cellulari.

Per i messaggi SMS, potete creare, modificare e personalizzare i messaggi solo in formato testo. È inoltre possibile visualizzare l&#39;anteprima dei messaggi SMS prima dell&#39;invio.

Per i messaggi LINE, è possibile inviare testo o immagini e collegamenti.

Per inviare messaggi SMS o LINE a un cellulare è necessario:

* Account esterno configurato sul canale **[!UICONTROL Mobile (SMS)]** o sul canale **[!UICONTROL LINE]**.
* Un modello di consegna SMS o LINE correttamente collegato a questo account esterno.

## Notifiche push {#push-notifications}

 Adobe Campaign consente di inviare [notifiche push personalizzate e segmentate](../../delivery/using/about-mobile-app-channel.md) su dispositivi mobili iOS e Android, tramite app dedicate. Una volta eseguiti i passaggi di configurazione e integrazione, è possibile creare e inviare le consegne per iOS e Android. Potete anche progettare notifiche avanzate con immagini o video.

## Direct mailing {#direct-mail}

[La direct mailing è un canale offline che ti consente di personalizzare e generare il file richiesto dai provider di direct mailing. ](../../delivery/using/about-direct-mail-channel.md) Offre la possibilità di combinare i canali online e offline all’interno dei percorsi dei clienti.

I canali online ti consentono di creare i messaggi (e-mail, SMS, consegna su app mobili e così via) e di inviarli al tuo pubblico direttamente da Adobe Campaign. Con i canali offline, la situazione è diversa. Quando prepari una consegna di direct mailing, Adobe Campaign genera un file contenente tutti i profili target e le informazioni del contatto selezionato, ad esempio l’indirizzo postale. Potrai quindi inviare questo file al provider di direct mailing, che si occuperà dell’invio effettivo.

## Altri canali {#other-channels}

 Adobe Campaign offre un modello di consegna telefonica, che consente di creare consegne esterne. L&#39;utilizzo di questo canale implica la configurazione di metodologie dedicate per elaborare i file di output. I passaggi di configurazione sono gli stessi di [Canale di posta diretta](../../delivery/using/about-direct-mail-channel.md).

>[!NOTE]
>
>Il canale telefonico non è disponibile. La sua attuazione richiede  consulenza del Adobe o un partner  Adobe. Per maggiori informazioni, contattate il rappresentante del Adobe .

Inoltre, le consegne di tipo &quot;Altro&quot; utilizzano un modello tecnico specifico che non esegue un processo: questo consente loro di gestire le azioni di marketing eseguite al di fuori della piattaforma Adobe Campaign .

Questo canale non ha un meccanismo specifico. Si tratta di un canale generico che dispone di una propria opzione di routing dell&#39;account esterno, del tipo di modello di consegna e dell&#39;attività del flusso di lavoro della campagna, proprio come qualsiasi altro canale di comunicazione disponibile in  Adobe Campaign.

Questo canale è progettato solo per scopi descrittivi, ad esempio per definire le consegne per le quali si desidera mantenere traccia della destinazione di una campagna eseguita in uno strumento diverso da  Adobe Campaign.

## Tipi di consegne{#types-of-deliveries}

Campaign dispone di tre tipi di oggetti di consegna:

### Consegna singola {#single-delivery}

Un **delivery** è un oggetto di consegna standalone che viene eseguito una volta. Può essere duplicata, preparata di nuovo, ma finché è nello stato finale (annullato, interrotto, finito), non può essere riutilizzata.

Le consegne possono essere create dall&#39;elenco delle consegne o all&#39;interno di un flusso di lavoro tramite un&#39;attività [Delivery](../../workflow/using/delivery.md).

I flussi di lavoro forniscono inoltre attività di consegna specifiche in base al tipo di canale che si desidera utilizzare. Per ulteriori informazioni su queste attività, consultare [questa sezione](../../workflow/using/cross-channel-deliveries.md).

### Consegna ricorrente {#recurring-delivery}

Una **consegna ricorrente** consente di creare una nuova consegna ogni volta che l&#39;attività viene eseguita. In questo modo si evita di dover creare una nuova consegna per le attività ricorrenti.

Ad esempio, se esegui questo tipo di attività una volta al mese, alla fine avrai 12 consegne dopo un anno.

Le consegne ricorrenti vengono create all&#39;interno dei flussi di lavoro tramite l&#39; [attività di consegna ricorrente](../../workflow/using/recurring-delivery.md). Un esempio di questa attività utilizzata è presentato in questa sezione: [Creazione di una consegna ricorrente in un flusso di lavoro di targeting](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Consegna continua {#continuous-delivery}

Una **consegna continua** consente di aggiungere nuovi destinatari a una consegna esistente, evitando di dover creare una nuova consegna ogni volta che viene eseguita.

Se un&#39;informazione nella consegna cambia (contenuto, nome, ecc.), viene creato un nuovo oggetto di consegna al momento dell&#39;esecuzione della consegna. Se non vengono modificate informazioni, lo stesso oggetto di consegna viene riutilizzato e i registri di consegna e tracciamento vengono aggiunti nello stesso oggetto.

Ad esempio, se esegui questo tipo di attività una volta al mese, finirai con un&#39;unica consegna dopo un anno (a condizione che non sia stata apportata alcuna modifica alla consegna).

Le consegne continue vengono create all&#39;interno dei flussi di lavoro tramite l&#39; [attività di consegna continua](../../workflow/using/continuous-delivery.md).
