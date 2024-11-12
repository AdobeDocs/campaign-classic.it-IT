---
product: campaign
title: Canali di comunicazione
description: Crea consegne per inviare messaggi personalizzati su canali diversi
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 61%

---

# Canali di comunicazione{#communication-channels}

Con Adobe Campaign, puoi inviare campagne cross-channel tra cui e-mail, SMS, messaggi LINE, notifiche push e direct mail; inoltre, puoi misurarne l’efficacia utilizzando vari [report](../../reporting/using/delivery-reports.md) dedicati. Questi messaggi sono progettati e inviati tramite consegna e possono essere personalizzati per ogni destinatario.

Le funzionalità di base includono il targeting, la definizione e la personalizzazione dei messaggi, l’esecuzione delle comunicazioni e i relativi rapporti operativi. Il punto di accesso funzionale principale è l’assistente alla consegna. Permette di sfruttare diverse funzionalità incluse in Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign offre una serie di strumenti per monitorare il recapito messaggi e ottimizzare l’invio delle e-mail. Per ulteriori informazioni, consulta [questa sezione](about-deliverability.md).

L’invio della consegna può essere automatizzato preparando una consegna e/o inviandola nel processo di un flusso di lavoro. Per ulteriori informazioni sulle attività di tipo consegna nei flussi di lavoro, consulta [questa sezione](../../workflow/using/about-action-activities.md).

Adobe Campaign offre i seguenti canali di consegna:

