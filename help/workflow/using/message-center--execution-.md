---
product: campaign
title: Centro messaggi (esecuzione)
description: Centro messaggi (esecuzione)
feature: Workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 2%

---


# Centro messaggi (esecuzione){#message-center-execution}



I flussi di lavoro descritti di seguito vengono installati con **Centro messaggi - Esecuzione** componente aggiuntivo per impostazione predefinita.

Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

![](assets/do-not-localize/v7.jpeg)[Documentazione di Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)

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
   <td> Questo flusso di lavoro ti consente di assegnare uno stato a un evento. Gli stati degli eventi sono i seguenti:<br /> 
    <ul> 
     <li> <p><strong>In sospeso</strong>: l’evento è in coda. Non è ancora stato associato alcun modello di messaggio.</p> </li> 
     <li> <p><strong>Consegna in sospeso</strong>: l’evento è in coda, gli è stato associato un modello di messaggio ed è attualmente in fase di elaborazione da parte della consegna.</p> </li> 
     <li> <p><strong>Inviato</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata inviata.</p> </li> 
     <li> <p><strong>Ignorato dalla consegna</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata ignorata.</p> </li> 
     <li> <p><strong>Errore di consegna</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna non è riuscita.</p> </li> 
     <li> <p><strong>Evento non coperto</strong>: l’evento non è stato associato a un modello di messaggio. L’evento non verrà rielaborato.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione di eventi batch</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Questo flusso di lavoro ti consente di mettere in coda gli eventi batch prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione di eventi in tempo reale</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di mettere in coda eventi in tempo reale prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
 </tbody> 
</table>

