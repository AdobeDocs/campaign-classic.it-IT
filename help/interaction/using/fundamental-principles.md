---
title: Principi fondamentali
seo-title: Principi fondamentali
description: Principi fondamentali
seo-description: null
page-status-flag: never-activated
uuid: 1ed3982b-7f9f-494d-8603-e856859bc31a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 695cf33f-1cc7-4ae8-8ef6-05aa65219411
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---


# Principi fondamentali{#fundamental-principles}

## Implementazione di ambienti {#deploying-environments}

Esistono due ambienti per ciascuna dimensione di targeting utilizzata per gestire le offerte:

* Un ambiente di progettazione in cui il manager dell’offerta si occupa della creazione e classificazione delle offerte, della loro modifica e dell’avvio del processo di approvazione, in modo che possano essere utilizzate. Anche le regole per ciascuna categoria, gli spazi di offerta su cui è possibile presentare le offerte e i filtri predefiniti utilizzati per definire l&#39;idoneità di un&#39;offerta sono definiti in questo ambiente.

   Le categorie possono anche essere pubblicate manualmente nell’ambiente online.

   La procedura di approvazione delle offerte è dettagliata nella sezione [Approvazione e attivazione di un&#39;offerta](../../interaction/using/approving-and-activating-an-offer.md) .

* Un ambiente live in cui le offerte approvate dall&#39;ambiente di progettazione, così come i vari spazi di offerta, filtri, categorie e regole configurati nell&#39;ambiente di progettazione, sono tutti reperibili. Durante una chiamata al motore delle offerte, il motore utilizzerà sempre le offerte dall&#39;ambiente live.

Un&#39;offerta viene distribuita solo sugli spazi di offerta selezionati durante il processo di approvazione. Pertanto, un&#39;offerta può essere live ma inutilizzabile su uno spazio di offerta che è anche live.

![](assets/architecture_interaction1.png)

## Tipi di interazione e metodi di contatto {#interaction-types-and-contact-methods}

Esistono due possibili tipi di interazioni: interazioni in entrata (iniziate da un contatto) e interazioni in uscita (iniziate dal creatore dell&#39;offerta).

Questi due tipi di interazioni possono essere eseguite in modalità unitaria (l&#39;offerta è calcolata per un singolo contatto), o in modalità batch (l&#39;offerta è calcolata per un insieme di contatti). Generalmente, le interazioni in entrata vengono eseguite in modalità unitaria e le interazioni in uscita vengono eseguite in modalità batch. Tuttavia, possono esservi alcune eccezioni, ad esempio per i messaggi transazionali, in cui l&#39;interazione in uscita viene eseguita in modalità unitaria (fare riferimento a [questa sezione](../../message-center/using/about-transactional-messaging.md)).

Non appena un&#39;offerta può o deve essere presentata (secondo le configurazioni effettuate), il motore dell&#39;offerta svolge il ruolo di intermediario: calcola automaticamente la migliore offerta possibile per un contatto tra quelli disponibili combinando i dati ricevuti sul contatto e le diverse regole che possono essere applicate come specificato nell&#39;applicazione.

![](assets/architecture_interaction2.png)

