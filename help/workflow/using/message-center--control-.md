---
product: campaign
title: Centro messaggi (Controllo)
description: Centro messaggi (Controllo)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 12%

---


# Centro messaggi (Controllo){#message-center-control}



Il flusso di lavoro descritto di seguito viene pianificato per l’esecuzione ogni ora. Viene installato con **Centro messaggi - Controllo** per impostazione predefinita.


Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

![](assets/do-not-localize/v7.jpeg)[  Documentazione di Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Centro messaggi &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
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

