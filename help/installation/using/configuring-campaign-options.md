---
product: campaign
title: Configurazione delle opzioni di Campaign
description: Scopri come configurare le opzioni di Campaign
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 4661a65c83f3b9b7da9ea902f387155c5933e59f
workflow-type: tm+mt
source-wordcount: '3991'
ht-degree: 1%

---

# Elenco opzioni di Campaign Classic{#configuring-campaign-options}

![](../../assets/v7-only.svg)

La **[!UICONTROL Administration / Platform / Options]** node ti consente di configurare le opzioni Adobe Campaign. Alcune sono integrate durante l’installazione di Campaign, altre possono essere aggiunte manualmente quando necessario. Le opzioni disponibili variano a seconda dei pacchetti installati con la tua istanza.


>[!CAUTION]
>
>* Le opzioni non elencate in questa pagina sono solo interne e **non deve essere modificato**.
>
>* La modifica o l’aggiornamento delle opzioni di Adobe Campaign possono essere eseguite solo dagli utenti esperti.


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
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Data dell'ultimo wideLogMsg recuperato dall'istanza di recapito messaggi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Data dell'ultimo wideLogMsg inviato all'istanza di recapito messaggi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identificatore dei report di consegna. Contatta il supporto per ottenere il tuo identificatore.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Elenco di schemi per i quali si desidera utilizzare gli indirizzi di test per il rendering della casella in entrata. (i nomi degli elementi sono separati da virgole) Ad esempio: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> Indirizzo e-mail CCN a cui l’MTA avanzato invierà una copia non elaborata delle e-mail inviate. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Consente all’operatore responsabile della consegna di confermare l’invio, se un operatore o un gruppo specifico di operatori è designato per avviare una consegna nelle proprietà della consegna.</p><p> A questo scopo, attiva l’opzione immettendo "1" come valore. Per disattivare questa opzione, immetti "0".</p><p> Il processo di conferma dell’invio funzionerà quindi come impostazione predefinita: solo l’operatore o il gruppo di operatori designati per l’invio nelle proprietà di consegna (o un amministratore) sarà in grado di confermare ed eseguire l’invio. Vedi <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">questa sezione</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign utilizza una variabile globale "Nms_DefaultRcpSchema" per aprire una finestra di dialogo con il database dei destinatari predefinito (nms:recipient).<br /> Il valore dell’opzione deve corrispondere al nome dello schema corrispondente alla tabella dei destinatari esterna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Numero minimo di destinatari affinché una consegna possa essere considerata come quella principale nel rapporto di fatturazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Provider di servizi di routing predefinito per i nuovi modelli.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Numero di BroadLogs creati per una consegna alla volta.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Inserimento (nella tabella) di registri (wideLogs) per transazioni : numero di righe da elaborare per batch.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Raggruppamento delle dimensioni delle parti di consegna durante l’analisi delle consegne di mid-sourcing.<br /> </td> 
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
   <td> L’inserimento di "1" come valore consente di escludere i destinatari che non desiderano più essere contattati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> L’inserimento di "1" come valore consente di ignorare automaticamente i doppi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Consente di definire la sintassi dell’indirizzo Errore utilizzato per rispondere a un messaggio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMask</span> <br /> </td> 
   <td> Consente di definire la sintassi dell’indirizzo Da utilizzato per l’invio di un messaggio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Consente di definire un limite di timeout (in secondi) per ricevere una risposta dal server durante il recupero di un'immagine scaricata da un URL personalizzato e allegata a un'e-mail. Se questo valore viene superato, il messaggio non può essere inviato. Il valore predefinito è 60 secondi.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Consente di definire la dimensione massima (in byte) consentita per un'immagine scaricata da un URL personalizzato e allegata a un'e-mail. Il valore predefinito è 100.000 byte. Quando si invia una bozza e si scaricano le immagini per elaborare l’e-mail, se la dimensione di un’immagine supera questo valore o se si verifica un problema di download, nei registri di consegna verrà visualizzato un errore e la consegna della bozza avrà esito negativo.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendationsAttachments</span> <br /> </td> 
   <td> Consente di impostare un numero massimo di allegati in un modello e-mail o e-mail transazionale. Se questo valore viene superato, nei registri di analisi della consegna o durante la pubblicazione del modello e-mail transazionale viene visualizzato un avviso. Il valore predefinito è 1 allegato.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Numero massimo di tentativi durante l’analisi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Script di pubblicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Disattiva il conteggio wideLogMsg per i messaggi push.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Visualizza il peso del messaggio nella procedura guidata di consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Indirizzo e-mail "error" predefinito a livello di istanza utilizzato per la consegna e-mail se lasciato vuoto dall’utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Indirizzo e-mail "da" predefinito a livello di istanza utilizzato per la consegna e-mail se lasciato vuoto dall’utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Indirizzo e-mail "risposta" predefinito a livello di istanza utilizzato per la consegna e-mail se lasciato vuoto dall’utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Nome comune del cliente. Utilizzato in alcuni messaggi di avviso visualizzati ai destinatari.<br /> "Stai ricevendo questo messaggio perché sei stato in contatto con ***** o con una società affiliata. Per non ricevere più messaggi da *****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Etichetta e-mail predefinita "da" a livello di istanza utilizzata per la consegna e-mail se lasciata vuota dall’utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Etichetta e-mail predefinita "risposta" a livello di istanza utilizzata per la consegna e-mail se lasciata vuota dall’utente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Periodo tra due tentativi di un messaggio e-mail (in secondi).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Periodo di tentativi per i messaggi e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formula utilizzata per calcolare la ponderazione di un messaggio per una consegna provvisoria.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Elenco degli indirizzi e-mail di inoltro autorizzati (dal modulo di elaborazione della posta in entrata). Gli indirizzi devono essere separati da virgole (o * per consentire tutti). Ad esempio xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Chiave AES utilizzata nel servlet 'lineImage' per codificare gli URL (canale LINE).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Sul canale "email" (usa come impostazione predefinita) : Numero massimo di errori accettati per gli errori SOFT durante l'invio prima di mettere il destinatario in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Sul canale "email" (usa come impostazione predefinita) : Periodo minimo da trascorrere dopo il precedente errore SOFT di riferimento, prima di tenere conto di un nuovo errore SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Sul canale "mobile" : Numero massimo di errori accettati per gli errori SOFT durante l'invio prima di mettere il destinatario in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Sul canale "mobile" : Periodo minimo da trascorrere dopo il precedente errore SOFT di riferimento, prima di tenere conto di un nuovo errore SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Consente di specificare un periodo massimo (espresso in ore) per limitare il numero di log di trasmissione recuperati ogni volta che il flusso di lavoro di sincronizzazione viene eseguito.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Numero massimo di chiamate nella sessione MidSourcing che possono essere eseguite in parallelo (3 per impostazione predefinita).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Ritardo personalizzato (in minuti) dopo il quale una consegna viene considerata come "ritardata", impostazione predefinita: 30 minuti.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Questa opzione è utilizzata dalla <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> flusso di lavoro tecnico durante il conteggio del numero di consegne in esecuzione.</p>Ti consente di definire il numero di giorni al di sopra dei quali le consegne con stato incoerente verranno escluse dal conteggio delle consegne in esecuzione.</p><p>Per impostazione predefinita, il valore è impostato su "7", il che significa che verranno escluse le consegne non coerenti con una durata superiore a 7 giorni.</p></td> 
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
   <td> L'URL del server della pagina speculare (per impostazione predefinita, deve essere identico a NmsTracking_ServerUrl).<br /> È il valore predefinito delle consegne e-mail quando l’URL non è specificato nella definizione del indirizzamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parametri dei messaggi SMS inviati: informazioni trasmesse al gateway SMS per indicare la priorità del messaggio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Numero di tentativi durante l’invio di messaggi SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Periodo durante il quale verranno eseguiti nuovi tentativi di messaggi SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Data ultimo consolidamento <span class="uicontrol">NmsUserAgent</span> statistiche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Nome dell’opzione che contiene i segmenti web e i relativi stati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Attiva/disattiva il supporto per i caratteri speciali per Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Caratteri validi per un indirizzo e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Aggiungi questa opzione con il valore "0" per disabilitare la modifica del codice XML delle consegne (fai clic con il pulsante destro del mouse su / <span class="uicontrol">Modifica origine XML</span> o <span class="uicontrol">CTRL+F4</span> scorciatoia).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Resources {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Nome opzione </th> 
   <th> Descrizione </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmResourceDir</span> <br /> </td> 
   <td> Posizione delle risorse da pubblicare nella console client di Adobe Campaign. Vedi <a href="../../delivery/using/formatting.md#image-referencing">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourceDirPreview</span> <br /> </td> 
   <td> Posizione delle risorse per l’anteprima nella console client di Adobe Campaign. Vedi <a href="../../delivery/using/formatting.md#image-referencing">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Elenco di maschere URL per le immagini saltate durante il caricamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configurazione del caricamento delle immagini. I valori possono essere none / tracking / script / list (possono essere ignorati dalle impostazioni facoltative dell'operatore). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Cartella in cui memorizzare le immagini sul server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Spazio per visualizzare i loghi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Cartella principale per le pubblicazioni.<br /> Per ulteriori informazioni sulla generazione dei contenuti di HTML e testo, consulta <a href="../../delivery/using/using-a-content-template.md">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Consente di definire il server in cui vengono memorizzate le immagini utilizzate nelle consegne per consentire al browser di ottenerle.<br /> Per le versioni di build &lt;= 5098, utilizziamo l’URL delle immagini caricate sull’istanza.<br /> Per le versioni di build &gt; 5098, utilizziamo invece l’URL pubblico della consegna o il <span class="uicontrol">XtkFileRes_Public_URL</span> URL dell'opzione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Consente di configurare il nome dell'istanza per il caricamento dell'immagine.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Consente di configurare la password per il caricamento delle immagini.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Consente di configurare gli URL dei file multimediali per il caricamento delle immagini.<br /> </td> 
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
   <td> Cronologia marketing mostrata per questo numero di mesi.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Periodo di validità predefinito di una campagna (in secondi).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Numero massimo di processi di consegna/flusso di lavoro/ipotesi/simulazione che possono essere elaborati alla volta, avviati dal flusso di lavoro operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Consente di monitorare il <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a> esecuzione tecnica del flusso di lavoro. Quando sono attivate (valore "1"), le informazioni di esecuzione vengono registrate nei registri di controllo del flusso di lavoro.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Periodo di tempo per le condizioni di targeting ed estrazione in modalità pianificata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Numero di record interessati dopo i quali le statistiche della tabella vengono ricalcolate automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo da visualizzare nell’angolo in alto a destra dei rapporti esportati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Numero di giorni di attesa tra i controlli dei flussi di lavoro in pausa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Attiva la convalida delle consegne dal proprietario dell’operazione immettendo "1" come valore. Per disattivare questa opzione, immetti "0".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Libreria JS aggiuntiva da caricare nell’attività del flusso di lavoro "Notifiche di risorse di marketing".<br /> </td> 
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
   <td> <span class="uicontrol">Schema RestrictEditingOOTBS</span> <br /> </td> 
   <td> (a partire dalla versione 21.1.3) Se è selezionato 1 (valore predefinito), questa opzione disattiva la modifica degli schemi incorporati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (a partire dalla versione 21.1.3) Se è selezionato 1 (valore predefinito), questa opzione disattiva la modifica dei codici JavaScript incorporati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Modalità di compatibilità di installazione: build&gt;6000) Quando attivata (valore "1"), questa opzione consente l'uso di vecchie password memorizzate nel database per la connessione ad account esterni o all'istanza.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Questa chiave viene utilizzata per crittografare la maggior parte delle password nel database. (account esterni, password LDAP..).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione consente l'inoltro di privilegi in JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione disattiva i controlli ACL durante un download di file (tramite fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione disabilita la sandbox dei file in Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Se impostato su "true", l'operatore non amministratore autorizzato ad aggiornare i valori xtkOption tramite la procedura guidata di distribuzione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Se è selezionato 1, questa opzione consente di utilizzare decryptString per decrittografare alcune password.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Immetti il valore "1" per tracciare l’eliminazione degli elementi con le informazioni Audit trail in mData, attraverso la modifica del relativo campo "modificato da" prima dell’eliminazione del record.<br /> </td> 
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
   <td> Libreria JavaScript da personalizzare per arricchire gli eventi. Devono contenere l'attuazione di queste due funzioni:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : arricchisce e salva gli eventi nel database (dove <span class="uicontrol">aiEventId</span> corrisponde alla tabella degli eventi in tempo reale elaborati).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : arricchisce e salva gli eventi nel database (dove <span class="uicontrol">aiEventId</span> corrisponde alla tabella ID degli eventi batch elaborati).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Data dell’ultimo aggiornamento dello stato dell’evento tramite i registri di consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> Libreria JavaScript da personalizzare per gli eventi di indirizzamento. Devono contenere l'attuazione di queste due funzioni:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">sendRtEvent(iEventId);</span> : restituisce il nome interno del messaggio transazionale selezionato per elaborare l’evento in tempo reale (dove <span class="uicontrol">iEventId</span> corrisponde all’ID dell’evento in tempo reale elaborato).</p> </li> 
     <li> <p> <span class="uicontrol">sendBatchEvent(iEventId);</span> : restituisce il nome interno del messaggio transazionale selezionato per elaborare l'evento batch (dove <span class="uicontrol">iEventId</span> corrisponde all'ID dell'evento batch elaborato).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di invio degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di invio degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Soglia di avviso per il numero medio di eventi in coda in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di coda degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Soglia di avviso per il tempo medio di accodamento degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Soglia di avviso per il numero medio di eventi in tempo reale in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Soglia di avviso per gli errori di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Soglia di avviso per gli errori di elaborazione degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Soglia di avviso per il numero massimo di eventi in coda in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Soglia di avviso per il numero massimo di eventi in tempo reale in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Soglia di avviso per il numero minimo di eventi in coda in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Soglia di avviso per il numero minimo di eventi in tempo reale in coda.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Soglia prima della condizione critica per la coda degli eventi in tempo reale in sospeso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Soglia prima dell'avviso per la coda degli eventi in sospeso in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Soglia di avviso per la velocità effettiva degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Soglia di avviso per la velocità effettiva degli eventi in tempo reale.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Dimensione del raggruppamento per il routing dell'evento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventState</span> <br /> </td> 
   <td> Aggiorna il puntatore dello stato RtEvent (ultima data fino al momento del recupero dei dati).<br /> </td> 
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
   <td> <p>Consente di definire il ritardo dopo il quale il registro di trasmissione viene cancellato dal database.</p><p>Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale la cronologia degli eventi viene cancellata dal database.</p><p>
   Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale gli eventi vengono cancellati dal database.</p><p>Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatePurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale le statistiche dell’evento vengono cancellate dal database.</p><p>Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale le proposte vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale le quarantene vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale le consegne riciclate vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i rifiuti vengono cancellati dal database.</p><p>Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i registri di tracciamento vengono cancellati dal database.</p><p>Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatePurgeDelay</span> <br /> </td> 
   <td><p> Consente di definire il ritardo dopo il quale le statistiche di tracciamento vengono cancellate dal database.</p><p> Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i visitatori vengono cancellati dal database.</p><p> Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Consente di definire il ritardo dopo il quale i risultati del flusso di lavoro vengono cancellati dal database.</p><p> Questa opzione viene creata automaticamente una volta che il ritardo viene modificato all’interno dell’interfaccia. Se modifichi il valore dall’elenco delle opzioni, deve essere espresso in secondi.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Opzioni del connettore di Data Warehouse di Azure SQL.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Consente di influenzare il comportamento di arresto incondizionato su tutti i flussi di lavoro e le query del database PostgreSQL in base ai seguenti valori potenziali:<ul>
    <li><p>0 - predefinito: interrompe il processo del flusso di lavoro, nessun impatto sul database<p></li>
    <li><p>1 - pg_cancel_backend: interrompe il processo del flusso di lavoro e annulla la query nel database<p></li>
    <li><p>2 - pg_end_backend: interrompe il processo del flusso di lavoro e termina la query nel database<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Nome della tablespace destinata a contenere i dati delle tabelle a barre di Adobe Campaign.<br />Vedi <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Nome della tablespace destinata a contenere gli indici delle tabelle a barre di Adobe Campaign.<br />Vedi <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Nome della tablespace destinata a contenere i dati delle tabelle di lavoro di Adobe Campaign.<br />Vedi <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Nome della tablespace destinata a contenere gli indici delle tabelle di lavoro di Adobe Campaign.<br />Vedi <a href="../../installation/using/creating-and-configuring-the-database.md">Creazione e configurazione del database</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Consente di configurare un database separato per le tabelle di lavoro in Microsoft SQL Server, al fine di ottimizzare i backup e la replica. L’opzione corrisponde al nome del database temporaneo: Se specificato, le tabelle di lavoro verranno scritte in questo database. Esempio: 'tempdb.dbo.' Il nome deve terminare con un punto. <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Leggi tutto</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Fuso orario dell’istanza Adobe Campaign. Vedi <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configurazione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> I campi stringa del database sono definiti con NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> I campi "datetime" del database memorizzano le informazioni sul fuso orario?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID del database. Inizia con 'u' per Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefisso aggiunto ai nomi interni generato automaticamente.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Numero massimo di risultati restituiti da una query su xtk:schema e xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Tutti gli schemi personalizzati, creati successivamente, con autopk="true" e senza l'attributo "pkSequence" otterranno una sequenza generata automaticamente "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _segg. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Durante la migrazione, la struttura ad albero viene riorganizzata automaticamente in base ai nuovi standard di versione.<br /> Questa opzione consente di disabilitare la migrazione automatica della struttura di navigazione. Se lo utilizzi, dopo la migrazione dovrai eliminare le cartelle obsolete, aggiungi le nuove cartelle ed esegui tutti i controlli necessari.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Tipo di dati:</span> Intero</p> </li> 
     <li> <p> <span class="uicontrol">Valore (testo)</span> : 1 </p> </li> 
    </ul> Questa opzione deve essere utilizzata solo se la struttura di navigazione preconfigurata ha subito troppe modifiche.<br /> Per ulteriori informazioni al riguardo, consulta <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Data dell’ultima elaborazione <span class="uicontrol">NmsEmailErrorState</span> pulizia della tabella.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informazioni relative all'errore che si è verificato nel post aggiornamento, seguendo la sintassi seguente:<br /> <strong>{Numero build}:{modalità: pre/post/..}:{Il 'lessThan'/'greaterOrEquelThan' in cui si è verificato l'errore + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Immetti il valore "1" in modo che l’aggiornamento delle statistiche non venga eseguito tramite il flusso di lavoro di pulizia.<br /> </td> 
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
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Tipi di risorse AEM che possono essere utilizzate in Adobe Campaign. I valori devono essere separati da virgole.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Consente di configurare i trigger di Experience Cloud. Il tipo di dati è "long text" e deve essere in formato JSON. Vedi <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Come utilizzare Experience Cloud Triggers con Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Questa opzione viene utilizzata quando si importano dati da un sistema di terze parti tramite un connettore di gestione delle relazioni con i clienti. L’opzione ti consente di raccogliere solo gli oggetti modificati dall’ultima importazione. Questa opzione deve essere creata e compilata manualmente come segue: 
    <ul> 
     <li> <p> <span class="uicontrol">Nome interno</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Valore (campo)</span> : data dell’ultima importazione, con aaaa/MM/gg hh:mm:formato ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Server Adobe Target utilizzato per l’integrazione. Questa opzione è già selezionata per impostazione predefinita. Questo valore corrisponde al server di dominio Adobe Target, seguito dal valore /m2. Ad esempio: tt.omtrdc.net/m2.<br /> Vedi <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Nome organizzazione Adobe Target. Questo valore corrisponde al nome del client Adobe Target.<br /> Vedi <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">questa sezione</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Opzione utilizzata per l’integrazione con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Opzione utilizzata per l’integrazione con Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Opzioni connettore teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Opzioni del connettore alveare.<br /> </td> 
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
   <td> '+ [schema della proposta] + "_" + extAccountSource.@executeInstanceId + [schema della proposizione] + "_" + vars.executeInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ schema della proposizione] + "_" + extAccountSource.@executeInstanceId + "_" + extAccountTarget.@executeInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Tracciamento del flusso di lavoro di sincronizzazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Attiva/disattiva la scrittura di proposizioni asincrone ("0" per disabilitare, "1" per abilitare).<br /> </td> 
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
   <td> Identificatore del cliente utilizzato per l'invio del report di fatturazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> URL di base interno per accedere al server dell'applicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Numero di build dell'istanza AC prima dell'ultimo aggiornamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> URL di base del server dell'applicazione Web pubblica.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Consente di continuare a utilizzare le vecchie funzioni SQL non dichiarate dopo la migrazione. Sconsigliamo vivamente di non utilizzare questa opzione a causa dei rischi per la sicurezza che introduce.<br /> </td> 
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
   <td> Script di calcolo tracked-URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Consente di definire l’account esterno del server di tracciamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Consente di definire il nome dell'istanza sul server di tracciamento.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> L’ultima volta che le informazioni di tracciamento sono state consolidate con nuovi dati.<br /> </td> 
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
   <td> Il puntatore tiene traccia degli ultimi eventi del messaggio elaborati tramite gli ID e la data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> URL sicuro del server di tracciamento frontale.<br /> </td> 
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
   <td> Nome della consegna virtuale progettata per la gestione del web tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Consente di definire la modalità di web tracking.<br /> </td> 
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
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Se è selezionata l’opzione 1, è necessario confermare manualmente l’eliminazione nell’interfaccia in un secondo passaggio. In caso contrario, i dati verranno cancellati senza conferma.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> Ritardo tra l'attesa della richiesta per l'eliminazione della conferma e la richiesta viene annullata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Numero massimo di errori consentiti durante l’elaborazione/eliminazione di una richiesta di accesso a dati personali.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Il ritardo tra la richiesta viene creato nella coda e i dati della richiesta vengono eliminati.<br /> </td> 
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
   <td> Attiva il server LDAP per l'autenticazione degli utenti e fornire autorizzazioni agli utenti.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Accesso applicazione per contattare il server per varie ricerche.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Password crittografata per l'accesso all'applicazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Abilita la creazione automatica di operatori e diritti in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Formula di calcolo per LDAP DN in base all'accesso.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Abilita la ricerca DN nella directory.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Tipo di autenticazione utilizzato per contattare il server LDAP (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
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
   <td> Filtro di ricerca per le autorizzazioni utente.<br /> </td> 
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
   <td> Il valore impostato su 1 consente l’aggiunta della barra di scorrimento ai moduli di dettaglio.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Istanza da utilizzare per l’annullamento della validità del modulo web in modalità "altri server".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Password dell’istanza da utilizzare per l’annullamento della validità del modulo web in modalità "altri server".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Opzione che consente di specificare la modalità di invalidazione dei moduli web: locale per impostazione predefinita, utilizza i server di tracciamento se l’opzione è "tracking" e utilizza un elenco personalizzato con l’opzione "altri server".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURL</span> <br /> </td> 
   <td> Elenco di indirizzi personalizzati dei server da contattare per l’annullamento della validità del modulo web (modalità "altri server").<br /> </td> 
  </tr> 
 </tbody> 
</table>
