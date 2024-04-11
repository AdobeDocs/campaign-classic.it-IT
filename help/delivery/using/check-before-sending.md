---
product: campaign
title: Controllare prima dell’invio
description: Quando il messaggio è pronto, esegui tutti i controlli prima di inviarlo
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 4%

---

# Esegui tutti i controlli prima dell’invio {#perform-all-checks}

Quando il messaggio è pronto, accertati che il suo contenuto sia visualizzato correttamente, su tutti i dispositivi, e non contenga errori quali personalizzazione errata o collegamenti interrotti.

Prima di inviare il messaggio, assicurati anche che i parametri e la configurazione siano coerenti con la consegna.

## Perché la convalida è fondamentale {#validation-is-key}

Prima di inviare una consegna, è necessario assicurarsi che i destinatari ricevano il messaggio che si desidera veramente inviare. A questo scopo, devi convalidare il contenuto del messaggio e i parametri di consegna.

Questo passaggio ti consente di rilevare eventuali errori e correggerli prima di consegnarli al target principale.

Vengono presentati i passaggi per la convalida di una consegna [in questa sezione](steps-validating-the-delivery.md).

## Rendering della casella in entrata {#inbox-and-email-rendering}

Il rendering della casella in entrata consente di visualizzare in anteprima i messaggi sui principali client e-mail, esaminare il contenuto e la reputazione e scoprire come i destinatari leggono i messaggi.

**Suggerimenti**:

* Puoi visualizzare il messaggio inviato nei diversi contesti in cui può essere ricevuto: posta sul web, servizio messaggi, dispositivi mobili, ecc.

* Le funzionalità di rendering della casella in entrata sono fondamentali per identificare se le campagne e-mail sono riuscite a superare i filtri dei principali ISP (provider di servizi Internet) e servizi di posta sul web. Tali strumenti inviano una copia pre-volo di un’e-mail a una rete di caselle in entrata di prova, in modo da poter vedere come verrà visualizzato il messaggio o come verrà eseguito il rendering tra questi servizi. Possono inoltre includere rapporti e opzioni di correzione del codice che consentono di identificare rapidamente e apportare correzioni che migliorano il recapito messaggi.

Per ulteriori informazioni, consulta [questa sezione](inbox-rendering.md).

## Messaggi di bozza {#proof-messages}

L’invio di bozze ti consente di controllare il collegamento di rinuncia, la pagina speculare e tutti gli altri collegamenti, convalidare il messaggio, verificare che siano visualizzate le immagini, rilevare eventuali errori, ecc. Puoi anche controllare la progettazione e il rendering su dispositivi diversi.

Per ulteriori informazioni, consulta [questa sezione](steps-validating-the-delivery.md#sending-a-proof).

## Configurare le consegne dei test A/B {#a-b-testing-deliveries}

Se disponi di diversi contenuti per una consegna e-mail, puoi utilizzare il test A/B per individuare la versione che avrà l’impatto maggiore sulla popolazione target.

**Suggerimenti**:

* Inviare le diverse versioni ad alcuni destinatari

* Seleziona quello con il tasso di successo più alto e invialo al resto della destinazione

Per ulteriori informazioni, consulta [questa sezione](get-started-a-b-testing.md).

## Assicurati che il messaggio sia consegnato {#make-sure-your-message-is-delivered}

Come ultimo passo, massimizza le opportunità e sfrutta la potenza di Adobe Campaign Classic per garantire che il messaggio venga effettivamente consegnato ai destinatari pertinenti.

### Seguire un processo di convalida

Puoi definire un processo di convalida completo, che coinvolga operatori e gruppi di Adobe Campaign, per convalidare sia il contenuto di destinazione che quello del messaggio. Ciò garantirà il monitoraggio e il controllo completo dei vari processi della campagna: targeting, contenuto, budget, estrazione e invio di una bozza. A seconda delle autorizzazioni, gli utenti riceveranno una notifica, riceveranno delle bozze e saranno in grado di convalidare o rifiutare il messaggio. Per ulteriori informazioni, consulta [questa sezione](../../campaign/using/marketing-campaign-approval.md).

### Usa ondate

È possibile aumentare progressivamente il volume inviato mediante scaglioni. In questo modo i messaggi non verranno contrassegnati come spam o quando desideri limitare il numero di messaggi al giorno. Utilizzando le scaglioni è possibile suddividere le consegne in più batch anziché inviare contemporaneamente volumi elevati di messaggi. Per ulteriori informazioni, consulta [questa sezione](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Assegnare priorità ai messaggi

Puoi impostare l’ordine di invio per le consegne indicando il livello di priorità. Per eseguire questa operazione:

1. Modifica le proprietà di consegna e seleziona la **[!UICONTROL Delivery]** scheda.

1. Definisci il livello di priorità per la consegna su una scala da **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>Non è possibile definire l’ordine di invio dei messaggi da una consegna.

### Configurare le affinità IP

Per controllare meglio il traffico SMTP in uscita, puoi gestire le affinità definendo quali indirizzi IP specifici possono essere utilizzati per ogni affinità. Questo ti consente di limitare il numero di e-mail per consegne specifiche a computer o indirizzi di output. Ad esempio, puoi utilizzare un’affinità per paese o sottodominio. Puoi quindi creare una tipologia per paese e collegare ogni affinità alla tipologia corrispondente.

Puoi eseguire le seguenti azioni:

* Definisci le affinità IP nel file di configurazione serverConf.xml. [Ulteriori informazioni](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Per ogni elemento IPAfinity, dichiarare gli indirizzi IP che è possibile utilizzare. [Ulteriori informazioni](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* In [tipologia](../../campaign-opt/using/about-campaign-typologies.md) a tua scelta, utilizza **[!UICONTROL Managing affinities with IP addresses]** campo per collegare le consegne al server di consegna (MTA) che gestisce tale affinità. [Ulteriori informazioni](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una volta inviata l’e-mail, controlla l’intestazione per verificare da quale indirizzo IP è stata inviata la consegna. L’amministratore della posta elettronica dovrebbe aiutarti a ottenere le informazioni sull’intestazione.

* Per le consegne SMS, assicurati che il canale SMS abbia un’affinità dedicata limitata a **uno** contenitore server applicazioni. [Ulteriori informazioni](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>La maggior parte di questi passaggi può essere eseguita solo da un utente esperto.

### Utilizzare le tipologie

Puoi utilizzare le regole di tipologia per escludere parte del target in base a criteri specifici. Ciò garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Ad esempio, puoi filtrare i destinatari minorenni dal target della newsletter. Ulteriori informazioni [in questo esempio](../../campaign-opt/using/filtering-rules.md).

### Evita allegati

Gli allegati rimangono uno dei vettori più comuni per la proliferazione di malware, soprattutto quando vengono inviati in massa. Includere un collegamento sicuro al documento invece di allegarlo. Questo garantisce un ulteriore livello di sicurezza per evitare la ridistribuzione involontaria e riduce notevolmente le possibilità che il messaggio venga rifiutato nei gateway e-mail in entrata per motivi di dimensioni o sicurezza.
