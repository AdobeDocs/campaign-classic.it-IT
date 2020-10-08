---
title: Profili operatore
seo-title: Profili operatore
description: Profili operatore
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 5%

---


# Profili operatore{#operator-profiles}

Esistono due tipi di operatori che utilizzano l&#39;interazione: gestori di offerte e gestori di distribuzione. Ciascuno di essi dispone di diritti specifici che consentono loro di accedere solo ad alcune parti dell&#39;albero e della piattaforma.

* **[!UICONTROL Offer manager]** : crea e mantiene le offerte. Se nel flusso di lavoro vengono utilizzate le offerte, per eseguire il flusso di lavoro l&#39;operatore dovrà essere nel gruppo **[!UICONTROL Administrator]** o **[!UICONTROL Offer managers]** dell&#39;operatore.
* **[!UICONTROL Delivery manager]** : approva e utilizza le offerte

I passaggi per la creazione di operatori specifici di Interaction sono identici a quelli utilizzati per creare tutti gli altri operatori sulla piattaforma. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/access-management.md#creating-an-operator). I diritti vengono configurati durante la creazione dell&#39;operatore.

## Gestione offerte {#offer-manager}

1. Creare un nuovo operatore.
1. Andate alla **[!UICONTROL Groups and named rights]** finestra, fate clic **[!UICONTROL Add]** e selezionate il **[!UICONTROL Offer manager]** gruppo.

   ![](assets/offer_operators_create_001.png)

I diritti assegnati al manager dell&#39;offerta consentono loro di eseguire le seguenti attività:

* Modificare **[!UICONTROL Design]** gli ambienti.
* Visualizzare **[!UICONTROL Live]** gli ambienti.
* Configurare le funzioni di amministrazione (spazi e filtri predefiniti).
* Creare e modificare le categorie.
* Creare offerte.
* Configurare l&#39;idoneità delle offerte.
* Approvare le offerte.

   >[!NOTE]
   >
   >Il manager dell’offerta può approvare un’offerta solo in due casi specifici. Il primo è se nessuno in particolare è stato specificato come revisore, il secondo è se l&#39;operatore responsabile della creazione dei modelli (con il diritto di assegnare i revisori) lo ha specificato come revisore nel modello di offerta su cui si basa l&#39;offerta.

## Direttore consegna {#delivery-manager}

1. Creare un nuovo operatore.
1. Andate alla **[!UICONTROL Groups and named rights]** finestra, fate clic **[!UICONTROL Add]** e selezionate il **[!UICONTROL Delivery manager]** gruppo.

   ![](assets/offer_operators_create_002.png)

I diritti assegnati al responsabile consegna sono/consentono loro di eseguire i seguenti compiti:

* Ambienti **[!UICONTROL Live]** di visualizzazione.
* Visualizzare e modificare le categorie delle offerte.
* Approva offerte se s/he è specificato come uno dei suoi revisori.

   >[!NOTE]
   >
   >Il manager consegna può approvare un&#39;offerta solo se è stato definito come revisore durante la configurazione dell&#39;offerta.

## Recupero dei diritti secondo l&#39;operatore {#recap-of-rights-according-to-operator}

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
   <td> Offerte in corso di modifica / Offerte dal vivo<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Ambiente<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Spazi<br /> </td> 
   <td> Lettura/scrittura<br /> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Filtri offerta predefiniti<br /> </td> 
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
   <td> Catalogo offerte<br /> </td> 
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
   <td> <strong>Manager consegna (modifica)</strong><br /> </td> 
   <td> <strong>Direttore consegna (dal vivo)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Livello struttura ad albero</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Offerte in corso di modifica / Offerte dal vivo<br /> </td> 
   <td> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Destinatario - Ambiente<br /> </td> 
   <td> </td> 
   <td> Leggi<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Spazi<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Filtri offerta predefiniti<br /> </td> 
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
   <td> Catalogo offerte<br /> </td> 
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

