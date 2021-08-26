---
product: campaign
title: Principi fondamentali
description: Principi fondamentali
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# Principi fondamentali{#fundamental-principles}

![](../../assets/v7-only.svg)

## Implementazione di ambienti {#deploying-environments}

Esistono due ambienti per ogni dimensione di targeting utilizzata per la gestione delle offerte:

* Un ambiente di progettazione in cui il gestore offerte si occupa di creare e classificare le offerte, modificarle e avviare il processo di approvazione in modo che possano essere utilizzate. In questo ambiente vengono definite anche le regole per ogni categoria, gli spazi di offerta su cui è possibile presentare le offerte e i filtri predefiniti utilizzati per definire l’idoneità di un’offerta.

   Le categorie possono anche essere pubblicate manualmente nell’ambiente online.

   La procedura per l’approvazione delle offerte è descritta nella sezione [Approvazione e attivazione di un’offerta](../../interaction/using/approving-and-activating-an-offer.md) .

* È possibile trovare un ambiente live in cui le offerte approvate dall’ambiente di progettazione, nonché i vari spazi di offerta, filtri, categorie e regole configurati nell’ambiente di progettazione. Durante una chiamata al motore di offerta, il motore utilizzerà sempre le offerte provenienti dall’ambiente live.

Un’offerta viene distribuita solo sugli spazi di offerta selezionati durante il processo di approvazione. Pertanto, un’offerta può essere live ma inutilizzabile su uno spazio di offerta anch’esso attivo.

![](assets/architecture_interaction1.png)

## Tipi di interazione e metodi di contatto {#interaction-types-and-contact-methods}

Esistono due possibili tipi di interazioni: interazioni in entrata (iniziate da un contatto) e interazioni in uscita (iniziate dal creatore di offerte).

Questi due tipi di interazioni possono essere eseguite in modalità unitaria (l&#39;offerta è calcolata per un singolo contatto), o in modalità batch (l&#39;offerta è calcolata per un insieme di contatti). Generalmente, le interazioni in entrata vengono eseguite in modalità unitaria e le interazioni in uscita vengono eseguite in modalità batch. Tuttavia, possono esserci alcune eccezioni, ad esempio per i messaggi transazionali, per cui l&#39;interazione in uscita viene eseguita in modalità unitaria (fare riferimento a [questa sezione](../../message-center/using/about-transactional-messaging.md)).

Non appena un&#39;offerta può o deve essere presentata (secondo le configurazioni effettuate), il motore di offerta svolge il ruolo di intermediario: calcola automaticamente la migliore offerta possibile per un contatto tra quelle disponibili combinando i dati ricevuti sul contatto e le diverse regole che possono essere applicate come specificato nell&#39;applicazione.

![](assets/architecture_interaction2.png)
