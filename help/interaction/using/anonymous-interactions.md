---
product: campaign
title: Interazioni anonime
description: Interazioni anonime
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 3%

---

# Interazioni anonime{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) Guarda questo [video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) per una panoramica del modo in cui le offerte vengono consegnate a target identificati e anonimi.

## Targeting e archiviazione di un ambiente per interazioni anonime {#targeting-and-storing-an-environment-for-anonymous-interactions}

Per impostazione predefinita, Interaction viene fornito con un ambiente preconfigurato per eseguire il targeting della tabella dei destinatari (offerte identificate). Se desideri eseguire il targeting di un’altra tabella (tabella dei visitatori per le offerte anonime o una tabella dei destinatari specifica), utilizza la procedura guidata di mappatura di destinazione per creare l’ambiente. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Quando crei un ambiente anonimo tramite la procedura guidata di creazione della mappatura, il **[!UICONTROL Environment dedicated to incoming anonymous interactions]** viene selezionata automaticamente nel file **[!UICONTROL General]** scheda.

Il **[!UICONTROL Targeting dimension]** viene completato automaticamente. Per impostazione predefinita, si collega alla tabella dei visitatori.

Il **[!UICONTROL Visitor folder]** viene visualizzato. Viene completato automaticamente per collegare **[!UICONTROL Visitors]** cartella. Questo campo consente di scegliere dove memorizzare i profili dei visitatori.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Se desideri filtrare diversi tipi di visitatori, ad esempio nel caso di offerte anonime presentate per uno o più marchi, devi creare un ambiente per ogni marchio e una **[!UICONTROL Visitors]** digita la cartella per ciascun ambiente.

## Catalogo delle offerte per interazioni anonime {#offer-catalog-for-anonymous-interactions}

Proprio come le interazioni in uscita, le interazioni in entrata sono organizzate in un catalogo di offerte composto da categorie e offerte.

Per creare categorie e spazi, applica lo stesso processo utilizzato per i visitatori identificati (consulta [Creazione di categorie di offerta](../../interaction/using/creating-offer-categories.md) e [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Visitatori anonimi {#anonymous-visitors}

I visitatori anonimi possono essere sottoposti a un processo di identificazione dei cookie durante la connessione. Questo riconoscimento implicito si basa sulla cronologia del browser del visitatore.

Durante questo passaggio, viene effettuato un confronto tra i dati recuperati dai cookie e quelli presenti nel database. In alcuni casi, i visitatori vengono riconosciuti (vengono quindi implicitamente identificati), in altri, non vengono riconosciuti (e quindi rimangono anonimi).

Per eseguire questa analisi, per lo spazio dell’offerta seleziona la **[!UICONTROL Implicitly identify the individual based on their browser history]** opzione.

![](assets/identification_anonymous_visitors.png)

## Elaborazione di visitatori anonimi non identificati {#processing-unidentified-anonymous-visitors}

Dopo l’analisi, se un visitatore anonimo non viene identificato, puoi memorizzarne i dati in un determinato spazio. Questo ti consentirà di suggerire offerte specifiche per questo tipo di visitatore, che corrispondono alle regole di tipologia specificate.

Se non esiste alcun elemento che ti consenta di identificare un contatto o se non desideri suggerire un’offerta identificata a un contatto che possa essere identificato implicitamente, puoi scegliere di eseguire un fallback in un ambiente anonimo.

A questo scopo, seleziona la **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**, quindi specifica l’ambiente dedicato a questi visitatori non identificati nel **[!UICONTROL Linked anonymous space]** quando si specifica uno spazio dell’offerta.

![](assets/anonymous_to_anonymous_environment.png)
