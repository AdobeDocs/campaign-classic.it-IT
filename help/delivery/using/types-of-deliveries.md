---
title: Tipi di consegne
seo-title: Tipi di consegne
description: Tipi di consegne
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Tipi di consegne{#types-of-deliveries}

Campaign dispone di tre tipi di oggetti di consegna:

## Consegna singola {#single-delivery}

Un **recapito** è un oggetto di consegna standalone che viene eseguito una volta. Può essere duplicata, preparata di nuovo, ma finché è nello stato finale (annullato, interrotto, finito), non può essere riutilizzata.

Le consegne possono essere create dall&#39;elenco delle consegne o all&#39;interno di un flusso di lavoro tramite un&#39;attività [Consegna](../../workflow/using/delivery.md) .

I flussi di lavoro forniscono inoltre attività di consegna specifiche in base al tipo di canale che si desidera utilizzare. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## Consegna ricorrente {#recurring-delivery}

Una consegna **** periodica consente di creare una nuova consegna ogni volta che l&#39;attività viene eseguita. In questo modo si evita di dover creare una nuova consegna per le attività ricorrenti.

Ad esempio, se esegui questo tipo di attività una volta al mese, alla fine avrai 12 consegne dopo un anno.

Le consegne ricorrenti vengono create all&#39;interno dei flussi di lavoro tramite l&#39;attività [di consegna](../../workflow/using/recurring-delivery.md)ricorrente. Un esempio di questa attività utilizzata è presentato in questa sezione: [Creazione di una consegna periodica in un flusso di lavoro](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)di targeting.

## Consegna continua {#continuous-delivery}

Una consegna **** continua consente di aggiungere nuovi destinatari a una consegna esistente, evitando di dover creare una nuova consegna ogni volta che viene eseguita.

Se un&#39;informazione nella consegna cambia (contenuto, nome, ecc.), viene creato un nuovo oggetto di consegna al momento dell&#39;esecuzione della consegna. Se non vengono modificate informazioni, lo stesso oggetto di consegna viene riutilizzato e i registri di consegna e tracciamento vengono aggiunti nello stesso oggetto.

Ad esempio, se esegui questo tipo di attività una volta al mese, finirai con un&#39;unica consegna dopo un anno (a condizione che non sia stata apportata alcuna modifica alla consegna).

Le consegne continue vengono create all&#39;interno dei flussi di lavoro tramite l&#39;attività [di consegna](../../workflow/using/continuous-delivery.md)continua.
