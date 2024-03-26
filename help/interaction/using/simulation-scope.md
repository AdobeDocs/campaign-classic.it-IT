---
product: campaign
title: Ambito della simulazione
description: Ambito della simulazione
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 2%

---

# Ambito della simulazione{#simulation-scope}



## Definizione del campo di applicazione {#definition-of-the-scope}

Apri **[!UICONTROL Scope]** per scegliere le impostazioni.

I seguenti elementi sono obbligatori:

* Ambiente o categoria di offerta.
* Spazio dell’offerta.
* Data di contatto. Le offerte non idonee alla data di contatto non vengono prese in considerazione.
* Popolazione target.

  Se non configuri un filtro sulla destinazione, verrà presa in considerazione l’intera tabella dei destinatari.

* Numero di proposte da simulare per target.

  Il destinatario riceverà un numero così elevato di proposte. Ad esempio, se immetti 5, ogni destinatario riceverà un massimo di 5 proposte di offerta.

  ![](assets/offer_simulation_009.png)

Per perfezionare le offerte da prendere in considerazione per la simulazione, puoi aggiungere uno o più temi (precedentemente specificati nelle categorie).

Puoi anche scegliere di eseguire la simulazione su tutte le offerte o solo su quelle online. Alcuni filtri ti consentono di modificare la selezione, se lo desideri.

>[!NOTE]
>
>Specificare una data di contatto. In questo modo il motore di interazione può ordinare le offerte nell’ambiente o nella categoria selezionati. Se non è configurata alcuna data, la simulazione genera un errore.

## Aggiunta di assi di reporting {#adding-reporting-axes}

Puoi migliorare l’analisi della simulazione aggiungendo assi di reporting sul target o sulle offerte stesse tramite **[!UICONTROL Calculations]** scheda.

A questo scopo, fai clic su **[!UICONTROL Add]** e scegliere i campi appropriati. Gli assi vengono utilizzati per il calcolo della simulazione e vengono visualizzati nel rapporto di analisi. Per ulteriori informazioni, consulta [Tracciamento della simulazione](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
