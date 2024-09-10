---
product: campaign
title: Configurazione delle opzioni di Campaign
description: Scopri come configurare le opzioni di Campaign
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '3831'
ht-degree: 1%

---

# Elenco delle opzioni di Campaign Classic{#configuring-campaign-options}

Il nodo **[!UICONTROL Administration / Platform / Options]** consente di configurare le opzioni di Adobe Campaign. Alcuni sono incorporati durante l’installazione di Campaign, altri possono essere aggiunti manualmente quando necessario. Le opzioni disponibili variano a seconda dei pacchetti installati con l’istanza.


>[!CAUTION]
>
>* Le opzioni non elencate in questa pagina sono solo interne e **non devono essere modificate**.
>
>* La modifica o l’aggiornamento delle opzioni di Adobe Campaign può essere eseguito solo da utenti esperti.

## Consegna {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Recapito messaggi_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Data dell'ultimo broadLogMsg recuperato dall'istanza di recapito messaggi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recapito messaggi_UltimoRegistroMessaggiSent</span> <br /> </td> 
   <td> Data dell'ultimo broadLogMsg inviato all'istanza di recapito messaggi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificatore dei rapporti di consegna. Contatta il supporto per ottenere il tuo identificatore.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Elenco di schemi per i quali si desidera utilizzare gli indirizzi di prova per il rendering della casella in entrata. (i nomi degli elementi sono separati da virgole). Esempio: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">INDIRIZZO_CCN_EMTA</span> </td> 
   <td> Indirizzo e-mail Ccn a cui l’MTA avanzato invierà una copia non elaborata delle e-mail inviate. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Consente all’operatore responsabile della consegna di confermare l’invio, se un operatore o un gruppo di operatori specifico è designato per avviare una consegna nelle proprietà della consegna.</p><p> A questo scopo, attiva l’opzione immettendo "1" come valore. Per disattivare questa opzione, immettere "0".</p><p> Il processo di conferma dell’invio funzionerà quindi come predefinito: solo l’operatore o il gruppo di operatori designati per l’invio nelle proprietà di consegna (o un amministratore) sarà in grado di confermare ed eseguire l’invio. Consulta <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">questa sezione</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign utilizza una variabile globale "Nms_DefaultRcpSchema" per la finestra di dialogo con il database dei destinatari predefinito (nms:recipient).<br /> Il valore dell'opzione deve corrispondere al nome dello schema che corrisponde alla tabella dei destinatari esterna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Numero minimo di destinatari affinché una consegna possa essere considerata come principale nel report di fatturazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Provider del servizio di routing predefinito per i nuovi modelli.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Dimensione minima del batch (numero di righe) per l'inserimento di broadLogs durante la preparazione di una consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Soglia di durata batch (numero di millisecondi) sotto la quale la dimensione batch per l'inserimento di broadLogs viene raddoppiata durante la preparazione di una consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Raggruppamento delle dimensioni delle parti di consegna durante l'analisi delle consegne mid-sourcing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Periodo di consegna predefinito per una consegna (in secondi).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Espressioni regolari per la normalizzazione dei messaggi di consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> L'immissione di "1" come valore consente di escludere i destinatari che non desiderano più essere contattati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> L'immissione di "1" come valore consente di ignorare automaticamente i duplicati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Consente di definire la sintassi dell'indirizzo di errore utilizzato durante la risposta a un messaggio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Consente di definire la sintassi dell'indirizzo mittente utilizzato per l'invio di un messaggio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Consente di definire un limite di timeout (in secondi) per ottenere una risposta dal server durante il recupero di un’immagine scaricata da un URL personalizzato e allegata a un’e-mail. Se questo valore viene superato, il messaggio non può essere inviato. Il valore predefinito è 60 secondi.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Consente di definire la dimensione massima (in byte) consentita per un’immagine scaricata da un URL personalizzato e allegata a un messaggio e-mail. Il valore predefinito è 100.000 byte (100 KB). Quando si invia una bozza e si scaricano le immagini per elaborare l'e-mail, se le dimensioni di un'immagine superano questo valore o si verifica un problema di download, nei registri di consegna viene visualizzato un errore e la consegna della bozza non riesce.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Consente di impostare un numero massimo di allegati in un messaggio e-mail o in un modello e-mail transazionale. Se questo valore viene superato, viene visualizzato un avviso nei registri di analisi della consegna o durante la pubblicazione del modello e-mail transazionale. Il valore predefinito è 1 allegato.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Numero massimo di tentativi durante l'analisi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Script di pubblicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Disattiva il conteggio broadLogMsg per i messaggi push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Visualizza il peso del messaggio nell'assistente alla consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Indirizzo e-mail predefinito di errore a livello di istanza utilizzato per la consegna e-mail se lasciato vuoto dall'utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Indirizzo e-mail predefinito del mittente a livello di istanza utilizzato per la consegna e-mail se lasciato vuoto dall'utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Indirizzo e-mail predefinito di risposta a livello di istanza utilizzato per la consegna e-mail se lasciato vuoto dall'utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nome comune del cliente. Utilizzato in alcuni messaggi di avviso visualizzati ai destinatari.<br /> "Stai ricevendo questo messaggio perché sei stato in contatto con "Organization" o un’azienda affiliata. Per non ricevere più messaggi da "Organization"<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Etichetta e-mail predefinita "Da" a livello di istanza utilizzata per la consegna e-mail se lasciata vuota dall'utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Etichetta e-mail di risposta predefinita a livello di istanza utilizzata per la consegna e-mail se lasciata vuota dall'utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Periodo tra due tentativi di un messaggio e-mail (in secondi).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Periodo di nuovi tentativi per i messaggi e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formula utilizzata per calcolare la ponderazione di un messaggio per una consegna provvisoria.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Elenco di indirizzi e-mail di inoltro autorizzati (dal modulo di elaborazione della posta in entrata). Gli indirizzi devono essere separati da virgole (o * per consentire tutti). Esempio: xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Chiave AES utilizzata nel servlet 'lineImage' per codificare gli URL (canale LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Sul canale "email" (usa come impostazione predefinita) : numero massimo di errori accettati, per gli errori SOFT durante l'invio prima di mettere in quarantena il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Sul canale "email" (usa come impostazione predefinita) : periodo minimo da trascorrere dal precedente errore SOFT di riferimento, prima di prendere in considerazione un nuovo errore SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Sul canale "mobile": numero massimo di errori accettati, per errori SOFT durante l'invio prima di mettere in quarantena il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Sul canale "mobile": periodo minimo da trascorrere dal precedente errore SOFT di riferimento, prima di prendere in considerazione un nuovo errore SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Consente di specificare un periodo massimo (espresso in ore) per limitare il numero di broadLog recuperati ogni volta che viene eseguito il flusso di lavoro di sincronizzazione.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Numero massimo di chiamate nella sessione MidSourcing, che possono essere eseguite in parallelo (3 per impostazione predefinita).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Ritardo personalizzato (in minuti) dopo il quale una consegna viene considerata "ritardata". Il valore predefinito è 30 minuti.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Questa opzione viene utilizzata dal flusso di lavoro tecnico <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> durante il conteggio del numero di consegne in esecuzione.</p>Consente di definire il numero di giorni oltre i quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.</p><p>Per impostazione predefinita, il valore è impostato su "7", il che significa che verranno escluse le consegne incoerenti precedenti a 7 giorni.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Riga 1 dell'indirizzo del mittente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Riga 3 dell'indirizzo del mittente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Riga 4 dell'indirizzo del mittente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Riga 6 dell'indirizzo del mittente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Riga 7 dell'indirizzo del mittente.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> L’URL del server della pagina speculare (per impostazione predefinita, deve essere identico a NmsTracking_ServerUrl).<br /> È il valore predefinito delle consegne e-mail quando l'URL non è specificato nella definizione di indirizzamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parametri dei messaggi SMS inviati: informazioni trasmesse al gateway SMS per indicare la priorità del messaggio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Numero di tentativi durante l'invio di messaggi SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Periodo durante il quale verranno eseguiti nuovi tentativi di messaggi SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Data ultimo consolidamento per le statistiche di <span class="uicontrol">NmsUserAgent</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nome dell'opzione che contiene i segmenti Web e i relativi stati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Attiva/disattiva il supporto di caratteri speciali per Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caratteri validi per un indirizzo e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Aggiungi questa opzione con il valore "0" per disabilitare l'edizione del codice XML delle consegne (fai clic con il pulsante destro del mouse / <span class="uicontrol">Modifica origine XML</span> o <span class="uicontrol">scelta rapida CTRL + F4</span>).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Risorse {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Posizione delle risorse da pubblicare nella console client di Adobe Campaign. Vedi <a href="../../delivery/using/formatting.md#image-referencing">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Posizione delle risorse da visualizzare in anteprima nella console client di Adobe Campaign. Vedi <a href="../../delivery/using/formatting.md#image-referencing">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Elenco delle maschere URL per le immagini ignorate durante il caricamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configurazione del caricamento delle immagini. I valori possono essere none / tracking / script / list (possono essere sostituiti dalle impostazioni facoltative dell’operatore). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Cartella in cui archiviare le immagini sul server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Spazio per visualizzare i logo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Cartella principale per le pubblicazioni.<br /> Per ulteriori informazioni sulla generazione di contenuti HTML e Text, fare riferimento a <a href="../../delivery/using/using-a-content-template.md">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Consente di definire il server in cui vengono memorizzate le immagini utilizzate nelle consegne per consentire al browser di ottenerle.<br /> Per le versioni di build &lt;= 5098, viene utilizzato l'URL delle immagini caricate nell'istanza.<br /> Per le versioni di build &gt; 5098, viene utilizzato l'URL pubblico della consegna o l'URL dell'opzione <span class="uicontrol">XtkFileRes_Public_URL</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Consente di configurare il nome dell'istanza per il caricamento dell'immagine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Consente di configurare la password per il caricamento dell'immagine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Consente di configurare gli URL multimediali per il caricamento delle immagini.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Durata di validità predefinita per le risorse online di una consegna (in secondi).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Nuovo URL per i file di risorse pubbliche.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Gestione di campagne e flussi di lavoro {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Cronologia marketing visualizzata per questo numero di mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DurataOperazione</span> <br /> </td> 
   <td> Periodo di validità predefinito di una campagna (in secondi).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Numero massimo di processi di consegna/flusso di lavoro/ipotesi/simulazione che possono essere elaborati alla volta, avviati dal flusso di lavoro operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Consente di monitorare l'esecuzione del flusso di lavoro tecnico <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Quando è attivata (valore "1"), le informazioni di esecuzione vengono registrate nei registri di controllo del flusso di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Periodo di tempo per le condizioni di targeting ed estrazione in modalità pianificata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Soglia_Analisi_Flusso di lavoro</span> <br /> </td> 
   <td> Numero di record interessati dopo i quali le statistiche della tabella vengono ricalcolate automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo da visualizzare nell'angolo in alto a destra dei report esportati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Numero di giorni di attesa tra i controlli per i flussi di lavoro in pausa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Attiva la convalida delle consegne da parte del proprietario dell’operazione immettendo "1" come valore. Per disattivare questa opzione, immettere "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Libreria JS aggiuntiva da caricare nell'attività del flusso di lavoro "Notifiche delle risorse di marketing".<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sicurezza {#security}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">LimitaModificaOOTBSchema</span> <br /> </td> 
   <td> (a partire dalla versione 21.1.3) Se è selezionato 1 (valore predefinito), questa opzione disattiva l'edizione degli schemi incorporati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (a partire dalla versione 21.1.3) Se è selezionato 1 (valore predefinito), questa opzione disattiva l'edizione dei codici JavaScript incorporati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Modalità di compatibilità di installazione: build&gt;6000) Quando è attivata (valore "1"), questa opzione consente l'utilizzo di password precedenti memorizzate nel database per la connessione ad account esterni o all'istanza.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Questa chiave viene utilizzata per crittografare la maggior parte delle password nel database. (account esterni, password LDAP...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione consente PrivilegeEscalation in JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Se si seleziona 1, questa opzione disabilita i controlli ACL durante il download di un file (tramite fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione disabilita la sandboxing dei file in Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Se impostato su 'true', un operatore non amministratore autorizzato è autorizzato ad aggiornare i valori xtkOption tramite la procedura guidata di distribuzione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione consente di utilizzare decryptString per decrittografare alcune password.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Immettere il valore "1" per tracciare l'eliminazione degli elementi con le informazioni di audit trail nei dati mData, mediante la modifica del relativo campo "Modificato da" prima dell'eliminazione del record.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Centro messaggi {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> Libreria JavaScript da personalizzare per arricchire gli eventi. Deve contenere l'implementazione di queste due funzioni:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : arricchisce e salva gli eventi nel database (dove <span class="uicontrol">aiEventId</span> corrisponde alla tabella degli eventi in tempo reale elaborati).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : arricchisce e salva gli eventi nel database (dove <span class="uicontrol">aiEventId</span> corrisponde alla tabella ID degli eventi batch elaborati).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Data dell'ultimo aggiornamento dello stato dell'evento tramite i registri di consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Libreria JavaScript da personalizzare per gli eventi di routing. Deve contenere l'implementazione di queste due funzioni:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : restituisce il nome interno del messaggio transazionale selezionato per elaborare l'evento in tempo reale (dove <span class="uicontrol">iEventId</span> corrisponde all'ID dell'evento in tempo reale elaborato).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : restituisce il nome interno del messaggio transazionale selezionato per elaborare l'evento batch (dove <span class="uicontrol">iEventId</span> corrisponde all'ID dell'evento batch elaborato).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Soglia di avviso del tempo medio di invio degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per il tempo medio di invio degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per il tempo medio di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Soglia di avviso per il numero medio di eventi in tempo reale messi in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di coda degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per il tempo medio di attesa degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per il numero medio di eventi in tempo reale messi in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Soglia di avviso per gli errori di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per gli errori di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Soglia di avviso per il numero massimo di eventi in tempo reale messi in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per il numero massimo di eventi in tempo reale messi in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Soglia di avviso per il numero minimo di eventi in tempo reale messi in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per il numero minimo di eventi in tempo reale messi in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Soglia prima della condizione critica per la coda di eventi in tempo reale in sospeso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Soglia prima dell'avviso per la coda di eventi in tempo reale in sospeso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Soglia di avviso per la velocità effettiva degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Soglia di avvertenza per la velocità effettiva degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Dimensione del raggruppamento per il routing dell'evento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Aggiorna puntatore dello stato di RtEvent (ultima data fino a quando i dati sono stati recuperati).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL del server del Centro messaggi utilizzato per inviare messaggi di benvenuto (canale LINE).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Database {#database}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Definisce l'ultima volta che il processo di pulizia è stato eseguito.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale broadlog viene cancellato dal database.</p><p>Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale la cronologia degli eventi viene cancellata dal database.</p><p>
   Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale gli eventi vengono cancellati dal database.</p><p>Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale le statistiche degli eventi vengono cancellate dal database.</p><p>Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale le proposte vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale le quarantene vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale le consegne riciclate vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i rifiuti vengono cancellati dal database.</p><p>Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i registri di tracciamento vengono cancellati dal database.</p><p>Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale le statistiche di tracciamento vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i visitatori vengono eliminati dal database.</p><p> Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i risultati del flusso di lavoro vengono cancellati dal database.</p><p> Questa opzione viene creata automaticamente una volta modificato il ritardo all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, questo deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opzioni del connettore di Azure SQL Datawarehouse.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Consente di modificare il comportamento di Arresto incondizionato su tutti i flussi di lavoro e le query del database PostgreSQL in base ai seguenti valori potenziali:<ul>
    <li><p>0 - impostazione predefinita: interrompe il processo del flusso di lavoro, senza alcun impatto sul database<p></li>
    <li><p>1 - pg_cancel_backend: interrompe il processo del flusso di lavoro e annulla la query nel database<p></li>
    <li><p>2 - pg_terminate_backend: interrompe il processo del flusso di lavoro e termina la query nel database<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nome della tablespace che deve contenere i dati delle tabelle ootb di Adobe Campaign.<br />Vedere <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nome della tablespace che deve contenere gli indici delle tabelle ootb di Adobe Campaign.<br />Vedere <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nome della tablespace che deve contenere i dati delle tabelle di lavoro di Adobe Campaign.<br />Vedere <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nome della tablespace che deve contenere gli indici delle tabelle di lavoro di Adobe Campaign.<br />Vedere <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server, al fine di ottimizzare i backup e la replica. L'opzione corrisponde al nome del database temporaneo: se specificato, le tabelle di lavoro verranno scritte in questo database. Esempio: 'tempdb.dbo.' (il nome deve terminare con un punto). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Ulteriori informazioni</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Fuso orario dell’istanza di Adobe Campaign. Vedi <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configurazione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> I campi stringa del database sono definiti con NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> I campi 'datetime' del database memorizzano le informazioni sul fuso orario?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID del database. Inizia con 'u' per Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefisso aggiunto ai nomi interni generati automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Numero massimo di risultati restituiti da una query su xtk:schema e xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Tutti gli schemi personalizzati, creati dopo questo tempo, con autopk="true" e senza l’attributo "pkSequence" otterranno una sequenza generata automaticamente "auto_ 
    &lt;spazio degli schemi&gt; 
     &lt;nomeschema&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante la migrazione, la struttura ad albero viene riorganizzata automaticamente in base ai nuovi standard di versione.<br /> Questa opzione consente di disabilitare la migrazione automatica della struttura di navigazione. Se lo si utilizza, dopo la migrazione sarà necessario eliminare le cartelle obsolete, aggiungere le nuove cartelle ed eseguire tutti i controlli necessari.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo di dati:</span> Intero</p> </li> 
     <li> <p> <span class="uicontrol">Valore (testo)</span> : 1 </p> </li> 
    </ul> Questa opzione deve essere utilizzata solo se la struttura di navigazione predefinita ha subito troppe modifiche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Data ultima elaborazione della pulizia della tabella <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informazioni relative all'errore che si è verificato nel post-aggiornamento, seguendo la sintassi seguente:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'majorOrEquelThan' where error + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Immettere il valore "1" in modo che l'aggiornamento delle statistiche non venga eseguito tramite il flusso di lavoro di pulizia.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integrazione {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">FiltroTipoRisorsaAEM</span> <br /> </td> 
   <td> Tipi di risorse AEM che possono essere utilizzate in Adobe Campaign. I valori devono essere separati da virgole.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Consente di configurare Experience Cloud Triggers. Il tipo di dati è "long text" e deve essere in formato JSON. Vedi <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Come utilizzare Experience Cloud Triggers con Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Questa opzione viene utilizzata quando si importano dati da un sistema di terze parti tramite un connettore di gestione delle relazioni con i clienti. L’abilitazione di questa opzione consente di raccogliere solo gli oggetti modificati dall’ultima importazione. Questa opzione deve essere creata e compilata manualmente come segue: 
    <ul> 
     <li> <p> <span class="uicontrol">Nome interno</span>: LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valore (campo)</span>: data dell'ultima importazione, in formato aaaa/MM/gg hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Server Adobe Target utilizzato per l’integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde al server di dominio Adobe Target, seguito dal valore /m2. Ad esempio: tt.omtrdc.net/m2.<br /> Vedere <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nome dell’organizzazione Adobe Target. Questo valore corrisponde al nome del client Adobe Target.<br /> Vedere <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Opzione utilizzata per l'integrazione con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Opzione utilizzata per l'integrazione con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata opzioni connettore.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Opzioni connettore hive.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Offerte {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Numero di coupon aggiornati per transazione SQL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [schema della proposta] + "_" + extAccountSource.@executionInstanceId + [schema della proposta] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ schema della proposta] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Tracciamento del flusso di lavoro di sincronizzazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Abilita/disabilita la scrittura di proposte asincrone ("0" per disabilitare, "1" per abilitare).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Consente di abilitare i coupon.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#server}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Identificatore dell'istanza di esecuzione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Identificatore cliente utilizzato per l'invio del report di fatturazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL di base interno per accedere al server applicazioni.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Numero di build dell'istanza AC prima dell'ultimo aggiornamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL di base del server applicazioni Web pubblico.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Consente di continuare a utilizzare le vecchie funzioni SQL non dichiarate dopo la migrazione. Si consiglia vivamente di non utilizzare questa opzione a causa dei rischi di sicurezza che comporta.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracciamento {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Opzione che consente di attivare il tracciamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Script di calcolo dell'URL tracciato.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Consente di definire l'account esterno del server di tracciamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Consente di definire il nome dell'istanza nel server di tracciamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> L'ultima volta che le informazioni di tracciamento sono state consolidate con nuovi dati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Apri script di calcolo URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Password per il server di tracciamento<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> Il puntatore tiene traccia degli ultimi eventi del messaggio elaborati tramite i relativi ID e data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> URL protetto del server di tracciamento frontale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL del server di tracciamento frontale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Elenco degli URL utilizzati per contattare i server di tracciamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Set di regole di identificazione del browser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script utilizzato per calcolare i tag di tracciamento Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Nome della consegna virtuale progettata per la gestione del tracciamento Web.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Consente di definire la modalità di tracciamento Web.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Privacy {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Richiesta di accesso a dati personali_ConfermaEliminazioneIn sospeso</span> <br /> </td> 
   <td> Se l’opzione 1 è selezionata, in un secondo passaggio dovrai confermare manualmente l’eliminazione nell’interfaccia. In caso contrario, i dati verranno eliminati senza conferma.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> Il ritardo tra le attese della richiesta per l'eliminazione della conferma e la richiesta è stato annullato.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Numero massimo di errori consentiti durante l'elaborazione/eliminazione di una richiesta di accesso a dati personali.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Ritardo tra la creazione della richiesta nella coda e l'eliminazione dei dati della richiesta.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Abilita il server LDAP da utilizzare per autenticare gli utenti e fornire le autorizzazioni agli utenti.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Accesso all'applicazione per contattare il server per varie ricerche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Password crittografata per l'accesso all'applicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Operatore_automatico XtkLdap</span> <br /> </td> 
   <td> Abilita creazione automatica di operatori e diritti in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Formula di calcolo per il DN LDAP basato sull'accesso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Abilita ricerca DN nella directory.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Base di ricerca.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> Filtro di ricerca DN.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Ambito di ricerca.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Meccanismo_XtkLdap</span> <br /> </td> 
   <td> Tipo di autenticazione utilizzato per contattare il server LDAP (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Diritti_XtkLdap</span> <br /> </td> 
   <td> Abilita la sincronizzazione di autorizzazioni e gruppi dalla directory LDAP ai diritti denominati in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> Attributo LDAP contenente il nome dell'autorizzazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Base di ricerca.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Filtro di ricerca per autorizzazioni utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Espressione per estrarre i nomi dei diritti Adobe Campaign dalle autorizzazioni LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Ambito di ricerca.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> Indirizzo server LDAP (è possibile specificare una porta specificando ':' come separatore).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Moduli web {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> Il valore impostato su 1 consente l'aggiunta della barra di scorrimento ai moduli di dettaglio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Istanza_XtkWebForm</span> <br /> </td> 
   <td> Istanza da utilizzare per l'annullamento del modulo Web in modalità 'altri server'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Password_XtkWebForm</span> <br /> </td> 
   <td> Password dell'istanza da utilizzare per l'annullamento del modulo Web in modalità 'altri server'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opzione che consente di specificare la modalità di invalidazione dei moduli web: locale per impostazione predefinita, utilizza i server di tracciamento se l'opzione è "tracciamento" e utilizza un elenco personalizzato con l'opzione "altri server".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> Elenco di indirizzi personalizzati dei server da contattare per l'annullamento del modulo Web (modalità "altri server").<br /> </td> 
  </tr> 
 </tbody> 
</table>
