---
product: campaign
title: Canale LINE
description: Canale LINE
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%
---

# Canale LINE{#line-channel}



Per impostazione predefinita, i flussi di lavoro descritti di seguito vengono installati con il modulo **LINE channel**. Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aggiornamento token di accesso LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna il token di accesso a LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elimina utenti LINE bloccati</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Questo flusso di lavoro assicura che i dati degli utenti LINE V2 vengano eliminati dopo che hanno bloccato l'account ufficiale LINE per 180 giorni.<br /> </td> 
  </tr> 
  <tr> 
   <td> Migrazione da <span class="uicontrol">MID a LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Questo flusso di lavoro genera l'ID degli utenti LINE V2 per la migrazione da LINE V1 a LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

