---
product: campaign
title: Configurare il test A/B
description: Scopri come configurare il test A/B in Campaign Classic.
feature: A/B Testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 3%

---

# Configurare il test A/B {#configuring-a-b-testing}

![](../../assets/common.svg)

Questa sezione descrive come creare un flusso di lavoro per eseguire test A/B.

1. Crea un nuovo flusso di lavoro e configura un [Query](../../workflow/using/query.md) attività per indirizzare la popolazione desiderata.

1. Aggiungi un [Divisione](../../workflow/using/split.md) attività per dividere la popolazione target in più sottoinsiemi.

1. Apri l’attività, quindi configura ogni sottoinsieme in base alle tue esigenze. Per ulteriori informazioni su come configurare un **[!UICONTROL Split]** attività, fai riferimento a [questa sezione](../../workflow/using/split.md).

   In questo esempio, vogliamo sottoporre a test 2 nuovi soggetti per una newsletter presentandoli ciascuno al 10% della popolazione target.

   ![](assets/ab-testing-split.png)

1. Aggiungi una transizione per inviare alla popolazione rimanente la newsletter con l’oggetto corrente. Per eseguire questa operazione, attiva il **[!UICONTROL Generate complement]** dall&#39;opzione **[!UICONTROL General]** scheda .

   ![](assets/ab-testing-complement.png)

1. Per ogni sottoinsieme, aggiungi la versione della consegna da testare.

   ![](assets/ab-testing-delivery.png)

Ora puoi avviare il flusso di lavoro. Una volta inviate le consegne, potrai tenere traccia del comportamento dei tre sottoinsiemi nei registri di consegna, in modo da individuare l’oggetto che ha avuto maggior successo.

I flussi di lavoro ti consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha ottenuto migliori prestazioni e inviandola alla popolazione rimanente. Per ulteriori informazioni, consulta questa sezione dedicata [caso d&#39;uso](a-b-testing-use-case.md).
