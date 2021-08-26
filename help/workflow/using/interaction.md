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

Per impostazione predefinita, i flussi di lavoro descritti di seguito sono installati con il componente aggiuntivo **Offer engine (Interaction)** .

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
   <td> Questo flusso di lavoro aggiorna l’aggregato <strong>Completo</strong> per il cubo <strong>Proposizione offerta</strong> . Viene attivato ogni giorno alle 6 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, consegna, offerta di marketing e data.<br /> Il cubo  <strong>Proposizione </strong> offerta viene quindi utilizzato per generare rapporti basati sulle offerte. Per ulteriori informazioni sui cubi, consulta <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna l'aggregato <strong>Completo</strong> per il cubo <strong>Centro messaggi</strong> . Viene attivato ogni giorno alle 3 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, data, stato ed evento.<br /> Il  <strong>cubo </strong> del centro messaggi viene quindi utilizzato per generare rapporti basati sugli eventi. Per ulteriori informazioni sui cubi, consulta <a href="../../reporting/using/about-cubes.md">questa sezione</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

