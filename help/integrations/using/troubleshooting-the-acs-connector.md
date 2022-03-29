---
product: campaign
title: Risolvere i problemi relativi al connettore ACS
description: Risolvere i problemi relativi al connettore ACS
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: 1bb1365ce5a4eb89447c5d736a42cd470c7f3bba
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# Risolvere i problemi relativi al connettore ACS{#troubleshooting-the-acs-connector}

![](../../assets/v7-only.svg)

A seconda dell’implementazione, puoi affrontare diversi problemi comuni.

* **Quali sono le differenze di interfaccia utente tra Campaign Standard e Campaign v7?**

   Campaign Standard e Campaign v7 funzionano in modo molto simile. La maggior parte dei concetti sono gli stessi, ma in alcuni casi l&#39;approccio può essere leggermente diverso. Di seguito sono riportati alcuni dei concetti che possono essere diversi nel contesto del connettore ACS:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> destinatari (o qualsiasi altra dimensione di profilo)<br /> </td> 
   <td> profiles<br /> </td> 
  </tr> 
  <tr> 
   <td> elenco<br /> </td> 
   <td> pubblico<br /> </td> 
  </tr> 
  <tr> 
   <td> flussi di lavoro delle campagne, targeting dei flussi di lavoro<br /> </td> 
   <td> workflow<br /> </td> 
  </tr> 
  <tr> 
   <td> operazioni<br /> </td> 
   <td> campagne<br /> </td> 
  </tr> 
  <tr> 
   <td> applicazioni web<br /> </td> 
   <td> pagine di destinazione<br /> </td> 
  </tr> 
  <tr> 
   <td> estensione tabella e schema personalizzata<br /> </td> 
   <td> estensione di risorse e risorse personalizzate<br /> </td> 
  </tr> 
  <tr> 
   <td> membri della semina<br /> </td> 
   <td> profili di test<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **I destinatari della mia istanza Campaign v7 non sono sincronizzati o visibili ad Campaign Standard.**

   Questo caso può verificarsi per diversi motivi:

   * I destinatari sono stati appena creati o aggiornati in Campaign v7. La sincronizzazione viene attivata ogni 15 minuti. Ciò significa che i destinatari aggiornati o appena creati saranno visibili in Campaign Standard dopo la sincronizzazione successiva.
   * L’implementazione può essere stata impostata per sincronizzare solo i destinatari da cartelle specifiche. I destinatari di altre cartelle non sono sincronizzati.
   * Il destinatario può essere sincronizzato ma non visibile in Campaign Standard. Controlla la mappatura dei diritti della cartella.

* **Non trovo i campi del profilo su cui devo basare la query in Campaign Standard.**

   Per impostazione predefinita, 20 campi della tabella nms:recipient sono sincronizzati con Campaign Standard. Fare riferimento all’elenco dettagliato dei campi sincronizzati. Qualsiasi campo aggiuntivo da recuperare in Campaign Standard deve essere mappato e configurato dal tuo consulente.

   Per accertarti che il campo da utilizzare sia disponibile, puoi controllare la definizione della risorsa profilo da **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Inoltre, tutti i dati allegati ai destinatari e memorizzati nelle tabelle relative a nms:destinatari non vengono sincronizzati per impostazione predefinita in Campaign Standard.

   Per poter utilizzare comunque i dati correlati, puoi eseguire il targeting in Campaign v7 e aggiungere dati aggiuntivi come spiegato in [Sincronizzazione dei tipi di pubblico](../../integrations/using/synchronizing-audiences.md) oppure puoi consultare il tuo consulente per scoprire le possibilità di personalizzazione.

