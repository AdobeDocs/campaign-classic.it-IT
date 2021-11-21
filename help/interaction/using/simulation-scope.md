---
product: campaign
title: Ambito della simulazione
description: Ambito della simulazione
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---

# Ambito della simulazione{#simulation-scope}

![](../../assets/v7-only.svg)

## Definizione dell&#39;ambito di applicazione {#definition-of-the-scope}

Apri **[!UICONTROL Scope]** scheda per scegliere le impostazioni.

Sono obbligatori i seguenti elementi:

* Ambiente o categoria di offerta.
* Spazio di offerta.
* Data di contatto. Le offerte non idonee alla data di contatto non vengono prese in considerazione.
* Popolazione target.

   Se non configuri un filtro sulla destinazione, verrà presa in considerazione l’intera tabella dei destinatari.

* Numero di proposte da simulare per target.

   Il destinatario riceverà queste numerose proposte. Ad esempio, se immetti 5, ogni destinatario riceverà un massimo di 5 proposte di offerta.

   ![](assets/offer_simulation_009.png)

Per perfezionare le offerte da prendere in considerazione per la simulazione, puoi aggiungere uno o più temi (precedentemente specificati nelle categorie).

Puoi anche scegliere di eseguire la simulazione su tutte le offerte o solo su quelle online. Alcuni filtri consentono di modificare la selezione, se lo desideri.

>[!NOTE]
>
>È necessario specificare una data di contatto. Questo consente al motore di interazione di ordinare le offerte nell’ambiente o nella categoria selezionati. Se non è configurata alcuna data, la simulazione genererà un errore.

## Aggiunta di assi di reporting {#adding-reporting-axes}

Puoi migliorare l’analisi di simulazione aggiungendo assi di reporting sul target o le offerte stesse tramite il **[!UICONTROL Calculations]** scheda .

A questo scopo, fai clic sul pulsante **[!UICONTROL Add]** e scegliere i campi appropriati. Gli assi verranno utilizzati per calcolare la simulazione e saranno visualizzati nel rapporto di analisi. Per ulteriori informazioni, consulta [Tracking della simulazione](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
