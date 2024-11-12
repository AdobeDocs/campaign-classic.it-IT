---
product: campaign
title: Definire il pubblico adatto
description: Scopri le best practice per la selezione del pubblico
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Audiences
role: User
hide: true
hidefromtoc: true
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 6%

---

# Definire il pubblico adatto {#define-the-right-audience}

La popolazione target è fondamentale: crea i tuoi elenchi con attenzione, testa le e-mail sui client e-mail e sui dispositivi mobili più diffusi e assicurati che i tuoi elenchi e-mail siano aggiornati (senza indirizzi sconosciuti o obsoleti). Puoi anche inviare bozze utili per impostare un ciclo di convalida completo.

Ulteriori informazioni sulle popolazioni di destinazione [in questa sezione](steps-defining-the-target-population.md)

## Rivolgersi al pubblico giusto {#target-the-right-audience}

Quando il contenuto è pronto, è necessario definire con attenzione chi riceverà il messaggio.

Per garantire la corretta consegna, desideri inviare i contenuti personalizzati più rilevanti ai destinatari giusti. Adobe Campaign ti consente di creare il target più preciso: puoi selezionare i destinatari in base all’età, alla localizzazione, a cosa hanno acquistato, se hanno fatto clic su un collegamento in una consegna precedente, ecc. Con Adobe Campaign, puoi anche definire profili di test, gruppi di controllo e indirizzi di seed per assicurarti che il target sia corretto.

## Mappature di destinazione {#target-mappings}

In Campaign Classic, per impostazione predefinita, i modelli di consegna sono destinati a **destinatari**. Adobe Campaign offre altre mappature di destinazione per le consegne, che puoi modificare in base alle tue esigenze.

Ad esempio, puoi distribuire ai visitatori i cui profili sono stati raccolti tramite social network o ai visitatori abbonati a un servizio di informazioni.

Queste mappature sono presentate [in questa sezione](selecting-a-target-mapping.md).

Puoi anche creare e utilizzare una mappatura di destinazione personalizzata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/target-mapping.md).

## Destinatari esterni {#external-recipients}

Puoi consegnare a destinatari memorizzati in un file esterno anziché salvati nel database. Per ulteriori informazioni, consulta [questa sezione](steps-defining-the-target-population.md#selecting-external-recipients).

## Invia ai tuoi abbonati {#send-to-subscribers}

Per inviare messaggi agli abbonati di una newsletter, puoi indirizzare direttamente questi ultimi al servizio di informazioni corrispondente. Per ulteriori informazioni, consulta [questa sezione](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Destinatari di test e indirizzi seed {#test-recipients-seed-addresses}

Per verificare la consegna, utilizza le bozze prima di inviare al target principale.

Accertati di selezionare i destinatari della bozza appropriati, in quanto convalidano il modulo e il contenuto del messaggio. I passaggi per definire i destinatari della bozza sono descritti in [questa sezione](steps-defining-the-target-population.md#selecting-the-proof-target).

Gli indirizzi di seed vengono utilizzati per eseguire il targeting dei destinatari che non corrispondono ai criteri di target definiti per testare una consegna prima di inviarla al target principale. Sono presentati [in questa sezione](about-seed-addresses.md).

## Deduplica indirizzi {#deduplicate-addresses}

È importante evitare di avere indirizzi e-mail duplicati, perché questo può avere un impatto sul target:

* Lo stesso messaggio può essere inviato più di una volta quando una destinazione viene divisa.

* Se un destinatario annulla l’iscrizione dopo aver ricevuto un messaggio, il suo profilo duplicato riceverà comunque messaggi futuri.

La deduplicazione degli indirizzi protegge la reputazione del mittente e garantisce una buona gestione della quarantena.

**Argomenti correlati:**

* [Attività di deduplicazione](../../workflow/using/deduplication.md).
* [Caso d’uso: utilizzo della funzionalità di unione dell’attività Deduplicazione](../../workflow/using/deduplication-merge.md)

## Indicizzare gli indirizzi e-mail {#index-addresses}

Per ottimizzare le prestazioni delle query SQL utilizzate nell’applicazione, è possibile dichiarare un indice dall’elemento principale dello schema di dati.

I passaggi per aggiungere un indice all&#39;indirizzo e-mail sono descritti in [questa sezione](../../configuration/using/database-mapping.md#indexed-fields).
