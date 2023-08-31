---
product: campaign
title: Introduzione ai test A/B
description: Ulteriori informazioni sui test A/B in Campaign
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---

# Introduzione ai test A/B {#get-started-a-b-testing}


Il test A/B consente di confrontare più versioni di una consegna tra di loro, al fine di identificare quale avrà l’impatto maggiore sulla popolazione target.

A tal fine, devi innanzitutto definire più varianti della consegna. Ogni variante viene quindi inviata a campioni di popolazione per determinare quale funziona meglio a seconda dei criteri scelti (aperture, reclami spam, clic su un collegamento specifico, ecc.).

Nell’esempio seguente, il target di consegna è stato suddiviso in due gruppi, ciascuno dei quali rappresenta il 50% della popolazione target. Ogni gruppo riceve due versioni della consegna con due diverse offerte promozionali. Dopo l’invio della consegna, si conclude che la variante A ha avuto risultati migliori, in base al numero di clic sulle offerte promozionali.

![](assets/a-b-testing-schema.png)

Con Campaign Classic, il test A/B viene implementato tramite flussi di lavoro, in cui si specifica la popolazione di destinazione e i gruppi che riceveranno ogni variante (vedi [Configurazione del test a/b](configuring-a-b-testing.md)).

Le fasi principali sono le seguenti:

1. **Target** popolazione desiderata.
1. **Dividi la popolazione** in sottoinsiemi in cui verranno testate le varianti della consegna.

   Ad esempio, puoi inviare una versione di una consegna a una piccola parte della popolazione target e un’altra versione alla popolazione rimanente. Ciò ti consente di testare una nuova versione di una consegna, anziché la consegna che viene solitamente inviata ai clienti. Puoi anche dividere la popolazione target in 3 gruppi per inviare loro tre versioni diverse di una consegna.

1. **Creare più versioni** della consegna corrispondente a ciascun sottoinsieme. La variante da sottoporre a test può essere l’oggetto, il contenuto del messaggio, il nome del mittente e così via.
1. Avvia il flusso di lavoro, quindi utilizza **registri di consegna** per analizzare il comportamento dei sottoinsiemi con ogni variante.

>[!NOTE]
>
>I flussi di lavoro consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha registrato prestazioni migliori e inviandola alla popolazione rimanente. Per ulteriori informazioni, consulta questa pagina dedicata [caso d’uso](a-b-testing-use-case.md).
