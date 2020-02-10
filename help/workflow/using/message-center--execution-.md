---
title: Centro messaggi (esecuzione)
seo-title: Centro messaggi (esecuzione)
description: Centro messaggi (esecuzione)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Centro messaggi (esecuzione){#message-center-execution}

Per impostazione predefinita, i flussi di lavoro descritti di seguito sono installati con il modulo **Centro messaggi - Esecuzione** . Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../message-center/using/about-transactional-messaging.md).

Per ulteriori informazioni su come configurare i flussi di lavoro tecnici relativi al modulo Centro messaggi, consulta [questa pagina](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aggiorna stato</span> evento <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span><br /> </td> 
   <td> Questo flusso di lavoro consente di assegnare uno stato a un evento. Gli stati dell'evento sono i seguenti:<br /> 
    <ul> 
     <li> <p><strong>In sospeso</strong>: l'evento è in coda. Non è ancora stato associato alcun modello di messaggio.</p> </li> 
     <li> <p><strong>In attesa di consegna</strong>: l'evento si trova in una coda, al quale è stato associato un modello di messaggio ed è attualmente in fase di elaborazione da parte del destinatario.</p> </li> 
     <li> <p><strong>Inviato</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata inviata.</p> </li> 
     <li> <p><strong>Ignorato dalla consegna</strong>: questo stato viene copiato dai registri di consegna. Significa che la consegna è stata ignorata.</p> </li> 
     <li> <p><strong>Errore</strong>di consegna: questo stato viene copiato dai registri di consegna. Significa che la consegna non è riuscita.</p> </li> 
     <li> <p><strong>Evento non coperto</strong>: l'evento non è stato associato a un modello di messaggio. L'evento non verrà rielaborato.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione degli eventi</span> batch <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span><br /> </td> 
   <td> Questo flusso di lavoro consente di mettere in coda gli eventi batch prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Elaborazione di eventi</span> in tempo reale <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span><br /> </td> 
   <td> Questo flusso di lavoro consente di mettere in coda gli eventi in tempo reale prima di associarli a un modello di messaggio. <br /> </td> 
  </tr> 
 </tbody> 
</table>

