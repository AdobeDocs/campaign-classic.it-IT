---
solution: Campaign Classic
product: campaign
title: Usa Adobe Campaign Explorer
description: Scopri come utilizzare Campaign Explorer
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f,f91d69a4-b794-40f0-b450-de862d7333e2
translation-type: tm+mt
source-git-commit: 8405eefb2e79deeeca07e0c8231bdfa5200ec185
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 3%

---

# Utilizza Adobe Campaign explorer {#using-adobe-campaign-explorer}

L’elenco di esplorazione di Adobe Campaign è accessibile tramite l’icona della barra degli strumenti. Consente di accedere ad Adobe Campaign a tutte le funzionalità, alle schermate di configurazione e a una visualizzazione più dettagliata di alcuni degli elementi della piattaforma.

L&#39;area di lavoro **[!UICONTROL Explorer]** è divisa in tre aree:

![](assets/s_ncs_user_navigation.png)

**1 - Albero**: puoi personalizzare il contenuto della struttura (aggiungere, spostare o eliminare nodi). Questa procedura è destinata esclusivamente agli utenti esperti. Per ulteriori informazioni al riguardo, consulta [questa sezione](#about-navigation-hierarchy).).

**2 - Elenco**: è possibile filtrare l’elenco, eseguire ricerche, aggiungere informazioni o ordinare dati. [Ulteriori informazioni](adobe-campaign-ui-lists.md).

**3 - Dettagli**: puoi visualizzare i dettagli dell’elemento selezionato. L’icona in alto a destra della sezione consente di visualizzare queste informazioni a schermo intero.

## Cartelle e struttura di navigazione{#about-navigation-hierarchy}

La struttura di navigazione funziona come un browser di file (ad esempio Esplora risorse). Le cartelle possono contenere sottocartelle. Quando si seleziona un nodo, viene visualizzata la visualizzazione corrispondente al nodo.

La visualizzazione visualizzata è un elenco associato a uno schema e un modulo di input per modificare la riga selezionata.

![](assets/d_ncs_integration_navigation.png)

Per aggiungere una nuova cartella alla struttura ad albero, fai clic con il pulsante destro del mouse sulla cartella del ramo in cui desideri inserire una cartella e seleziona **[!UICONTROL Add new folder]** . Nel menu di scelta rapida, selezionare il tipo di file da creare.

![](assets/d_ncs_integration_navigation_create.png)

Scopri come configurare la struttura di navigazione Campaign [in questa sezione](../../configuration/using/configuration.md).

Scopri come impostare le autorizzazioni sulle cartelle [in questa sezione](access-management-folders.md).

## Best practice per la configurazione delle cartelle

* **Utilizzare le cartelle incorporate**

   L’utilizzo delle cartelle integrate facilita l’utilizzo, la manutenzione e la risoluzione dei problemi dell’applicazione da parte delle persone non coinvolte nel progetto. Non creare strutture di cartelle personalizzate per destinatari, elenchi, consegne, ecc., ma utilizzare le cartelle standard come Amministrazione, Profili e destinazioni, Gestione campagne.

* **Creare sottocartelle**

   Posiziona i flussi di lavoro tecnici nella cartella standard: Workflow di amministrazione/produzione/tecnica e crea sottodirectory per tipo di flusso di lavoro.

* **Imposta una convenzione di denominazione**

   Ad esempio, è possibile denominare i flussi di lavoro in ordine alfabetico in modo che vengano visualizzati in ordine alfabetico nell’ordine di esecuzione.

   Ad esempio:

   * A1 - destinatari dell’importazione, inizia alle 10:00;
   * A2: i biglietti per l’importazione iniziano alle 11:00.

* **Creare modelli con cui gli utenti possano iniziare**

   Crea modelli di consegna, modelli di flusso di lavoro e modelli di campagna specifici per gli utenti. Questa struttura può risparmiare tempo e garantire che la corretta mappatura e tipologie di consegna siano utilizzate per ogni utente.

## Risoluzione dello schermo {#screen-resolution}

Per una navigazione e un utilizzo ottimali, l&#39;Adobe consiglia di utilizzare una risoluzione minima dello schermo di 1600x900 pixel.

>[!CAUTION]
>
>Le risoluzioni inferiori a 1600x900 pixel sono supportate da Adobe Campaign.

Nell’area di lavoro **[!UICONTROL Explorer]**, se alcune parti della zona **[!UICONTROL Details]** sembrano troncate, espandetela utilizzando la freccia posta sopra la zona o fai clic sul pulsante **[!UICONTROL Enlarge]** .

![](assets/s_ncs_user_resolution.png)

## Sfogliare e personalizzare gli elenchi {#browsing-lists}

Scopri come sfogliare, gestire e personalizzare gli elenchi [in questa sezione](adobe-campaign-ui-lists.md).