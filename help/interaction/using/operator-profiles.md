---
product: campaign
title: Profili operatore
description: Profili operatore
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---

# Profili operatore{#operator-profiles}



Esistono due tipi di operatori che utilizzano l’interazione: gestori delle offerte e responsabili della consegna. Ognuno di essi dispone di diritti specifici che consentono loro di accedere solo ad alcune parti dell’albero e della piattaforma.

* **[!UICONTROL Offer manager]** : crea e mantiene le offerte. Se le offerte vengono utilizzate nel flusso di lavoro, l&#39;operatore dovrà trovarsi nel gruppo di operatori **[!UICONTROL Administrator]** o **[!UICONTROL Offer managers]** per eseguire il flusso di lavoro.
* **[!UICONTROL Delivery manager]** : approva e utilizza le offerte

I passaggi per la creazione di operatori specifici per l’interazione sono identici a quelli utilizzati per creare tutti gli altri operatori sulla piattaforma. Per ulteriori informazioni, consulta [questa sezione](../../platform/using/access-management.md). I diritti vengono configurati durante la creazione dell’operatore.

## Gestione offerte {#offer-manager}

1. Crea un nuovo operatore.
1. Passare alla finestra **[!UICONTROL Groups and named rights]**, fare clic su **[!UICONTROL Add]** e selezionare il gruppo **[!UICONTROL Offer manager]**.

   ![](assets/offer_operators_create_001.png)

I diritti assegnati al gestore delle offerte consentono loro di svolgere le seguenti attività:

* Modificare gli ambienti **[!UICONTROL Design]**.
* Visualizza gli ambienti **[!UICONTROL Live]**.
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
1. Passare alla finestra **[!UICONTROL Groups and named rights]**, fare clic su **[!UICONTROL Add]** e selezionare il gruppo **[!UICONTROL Delivery manager]**.

   ![](assets/offer_operators_create_002.png)

I diritti assegnati ai responsabili della consegna consentono loro di svolgere i seguenti compiti:

* Visualizza **[!UICONTROL Live]** ambienti.
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
   <td> Spazi<br /> </td> 
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
   <td> Catalogo offerte<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria offerta<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestione consegne (modifica)</strong><br /> </td> 
   <td> <strong>Gestione consegne (in tempo reale)</strong><br /> </td> 
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
   <td> Spazi<br /> </td> 
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
   <td> Catalogo offerte<br /> </td> 
   <td> Letto<br /> </td> 
   <td> Letto<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria offerta<br /> </td> 
   <td> </td> 
   <td> Letto<br /> </td> 
  </tr> 
 </tbody> 
</table>
