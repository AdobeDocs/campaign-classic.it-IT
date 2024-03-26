---
product: campaign
title: Interazione
description: Interazione
feature: Workflows, Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 7%

---


# Interazione{#interaction}



I flussi di lavoro descritti di seguito vengono installati con **Motore di offerta (interazione)** componente aggiuntivo per impostazione predefinita.

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
   <td> Questo flusso di lavoro aggiorna <strong>Completo</strong> aggregato per <strong>Proposta di offerta</strong> cubo. Per impostazione predefinita viene attivato ogni giorno alle 6. Questo aggregato acquisisce le seguenti dimensioni: Canale, Consegna, Offerta di marketing e Data.<br /> Il <strong>Proposta di offerta</strong> Il cubo viene quindi utilizzato per generare rapporti basati sulle offerte. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/ac-cubes.md">questa sezione</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Calcolo dell'aggregazione completa MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna <strong>Completo</strong> aggregato per <strong>Centro messaggi</strong> cubo. Viene attivato ogni giorno alle 3 per impostazione predefinita. Questo aggregato acquisisce le seguenti dimensioni: Canale, Data, Stato e Tipo evento.<br /> Il <strong>Centro messaggi</strong> Il cubo viene quindi utilizzato per generare rapporti basati sugli eventi. Ulteriori informazioni sui cubi sono disponibili in <a href="../../reporting/using/ac-cubes.md">questa sezione</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

