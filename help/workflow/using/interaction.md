---
title: Interazione
seo-title: Interazione
description: Interazione
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# Interazione{#interaction}

I flussi di lavoro descritti di seguito vengono installati con il modulo **Offer Engine (Interaction)** per impostazione predefinita. For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo (cubo propositionrcp)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Completa</strong> per il cubo delle proposte <strong>di</strong> offerta. Viene attivato ogni giorno alle 6 del mattino per impostazione predefinita. Questo aggregato acquisisce le dimensioni seguenti: Canale, Consegna, Offerta marketing e Data.<br /> Il cubo <strong>Offerta</strong> viene quindi utilizzato per generare rapporti basati sulle offerte. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo di MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

