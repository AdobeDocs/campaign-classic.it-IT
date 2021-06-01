---
product: campaign
title: Centro messaggi (Esecuzione)
description: Centro messaggi (Esecuzione)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# Centro messaggi (Esecuzione){#message-center-execution}

I flussi di lavoro descritti di seguito sono installati per impostazione predefinita con il modulo **Centro messaggi - Esecuzione** . Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../message-center/using/about-transactional-messaging.md).

Per ulteriori informazioni su come configurare i flussi di lavoro tecnici relativi al modulo Centro messaggi, consulta [questa pagina](../../message-center/using/technical-workflows.md).

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
   <td> Questo flusso di lavoro ti consente di assegnare uno stato a un evento. Gli stati dell'evento sono i seguenti:<br /> 
    <ul> 
     <li> <p><strong>In sospeso</strong>: l’evento è in coda. Non è ancora stato associato alcun modello di messaggio.</p> </li> 
     <li> <p><strong>Consegna</strong> in sospeso: l’evento è in coda, è stato associato un modello di messaggio ed è attualmente in fase di elaborazione da parte della consegna.</p> </li> 
     <li> <p><strong>Inviato</strong>: questo stato viene copiato dai log di consegna. Significa che la consegna è stata inviata.</p> </li> 
     <li> <p><strong>Ignorato dalla consegna</strong>: questo stato viene copiato dai log di consegna. Significa che la consegna è stata ignorata.</p> </li> 
     <li> <p><strong>Errore</strong> di consegna: questo stato viene copiato dai log di consegna. Significa che la consegna non è riuscita.</p> </li> 
     <li> <p><strong>Evento non trattato</strong>: impossibile associare l'evento a un modello di messaggio. L’evento non verrà rielaborato.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Eventi batch di elaborazione</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di mettere gli eventi batch in una coda prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione di eventi in tempo reale</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di mettere gli eventi in tempo reale in una coda prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
 </tbody> 
</table>

