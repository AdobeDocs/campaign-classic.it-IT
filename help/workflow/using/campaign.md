---
product: campaign
title: Campaign
description: Campaign
feature: Workflows
topic-tags: technical-workflows
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# Campaign{#campaign}

![](../../assets/common.svg)

I flussi di lavoro descritti di seguito sono installati con **Campaign** modulo per impostazione predefinita. Per ulteriori informazioni su questo modulo, consulta questo [sezione](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Questi flussi di lavoro DEVONO essere avviati affinché i processi della campagna vengano eseguiti a livello di campagna.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcolo del costo</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia il calcolo delle linee di spesa e di costo relative a budget, piani, programmi, campagne, consegne e attività.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Ordini e avvisi</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia il calcolo delle scorte sulle linee dell'ordine e gestisce le soglie degli avvisi di avviso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi sulle consegne nelle campagne</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro attiva le consegne approvate e avvia la post-elaborazione del provider di servizi per una consegna esterna. Invia inoltre notifiche e promemoria di approvazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi campagna</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro gestisce i lavori per le campagne di marketing (targeting di lanci, estrazione file, ecc.). Crea inoltre flussi di lavoro relativi a campagne ricorrenti e periodiche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi dei fornitori di servizi</span> <br /> </td> 
   <td> <span class="uicontrol">fornitoreMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia l'elaborazione del provider (e-mail al router e post-elaborazione) una volta che le consegne sono state approvate. <br /> </td> 
  </tr> 
 </tbody> 
</table>

