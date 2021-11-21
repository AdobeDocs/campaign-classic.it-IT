---
product: campaign
title: Controllare prima dell’invio
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 4%

---

# Esegui tutti i controlli prima dell’invio {#perform-all-checks}

![](../../assets/common.svg)

Quando il messaggio è pronto, accertati che il relativo contenuto sia visualizzato correttamente, su tutti i dispositivi, e non contenga errori quali personalizzazione errata o collegamenti interrotti.

Prima di inviare il messaggio, assicurati anche che i parametri e la configurazione siano coerenti con la consegna.

## Perché la convalida è fondamentale {#validation-is-key}

Prima di inviare una consegna, è necessario assicurarsi che i destinatari ricevano il messaggio che si desidera inviare loro. A questo scopo, devi convalidare il contenuto del messaggio e i parametri di consegna.

Questo passaggio ti consente di rilevare eventuali errori e correggerli prima di consegnarli al target principale.

Vengono descritti i passaggi per la convalida di una consegna [in questa sezione](steps-validating-the-delivery.md).

## Rendering della casella in entrata {#inbox-and-email-rendering}

Il rendering della casella in entrata consente di visualizzare in anteprima i messaggi sui principali client e-mail, di eseguire la scansione del contenuto e della reputazione, di scoprire come i destinatari leggono i messaggi.

**Suggerimenti**:

* Puoi visualizzare il messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto: webmail, servizio messaggi, dispositivi mobili, ecc.

* Le funzionalità di rendering della casella in entrata sono fondamentali per identificare se le campagne e-mail sono riuscite a superare i filtri dei principali ISP (Internet Service Providers) e dei servizi di posta web. Tali strumenti inviano una copia pre-volo di un’e-mail a una rete di caselle in entrata di prova, in modo da visualizzare il messaggio o eseguirne il rendering in questi servizi. Possono anche includere rapporti e opzioni di correzione del codice che ti aiutano a identificare rapidamente e a risolvere i problemi che migliorano il recapito messaggi.

Ulteriori informazioni [in questa sezione](inbox-rendering.md).

## Messaggi di prova {#proof-messages}

L’invio di bozze consente di controllare il collegamento di rinuncia, la pagina speculare e qualsiasi altro collegamento, convalidare il messaggio, verificare che le immagini siano visualizzate, rilevare eventuali errori e così via. Puoi anche controllare la progettazione e il rendering su diversi dispositivi.

Ulteriori informazioni [in questa sezione](steps-validating-the-delivery.md#sending-a-proof).

## Configurare le consegne di test A/B {#a-b-testing-deliveries}

Se disponi di più contenuti per una consegna e-mail, puoi utilizzare il test A/B per scoprire quale versione avrà il maggiore impatto sulla popolazione target.

**Suggerimenti**:

* Inviare versioni diverse ad alcuni dei tuoi destinatari

* Seleziona quella con il tasso di successo più alto e inviala al resto del target

Ulteriori informazioni [in questa sezione](get-started-a-b-testing.md).

## Assicurati che il messaggio sia stato recapitato {#make-sure-your-message-is-delivered}

Come ultimo passo, massimizza le tue possibilità e sfrutta la potenza di Adobe Campaign Classic per garantire che il messaggio venga effettivamente consegnato ai destinatari pertinenti.

### Eseguire un processo di convalida

È possibile definire un processo di convalida completo, che coinvolga gli operatori e i gruppi Adobe Campaign, per convalidare sia il target che il contenuto del messaggio. In questo modo si garantirà il pieno controllo e controllo dei vari processi della campagna: targeting, contenuto, budget, estrazione e invio di una bozza. A seconda delle loro autorizzazioni, gli utenti riceveranno notifiche e bozze per convalidare o rifiutare il messaggio. Ulteriori informazioni [in questa sezione](../../campaign/using/marketing-campaign-approval.md).

### Usa onde

Puoi aumentare progressivamente il volume inviato utilizzando le onde. In questo modo si evita di contrassegnare i messaggi come spam o quando si desidera limitare il numero di messaggi al giorno. Utilizzando le ondate è possibile dividere le consegne in più batch invece di inviare volumi elevati di messaggi contemporaneamente. Ulteriori informazioni [in questa sezione](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Assegnare priorità ai messaggi

Puoi impostare l’ordine di invio per le consegne specificando il livello di priorità. Per eseguire questa operazione:

1. Modifica le proprietà di consegna e seleziona il **[!UICONTROL Delivery]** scheda .

1. Definisci il livello di priorità per la consegna su una scala da **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>Non è possibile definire l’ordine di invio dei messaggi dall’interno di una consegna.

### Impostazione delle affinità IP

Per controllare meglio il traffico SMTP in uscita, puoi gestire le affinità definendo quali indirizzi IP specifici possono essere utilizzati per ogni affinità. Ciò ti consente di limitare il numero di e-mail per consegne specifiche a computer o indirizzi di output. Ad esempio, puoi utilizzare un’affinità per paese o sottodominio. Puoi quindi creare una tipologia per paese e collegare ogni affinità alla tipologia corrispondente.

Puoi:

* Definisci le affinità IP nel file di configurazione serverConf.xml. [Ulteriori informazioni](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Per ogni elemento IPAffinity, dichiarare gli indirizzi IP che possono essere utilizzati. [Ulteriori informazioni](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In [tipologia](../../campaign-opt/using/about-campaign-typologies.md) di tua scelta, utilizza **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne al server di consegna (MTA) che gestisce tale affinità. [Ulteriori informazioni](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una volta inviata l’e-mail, controlla l’intestazione per verificare da quale indirizzo IP è stata inviata la consegna. L’amministratore di e-mail deve essere in grado di ottenere le informazioni relative all’intestazione.

>[!NOTE]
>
>La maggior parte di questi passaggi può essere eseguita solo da un utente esperto.

### Utilizzare le tipologie

Puoi utilizzare le regole di tipologia per escludere parte del target in base a criteri specifici. Ciò garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Ad esempio, puoi filtrare i destinatari meno recenti dal target della newsletter. Ulteriori informazioni [in questo esempio](../../campaign-opt/using/filtering-rules.md).

### Evitare allegati

Gli allegati rimangono uno dei vettori più comuni per la proliferazione del malware, soprattutto quando sono inviati alla rinfusa. Includi un collegamento sicuro al documento invece di allegarlo. Questo garantisce un ulteriore livello di sicurezza per evitare una ridistribuzione non intenzionale e riduce notevolmente le possibilità che il messaggio venga rifiutato nei gateway e-mail in entrata per motivi di dimensione o sicurezza dei messaggi.
