---
product: campaign
title: Principi fondamentali
description: Principi fondamentali
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 3%

---

# Principi fondamentali{#fundamental-principles}



## Distribuzione di ambienti {#deploying-environments}

Esistono due ambienti per ogni dimensione di targeting utilizzata durante la gestione delle offerte:

* Un ambiente di progettazione in cui il gestore delle offerte si occupa di creare e classificare le offerte, modificarle e avviare il processo di approvazione in modo che possano essere utilizzate. In questo ambiente sono definite anche le regole per ogni categoria, gli spazi di offerta su cui possono essere presentate le offerte e i filtri predefiniti utilizzati per definire l’idoneità di un’offerta.

  Le categorie possono inoltre essere pubblicate manualmente nell&#39;ambiente online.

  Il processo di approvazione delle offerte è descritto nel [Approvazione e attivazione di un’offerta](../../interaction/using/approving-and-activating-an-offer.md) sezione.

* Ambiente live in cui sono disponibili offerte approvate dall’ambiente di progettazione, nonché vari spazi di offerta, filtri, categorie e regole configurati nell’ambiente di progettazione. Durante una chiamata al motore di offerta, il motore utilizzerà sempre le offerte dell’ambiente live.

Un’offerta viene distribuita solo sugli spazi dell’offerta selezionati durante il processo di approvazione. Pertanto, un’offerta può essere live ma inutilizzabile in uno spazio dell’offerta che è anche live.

![](assets/architecture_interaction1.png)

## Tipi di interazione e metodi di contatto {#interaction-types-and-contact-methods}

Esistono due possibili tipi di interazioni: le interazioni in entrata (avviate da un contatto) e le interazioni in uscita (avviate dal designer dell’offerta).

Questi due tipi di interazioni possono essere eseguiti in modalità unitaria (l’offerta viene calcolata per un singolo contatto) o in modalità batch (l’offerta viene calcolata per un insieme di contatti). In genere, le interazioni in entrata vengono eseguite in modalità unitaria, mentre le interazioni in uscita vengono eseguite in modalità batch. Tuttavia, possono esserci alcune eccezioni, ad esempio per i messaggi transazionali, in cui l’interazione in uscita viene eseguita in modalità unitaria (fare riferimento a [questa sezione](../../message-center/using/about-transactional-messaging.md)).

Non appena un’offerta può o deve essere presentata (in base alle configurazioni effettuate), il motore di offerta svolge il ruolo di intermediario: calcola automaticamente la migliore offerta possibile per un contatto tra quelli disponibili combinando i dati ricevuti sul contatto e le diverse regole che possono essere applicate come specificato nell’applicazione.

![](assets/architecture_interaction2.png)
