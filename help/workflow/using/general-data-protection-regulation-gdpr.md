---
product: campaign
title: Flussi di lavoro del regolamento sulla protezione dei dati sulla privacy
description: Ulteriori informazioni sui flussi di lavoro del Regolamento sulla protezione dei dati sulla privacy
hide: true
feature: Workflows, Privacy
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 7%
---

# Regolamento sulla protezione dei dati personali{#general-data-protection-regulation-gdpr}



Per impostazione predefinita, i flussi di lavoro descritti di seguito vengono installati con il modulo **Privacy Data Protection Regulation**. Per ulteriori informazioni su questo modulo, consulta questo [articolo](https://helpx.adobe.com/it/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Raccogli richieste di accesso a dati personali</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> Questo flusso di lavoro genera i dati del destinatario memorizzati in Adobe Campaign e li rende disponibili per il download nella schermata della richiesta di accesso a dati personali.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elimina dati richieste privacy</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> Questo flusso di lavoro elimina i dati del destinatario memorizzati in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia richieste di accesso a dati personali</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> Questo flusso di lavoro cancella i file di richiesta di accesso che sono più vecchi di 90 giorni.<br /> </td> 
  </tr> 
 </tbody> 
</table>

