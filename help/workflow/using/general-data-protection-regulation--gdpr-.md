---
product: campaign
title: Flussi di lavoro del regolamento sulla protezione dei dati sulla privacy
description: Ulteriori informazioni sui flussi di lavoro del Regolamento sulla protezione dei dati sulla privacy
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Privacy
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 9%

---


# Regolamento sulla protezione dei dati personali{#general-data-protection-regulation-gdpr}



I flussi di lavoro descritti di seguito vengono installati con **Regolamento sulla protezione dei dati personali** per impostazione predefinita. Per ulteriori informazioni su questo modulo, consulta questa [articolo](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Raccogliere richieste di privacy</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> Questo flusso di lavoro genera i dati del destinatario memorizzati in Adobe Campaign e li rende disponibili per il download nella schermata della richiesta di accesso a dati personali.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Eliminare i dati delle richieste di privacy</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> Questo flusso di lavoro elimina i dati del destinatario memorizzati in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia richiesta di accesso a dati personali</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> Questo flusso di lavoro cancella i file di richiesta di accesso che sono più vecchi di 90 giorni.<br /> </td> 
  </tr> 
 </tbody> 
</table>

