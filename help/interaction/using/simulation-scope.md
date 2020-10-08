---
title: Ambito della simulazione
seo-title: Ambito della simulazione
description: Ambito della simulazione
seo-description: null
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 3%

---


# Ambito della simulazione{#simulation-scope}

## Definizione del campo di applicazione {#definition-of-the-scope}

Aprite la **[!UICONTROL Scope]** scheda per scegliere le impostazioni.

Sono obbligatori i seguenti elementi:

* Ambiente o categoria di offerte.
* Spazio disponibile.
* Data di contatto. Le offerte non ammissibili alla data di contatto non sono prese in considerazione.
* Popolazione bersaglio.

   Se non configuri un filtro sulla destinazione, verrà presa in considerazione l&#39;intera tabella dei destinatari.

* Numero di proposizioni da simulare per target.

   Il destinatario riceverà queste numerose proposte. Ad esempio, se immetti 5, ogni destinatario riceverà un massimo di 5 proposte di offerta.

   ![](assets/offer_simulation_009.png)

Per perfezionare le offerte da prendere in considerazione per la simulazione, potete aggiungere uno o più temi (specificati in precedenza nelle categorie).

Potete anche scegliere di effettuare la simulazione su tutte le offerte o solo su quelle online. Alcuni filtri consentono di modificare la selezione se lo si desidera.

>[!NOTE]
>
>È necessario specificare una data di contatto. Questo consente al motore di interazione di ordinare le offerte nell&#39;ambiente o nella categoria selezionati. Se non è configurata alcuna data, la simulazione genererà un errore.

## Aggiunta di assi di reporting {#adding-reporting-axes}

Potete migliorare l&#39;analisi di simulazione aggiungendo assi di reporting sulla destinazione o le offerte stesse tramite la **[!UICONTROL Calculations]** scheda.

A questo scopo, fate clic sul **[!UICONTROL Add]** pulsante e scegliete i campi appropriati. Gli assi verranno utilizzati per calcolare la simulazione e visualizzati nel rapporto di analisi. For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

