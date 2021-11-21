---
product: campaign
title: Interazione
description: Interazione
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---


# Interazione{#interaction}

![](../../assets/common.svg)

I flussi di lavoro descritti di seguito sono installati con **Motore di offerta (Interazione)** add-on per impostazione predefinita.

Per ulteriori informazioni, a seconda della versione di Campaign, consulta queste sezioni:

![](assets/do-not-localize/v7.jpeg)[  Documentazione di Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> Questo flusso di lavoro aggiorna le <strong>Completo</strong> aggregato per <strong>Proposta di offerta</strong> cubo. Viene attivato ogni giorno alle 6 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, consegna, offerta di marketing e data.<br /> La <strong>Proposta di offerta</strong> viene quindi utilizzato per generare rapporti basati sulle offerte. Puoi saperne di più sui cubi in <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna le <strong>Completo</strong> aggregato per <strong>Centro messaggi</strong> cubo. Viene attivato ogni giorno alle 3 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, data, stato ed evento.<br /> La <strong>Centro messaggi</strong> Il cubo viene quindi utilizzato per generare report basati su eventi. Puoi saperne di più sui cubi in <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

