---
product: campaign
title: Utilizzare Adobe Campaign Explorer
description: Scopri come utilizzare Campaign Explorer
feature: Overview
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 3%

---

# Utilizzare Adobe Campaign Explorer {#using-adobe-campaign-explorer}



Adobe Campaign Explorer è accessibile tramite l’icona della barra degli strumenti. Consente di accedere ad Adobe Campaign per tutte le funzionalità di Adobe Campaign, le schermate di configurazione e una visualizzazione più dettagliata di alcuni elementi della piattaforma.

Il **[!UICONTROL Explorer]** l’area di lavoro è suddivisa in tre aree:

![](assets/s_ncs_user_navigation.png)

**1 - Albero**: puoi personalizzare il contenuto della struttura (aggiungere, spostare o eliminare nodi). Questa procedura è destinata esclusivamente agli utenti esperti. Per ulteriori informazioni, consulta  [questa sezione](#about-navigation-hierarchy).).

**2 - Elenco**: puoi filtrare questo elenco, eseguire ricerche, aggiungere informazioni o ordinare dati. [Ulteriori informazioni](adobe-campaign-ui-lists.md).

**3 - Dettagli**: puoi visualizzare i dettagli dell’elemento selezionato. L’icona nella sezione in alto a destra consente di visualizzare queste informazioni in formato a schermo intero.

## Cartelle e struttura di navigazione{#about-navigation-hierarchy}

La struttura di spostamento funziona come un browser di file, ad esempio Esplora risorse. Le cartelle possono contenere sottocartelle. Selezionando un nodo viene visualizzata la vista corrispondente al nodo.

La vista visualizzata è un elenco associato a uno schema e un modulo di input per modificare la riga selezionata.

![](assets/d_ncs_integration_navigation.png)

Per aggiungere una nuova cartella alla struttura, fare clic con il pulsante destro del mouse sulla cartella nel ramo in cui si desidera inserire una cartella e selezionare **[!UICONTROL Add new folder]** . Nel menu di scelta rapida, selezionate il tipo di file da creare.

![](assets/d_ncs_integration_navigation_create.png)

Scopri come configurare la struttura di navigazione di Campaign [in questa sezione](../../configuration/using/configuration.md).

Scopri come impostare le autorizzazioni sulle cartelle [in questa sezione](access-management-folders.md).

## Best practice per la configurazione delle cartelle

* **Utilizzare le cartelle incorporate**

  L’utilizzo delle cartelle incorporate semplifica l’utilizzo, la manutenzione e la risoluzione dei problemi dell’applicazione da parte degli utenti non coinvolti nel progetto. Non devi creare strutture di cartelle personalizzate per destinatari, elenchi, consegne e così via, ma utilizza le cartelle standard come Amministrazione, Profili e destinazioni, Gestione campagne.

* **Creare sottocartelle**

  Posiziona i flussi di lavoro tecnici nella cartella standard: Amministrazione / Produzione / Flussi di lavoro tecnici e crea sottodirectory per tipo di flusso di lavoro.

* **Impostare una convenzione di denominazione**

  Ad esempio, puoi denominare i flussi di lavoro in ordine alfabetico, in modo che vengano visualizzati ordinati in base all’ordine di esecuzione.

  Ad esempio:

   * A1 - destinatari delle importazioni, inizia alle 10:00;
   * A2 - l&#39;importazione dei biglietti inizia alle 11:00.

* **Creare modelli con cui iniziare gli utenti**

  Crea modelli di consegna, modelli di flusso di lavoro e modelli di campagna specifici per gli utenti. Questa struttura può risparmiare tempo e garantire che vengano utilizzate la mappatura e le tipologie di consegna corrette per ogni utente.

## Risoluzione dello schermo {#screen-resolution}

Per una navigazione e un’usabilità ottimali, Adobe consiglia di utilizzare una risoluzione minima dello schermo di 1600x900 pixel.

>[!CAUTION]
>
>Adobe Campaign non supporta risoluzioni inferiori a 1600x900 pixel.

In **[!UICONTROL Explorer]** workspace, se alcune parti del **[!UICONTROL Details]** la zona viene visualizzata come troncata, espandila utilizzando la freccia sopra la zona o fai clic sul pulsante **[!UICONTROL Enlarge]** pulsante.

![](assets/s_ncs_user_resolution.png)

## Sfogliare e personalizzare gli elenchi {#browsing-lists}

Scopri come navigare, gestire e personalizzare gli elenchi [in questa sezione](adobe-campaign-ui-lists.md).
