---
product: campaign
title: Centro messaggi (controllo)
description: Centro messaggi (controllo)
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
source-wordcount: '152'
ht-degree: 1%
---

# Centro messaggi (controllo){#message-center-control}



Il flusso di lavoro descritto di seguito viene pianificato per l’esecuzione ogni ora. Per impostazione predefinita, è installato con il modulo **Centro messaggi - Controllo**.


Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

![](assets/do-not-localize/v7.jpeg)[Documentazione di Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Centro messaggi &lt;nome_account_esterno&gt;<br /> </td> 
   <td> mcSynch_&lt;nome_account_esterno&gt;<br /> </td> 
   <td> Questo flusso di lavoro:<br /> 
    <ul> 
     <li> <p>recupera l’elenco degli eventi elaborati dalle operazioni.</p> </li> 
     <li> <p>si sincronizza con la tabella NmsBroadLogMsg per recuperare le qualifiche dei messaggi di consegna.</p> </li> 
     <li> <p>recupera i registri di consegna degli eventi non appena la sincronizzazione con la tabella NmsBroadLogMsg è stata completata.</p> </li> 
     <li> <p>si sincronizza con la tabella NmsTrackingUrl per recuperare il tracciamento per gli URL di consegna.</p> </li> 
     <li> <p>recupera gli URL di tracciamento degli eventi non appena la sincronizzazione con la tabella NmsTrackingUrl è stata completata.</p> </li> 
     <li> <p>consente di recuperare tutti gli indirizzi e-mail messi in quarantena ogni tre ore dopo l’invio di una consegna.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

