---
product: campaign
title: Interazione
description: Interazione
hide: true
feature: Workflows, Interaction, Offers
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 2%
---

# Interazione{#interaction}



I flussi di lavoro descritti di seguito vengono installati con il componente aggiuntivo **Offer Engine (Interaction)** per impostazione predefinita.

Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

![](assets/do-not-localize/v7.jpeg)[Documentazione di Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Full</strong> per il cubo <strong>Proposta di offerte</strong>. Per impostazione predefinita viene attivato ogni giorno alle 6. Questo aggregato acquisisce le dimensioni seguenti: Canale, Consegna, Offerta di marketing e Data.<br /> Il cubo <strong>Proposta di offerte</strong> viene quindi utilizzato per generare rapporti basati sulle offerte. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/ac-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo aggregato completo MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna l'aggregazione <strong>Full</strong> per il cubo <strong>Centro messaggi</strong>. Viene attivato ogni giorno alle 3 per impostazione predefinita. Questo aggregato acquisisce le dimensioni seguenti: Canale, Data, Stato e Tipo evento.<br /> Il cubo <strong>Centro messaggi</strong> viene quindi utilizzato per generare report basati sugli eventi. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/ac-cubes.md">questa sezione</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

