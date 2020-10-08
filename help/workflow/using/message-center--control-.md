---
title: Centro messaggi (Controllo)
seo-title: Centro messaggi (Controllo)
description: Centro messaggi (Controllo)
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 8%

---


# Centro messaggi (Controllo){#message-center-control}

Il flusso di lavoro descritto di seguito è pianificato per essere eseguito ogni ora. È installato con il modulo **Message Center - Control** per impostazione predefinita. For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

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
   <td> mcSynch_&lt;nome_account_esterno&gt;<br /> </td> 
   <td> Flusso di lavoro:<br /> 
    <ul> 
     <li> <p>recupera l'elenco degli eventi elaborati dalle operazioni.</p> </li> 
     <li> <p>si sincronizza con la tabella NmsBroadLogMsg al fine di recuperare i titoli dei messaggi di consegna.</p> </li> 
     <li> <p>recupera i registri di consegna degli eventi non appena la sincronizzazione con la tabella NmsBroadLogMsg è stata completata.</p> </li> 
     <li> <p>si sincronizza con la tabella NmsTrackingUrl per recuperare il tracciamento degli URL di consegna.</p> </li> 
     <li> <p>recupera gli URL di tracciamento evento non appena la sincronizzazione con la tabella NmsTrackingUrl è stata completata.</p> </li> 
     <li> <p>consente di recuperare tutti gli indirizzi e-mail messi in quarantena ogni tre ore dopo l’invio di una consegna.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

