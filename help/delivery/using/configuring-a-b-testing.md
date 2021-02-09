---
solution: Campaign Classic
product: campaign
title: Configurazione del test A/B
description: Scoprite come configurare il test A/B in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: a341980e9d940857388bb2755e5eaa74824cf6ea
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# Configurazione test A/B {#configuring-a-b-testing}

In questa sezione viene illustrato come creare un flusso di lavoro per eseguire test A/B.

1. Create un nuovo flusso di lavoro, quindi configurate un&#39;attività [Query](../../workflow/using/query.md) per la popolazione desiderata.

1. Aggiungete un&#39;attività [Split](../../workflow/using/split.md) per dividere la popolazione di destinazione in più sottoinsiemi.

1. Aprite l&#39;attività, quindi configurate ogni sottoinsieme in base alle vostre esigenze. Per ulteriori informazioni su come configurare un&#39;attività **[!UICONTROL Split]**, consultare [questa sezione](../../workflow/using/split.md).

   In questo esempio, vogliamo sottoporre a test 2 nuovi soggetti per una newsletter presentandone ciascuno al 10% della popolazione interessata.

   ![](assets/ab-testing-split.png)

1. Aggiungete una transizione per inviare alla popolazione rimanente la newsletter con l’oggetto corrente. A questo scopo, attivare l&#39;opzione **[!UICONTROL Generate complement]** dalla scheda **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Per ciascun sottoinsieme, aggiungete la versione della consegna da sottoporre a test.

   ![](assets/ab-testing-delivery.png)

Ora puoi avviare il flusso di lavoro. Una volta inviate le consegne, sarà possibile monitorare il comportamento dei tre sottoinsiemi nei registri di consegna, in modo da vedere quale oggetto ha avuto maggior successo.

I flussi di lavoro consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha funzionato meglio e inviarla alla popolazione rimanente. Per ulteriori informazioni, fare riferimento a questo [caso d&#39;uso ](../../delivery/using/a-b-testing-use-case.md) dedicato.
