---
product: campaign
title: Centro messaggi (Controllo)
description: Centro messaggi (Controllo)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 7%

---


# Centro messaggi (Controllo){#message-center-control}

Il flusso di lavoro descritto di seguito è pianificato per l’esecuzione ogni ora. Per impostazione predefinita, è installato con il modulo **Centro messaggi - Control** . Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../message-center/using/about-transactional-messaging.md).

Per ulteriori informazioni su come configurare i flussi di lavoro tecnici relativi al modulo Centro messaggi, consulta [questa pagina](../../message-center/using/technical-workflows.md).

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

