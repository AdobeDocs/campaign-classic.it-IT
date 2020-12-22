---
solution: Campaign Classic
product: campaign
title: Definire il pubblico adatto
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: fe7ff64d24113e026a47aa1c9f08daacce2b383e
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---


# Definire il pubblico adatto {#define-the-right-audience}

La popolazione mirata è la chiave: create con attenzione gli elenchi, verificate i messaggi e-mail sui client e dispositivi mobili più diffusi e verificate che gli elenchi delle e-mail siano aggiornati (senza indirizzi sconosciuti o obsoleti). È inoltre possibile inviare delle prove che aiutino a configurare un ciclo di convalida completo.

Ulteriori informazioni sulle popolazioni di destinazione [in questa sezione](../../delivery/using/steps-defining-the-target-population.md)

## Esegue il targeting dell&#39;audience giusta {#target-the-right-audience}

Quando il contenuto è pronto, è necessario definire con attenzione chi riceverà il messaggio.

Per garantire il successo della distribuzione, è necessario inviare i contenuti personalizzati più rilevanti ai destinatari giusti.  Adobe Campaign consente di realizzare il target più preciso: potete selezionare i destinatari in base alla loro età, localizzazione, cosa hanno acquistato, se hanno fatto clic su un collegamento in una consegna precedente, ecc. Con  Adobe Campaign, potete anche definire profili di test, gruppi di controllo e indirizzi iniziali per essere certi che la destinazione sia corretta.

## Mappature di destinazione {#target-mappings}

In Campaign Classic, per impostazione predefinita, i modelli di consegna sono destinati ai **Destinatari**.  Adobe Campaign offre altre mappature di destinazione per le consegne, che potete modificare in base alle vostre esigenze.

Ad esempio, potete trasmettere ai visitatori i cui profili sono stati raccolti tramite social network o ai visitatori che hanno sottoscritto un servizio di informazione.

Questi mapping sono presentati [in questa sezione](../../delivery/using/selecting-a-target-mapping.md).

Potete anche creare e utilizzare una mappatura di destinazione personalizzata. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/target-mapping.md).

## Destinatari esterni {#external-recipients}

È possibile inviare i dati ai destinatari memorizzati in un file esterno anziché salvati nel database. Ulteriori informazioni [in questa sezione](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Invia ai tuoi abbonati {#send-to-subscribers}

Per inviare messaggi agli abbonati di una newsletter, potete indirizzare direttamente gli abbonati al servizio di informazioni corrispondente. Ulteriori informazioni [in questa sezione](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Destinatari del test e indirizzi iniziali {#test-recipients-seed-addresses}

Per verificare la consegna, utilizzate le prove prima di inviare alla destinazione principale.

Accertarsi di aver selezionato i destinatari della prova appropriati, in quanto convalidano il modulo e il contenuto del messaggio. I passaggi per definire i destinatari della prova sono presentati [in questa sezione](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Gli indirizzi dei semi vengono utilizzati per i destinatari a cui non corrispondono i criteri di destinazione definiti, al fine di verificare la consegna prima dell&#39;invio alla destinazione principale. Vengono presentati [in questa sezione](../../delivery/using/about-seed-addresses.md).

## Indirizzi di deduplicazione {#deduplicate-addresses}

È importante evitare di avere indirizzi e-mail duplicati, in quanto ciò può avere un impatto sulla destinazione:

* Lo stesso messaggio può essere inviato più volte quando una destinazione viene divisa.

* Se un destinatario annulla la sottoscrizione dopo aver ricevuto un messaggio, il profilo duplicato riceverà comunque messaggi futuri.

Gli indirizzi di deduplicazione proteggono la reputazione dell&#39;invio e garantiscono una buona gestione della quarantena.

**Argomenti correlati:**

* [Attività](../../workflow/using/deduplication.md) di deduplicazione.
* [Caso di utilizzo: Utilizzo della funzionalità di unione dell&#39;attività di deduplicazione](../../workflow/using/deduplication-merge.md)

## Indirizzi e-mail indice {#index-addresses}

Per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione, è possibile dichiarare un indice dall&#39;elemento principale dello schema di dati.

I passaggi per aggiungere un indice all&#39;indirizzo e-mail sono descritti [in questa sezione](../../configuration/using/database-mapping.md#indexed-fields).
