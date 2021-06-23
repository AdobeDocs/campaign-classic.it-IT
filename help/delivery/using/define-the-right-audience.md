---
product: campaign
title: Definire il pubblico adatto
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---

# Definire il pubblico adatto {#define-the-right-audience}

La popolazione mirata è la chiave: crea gli elenchi con attenzione, verifica le e-mail sui client e-mail e sui dispositivi mobili più diffusi e assicurati che gli elenchi e-mail siano aggiornati (senza indirizzi sconosciuti o obsoleti). È inoltre possibile inviare bozze che consentono di impostare un ciclo di convalida completo.

Ulteriori informazioni sulle popolazioni target [in questa sezione](steps-defining-the-target-population.md)

## Eseguire il targeting del pubblico giusto {#target-the-right-audience}

Quando il contenuto è pronto, è necessario definire attentamente chi riceverà il messaggio.

Per garantire il successo della consegna, devi inviare i contenuti personalizzati più rilevanti ai destinatari giusti. Adobe Campaign consente di creare il target più preciso: puoi selezionare i destinatari in base alla loro età, localizzazione, cosa hanno acquistato, se hanno fatto clic su un collegamento in una consegna precedente, ecc. Con Adobe Campaign puoi anche definire profili di test, gruppi di controllo e indirizzi di seed per assicurarti che il target sia corretto.

## Mappature di Target {#target-mappings}

In Campaign Classic, per impostazione predefinita, i modelli di consegna sono destinati a **Destinatari**. Adobe Campaign offre altre mappature di destinazione per le consegne, che puoi modificare in base alle tue esigenze.

Ad esempio, puoi consegnare ai visitatori i cui profili sono stati raccolti tramite social network o ai visitatori abbonati a un servizio di informazione.

Queste mappature sono presentate [in questa sezione](selecting-a-target-mapping.md).

Puoi anche creare e utilizzare una mappatura di destinazione personalizzata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/target-mapping.md).

## Destinatari esterni {#external-recipients}

Puoi inviare messaggi ai destinatari memorizzati in un file esterno anziché in un database. Ulteriori informazioni [in questa sezione](steps-defining-the-target-population.md#selecting-external-recipients).

## Invia ai tuoi abbonati {#send-to-subscribers}

Per inviare messaggi agli abbonati di una newsletter, potete eseguire il targeting diretto degli abbonati al servizio di informazioni corrispondente. Ulteriori informazioni [in questa sezione](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Destinatari del test e indirizzi di seed {#test-recipients-seed-addresses}

Per verificare la consegna, utilizza le bozze prima di inviare al target principale.

Assicurati di selezionare i destinatari della bozza appropriati, in quanto convalidano il modulo e il contenuto del messaggio. I passaggi per la definizione dei destinatari della bozza sono descritti [in questa sezione](steps-defining-the-target-population.md#selecting-the-proof-target).

Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non soddisfano i criteri di target definiti al fine di testare una consegna prima di inviarla al target principale. Vengono presentati [in questa sezione](about-seed-addresses.md).

## Indirizzi duplicati {#deduplicate-addresses}

È importante evitare di duplicare gli indirizzi e-mail, perché questo può avere un impatto sul target:

* Lo stesso messaggio può essere inviato più volte quando una destinazione viene suddivisa.

* Se un destinatario annulla l’abbonamento dopo aver ricevuto un messaggio, il suo profilo duplicato riceverà comunque messaggi futuri.

La deduplicazione degli indirizzi protegge la reputazione dell’invio e garantisce una buona gestione della quarantena.

**Argomenti correlati:**

* [Attività di deduplicazione](../../workflow/using/deduplication.md).
* [Caso di utilizzo: Utilizzo della funzionalità di unione dell’attività Deduplication](../../workflow/using/deduplication-merge.md)

## Indirizzi e-mail di indice {#index-addresses}

Per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione, è possibile dichiarare un indice dall&#39;elemento principale dello schema dati.

I passaggi per aggiungere un indice all&#39;indirizzo e-mail sono descritti [in questa sezione](../../configuration/using/database-mapping.md#indexed-fields).
