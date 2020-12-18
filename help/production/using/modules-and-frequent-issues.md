---
solution: Campaign Classic
product: campaign
title: Moduli e problemi frequenti
description: Moduli e problemi frequenti
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---


# Moduli e problemi frequenti{#modules-and-frequent-issues}

Di seguito è riportato un elenco di moduli interessati da problemi frequenti:

<table> 
 <thead> 
  <tr> 
   <th> Modulo </th> 
   <th> Ambito esecuzione </th> 
   <th> Risoluzione dei problemi </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> export </td> 
   <td> Esecuzione di un processo di esportazione<br /> </td> 
   <td> L'operatore che ha pianificato l'esportazione deve riavviarla. Riavvio delta o completo.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Esecuzione di un processo di importazione<br /> </td> 
   <td> L'operatore che ha pianificato l'esportazione deve riavviarla. Verificare la presenza di duplicati nel database.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Lettura della casella di posta indesiderata<br /> </td> 
   <td> Controllare questo modulo se i messaggi di rimbalzo non vengono più inoltrati.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Invia e-mail<br /> </td> 
   <td> Controllare il modulo se le e-mail non vengono più inviate.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Mantiene le statistiche di connessione MTA<br /> </td> 
   <td> Controllare il modulo se le e-mail non vengono più inviate.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Scrittura del registro<br /> </td> 
   <td> Se alcuni file di registro mancano, verificare che il modulo utilizzi la porta 6666. Fare riferimento a <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Elenco delle porte aperte</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> tracking </td> 
   <td> Consolidamento e recupero dei registri di tracciamento<br /> </td> 
   <td> Controllare questo modulo se i registri di monitoraggio non vengono più inoltrati.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Tracciamento del registro scrittura ed eliminazione del server<br /> </td> 
   <td> Controllare questo modulo se i registri di monitoraggio non vengono più inoltrati e non ci sono tracce di log nei file sul server. Fare riferimento a <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemi relativi ai registri di tracciamento</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> cane da guardia </td> 
   <td> Avvio e monitoraggio dell'istanza<br /> </td> 
   <td> Controllare questo modulo se non viene avviato alcun processo.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Server applicazione (HTTP e SOAP)<br /> </td> 
   <td> Controllare questo modulo se la console e le connessioni Web non funzionano e attivare un errore di tipo <strong>xtk:session</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Controlla l'esecuzione dell'istanza del flusso di lavoro.<br /> </td> 
   <td> In caso di problemi, riavviare il modulo. Se necessario, applicare la procedura per aumentare la precisione dei log descritti nella sezione <a href="../../production/using/log-precision.md" target="_blank">Precisione log</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

