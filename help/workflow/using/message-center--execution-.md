---
product: campaign
title: Centro messaggi (Esecuzione)
description: Centro messaggi (Esecuzione)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 9%

---


# Centro messaggi (Esecuzione){#message-center-execution}

![](../../assets/common.svg)

I flussi di lavoro descritti di seguito sono installati con **Centro messaggi - Esecuzione** add-on per impostazione predefinita.

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
   <td> <span class="uicontrol">Update event status</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Questo flusso di lavoro ti consente di assegnare uno stato a un evento. Gli stati dell’evento sono i seguenti:<br /> 
    <ul> 
     <li> <p><strong>In sospeso</strong>: l’evento è in coda. Non è ancora stato associato alcun modello di messaggio.</p> </li> 
     <li> <p><strong>Consegna in sospeso</strong>: l’evento è in coda, è stato associato un modello di messaggio ed è attualmente in fase di elaborazione da parte della consegna.</p> </li> 
     <li> <p><strong>Inviato</strong>: questo stato viene copiato dai log di consegna. Significa che la consegna è stata inviata.</p> </li> 
     <li> <p><strong>Ignorato dalla consegna</strong>: questo stato viene copiato dai log di consegna. Significa che la consegna è stata ignorata.</p> </li> 
     <li> <p><strong>Errore di consegna</strong>: questo stato viene copiato dai log di consegna. Significa che la consegna non è riuscita.</p> </li> 
     <li> <p><strong>Evento non coperto</strong>: impossibile associare l'evento a un modello di messaggio. L’evento non verrà rielaborato.</p> </li> 
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

