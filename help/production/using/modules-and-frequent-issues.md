---
product: campaign
title: Moduli e problemi frequenti
description: Moduli e problemi frequenti
feature: Monitoring, Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 9%

---

# Moduli e problemi frequenti{#modules-and-frequent-issues}



Elenco dei moduli interessati da problemi frequenti:

<table> 
 <thead> 
  <tr> 
   <th> Modulo </th> 
   <th> Ambito di esecuzione </th> 
   <th> Risoluzione dei problemi </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> esporta </td> 
   <td> Esecuzione di un processo di esportazione<br /> </td> 
   <td> L'operatore che ha pianificato l'esportazione deve riavviarla. Delta o riavvio completo.<br /> </td> 
  </tr> 
  <tr> 
   <td> importa </td> 
   <td> Esecuzione di un processo di importazione<br /> </td> 
   <td> L'operatore che ha pianificato l'esportazione deve riavviarla. Verificare la presenza di duplicati nel database.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lettura della casella di posta non recapitata<br /> </td> 
   <td> Seleziona questo modulo se i messaggi non recapitati non vengono più inoltrati.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Consegna e-mail<br /> </td> 
   <td> Seleziona questo modulo se le e-mail non vengono più inviate.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Gestisce le statistiche di connessione MTA<br /> </td> 
   <td> Seleziona questo modulo se le e-mail non vengono più inviate.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Scrittura registro<br /> </td> 
   <td> Se nei file di registro mancano alcuni registri, verificare che il modulo utilizzi la porta 6666. Fai riferimento a <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Elenco delle porte aperte</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracciamento </td> 
   <td> Consolidamento e recupero dei registri di tracciamento<br /> </td> 
   <td> Seleziona questo modulo se i registri di tracciamento non vengono più inoltrati.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Tracciamento della scrittura del registro e rimozione del server<br /> </td> 
   <td> Controlla questo modulo se i registri di tracciamento non vengono più inoltrati e non ci sono tracce di registri nei file sul server. Fai riferimento a <a href="../../production/using/tracking-logs-issues.md" target="_blank">Tracking dei problemi dei registri</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> watchdog </td> 
   <td> Istanza di avvio e monitoraggio<br /> </td> 
   <td> Seleziona questo modulo se non si avviano processi.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Server applicazioni (HTTP e SOAP)<br /> </td> 
   <td> Seleziona questo modulo se la console e le connessioni web non funzionano e attiva un <strong>xtk:session</strong> errore di tipo<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controlla l’esecuzione dell’istanza del flusso di lavoro.<br /> </td> 
   <td> In caso di problemi, riavviare il modulo. Se necessario, applica la procedura per aumentare la precisione dei registri descritta nel <a href="../../production/using/log-precision.md" target="_blank">Precisione dei registri</a> sezione.<br /> </td> 
  </tr> 
 </tbody> 
</table>
