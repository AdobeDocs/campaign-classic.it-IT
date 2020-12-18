---
solution: Campaign Classic
product: campaign
title: Campagna
description: Campagna
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# Campagna{#campaign}

I flussi di lavoro descritti di seguito vengono installati con il modulo **Campaign** per impostazione predefinita. Per ulteriori informazioni su questo modulo, consultare la sezione [sezione](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Questi flussi di lavoro DEVONO essere avviati per consentire l&#39;esecuzione dei processi della campagna a livello di campagna.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcolo costi</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia il calcolo delle linee di spesa e di costo per budget, piani, programmi, campagne, consegne e attività.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Ordini e avvisi</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia il calcolo delle scorte sulle linee dell'ordine e gestisce le soglie degli avvisi di avviso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi sulle consegne nelle campagne</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro attiva le consegne approvate e avvia la post-elaborazione del provider di servizi per una consegna esterna. Invia inoltre notifiche di approvazione e promemoria.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi campagna</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro gestisce i processi per le campagne di marketing (targeting di lancio, estrazione file, ecc.). Crea inoltre flussi di lavoro correlati a campagne ricorrenti e periodiche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi relativi ai fornitori di servizi</span> <br /> </td> 
   <td> <span class="uicontrol">fornitoreMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia l'elaborazione del provider (e-mail al router e post-elaborazione) una volta che le consegne sono state approvate. <br /> </td> 
  </tr> 
 </tbody> 
</table>

