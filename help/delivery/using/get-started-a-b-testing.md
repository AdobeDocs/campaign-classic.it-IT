---
solution: Campaign Classic
product: campaign
title: Introduzione ai test A/B
description: Ulteriori informazioni sui test A/B in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Introduzione ai test A/B {#get-started-a-b-testing}

I test A/B consentono di confrontare più versioni di una distribuzione tra loro, al fine di identificare quale avrà il maggiore impatto sulla popolazione interessata.

A questo scopo, è innanzitutto necessario definire più varianti della consegna. Ogni variante viene quindi inviata a campioni di popolazione per determinare quale funziona meglio a seconda dei criteri di scelta (aperture, spam reclami, clic su un collegamento specifico, ...).

Nell&#39;esempio seguente, la destinazione di consegna è stata suddivisa in due gruppi, ciascuno dei quali rappresenta il 50% della popolazione mirata. Ogni gruppo riceve due versioni della consegna con due diverse offerte promozionali. Dopo l&#39;invio, si conclude che la variante A è stata eseguita meglio, in base al numero di clic sulle offerte promozionali.

![](assets/a-b-testing-schema.png)

Con i Campaign Classic, i test A/B vengono implementati tramite flussi di lavoro, in cui è possibile specificare la popolazione di destinazione e i gruppi che riceveranno ciascuna variante (vedere [Configurazione dei test a/b](../../delivery/using/configuring-a-b-testing.md)).

Le fasi principali sono:

1. **Si** rivolge alla popolazione desiderata.
1. **Dividere la** popolazione in sottoinsiemi su cui verranno testate le varianti della consegna.

   Ad esempio, potete inviare una versione di una consegna a una piccola parte della popolazione di destinazione e un&#39;altra versione alla popolazione rimanente. Questo consente di testare una nuova versione di una consegna invece della consegna che viene solitamente inviata ai clienti. Potete anche dividere la popolazione di destinazione in 3 gruppi per inviarli tre diverse versioni di una consegna.

1. **Create più** versioni della consegna corrispondente a ciascun sottoinsieme. La variante da verificare può essere l&#39;oggetto, il contenuto del messaggio, il nome del mittente e così via.
1. Avviate il flusso di lavoro, quindi utilizzate i **log di consegna** per analizzare il comportamento dei sottoinsiemi con ciascuna variante.

>[!NOTE]
>
>I flussi di lavoro consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha funzionato meglio e inviarla alla popolazione rimanente. Per ulteriori informazioni, fare riferimento a questo [caso d&#39;uso ](../../delivery/using/a-b-testing-use-case.md) dedicato.
