---
product: campaign
title: Configurare il test A/B
description: Scopri come configurare il test A/B in Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 3%

---

# Configurare il test A/B {#configuring-a-b-testing}

Questa sezione descrive come creare un flusso di lavoro per eseguire test A/B.

1. Crea un nuovo flusso di lavoro, quindi configura un’attività Query per eseguire il targeting della popolazione desiderata. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=it){target="_blank"}.

1. Aggiungi un’attività Split per suddividere la popolazione target in più sottoinsiemi. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=it){target="_blank"}.

1. Apri l’attività, quindi configura ogni sottoinsieme in base alle tue esigenze. Per ulteriori informazioni su come configurare un&#39;attività **[!UICONTROL Split]**, vedere [questa sezione](../../workflow/using/split.md).

   In questo esempio, vogliamo testare 2 nuovi argomenti per una newsletter presentandoli a ciascuno di loro al 10% della popolazione target.

   ![](assets/ab-testing-split.png)

1. Aggiungi una transizione per inviare alla popolazione rimanente la newsletter con l’oggetto corrente. A tale scopo, attivare l&#39;opzione **[!UICONTROL Generate complement]** dalla scheda **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Per ogni sottoinsieme, aggiungi la versione della consegna da testare.

   ![](assets/ab-testing-delivery.png)

Ora puoi avviare il flusso di lavoro. Una volta inviate le consegne, potrai tenere traccia del comportamento dei tre sottoinsiemi nei registri di consegna, per vedere quale soggetto ha ottenuto il maggior successo.

I flussi di lavoro consentono inoltre di automatizzare i processi identificando automaticamente la variante di consegna che ha registrato prestazioni migliori e inviandola alla popolazione rimanente. Per ulteriori informazioni, consulta questo [caso d&#39;uso](a-b-testing-use-case.md) dedicato.
