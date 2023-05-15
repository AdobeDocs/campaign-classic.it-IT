---
product: campaign
title: Moduli e problemi frequenti
description: Moduli e problemi frequenti
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

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
   <td> esportare </td> 
   <td> Esecuzione di un processo di esportazione<br /> </td> 
   <td> L’operatore che ha pianificato l’esportazione deve riavviarla. Delta o riavvio completo.<br /> </td> 
  </tr> 
  <tr> 
   <td> importare </td> 
   <td> Esecuzione di un processo di importazione<br /> </td> 
   <td> L’operatore che ha pianificato l’esportazione deve riavviarla. Controlla la presenza di duplicati nel database.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lettura della casella di posta non recapitata<br /> </td> 
   <td> Controlla questo modulo se le mail non recapitate non vengono più inoltrate.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Invia e-mail<br /> </td> 
   <td> Controlla questo modulo se le e-mail non vengono più inviate.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantiene le statistiche di connessione MTA<br /> </td> 
   <td> Controlla questo modulo se le e-mail non vengono più inviate.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Scrittura del registro<br /> </td> 
   <td> Se mancano alcuni log nei file di log, controlla che il modulo utilizzi la porta 6666. Fai riferimento a <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Elenco delle porte aperte</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracciamento </td> 
   <td> Consolidamento e recupero dei registri di tracciamento<br /> </td> 
   <td> Controlla questo modulo se i registri di tracciamento non sono più inoltrati.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Tracking del server di scrittura e pulizia del registro<br /> </td> 
   <td> Controlla questo modulo se i log di tracciamento non sono più inoltrati e non ci sono tracce di log nei file sul server. Fai riferimento a <a href="../../production/using/tracking-logs-issues.md" target="_blank">Tracking dei problemi dei log</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> cane da guardia </td> 
   <td> Avvio e monitoraggio dell'istanza<br /> </td> 
   <td> Controlla questo modulo se non iniziano i processi.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Server applicazioni (HTTP e SOAP)<br /> </td> 
   <td> Controlla questo modulo se la console e le connessioni web non funzionano e attiva un <strong>xtk:session</strong> errore di tipo<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controlla l’esecuzione dell’istanza del flusso di lavoro.<br /> </td> 
   <td> In caso di problemi, riavviare il modulo. Se necessario, applicare la procedura per aumentare la precisione dei tronchi descritti nella <a href="../../production/using/log-precision.md" target="_blank">Precisione dei log</a> sezione .<br /> </td> 
  </tr> 
 </tbody> 
</table>
