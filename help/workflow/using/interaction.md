---
product: campaign
title: Interazione
description: Interazione
hide: true
hidefromtoc: true
feature: Workflows, Interaction, Offers
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 3%

---


# Interazione{#interaction}



I flussi di lavoro descritti di seguito vengono installati con il componente aggiuntivo **Offer Engine (Interaction)** per impostazione predefinita.

Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

![](assets/do-not-localize/v7.jpeg) [Documentazione di Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png) [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Full</strong> per il cubo <strong>Proposta di offerte</strong>. Per impostazione predefinita viene attivato ogni giorno alle 6. Questo aggregato acquisisce le seguenti dimensioni: Canale, Consegna, Offerta di marketing e Data.<br /> Il cubo <strong>Proposta di offerte</strong> viene quindi utilizzato per generare rapporti basati sulle offerte. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/ac-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Full</strong> per il cubo <strong>Centro messaggi</strong>. Viene attivato ogni giorno alle 3 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, Data, Stato e Tipo evento.<br /> Il cubo <strong>Centro messaggi</strong> viene quindi utilizzato per generare report basati sugli eventi. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/ac-cubes.md">questa sezione</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

