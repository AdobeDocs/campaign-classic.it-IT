---
product: campaign
title: Profili operatore
description: Profili operatore
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 3%

---

# Profili operatore{#operator-profiles}



Esistono due tipi di operatori che utilizzano l’interazione: gestori delle offerte e responsabili della consegna. Ognuno di essi dispone di diritti specifici che consentono loro di accedere solo ad alcune parti dell’albero e della piattaforma.

* **[!UICONTROL Offer manager]** : crea e mantiene le offerte. Tieni presente che se le offerte vengono utilizzate nel flusso di lavoro, l’operatore dovrà trovarsi nel **[!UICONTROL Administrator]** o **[!UICONTROL Offer managers]** per eseguire il flusso di lavoro.
* **[!UICONTROL Delivery manager]** : approva e utilizza le offerte

I passaggi per la creazione di operatori specifici per l’interazione sono identici a quelli utilizzati per creare tutti gli altri operatori sulla piattaforma. Per ulteriori informazioni, consulta [questa sezione](../../platform/using/access-management.md). I diritti vengono configurati durante la creazione dell’operatore.

## Gestione offerte {#offer-manager}

1. Crea un nuovo operatore.
1. Vai a **[!UICONTROL Groups and named rights]** finestra, fai clic su **[!UICONTROL Add]** e seleziona la **[!UICONTROL Offer manager]** gruppo.

   ![](assets/offer_operators_create_001.png)

I diritti assegnati al gestore delle offerte consentono loro di svolgere le seguenti attività:

* Modifica **[!UICONTROL Design]** ambienti.
* Visualizza **[!UICONTROL Live]** ambienti.
* Configurare le funzioni di amministrazione (spazi e filtri predefiniti).
* Creare e modificare le categorie.
* Creare le offerte.
* Configurare l’idoneità per le offerte.
* Approvare le offerte.

  >[!NOTE]
  >
  >Il gestore delle offerte può approvare un’offerta solo in due casi specifici. Il primo è se nessuno in particolare è stato specificato come revisore, il secondo è se l’operatore responsabile della creazione dei modelli (con il diritto di assegnare i revisori) li ha specificati come revisori nel modello di offerta su cui era basata l’offerta.

## Responsabile della consegna {#delivery-manager}

1. Crea un nuovo operatore.
1. Vai a **[!UICONTROL Groups and named rights]** finestra, fai clic su **[!UICONTROL Add]** e seleziona la **[!UICONTROL Delivery manager]** gruppo.

   ![](assets/offer_operators_create_002.png)

I diritti assegnati ai responsabili della consegna consentono loro di svolgere i seguenti compiti:

* Visualizzazione **[!UICONTROL Live]** ambienti.
* Visualizzare e modificare le categorie di offerta.
* Approva le offerte se il responsabile della consegna è specificato come uno dei suoi revisori.

  >[!NOTE]
  >
  >I responsabili della consegna possono approvare un’offerta solo se sono stati definiti come revisori durante la configurazione dell’offerta.

## Riepilogo dei diritti in base all’operatore {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestione offerte (modifica)</strong><br /> </td> 
   <td> <strong>Gestione offerte (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Livello struttura ad albero</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offerte in fase di modifica / Offerte live<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Ambiente<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Amministrazione<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Spaces<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Filtri di offerta predefiniti<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipologia<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Regole di tipologia<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogo delle offerte<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria di offerta<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestione delle consegne (modifica)</strong><br /> </td> 
   <td> <strong>Gestione delle consegne (in tempo reale)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Livello struttura ad albero</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offerte in fase di modifica / Offerte live<br /> </td> 
   <td> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Ambiente<br /> </td> 
   <td> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Amministrazione<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Spaces<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Filtri di offerta predefiniti<br /> </td> 
   <td> Letto<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipologia<br /> </td> 
   <td> Letto<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Regole di tipologia<br /> </td> 
   <td> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogo delle offerte<br /> </td> 
   <td> Letto<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria di offerta<br /> </td> 
   <td> </td> 
   <td> Letto<br /> </td> 
  </tr> 
 </tbody> 
</table>
