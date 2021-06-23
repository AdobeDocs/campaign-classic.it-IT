---
product: campaign
title: Configurazione del test A/B
description: Scopri come configurare il test A/B in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 3%

---

# Configurazione del test A/B {#configuring-a-b-testing}

Questa sezione descrive come creare un flusso di lavoro per eseguire test A/B.

1. Crea un nuovo flusso di lavoro e configura un’attività [Query](../../workflow/using/query.md) per eseguire il targeting della popolazione desiderata.

1. Aggiungi un&#39;attività [Dividi](../../workflow/using/split.md) per suddividere la popolazione target in più sottoinsiemi.

1. Apri l’attività, quindi configura ogni sottoinsieme in base alle tue esigenze. Per ulteriori informazioni su come configurare un&#39;attività **[!UICONTROL Split]**, consulta [questa sezione](../../workflow/using/split.md).

   In questo esempio, vogliamo sottoporre a test 2 nuovi soggetti per una newsletter presentandoli ciascuno al 10% della popolazione target.

   ![](assets/ab-testing-split.png)

1. Aggiungi una transizione per inviare alla popolazione rimanente la newsletter con l’oggetto corrente. A questo scopo, attiva l’opzione **[!UICONTROL Generate complement]** dalla scheda **[!UICONTROL General]** .

   ![](assets/ab-testing-complement.png)

1. Per ogni sottoinsieme, aggiungi la versione della consegna da testare.

   ![](assets/ab-testing-delivery.png)

Ora puoi avviare il flusso di lavoro. Una volta inviate le consegne, potrai tenere traccia del comportamento dei tre sottoinsiemi nei registri di consegna, in modo da individuare l’oggetto che ha avuto maggior successo.

I flussi di lavoro ti consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha ottenuto migliori prestazioni e inviandola alla popolazione rimanente. Per ulteriori informazioni, consulta questo [caso d’uso ](a-b-testing-use-case.md) dedicato.
