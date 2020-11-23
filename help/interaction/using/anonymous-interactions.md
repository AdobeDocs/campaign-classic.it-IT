---
solution: Campaign Classic
product: campaign
title: Interazioni anonime
description: Interazioni anonime
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# Interazioni anonime{#anonymous-interactions}

Guardate questo [video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) per una panoramica di come le offerte vengono distribuite a target identificati e anonimi.

## Targeting e archiviazione di un ambiente per interazioni anonime {#targeting-and-storing-an-environment-for-anonymous-interactions}

Per impostazione predefinita, Interaction viene fornito con un ambiente preconfigurato per il targeting della tabella dei destinatari (offerte identificate). Se desiderate eseguire il targeting di un&#39;altra tabella (tabella visitatore per le offerte anonime o una tabella di destinazione specifica), dovete utilizzare la procedura guidata di mappatura della destinazione per creare l&#39;ambiente. Per ulteriori informazioni, consultate [Creazione di un ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)di offerte.

Quando si crea un ambiente anonimo tramite la procedura guidata di creazione della mappatura, la **[!UICONTROL Environment dedicated to incoming anonymous interactions]** casella viene selezionata automaticamente nella **[!UICONTROL General]** scheda dell&#39;ambiente.

Il modulo **[!UICONTROL Targeting dimension]** viene completato automaticamente. Per impostazione predefinita, collega la tabella del visitatore.

Viene **[!UICONTROL Visitor folder]** visualizzato il campo. Viene automaticamente completato per il collegamento alla **[!UICONTROL Visitors]** cartella. Questo campo consente di scegliere dove memorizzare i profili dei visitatori.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Se desiderate filtrare diversi tipi di visitatori, ad esempio nel caso di offerte anonime presentate per uno o più marchi, dovete creare un ambiente per ciascun marchio e una cartella di **[!UICONTROL Visitors]** tipo per ciascun ambiente.

## Catalogo delle offerte per le interazioni anonime {#offer-catalog-for-anonymous-interactions}

Proprio come le interazioni in uscita, le interazioni in entrata sono organizzate in un catalogo di offerte, composto da categorie e offerte.

Per creare categorie e spazi, applicate lo stesso processo utilizzato per i visitatori identificati (consultate [Creazione di categorie](../../interaction/using/creating-offer-categories.md) di offerte e [Creazione di un ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)di offerte).

## Visitatori anonimi {#anonymous-visitors}

I visitatori anonimi possono essere inviati a un processo di identificazione dei cookie quando si connettono. Questo riconoscimento implicito si basa sulla cronologia del browser del visitatore.

Durante questo passaggio, viene effettuato un confronto tra i dati recuperati dai cookie e quelli presenti nel database. In alcuni casi, il visitatore viene riconosciuto (viene quindi identificato implicitamente), in altri casi, non viene riconosciuto (e quindi rimane anonimo).

Per eseguire questa analisi, per lo spazio dell&#39;offerta, selezionate l&#39; **[!UICONTROL Implicitly identify the individual based on their browser history]** opzione.

![](assets/identification_anonymous_visitors.png)

## Elaborazione di visitatori anonimi non identificati {#processing-unidentified-anonymous-visitors}

Dopo l&#39;analisi, se un visitatore anonimo non è identificato, puoi archiviare i dati in uno spazio specifico. In questo modo potrete suggerire offerte specificamente indirizzate a questo tipo di visitatore, in linea con le regole di tipologia specificate.

Se non esiste alcun elemento che consenta di identificare un contatto, o se non si desidera suggerire un&#39;offerta identificata a un contatto che possa essere implicitamente identificato, è possibile scegliere di eseguire un fallback su un ambiente anonimo.

Per eseguire questa operazione, controllate **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**, quindi specificate l&#39;ambiente dedicato a questi visitatori non identificati nel **[!UICONTROL Linked anonymous space]** momento in cui specificate uno spazio per l&#39;offerta.

![](assets/anonymous_to_anonymous_environment.png)

