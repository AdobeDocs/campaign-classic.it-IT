---
solution: Campaign Classic
product: campaign
title: Controllare prima dell’invio
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 4%

---


# Eseguire tutti i controlli prima dell&#39;invio di {#perform-all-checks}

Una volta che il messaggio è pronto, accertati che il contenuto sia visualizzato correttamente, su tutti i dispositivi, e non contenga errori quali personalizzazione errata o collegamenti interrotti.

Prima di inviare il messaggio, assicurati anche che i parametri e la configurazione siano coerenti con la consegna.

## Perché la convalida è la chiave {#validation-is-key}

Prima di inviare una consegna, è necessario assicurarsi che i destinatari ricevano il messaggio che si desidera inviare. A tal fine, devi convalidare il contenuto del messaggio e i parametri di consegna.

Questo passaggio consente di rilevare eventuali errori e correggerli prima di inviarli alla destinazione principale.

I passaggi per la convalida di una consegna sono presentati [in questa sezione](../../delivery/using/steps-validating-the-delivery.md).

## Rendering della casella in entrata {#inbox-and-email-rendering}

Il rendering della casella in entrata consente di visualizzare l&#39;anteprima dei messaggi sui principali client e-mail, acquisire il contenuto e la reputazione, scoprire in che modo i destinatari leggono i messaggi.

**Suggerimenti**:

* Puoi visualizzare il messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto: webmail, servizio messaggi, mobile, ecc.

* Le funzionalità di rendering della inbox sono fondamentali per identificare se le campagne e-mail riescono a superare i filtri dei principali provider di servizi Internet (provider di servizi Internet) e dei servizi di posta elettronica. Tali strumenti inviano una copia pre-verifica di un messaggio e-mail a una rete di caselle in entrata di prova, in modo da visualizzare il modo in cui il messaggio verrà visualizzato, o renderizzato, tra questi servizi. Possono inoltre includere rapporti e opzioni di correzione del codice che consentono di identificare e correggere rapidamente i problemi di recapito.

Ulteriori informazioni [in questa sezione](../../delivery/using/inbox-rendering.md).

## Messaggi di prova {#proof-messages}

L&#39;invio di prove consente di controllare il collegamento di rinuncia, la pagina mirror e qualsiasi altro collegamento, convalidare il messaggio, verificare che le immagini siano visualizzate, rilevare eventuali errori, ecc. È inoltre possibile controllare la progettazione e il rendering su diversi dispositivi.

Ulteriori informazioni [in questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Configurare le consegne di test A/B {#a-b-testing-deliveries}

Se disponete di diversi contenuti per la consegna delle e-mail, potete utilizzare il test A/B per scoprire quale versione avrà il maggiore impatto sulla popolazione interessata.

**Suggerimenti**:

* Inviare le diverse versioni ad alcuni dei destinatari

* Seleziona quella con il tasso di successo più elevato e inviala al resto della destinazione

Ulteriori informazioni [in questa sezione](../../workflow/using/a-b-testing.md).

## Assicurati che il messaggio sia stato inviato {#make-sure-your-message-is-delivered}

Come ultimo passo, massimizza le tue possibilità e sfrutta la potenza di Adobe Campaign Classic per garantire che il messaggio venga effettivamente recapitato ai destinatari interessati.

### Procedura di convalida

È possibile definire un processo di convalida completo, che coinvolga  operatori e gruppi Adobe Campaign, per convalidare sia la destinazione che il contenuto del messaggio. Ciò garantirà il pieno monitoraggio e controllo dei vari processi della campagna: targeting, contenuto, budget, estrazione e invio di una prova. A seconda delle autorizzazioni assegnate, gli utenti riceveranno una notifica, riceveranno prove di validità e potranno convalidare o rifiutare il messaggio. Ulteriori informazioni [in questa sezione](../../campaign/using/marketing-campaign-approval.md#approval-process).

### Usa onde

Potete aumentare progressivamente il volume inviato utilizzando le onde. In questo modo i messaggi non verranno contrassegnati come spam o se si desidera limitare il numero di messaggi al giorno. Utilizzando le onde è possibile dividere le consegne in più batch anziché inviare contemporaneamente volumi elevati di messaggi. Ulteriori informazioni [in questa sezione](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Priorità dei messaggi

È possibile impostare l&#39;ordine di invio per le consegne specificando il livello di priorità. Per eseguire questa operazione:

1. Modificate le proprietà di consegna e selezionate la scheda **[!UICONTROL Delivery]**.

1. Definire il livello di priorità per la consegna su una scala da **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>Non è possibile definire l&#39;ordine di invio dei messaggi dall&#39;interno di una consegna.

### Impostazione delle affinità IP

Per controllare meglio il traffico SMTP in uscita, puoi gestire le affinità definendo quali indirizzi IP specifici possono essere utilizzati per ogni affinità. Questo consente di limitare il numero di e-mail per consegne specifiche verso computer o indirizzi di output. Ad esempio, è possibile utilizzare un&#39;affinità per paese o sottodominio. Potete quindi creare una tipologia per paese e collegare ciascuna affinità alla tipologia corrispondente.

Puoi:

* Definite le affinità IP nel file di configurazione serverConf.xml. [Ulteriori informazioni](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Per ciascun elemento IPAffinity, dichiarare gli indirizzi IP che possono essere utilizzati. [Ulteriori informazioni](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Nella [tipologia](../../campaign/using/about-campaign-typologies.md) di tua scelta, utilizza il campo **[!UICONTROL Managing affinities with IP addresses]** per collegare le consegne al server di consegna (MTA) che gestisce tale affinità. [Ulteriori informazioni](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una volta inviato il messaggio e-mail, controllate l&#39;intestazione per verificare da quale indirizzo IP è stato inviato il messaggio. L’amministratore dell’e-mail deve essere in grado di ottenere le informazioni di intestazione.

>[!NOTE]
>
>La maggior parte di questi passaggi può essere eseguita solo da un utente esperto.

### Utilizzare le tipologie

Potete utilizzare le regole di tipologia per escludere parte della destinazione in base a criteri specifici. Ciò garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Ad esempio, potete filtrare i destinatari meno recenti dalla destinazione della newsletter. Ulteriori informazioni [in questo esempio](../../campaign/using/filtering-rules.md).

### Evitare gli allegati

Gli allegati rimangono uno dei vettori più comuni per la proliferazione di malware, soprattutto quando sono inviati in massa. Includete un collegamento protetto al documento invece di allegarlo. Questo garantisce un ulteriore livello di sicurezza per impedire la ridistribuzione indesiderata e riduce notevolmente le possibilità che il messaggio venga rifiutato nei gateway e-mail in ingresso per motivi di dimensione o sicurezza del messaggio.
