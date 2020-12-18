---
solution: Campaign Classic
product: campaign
title: Risoluzione dei problemi relativi al connettore ACS
description: Risoluzione dei problemi relativi al connettore ACS
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---


# Risoluzione dei problemi relativi al connettore ACS{#troubleshooting-the-acs-connector}

A seconda dell’implementazione, potete affrontare diversi problemi comuni.

* **Quali sono le differenze di interfaccia tra Campaign Standard e Campaign v7?**

   Campaign Standard e Campaign v7 funzionano in modo molto simile. La maggior parte dei concetti sono identici, ma in alcuni casi l&#39;approccio può essere leggermente diverso. Di seguito sono riportati alcuni dei concetti che possono essere diversi nel contesto del connettore ACS:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> destinatari (o qualsiasi altra dimensione del profilo)<br /> </td> 
   <td> profile<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> flussi di lavoro campagna, flussi di lavoro di targeting<br /> </td> 
   <td> workflow<br /> </td> 
  </tr> 
  <tr> 
   <td> operations<br /> </td> 
   <td> campagne<br /> </td> 
  </tr> 
  <tr> 
   <td> applicazioni Web<br /> </td> 
   <td> pagine di destinazione<br /> </td> 
  </tr> 
  <tr> 
   <td> estensione personalizzata tabella e schema<br /> </td> 
   <td> estensione risorse personalizzate<br /> </td> 
  </tr> 
  <tr> 
   <td> seed members<br /> </td> 
   <td> profili di prova<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **I destinatari dell&#39;istanza Campaign v7 non sono sincronizzati o visibili ai Campaign Standard.**

   Questo caso può verificarsi per diversi motivi:

   * I destinatari sono stati appena creati o aggiornati in Campaign v7. La sincronizzazione viene attivata ogni 15 minuti. Ciò significa che i destinatari aggiornati o appena creati saranno visibili in Campaign Standard dopo la sincronizzazione successiva.
   * L’implementazione può essere stata impostata per sincronizzare solo i destinatari da cartelle specifiche. I destinatari di altre cartelle non vengono sincronizzati.
   * Il destinatario può essere sincronizzato ma non visibile in Campaign Standard. Controllate la mappatura dei diritti di cartella.

* **Non trovo i campi del profilo su cui devo basare la query in Campaign Standard.**

   Per impostazione predefinita, 20 campi della tabella nms:Recipients sono sincronizzati con Campaign Standard. Fare riferimento all&#39;elenco dettagliato dei campi sincronizzati. Qualsiasi campo aggiuntivo da recuperare in Campaign Standard deve essere mappato e configurato dal consulente.

   Per essere certi che il campo che si desidera utilizzare sia disponibile, è possibile controllare la definizione delle risorse del profilo da **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Inoltre, tutti i dati associati ai destinatari e memorizzati nelle tabelle correlate a nms:Recipients non sono sincronizzati per impostazione predefinita con Campaign Standard.

   Per poter ancora utilizzare i dati correlati, puoi eseguire il targeting in Campaign v7 e aggiungere dati aggiuntivi come spiegato nella sezione [Sincronizzazione dei tipi di pubblico](../../integrations/using/synchronizing-audiences.md), oppure consultare il tuo consulente per esplorare le possibilità di personalizzazione.

* **Sto utilizzando un&#39;altra dimensione di profilo rispetto a quella predefinita di nms:destinatario in Campaign v7, come posso sincronizzarle con il Campaign Standard?**

   Campaign Standard utilizza una risorsa di targeting univoca denominata **profile**. L&#39;implementazione di base della funzione Campaign Standard Connect fornisce una mappatura predefinita tra i destinatari di Campaign v7 e i profili Campaign Standard.

   Se utilizzi un’altra dimensione di profilo in Campaign v7 o se ne utilizzi più, questi devono essere mappati con profili Campaign Standard. Per rispondere a questa particolare esigenza, fare riferimento al proprio consulente.

* **Voglio condividere un elenco di profili con Campaign Standard tramite un flusso di lavoro, ma non riesco a trovare il pubblico in Campaign Standard**.

   Le audience si trovano nel menu **[!UICONTROL Audiences]** in Campaign Standard. Hanno l&#39;etichetta specificata nell&#39;attività **[!UICONTROL List update]** nel flusso di lavoro di Campaign v7. Sono soggetti alla mappatura delle cartelle definita durante l’implementazione.

   La prima cosa da verificare è se il flusso di lavoro è terminato senza errori. Se si nota un errore sull&#39;attività **[!UICONTROL List update]**, significa che la sincronizzazione con Campaign Standard potrebbe non essere riuscita. Per visualizzare maggiori dettagli su cosa è andato storto, andare a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene i flussi di lavoro di sincronizzazione attivati dall&#39;esecuzione dell&#39;attività **[!UICONTROL List update]**.

   Inoltre, accertatevi che l&#39;opzione **[!UICONTROL Share with ACS]** sia selezionata nell&#39;attività **[!UICONTROL List update]** e che il flusso di lavoro sia stato eseguito correttamente.

   I profili dei destinatari contenuti nell&#39;elenco devono essere stati sincronizzati con i Campaign Standard prima dell&#39;esecuzione del flusso di lavoro. Una volta condiviso con l&#39;Campaign Standard, i destinatari dell&#39;elenco vengono riconciliati con i profili Campaign Standard, il che significa che devono esistere. I destinatari dell&#39;elenco che non possono essere riconciliati con i profili in Campaign Standard vengono ignorati.

   Se condividete un elenco composto da profili e non ne viene sincronizzato nessuno con il Campaign Standard, viene creata un&#39;audience Query vuota nel Campaign Standard che non può essere utilizzata.

* **Ho ricevuto una notifica in cui si informa che un flusso di lavoro di sincronizzazione è in stato di errore. Cosa devo fare?**

   Verifica la configurazione dell’account esterno sia in Campaign Standard che in Campaign v7 verificando la connessione:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **Non ho un gruppo di sicurezza disponibile per la mappatura delle cartelle tra Campaign v7 e Campaign Standard.**

   È innanzitutto necessario sincronizzare i gruppi di sicurezza da **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Questa azione verifica i gruppi di sicurezza disponibili in Campaign Standard. Una volta sincronizzata, potete trovare i gruppi di sicurezza durante la configurazione della mappatura delle cartelle.

* **Non è possibile modificare un profilo, un&#39;audience o una pagina di destinazione in Campaign Standard. Cosa significa?**

   Le risorse sincronizzate da Campaign v7 sono in modalità di sola lettura in Campaign Standard, per garantire la coerenza dei dati. Se dovete modificare uno di questi elementi, potete farlo in Campaign v7 e replicare la modifica in Campaign Standard.

