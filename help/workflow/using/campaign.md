---
product: campaign
title: Campaign
description: Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows
topic-tags: technical-workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 7%

---


# Campaign{#campaign}



I flussi di lavoro descritti di seguito vengono installati con **Campagna** per impostazione predefinita. Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Questi flussi di lavoro DEVONO essere avviati affinché i processi della campagna possano essere eseguiti a livello di campagna.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Calcolo dei costi</span> <br /> </td> 
   <td> <span class="uicontrol">budgetManagement</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia il calcolo delle righe spese e costi per budget, piani, programmi, campagne, consegne e attività.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Magazzino: Ordini e avvisi</span> <br /> </td> 
   <td> <span class="uicontrol">stockManagement</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia il calcolo delle scorte nelle linee dell'ordine e gestisce le soglie degli avvisi di avvertenza.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi su consegne nelle campagne</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryManagement</span> <br /> </td> 
   <td> Questo flusso di lavoro attiva le consegne approvate e avvia la post-elaborazione del provider di servizi per una consegna esterna. Invia inoltre notifiche di approvazione e promemoria.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi della campagna</span> <br /> </td> 
   <td> <span class="uicontrol">operationManagement</span> <br /> </td> 
   <td> Questo flusso di lavoro gestisce i processi per le campagne di marketing (avvio, targeting, estrazione file, ecc.). Crea anche flussi di lavoro relativi a campagne ricorrenti e periodiche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Processi nei provider di servizi</span> <br /> </td> 
   <td> <span class="uicontrol">gestioneFornitori</span> <br /> </td> 
   <td> Questo flusso di lavoro avvia l’elaborazione del provider (e-mail al router e post-elaborazione) dopo l’approvazione delle consegne. <br /> </td> 
  </tr> 
 </tbody> 
</table>

