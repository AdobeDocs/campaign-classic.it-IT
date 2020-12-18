---
solution: Campaign Classic
product: campaign
title: Centro messaggi (Esecuzione)
description: Centro messaggi (Esecuzione)
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# Centro messaggi (Esecuzione){#message-center-execution}

I flussi di lavoro descritti di seguito vengono installati con il modulo **Message Center - Execution** per impostazione predefinita. Per ulteriori informazioni su questo modulo, consultare la sezione [sezione](../../message-center/using/about-transactional-messaging.md).

Per ulteriori informazioni su come configurare i flussi di lavoro tecnici relativi al modulo Centro messaggi, fare riferimento a [questa pagina](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update event status</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di assegnare uno stato a un evento. Gli stati dell'evento sono i seguenti:<br /> 
    <ul> 
     <li> <p><strong>In sospeso</strong>: l'evento è in coda. Non è ancora stato associato alcun modello di messaggio.</p> </li> 
     <li> <p><strong>In attesa di consegna</strong>: l'evento si trova in una coda, al quale è stato associato un modello di messaggio ed è attualmente in fase di elaborazione da parte del destinatario.</p> </li> 
     <li> <p><strong>Inviato</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata inviata.</p> </li> 
     <li> <p><strong>Ignorato dalla consegna</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata ignorata.</p> </li> 
     <li> <p><strong>Errore</strong> di consegna: questo stato viene copiato dai registri di consegna. Significa che la consegna non è riuscita.</p> </li> 
     <li> <p><strong>Evento non coperto</strong>: l'evento non è stato associato a un modello di messaggio. L'evento non verrà rielaborato.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione degli eventi batch</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di mettere in coda gli eventi batch prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione di eventi in tempo reale</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di mettere in coda gli eventi in tempo reale prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
 </tbody> 
</table>

