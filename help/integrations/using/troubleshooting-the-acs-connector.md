---
product: campaign
title: Risolvere i problemi relativi al connettore ACS
description: Risolvere i problemi relativi al connettore ACS
feature: ACS Connector, Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
hidefromtoc: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---

# Risolvere i problemi relativi al connettore ACS{#troubleshooting-the-acs-connector}



A seconda dell’implementazione, puoi riscontrare diversi problemi comuni.

* **Quali sono le differenze a livello di interfaccia utente tra Campaign Standard e Campaign v7?**

  Campaign Standard e Campaign v7 funzionano in modo molto simile. La maggior parte dei concetti sono gli stessi, ma in alcuni casi l’approccio può essere leggermente diverso. Di seguito sono riportati alcuni dei concetti che potrebbero differire nel contesto del connettore ACS:

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
   <td> profili<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> pubblico<br /> </td> 
  </tr> 
  <tr> 
   <td> flussi di lavoro per campagne, flussi di lavoro di targeting<br /> </td> 
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
   <td> tabella personalizzata ed estensione dello schema<br /> </td> 
   <td> risorsa personalizzata ed estensione della risorsa<br /> </td> 
  </tr> 
  <tr> 
   <td> membri seed<br /> </td> 
   <td> profili di test<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **I destinatari della mia istanza di Campaign v7 non sono sincronizzati o visibili a Campaign Standard.**

  Questo caso può verificarsi per diversi motivi:

   * I destinatari sono stati appena creati o aggiornati in Campaign v7. La sincronizzazione viene attivata ogni 15 minuti. Ciò significa che i destinatari aggiornati o appena creati saranno visibili in Campaign Standard dopo la successiva sincronizzazione.
   * L’implementazione può essere impostata per sincronizzare solo i destinatari da cartelle specifiche. I destinatari di altre cartelle non sono sincronizzati.
   * Il destinatario può essere sincronizzato ma non visibile in Campaign Standard. Controlla la mappatura dei diritti della cartella.

* **Non trovo i campi del profilo su cui devo basare la query in Campaign Standard.**

  Per impostazione predefinita, 20 campi della tabella nms:recipient sono sincronizzati con Campaign Standard. Consulta l’elenco dettagliato dei campi sincronizzati. Qualsiasi campo aggiuntivo da recuperare in Campaign Standard deve essere mappato e configurato dal tuo consulente.

  Per assicurarti che il campo da utilizzare sia disponibile, puoi controllare la definizione della risorsa profilo da **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

  Inoltre, tutti i dati allegati ai destinatari e memorizzati nelle tabelle relative a nms:recipients non vengono sincronizzati per impostazione predefinita con Campaign Standard.

  Per poter continuare a utilizzare i dati correlati, puoi eseguire il targeting in Campaign v7 e aggiungere dati aggiuntivi come spiegato nella [Sincronizzare i tipi di pubblico](../../integrations/using/synchronizing-audiences.md) oppure puoi rivolgerti al tuo consulente per scoprire le possibilità di personalizzazione.

* **In Campaign v7, utilizzo una dimensione di profilo diversa da nms:recipient predefinita, come posso sincronizzarle con Campaign Standard?**

  Campaign Standard utilizza una risorsa di targeting univoca denominata **profili**. L’implementazione di base della funzione Campaign Standard Connect fornisce una mappatura predefinita tra i destinatari di Campaign v7 e i profili di Campaign Standard.

  Se utilizzi un’altra dimensione di profilo in Campaign v7, o se ne utilizzi diverse, tutte devono essere mappate con i profili di Campaign Standard. Per rispondere a questa esigenza specifica, rivolgiti al tuo consulente.

* **Voglio condividere un elenco di profili con Campaign Standard tramite un flusso di lavoro, ma non posso trovare il mio pubblico in Campaign Standard**.

  I tipi di pubblico si trovano in **[!UICONTROL Audiences]** in Campaign Standard. Hanno l’etichetta specificata nel **[!UICONTROL List update]** attività nel flusso di lavoro di Campaign v7. Sono soggette alla mappatura delle cartelle definita durante l’implementazione.

  La prima cosa da verificare è se il flusso di lavoro è stato completato senza errori. Se noti un errore in **[!UICONTROL List update]** significa che la sincronizzazione con Campaign Standard potrebbe non essere riuscita. Per visualizzare ulteriori dettagli su ciò che è andato storto, vai a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene flussi di lavoro di sincronizzazione attivati da **[!UICONTROL List update]** esecuzione dell’attività.

  Inoltre, assicurati che le **[!UICONTROL Share with ACS]** l&#39;opzione è selezionata in **[!UICONTROL List update]** e che il flusso di lavoro sia stato eseguito correttamente.

  I profili dei destinatari contenuti nell’elenco devono essere stati sincronizzati con Campaign Standard prima dell’esecuzione del flusso di lavoro. Una volta condiviso con Campaign Standard, i destinatari dell’elenco vengono riconciliati con i profili Campaign Standard, il che significa che devono esistere lì. I destinatari dell’elenco che non possono essere riconciliati con i profili in Campaign Standard vengono ignorati.

  Se condividi un elenco costituito da profili e nessuno di questi è sincronizzato con Campaign Standard, in Campaign Standard viene creato un pubblico di tipo Query vuoto che non può essere utilizzato.

* **Ho ricevuto una notifica che indica che un flusso di lavoro di sincronizzazione è in stato di errore. Cosa devo fare?**

  Controlla la configurazione dell’account esterno in Campaign Standard e Campaign v7 verificando la connessione:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **Non sono disponibile gruppi di sicurezza per la mappatura di cartelle tra Campaign v7 e Campaign Standard.**

  Devi prima sincronizzare i gruppi di sicurezza da **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Questa azione controlla i gruppi di sicurezza disponibili in Campaign Standard. Una volta sincronizzati, è possibile trovare i gruppi di sicurezza durante la configurazione della mappatura delle cartelle.

* **Non è possibile modificare un profilo, un pubblico o una pagina di destinazione in Campaign Standard. Che cosa significa?**

  Le risorse sincronizzate da Campaign v7 sono in modalità di sola lettura in Campaign Standard, per garantire la coerenza dei dati. Se devi modificare uno di questi elementi, puoi farlo in Campaign v7 e quindi replicare la modifica in Campaign Standard.

* **Si verificano errori in [ACS] Flusso di lavoro di replica del registro di consegna del profilo. Cosa devo fare?**

  Se per inviare e-mail con URL tracciati vengono utilizzate sia le istanze di Campaign Classic che di Campaign Standard, durante la sincronizzazione potrebbe verificarsi un problema relativo agli ID di tag URL duplicati. In questo caso, il **[ACS] Replica del registro di consegna del profilo** Il flusso di lavoro di (newRcpDeliveryLogReplication) non riesce e viene restituito il seguente errore:

  ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

  Per risolvere il problema ed evitare che si verifichi di nuovo, aggiorna il **Aggiorna URL di tracciamento** (writerTrackingUrls) nel flusso di lavoro e aggiungi il prefisso &quot;ACS&quot; all’espressione di origine @tagId.