* **Sto utilizzando una dimensione di profilo diversa da quella predefinita di nms:recipient in Campaign v7, come posso sincronizzarle con Campaign Standard?**

   Campaign Standard utilizza una risorsa di targeting univoca denominata **profiles**. L’implementazione di base della funzione Campaign Standard Connect fornisce una mappatura predefinita tra i destinatari di Campaign v7 e i profili Campaign Standard.

   Se utilizzi un’altra dimensione di profilo in Campaign v7 o se ne utilizzi più, tutti devono essere mappati con profili Campaign Standard. Fai riferimento al tuo consulente per rispondere a questa particolare esigenza.

* **Voglio condividere un elenco di profili con Campaign Standard tramite un flusso di lavoro ma non riesco a trovare il mio pubblico in Campaign Standard**.

   I tipi di pubblico si trovano nella **[!UICONTROL Audiences]** in Campaign Standard. Hanno l’etichetta specificata nella **[!UICONTROL List update]** nel flusso di lavoro di Campaign v7. Sono soggetti alla mappatura delle cartelle definita durante l’implementazione.

   La prima cosa da verificare è se il flusso di lavoro è stato completato senza errori. Se noti un errore sul **[!UICONTROL List update]** attività, significa che la sincronizzazione con Campaign Standard potrebbe non essere riuscita. Per avere maggiori dettagli su cosa è andato storto, vai a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene i flussi di lavoro di sincronizzazione attivati da **[!UICONTROL List update]** esecuzione dell’attività.

   Inoltre, assicurati che il **[!UICONTROL Share with ACS]** è selezionata l’opzione **[!UICONTROL List update]** e che il flusso di lavoro è stato eseguito correttamente.

   Tieni presente che i profili dei destinatari contenuti nell’elenco devono essere stati sincronizzati con Campaign Standard prima dell’esecuzione del flusso di lavoro. Una volta condivisi con Campaign Standard, i destinatari dell’elenco vengono riconciliati con i profili Campaign Standard, il che significa che devono esistere lì. I destinatari dell’elenco che non possono essere riconciliati con i profili in Campaign Standard vengono ignorati.

   Se condividi un elenco di profili e non ne esegui la sincronizzazione con Campaign Standard, in Campaign Standard viene creato un pubblico Query vuoto che non può essere utilizzato.

* **Ho ricevuto una notifica che indica che un flusso di lavoro di sincronizzazione è in stato di errore. Cosa dovrei fare?**

   Controlla la configurazione dell’account esterno sia in Campaign Standard che in Campaign v7 testando la connessione:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **Non ho un gruppo di sicurezza disponibile per la mappatura delle cartelle tra Campaign v7 e Campaign Standard.**

   Devi innanzitutto sincronizzare i gruppi di sicurezza da **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Questa azione controlla i gruppi di sicurezza disponibili in Campaign Standard. Una volta sincronizzato, è possibile trovare i gruppi di sicurezza durante la configurazione della mappatura delle cartelle.

* **Non è possibile modificare un profilo, un pubblico o una pagina di destinazione in Campaign Standard. Cosa significa?**

   Le risorse sincronizzate da Campaign v7 sono in modalità di sola lettura in Campaign Standard, per garantire la coerenza dei dati. Se devi modificare uno di questi elementi, puoi farlo in Campaign v7 e replicare la modifica in Campaign Standard.

* **Gli errori si verificano nel [ACS] Flusso di lavoro di replica del registro di consegna del profilo. Cosa dovrei fare?**

   Nel caso in cui le istanze Campaign Classic e Campaign Standard siano utilizzate per inviare e-mail con URL tracciati, potrebbe verificarsi un problema con tagID URL duplicati durante la sincronizzazione. In questo caso, il **[ACS] Replica del registro di consegna del profilo** (newRcpDeliveryLogReplication) il flusso di lavoro continua a non riuscire con il seguente errore:

   ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

   Per risolvere il problema ed evitare che si verifichi di nuovo, aggiorna il **Aggiorna gli URL di tracciamento** (writerTrackingUrls) nel flusso di lavoro e aggiungi il prefisso &quot;ACS&quot; all&#39;espressione sorgente @tagId.