1. **Canale e-mail**: le consegne e-mail ti consentono di inviare e-mail personalizzate alla popolazione target. Consulta [Informazioni sul canale e-mail](about-email-channel.md).
1. **Canale direct mail**: le consegne tramite direct mail ti consentono di generare un file di estrazione che contiene dati sulla popolazione target. Consulta [Informazioni sul canale direct mailing](about-direct-mail-channel.md).
1. **Canale mobile**: le consegne sui canali mobili ti consentono di inviare messaggi SMS o LINE personalizzati alla popolazione target. Consulta [Canale SMS](sms-channel.md).
1. **Canale app mobile**: le consegne tramite app mobile ti consentono di inviare notifiche ai sistemi iOS e Android. Consulta il capitolo [Canale app mobile](about-mobile-app-channel.md).

   Altri canali sono descritti in [questa sezione](#other-channels).

   >[!NOTE]
   >
   >Il numero di canali disponibili dipende dal contratto. Controlla il contratto di licenza.

Le consegne possono essere eseguite **online** (tramite e-mail, uno dei canali mobili e notifiche push) e **offline** (canale direct mailing).

A seconda del canale, le modalità di consegna possono essere:

* Consegna diretta di massa tramite Adobe Campaign (modalità predefinita per il canale e-mail).
* Consegna esterna tramite un operatore specializzato a cui viene fornito il file di output generato dall’assistente alla consegna (modalità predefinita per il canale direct mailing).

Gli account esterni sono configurati tramite il nodo **[!UICONTROL Administration > Platform > External accounts]**. Questa configurazione deve essere eseguita solo da utenti esperti.

## Consegne e-mail {#email-deliveries}

Il [canale e-mail](about-email-channel.md) è uno dei canali principali di Adobe Campaign e ti consente di pianificare e inviare e-mail personalizzate a target specifici.

Puoi inviare diversi tipi di e-mail:

* E-mail singole: e-mail che puoi inviare una volta a un target definito. Vengono solitamente utilizzate per promuovere un contenuto specifico che viene preparato e inviato una sola volta (newsletter, e-mail promozionale, ecc.).
* E-mail ricorrenti: in una campagna, invia regolarmente la stessa e-mail e aggrega ogni invio e i relativi rapporti su base periodica. Viene inviata la stessa e-mail, ma in genere a un target diverso, in base a quello idoneo per il giorno dell’invio. Un esempio comune è un’e-mail di compleanno. Per ulteriori informazioni, consulta [Consegne ricorrenti](../../workflow/using/recurring-delivery.md).
* E-mail transazionali: e-mail unitarie che vengono attivate in base al comportamento della clientela. Consulta [Messaggistica transazionale](../../message-center/using/about-transactional-messaging.md).

Per informazioni sull&#39;utilizzo e sui consigli per la consegna, consulta la sezione sulle [best practice per la consegna](delivery-best-practices.md) della campagna.

Per ulteriori informazioni sui diversi tipi di consegna, consulta [questa sezione](#types-of-deliveries).

## Consegne su dispositivi mobili {#mobile-deliveries}

Adobe Campaign consente di consegnare messaggi [SMS](sms-channel.md) e [LINE](line-channel.md) su dispositivi mobili.

Per i messaggi SMS, puoi creare, modificare e personalizzare i messaggi solo in formato testo. Puoi anche visualizzare in anteprima i messaggi SMS prima che vengano inviati.

Per i messaggi LINE, puoi inviare testo o immagini e collegamenti.

Per consegnare messaggi SMS o LINE a un telefono cellulare, è necessario:

* Un account esterno configurato sul canale **[!UICONTROL Mobile (SMS)]** o **[!UICONTROL LINE]**.
* Un modello di consegna SMS o LINE correttamente collegato a tale account esterno.

## Notifiche push {#push-notifications}

Adobe Campaign ti consente di inviare [notifiche push](about-mobile-app-channel.md) personalizzate e segmentate sui dispositivi mobili iOS e Android tramite app dedicate. Una volta eseguiti i passaggi di configurazione e integrazione, è possibile creare e inviare le consegne di iOS e Android. Puoi anche progettare notifiche avanzate con immagini o video.

## Direct mail {#direct-mail}

[Direct mail](about-direct-mail-channel.md) è un canale offline che consente di personalizzare e generare il file richiesto dai provider di direct mailing. Offre la possibilità di combinare i canali online e offline all’interno dei percorsi dei clienti.

I canali online ti consentono di creare i messaggi (e-mail, SMS, consegna tramite app mobile, ecc.) e inviarli al pubblico direttamente da Adobe Campaign. Con i canali offline, la situazione è diversa. Quando prepari una consegna di direct mailing, Adobe Campaign genera un file contenente tutti i profili target e le informazioni del contatto selezionato, ad esempio l’indirizzo postale. Potrai quindi inviare questo file al provider di direct mailing, che si occuperà dell’invio effettivo.

## Altri canali {#other-channels}

Adobe Campaign offre il modello di consegna telefonica, utilizzato per creare consegne esterne. L’utilizzo di questo canale implica la configurazione di metodologie dedicate per l’elaborazione dei file di output. I passaggi di configurazione sono gli stessi del [Canale direct mail](about-direct-mail-channel.md).

>[!NOTE]
>
>Il canale telefonico non è disponibile come standard. L’implementazione richiede il coinvolgimento del team di consulenza o di un partner di Adobe. Per maggiori informazioni, contatta il tuo rappresentante Adobe.

Inoltre, le consegne di tipo &quot;Altro&quot; utilizzano un modello tecnico specifico che non esegue un processo: questo consente loro di gestire le azioni di marketing eseguite al di fuori della piattaforma Adobe Campaign.

Questo canale non dispone di un meccanismo specifico. Si tratta di un canale generico con una propria opzione di indirizzamento dell’account esterno, un tipo di modello di consegna e un’attività del flusso di lavoro della campagna, come qualsiasi altro canale di comunicazione disponibile in Adobe Campaign.

Questo canale è progettato solo a scopo descrittivo, ad esempio per definire consegne per le quali desideri tenere traccia del target di una campagna eseguita in uno strumento diverso da Adobe Campaign.

## Tipi di consegne{#types-of-deliveries}

In Campaign sono disponibili tre tipi di oggetti di consegna:

### Consegna unica {#single-delivery}

Una **consegna** è un oggetto di consegna autonoma che viene eseguito una volta. Può essere duplicato, preparato di nuovo, ma finché è nel suo stato finale (annullato, interrotto, finito), non può essere riutilizzato.

Le consegne possono essere create dall’elenco delle consegne o all’interno di un flusso di lavoro tramite un’attività di [Consegna](../../workflow/using/delivery.md).

I flussi di lavoro forniscono anche attività di consegna specifiche in base al tipo di canale che desideri utilizzare. Per ulteriori informazioni su tali attività, consulta [questa sezione](../../workflow/using/cross-channel-deliveries.md).

### Consegna ricorrente {#recurring-delivery}

Una **consegna ricorrente** ti consente di creare una nuova consegna ogni volta che l&#39;attività viene eseguita. In questo modo si evita di dover creare una nuova consegna per attività ricorrenti.

Ad esempio, se esegui questo tipo di attività una volta al mese, dopo un anno ti ritroverai 12 consegne.

Le consegne ricorrenti vengono create all’interno dei flussi di lavoro tramite l’[attività Consegna ricorrente](../../workflow/using/recurring-delivery.md). Un esempio di questa attività in uso è presentato in questa sezione: [Creazione di una consegna ricorrente in un flusso di lavoro di targeting](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Consegna continua {#continuous-delivery}

Una **consegna continua** consente di aggiungere nuovi destinatari a una consegna esistente, evitando di dover crearne una nuova ogni volta che viene eseguita.

Se un’informazione nella consegna cambia (contenuto, nome, ecc.), nell’esecuzione della consegna viene creato un nuovo oggetto di consegna. Se non è stata modificata alcuna informazione, viene riutilizzato lo stesso oggetto di consegna e i registri di consegna e di tracciamento vengono aggiunti nello stesso oggetto.

Ad esempio, se esegui questo tipo di attività una volta al mese, ti ritroverai una singola consegna dopo un anno (purché non sia stata apportata alcuna modifica alla consegna).

Le consegne continue vengono create all’interno dei flussi di lavoro tramite l’[attività Consegna continua](../../workflow/using/continuous-delivery.md).
