---
solution: Campaign Classic
product: campaign
title: Interazione
description: Interazione
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# Interazione{#interaction}

I flussi di lavoro descritti di seguito vengono installati con il modulo **Offer Engine (Interaction)** per impostazione predefinita. Per ulteriori informazioni su questo modulo, consultare la sezione [sezione](../../interaction/using/interaction-and-offer-management.md).

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
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Completa</strong> per il cubo <strong>Proposizione offerta</strong>. Viene attivato ogni giorno alle 6 del mattino per impostazione predefinita. Questo aggregato acquisisce le dimensioni seguenti: Canale, Consegna, Offerta marketing e Data.<br /> Il cubo  <strong>Proposizione </strong> offerta viene quindi utilizzato per generare rapporti basati sulle offerte. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo di MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Full</strong> per il cubo <strong>Message center</strong>. Viene attivato ogni giorno alle 3 del mattino per impostazione predefinita. Questo aggregato acquisisce le dimensioni seguenti: Canale, Data, Stato ed Evento.<br /> Il  <strong>Centercubo </strong> Messaggio viene quindi utilizzato per generare rapporti basati sugli eventi. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

