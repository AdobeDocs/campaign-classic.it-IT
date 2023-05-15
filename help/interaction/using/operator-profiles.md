---
product: campaign
title: Profili operatore
description: Profili operatore
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 9%

---

# Profili operatore{#operator-profiles}



Esistono due tipi di operatori che utilizzano l’interazione: responsabili dell&#39;offerta e responsabili della consegna. Ognuno di essi ha diritti specifici che gli danno accesso solo ad alcune parti dell&#39;albero e della piattaforma.

* **[!UICONTROL Offer manager]** : crea e gestisce le offerte. Se nel flusso di lavoro vengono utilizzate le offerte , l’operatore deve trovarsi nella variabile **[!UICONTROL Administrator]** o **[!UICONTROL Offer managers]** gruppo di operatori per eseguire il flusso di lavoro.
* **[!UICONTROL Delivery manager]** : approva e utilizza le offerte

I passaggi per la creazione di operatori specifici dell’interazione sono identici a quelli utilizzati per creare tutti gli altri operatori sulla piattaforma. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/access-management.md). I diritti vengono configurati durante la creazione dell’operatore.

## Gestione delle offerte {#offer-manager}

1. Crea un nuovo operatore.
1. Vai a **[!UICONTROL Groups and named rights]** finestra, fai clic su **[!UICONTROL Add]** e seleziona la **[!UICONTROL Offer manager]** gruppo.

   ![](assets/offer_operators_create_001.png)

I diritti assegnati al gestore delle offerte consentono loro di eseguire le seguenti attività:

* Modifica **[!UICONTROL Design]** ambienti.
* Visualizza **[!UICONTROL Live]** ambienti.
* Configura le funzioni di amministrazione (spazi e filtri predefiniti).
* Creare e modificare le categorie.
* Crea offerte.
* Configura l’idoneità delle offerte.
* Approvare le offerte.

   >[!NOTE]
   >
   >Il gestore delle offerte può approvare un’offerta solo in due casi specifici. Il primo è se nessuno in particolare è stato specificato come revisore e il secondo se l’operatore responsabile della creazione di modelli (con il diritto di assegnare i revisori) li ha specificati come revisore nel modello di offerta su cui si basa l’offerta.

## Responsabile della consegna {#delivery-manager}

1. Crea un nuovo operatore.
1. Vai a **[!UICONTROL Groups and named rights]** finestra, fai clic su **[!UICONTROL Add]** e seleziona la **[!UICONTROL Delivery manager]** gruppo.

   ![](assets/offer_operators_create_002.png)

I diritti assegnati ai gestori della consegna consentono loro di svolgere i seguenti compiti:

* Visualizzazione **[!UICONTROL Live]** ambienti.
* Visualizza e modifica le categorie di offerte.
* Approva le offerte se questo delivery manager è specificato come uno dei suoi revisori.

   >[!NOTE]
   >
   >I gestori di consegne possono approvare un’offerta solo se sono stati definiti come revisore durante la configurazione dell’offerta.

## Recupero dei diritti secondo l&#39;operatore {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestione delle offerte (modifica)</strong><br /> </td> 
   <td> <strong>Gestione delle offerte (in diretta)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Livello struttura ad albero</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offerte in corso di modifica / Offerte live<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Ambiente<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Amministrazione<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Spazi<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Filtri per offerte predefiniti<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipologia<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Regole di tipologia<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogo delle offerte<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria offerta<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Gestione consegne (modifica)</strong><br /> </td> 
   <td> <strong>Direttore consegna (dal vivo)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Livello struttura ad albero</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offerte in corso di modifica / Offerte live<br /> </td> 
   <td> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Ambiente<br /> </td> 
   <td> </td> 
   <td> Leggi<br /> </td> 
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
   <td> Filtri per offerte predefiniti<br /> </td> 
   <td> Leggi<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Tipologia<br /> </td> 
   <td> Leggi<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Regole di tipologia<br /> </td> 
   <td> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogo delle offerte<br /> </td> 
   <td> Leggi<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Categoria offerta<br /> </td> 
   <td> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
 </tbody> 
</table>
