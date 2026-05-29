---
product: campaign
title: Controllare prima dell’invio
description: Quando il messaggio è pronto, esegui tutti i controlli prima di inviarlo
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
hide: true
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
TQID: https://experienceleague.adobe.com/ngnYPos--1A5p7WN-fJnxaLt-yHG50lWHid4wbbyVZw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 904
ht-degree: 4%

---

# Esegui tutti i controlli prima dell’invio {#perform-all-checks}

Quando il messaggio è pronto, accertati che il suo contenuto sia visualizzato correttamente, su tutti i dispositivi, e non contenga errori quali personalizzazione errata o collegamenti interrotti.

Prima di inviare il messaggio, assicurati anche che i parametri e la configurazione siano coerenti con la consegna.

## Perché la convalida è fondamentale {#validation-is-key}

Prima di inviare una consegna, è necessario assicurarsi che i destinatari ricevano il messaggio che si desidera veramente inviare. A questo scopo, devi convalidare il contenuto del messaggio e i parametri di consegna.

Questo passaggio ti consente di rilevare eventuali errori e correggerli prima di consegnarli al target principale.

I passaggi per la convalida di una consegna sono descritti [in questa sezione](steps-validating-the-delivery.md).

## Rendering della casella in entrata {#inbox-and-email-rendering}

Il rendering della casella in entrata consente di visualizzare in anteprima i messaggi sui principali client e-mail, esaminare il contenuto e la reputazione e scoprire come i destinatari leggono i messaggi.

**suggerimenti**:

* Puoi visualizzare il messaggio inviato nei diversi contesti in cui può essere ricevuto: posta sul web, servizio messaggi, dispositivi mobili, ecc.

* Le funzionalità di rendering della casella in entrata sono fondamentali per identificare se le campagne e-mail sono riuscite a superare i filtri dei principali ISP (provider di servizi Internet) e servizi di posta sul web. Tali strumenti inviano una copia pre-volo di un’e-mail a una rete di caselle in entrata di prova, in modo da poter vedere come verrà visualizzato il messaggio o come verrà eseguito il rendering tra questi servizi. Possono inoltre includere rapporti e opzioni di correzione del codice che consentono di identificare rapidamente e apportare correzioni che migliorano il recapito messaggi.

Per ulteriori informazioni, consulta [questa sezione](inbox-rendering.md).

## Messaggi di bozza {#proof-messages}

L’invio di bozze ti consente di controllare il collegamento di rinuncia, la pagina speculare e tutti gli altri collegamenti, convalidare il messaggio, verificare che siano visualizzate le immagini, rilevare eventuali errori, ecc. Puoi anche controllare la progettazione e il rendering su dispositivi diversi.

Per ulteriori informazioni, consulta [questa sezione](steps-validating-the-delivery.md#sending-a-proof).

## Configurare le consegne dei test A/B {#a-b-testing-deliveries}

Se disponi di diversi contenuti per una consegna e-mail, puoi utilizzare il test A/B per individuare la versione che avrà l’impatto maggiore sulla popolazione target.

**suggerimenti**:

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

1. Modificare le proprietà di consegna e selezionare la scheda **[!UICONTROL Delivery]**.

1. Definisci il livello di priorità per la consegna su una scala da **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>Non è possibile definire l’ordine di invio dei messaggi da una consegna.

### Configurare le affinità IP

Per controllare meglio il traffico SMTP in uscita, puoi gestire le affinità definendo quali indirizzi IP specifici possono essere utilizzati per ogni affinità. Questo ti consente di limitare il numero di e-mail per consegne specifiche a computer o indirizzi di output. Ad esempio, puoi utilizzare un’affinità per paese o sottodominio. Puoi quindi creare una tipologia per paese e collegare ogni affinità alla tipologia corrispondente.

Puoi eseguire le seguenti azioni:

* Definisci le affinità IP nel file di configurazione serverConf.xml. [Ulteriori informazioni](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Per ogni elemento IPAfinity, dichiarare gli indirizzi IP che è possibile utilizzare. [Ulteriori informazioni](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Nella [tipologia](../../campaign-opt/using/about-campaign-typologies.md) scelta, utilizza il campo **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne al server di consegna (MTA) che gestisce tale affinità. [Ulteriori informazioni](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una volta inviata l’e-mail, controlla l’intestazione per verificare da quale indirizzo IP è stata inviata la consegna. L’amministratore della posta elettronica dovrebbe aiutarti a ottenere le informazioni sull’intestazione.

* Per le consegne SMS, assicurati che il canale SMS abbia un&#39;affinità dedicata limitata al contenitore del server applicazioni **one**. [Ulteriori informazioni](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>La maggior parte di questi passaggi può essere eseguita solo da un utente esperto.

### Utilizzare le tipologie

Puoi utilizzare le regole di tipologia per escludere parte del target in base a criteri specifici. Ciò garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Ad esempio, puoi filtrare i destinatari minorenni dal target della newsletter. Ulteriori informazioni [in questo esempio](../../campaign-opt/using/filtering-rules.md).

### Evita allegati

Gli allegati rimangono uno dei vettori più comuni per la proliferazione di malware, soprattutto quando vengono inviati in massa. Includere un collegamento sicuro al documento invece di allegarlo. Questo garantisce un ulteriore livello di sicurezza per evitare la ridistribuzione involontaria e riduce notevolmente le possibilità che il messaggio venga rifiutato nei gateway e-mail in entrata per motivi di dimensioni o sicurezza.
