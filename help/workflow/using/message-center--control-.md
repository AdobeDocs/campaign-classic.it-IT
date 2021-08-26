---
product: campaign
title: Centro messaggi (Controllo)
description: Centro messaggi (Controllo)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 10%

---


# Centro messaggi (Controllo){#message-center-control}

![](../../assets/common.svg)

Il flusso di lavoro descritto di seguito è pianificato per l’esecuzione ogni ora. Per impostazione predefinita, è installato con il modulo **Centro messaggi - Control** .


Per ulteriori informazioni, a seconda della versione di Campaign, consulta queste sezioni:

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
   <td> Centro messaggi &lt;nome_account_esterno&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Questo flusso di lavoro:<br /> 
    <ul> 
     <li> <p>recupera l’elenco degli eventi elaborati dalle operazioni.</p> </li> 
     <li> <p>si sincronizza con la tabella NmsBroadLogMsg per recuperare i requisiti dei messaggi di consegna.</p> </li> 
     <li> <p>recupera i registri di consegna degli eventi non appena la sincronizzazione con la tabella NmsBroadLogMsg è stata completata.</p> </li> 
     <li> <p>si sincronizza con la tabella NmsTrackingUrl al fine di recuperare il tracciamento per gli URL di consegna.</p> </li> 
     <li> <p>recupera gli URL di tracciamento degli eventi non appena la sincronizzazione con la tabella NmsTrackingUrl è stata completata.</p> </li> 
     <li> <p>consente di recuperare tutti gli indirizzi e-mail messi in quarantena ogni tre ore dopo l’invio di una consegna.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

