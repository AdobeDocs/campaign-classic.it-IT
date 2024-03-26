---
product: campaign
title: Canale LINE
description: Canale LINE
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 8%

---


# Canale LINE{#line-channel}



I flussi di lavoro descritti di seguito vengono installati con **Canale LINE** per impostazione predefinita. Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aggiornamento del token di accesso LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna il token di accesso alla LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elimina utenti LINE bloccati</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Questo flusso di lavoro assicura che i dati degli utenti LINE V2 vengano eliminati dopo che hanno bloccato l’account ufficiale LINE per 180 giorni.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Migrazione da MID a LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Questo flusso di lavoro genera l’ID degli utenti LINE V2 per la migrazione da LINE V1 a LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

