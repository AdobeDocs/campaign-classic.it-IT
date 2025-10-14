---
product: campaign
title: Interazioni anonime
description: Interazioni anonime
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 1%

---

# Interazioni anonime{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) Guarda questo [video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) per una panoramica sul modo in cui le offerte vengono distribuite a destinazioni identificate e anonime.

## Targeting e archiviazione di un ambiente per interazioni anonime {#targeting-and-storing-an-environment-for-anonymous-interactions}

Per impostazione predefinita, Interaction viene fornito con un ambiente preconfigurato per eseguire il targeting della tabella dei destinatari (offerte identificate). Se desideri eseguire il targeting per un’altra tabella (tabella dei visitatori per le offerte anonime o una tabella dei destinatari specifica), utilizza l’assistente alla mappatura di destinazione per creare l’ambiente. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Quando si crea un ambiente anonimo tramite l&#39;Assistente alla creazione della mappatura, la casella **[!UICONTROL Environment dedicated to incoming anonymous interactions]** viene selezionata automaticamente nella scheda **[!UICONTROL General]** dell&#39;ambiente.

**[!UICONTROL Targeting dimension]** è completato automaticamente. Per impostazione predefinita, si collega alla tabella dei visitatori.

Viene visualizzato il campo **[!UICONTROL Visitor folder]**. Il collegamento alla cartella **[!UICONTROL Visitors]** viene completato automaticamente. Questo campo consente di scegliere dove memorizzare i profili dei visitatori.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Se desideri filtrare diversi tipi di visitatori, ad esempio nel caso di offerte anonime presentate per uno o più marchi, devi creare un ambiente per ogni marchio e una cartella di tipo **[!UICONTROL Visitors]** per ogni ambiente.

## Catalogo delle offerte per interazioni anonime {#offer-catalog-for-anonymous-interactions}

Proprio come le interazioni in uscita, le interazioni in entrata sono organizzate in un catalogo di offerte composto da categorie e offerte.

Per creare categorie e spazi, applica lo stesso processo dei visitatori identificati (consulta [Creazione di categorie di offerta](../../interaction/using/creating-offer-categories.md) e [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Visitatori anonimi {#anonymous-visitors}

I visitatori anonimi possono essere sottoposti a un processo di identificazione dei cookie durante la connessione. Questo riconoscimento implicito si basa sulla cronologia del browser del visitatore.

Durante questo passaggio, viene effettuato un confronto tra i dati recuperati dai cookie e quelli presenti nel database. In alcuni casi, i visitatori vengono riconosciuti (vengono quindi implicitamente identificati), in altri, non vengono riconosciuti (e quindi rimangono anonimi).

Per eseguire questa analisi, per lo spazio dell&#39;offerta selezionare l&#39;opzione **[!UICONTROL Implicitly identify the individual based on their browser history]**.

![](assets/identification_anonymous_visitors.png)

## Elaborazione di visitatori anonimi non identificati {#processing-unidentified-anonymous-visitors}

Dopo l’analisi, se un visitatore anonimo non viene identificato, puoi memorizzarne i dati in un determinato spazio. Questo ti consentirà di suggerire offerte specifiche per questo tipo di visitatore, che corrispondono alle regole di tipologia specificate.

Se non esiste alcun elemento che ti consenta di identificare un contatto o se non desideri suggerire un’offerta identificata a un contatto che possa essere identificato implicitamente, puoi scegliere di eseguire un fallback in un ambiente anonimo.

A questo scopo, controlla **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**, quindi specifica l&#39;ambiente dedicato a questi visitatori non identificati in **[!UICONTROL Linked anonymous space]** quando specifichi uno spazio dell&#39;offerta.

![](assets/anonymous_to_anonymous_environment.png)
