---
product: campaign
title: Introduzione ai test A/B
description: Ulteriori informazioni sui test A/B in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 3%

---

# Introduzione ai test A/B {#get-started-a-b-testing}

Il test A/B ti consente di confrontare più versioni di una consegna rispetto alle altre, per identificare quale avrà il maggiore impatto sulla popolazione target.

A questo scopo, devi innanzitutto definire più varianti della consegna. Ogni variante viene quindi inviata a campioni di popolazione per determinare quale funziona meglio a seconda dei criteri scelti (aperture, reclami di spam, clic su un collegamento specifico, ...).

Nell’esempio seguente, il target di consegna è stato suddiviso in due gruppi, ciascuno dei quali rappresenta il 50% della popolazione target. Ogni gruppo riceve due versioni della consegna con due diverse offerte promozionali. Dopo l’invio della consegna, si conclude che la variante A ha ottenuto risultati migliori, in base al numero di clic sulle offerte promozionali.

![](assets/a-b-testing-schema.png)

Con Campaign Classic, i test A/B vengono implementati tramite flussi di lavoro, in cui è possibile specificare il gruppo di destinazione e i gruppi che riceveranno ogni variante (consulta [Configurazione dei test a/b](configuring-a-b-testing.md)).

Le fasi principali sono:

1. **** Esegue il targeting della popolazione desiderata.
1. **Dividi la** popolazione in sottoinsiemi in cui testerai le varianti della consegna.

   Ad esempio, puoi inviare una versione di una consegna a una piccola parte della popolazione target e un’altra versione alla popolazione rimanente. Ciò ti consente di testare una nuova versione di una consegna rispetto alla consegna che di solito viene inviata ai clienti. Puoi anche dividere la popolazione target in 3 gruppi per inviare loro tre diverse versioni di una consegna.

1. **Crea più** versioni della consegna corrispondenti a ciascun sottoinsieme. La variante da testare può essere l’oggetto, il contenuto del messaggio, il nome del mittente e così via.
1. Avvia il flusso di lavoro, quindi utilizza i **registri di consegna** per analizzare il comportamento dei sottoinsiemi con ogni variante.

>[!NOTE]
>
>I flussi di lavoro ti consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha ottenuto migliori prestazioni e inviandola alla popolazione rimanente. Per ulteriori informazioni, consulta questo [caso d’uso ](a-b-testing-use-case.md) dedicato.
