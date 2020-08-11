---
title: Punti chiave per la gestione della recapito in Adobe Campaign Classic
description: Quali sono i punti chiave da verificare nella gestione della recapito in Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 24d2dded38ddb922891a7264d9efea02cb448323
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---


# Punti chiave della realizzazione{#deliverability-key-points}

Per ottimizzare la recapito dei messaggi e-mail di  Adobe Campaign, si consiglia di utilizzare le procedure ottimali elencate di seguito. I problemi di recapito sono generalmente legati alle misure di protezione contro lo spam attuate dai provider di servizi Internet e dagli amministratori dei server di posta elettronica.

**Per &quot;recapito** e-mail&quot; si intende l&#39;insieme di caratteristiche che determinano la capacità di un messaggio di raggiungere la sua destinazione, tramite un indirizzo e-mail personale, entro breve tempo, e con la qualità prevista in termini di contenuto e formato.

Queste caratteristiche sono suddivise in quattro categorie principali:
* Qualità dei dati
* Messaggio e contenuto
* Invio dell&#39;infrastruttura
* Reputazione

Insieme, costituiscono la base di un programma di recapito e-mail di successo.

Il tasso **di** recapito corrisponde al numero di messaggi e-mail inviati correttamente ai destinatari.

Il tasso di recapito dipende da numerosi fattori, in particolare:
* Configurazione corretta delle istanze
* La reputazione del tuo indirizzo IP
* Qualità degli indirizzi interessati
* Bassi reclami e tassi di rimbalzo
* Contenuto del messaggio
* Autenticazione dei messaggi (SPF, DKIM, DMARC)
* reputazione mittente

Di seguito è riportato un elenco dei punti chiave da verificare per garantire una buona consegna.

## Controllare la configurazione di rete {#network-configuration}

Gli spammer cercano di nascondere la loro identità reale e di conseguenza rendono i loro server difficili da identificare. Una configurazione di rete legittima che non tenti di nascondere l&#39;identità del server è essenziale per inviare e-mail in grandi volumi.

## Invia a indirizzi validi {#valid-addresses}

Gli spammer usano spesso generatori di indirizzi basati su elenchi di nomi e nomi frequenti; inoltre, raramente elaborano le notifiche tecniche inviate dai server di posta. Un elevato numero di indirizzi non validi viene spesso interpretato come un segno di spam. I meccanismi di doppio consenso e l&#39;efficace gestione dei messaggi tecnici di rimbalzo consentono di evitare questo problema.

## Riduzione di reclami e tassi di rimbalzo {#reduce-complaint-rates}

Gli ISP solitamente dispongono di uno strumento importante per segnalare un messaggio ricevuto come spam. Questo permette di identificare fonti inaffidabili. Soddisfacendo rapidamente le richieste di rifiuto, utilizzando regolarmente un determinato elenco, verificando il consenso tramite un sistema di doppio consenso e implementando i cicli di feedback, potete ridurre le tariffe dei reclami.

## Invia agli indirizzi delle melanzane {#honeypot-addresses}

ISP e altre organizzazioni (vedere il sito web [Project Honey Pot](https://www.projecthoneypot.org/) ) fanno uso di cassette postali che non corrispondono a persone fisiche ma sono create semplicemente per ingannare gli spammer. Questi cosiddetti indirizzi &quot;vaso di miele&quot; sono pubblicati sul Web per essere raccolti dagli spambots e quindi catturare mittenti illegittimi. L&#39;uso di un doppio meccanismo di opt-in impedisce l&#39;aggiunta di questo tipo di indirizzo a un elenco. Quando si utilizza un elenco di terze parti, è necessario essere certi dei metodi utilizzati dal relativo manutentore.

## Adatta il contenuto del messaggio {#message-content}

In misura minore, il contenuto di alcuni messaggi può portare alcuni filtri per rilevarlo come spam. L&#39;uso di determinate parole, l&#39;uso di punti esclamativi nella riga dell&#39;oggetto e all&#39;interno dei messaggi sono letti come segni di spam. È noto che gli spammers sostituiscono il testo con le immagini per evitare che il testo offensivo venga analizzato automaticamente dai filtri anti-spam. In risposta a ciò, un messaggio (in formato HTML) con un&#39;elevata percentuale di immagini, o immagini come allegati, potrebbe finire per essere bloccato.

## Lavora sulla tua reputazione {#reputation}

Gli spammer fanno consegne programmate per mantenere la loro reputazione nel tempo. A volte devono adattare il piano di marketing per soddisfare le migliori pratiche imposte dai provider di servizi Internet e quindi, dopo un picco di reputazione (accelerazione), configurano consegne regolari.

## Best practice {#best-practices}

Scopri le best practice relative alla recapito dei contenuti con  Adobe Campaign. Utilizzate i collegamenti di seguito per navigare tra gli argomenti e trovare istruzioni.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="Inizio" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>Inizio</strong>
    </a>
    </div>
    <p>
    <em>Avvio di una nuova piattaforma</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="Progettazione" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>Progettazione</strong>
    </a>
    </div>
    <p>
    <em>Controllo del contenuto dei messaggi</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="Progettazione" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>Invia</strong>
    </a>
    </div>
    <p>
    <em>Migliorare la tua reputazione</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="Ottimizza" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>Ottimizza</strong>
    </a>
    </div>
    <p>
    <em>Raccomandazioni tecniche</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="Controlla" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>Monitor</strong>
    </a>
    </div>
    <p>
    <em>Strumenti di monitoraggio</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="Ottimizza" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>Risoluzione dei problemi</strong>
    </a>
    </div>
    <p>
    <em>Risolvere i problemi</em>
    <p>
  </td>
</tr>
</table>
