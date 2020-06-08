---
title: Flusso di lavoro di pulizia del database
seo-title: Flusso di lavoro di pulizia del database
description: Flusso di lavoro di pulizia del database
seo-description: null
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c8cfdb67a4be2bc27baa363032c74a4aa8665e2a
workflow-type: tm+mt
source-wordcount: '2908'
ht-degree: 0%

---


# Flusso di lavoro di pulizia del database{#database-cleanup-workflow}

## Introduzione {#introduction}

Il **[!UICONTROL Database cleanup]** flusso di lavoro accessibile tramite il **[!UICONTROL Administration > Production > Technical workflows]** nodo, consente di eliminare i dati obsoleti per evitare la crescita esponenziale del database. Il flusso di lavoro viene attivato automaticamente senza l&#39;intervento dell&#39;utente.

![](assets/ncs_cleanup_workflow.png)

## Configurazione {#configuration}

La pulizia del database è configurata su due livelli: nel pianificatore del flusso di lavoro e nella procedura guidata di distribuzione.

### Utilità di pianificazione {#the-scheduler}

>[!NOTE]
>
>For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

Per impostazione predefinita, il **[!UICONTROL Database cleanup]** flusso di lavoro è configurato per iniziare ogni giorno alle 4 del mattino. L&#39;utilità di pianificazione consente di modificare la frequenza di attivazione del flusso di lavoro. Sono disponibili le seguenti frequenze:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>Affinché il flusso di lavoro possa iniziare alla data e all&#39;ora definite nel pianificatore, è necessario avviare il motore del flusso di lavoro (wfserver). **[!UICONTROL Database cleanup]** In caso contrario, la pulizia del database non verrà eseguita fino all&#39;avvio successivo del motore del flusso di lavoro.

### Procedura guidata di distribuzione {#deployment-wizard}

Il **[!UICONTROL Deployment wizard]** , accessibile tramite il **[!UICONTROL Tools > Advanced]** menu, consente di configurare per quanto tempo vengono salvati i dati. I valori sono espressi in giorni. Se questi valori non vengono modificati, il flusso di lavoro utilizzerà i valori predefiniti.

![](assets/ncs_cleanup_deployment-wizard.png)

I campi della **[!UICONTROL Purge of data]** finestra coincidono con le seguenti opzioni. Sono utilizzati da alcune delle attività eseguite dal **[!UICONTROL Database cleanup]** flusso di lavoro:

* Tracciamento consolidato: **NmsCleanup_TrackingStatePurgeDelay** (fare riferimento alla [pulizia dei registri](#cleanup-of-tracking-logs)di tracciamento)
* Registri di consegna: **NmsCleanup_BroadLogPurgeDelay** (fare riferimento alla [pulizia dei registri](#cleanup-of-delivery-logs)di consegna)
* Registri di tracciamento: **NmsCleanup_TrackingLogPurgeDelay** (fare riferimento alla [pulizia dei registri](#cleanup-of-tracking-logs)di monitoraggio)
* Consegne eliminate: **NmsCleanup_RecycledDeliveryPurgeDelay** (fare riferimento alla [pulizia delle consegne da eliminare o riciclare](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importa rifiuti: **NmsCleanup_RejectPurgeDelay** (fare riferimento alla [pulizia dei rifiuti generati dalle importazioni](#cleanup-of-rejects-generated-by-imports-))
* Profili visitatore: **NmsCleanup_VisitorPurgeDelay** (fare riferimento a [Pulizia dei visitatori](#cleanup-of-visitors))
* Proposte di offerta: **NmsCleanup_PropositionPurgeDelay** (fare riferimento a [Pulizia delle proposizioni](#cleanup-of-propositions))

   >[!NOTE]
   >
   >Il **[!UICONTROL Offer propositions]** campo è disponibile solo quando è installato il modulo **Interazione** .

* Eventi: **NmsCleanup_EventPurgeDelay** (fare riferimento alla [pulizia degli eventi](#cleansing-expired-events)scaduti)
* Eventi archiviati: **NmsCleanup_EventHistoPurgeDelay** (fare riferimento alla [pulizia degli eventi](#cleansing-expired-events)scaduti)

   >[!NOTE]
   >
   >I campi **[!UICONTROL Events]** e **[!UICONTROL Archived events]** sono disponibili solo se è installato il modulo Centro **** messaggi.

* Audit trail: **XtkCleanup_AuditTrailPurgeDelay** (fare riferimento a [Pulizia dell&#39;audit trail](#cleanup-of-audit-trail))

Tutte le attività eseguite dal **[!UICONTROL Database cleanup]** flusso di lavoro sono descritte nella sezione seguente.

## Attività eseguite dal flusso di lavoro di pulizia del database {#tasks-carried-out-by-the-database-cleanup-workflow}

Alla data e all&#39;ora definite nel pianificatore del flusso di lavoro (vedere [l&#39;Utilità di pianificazione](#the-scheduler)), il motore del flusso di lavoro avvia il processo di pulizia del database. La pulizia del database si collega al database ed esegue le attività nella sequenza mostrata di seguito.

>[!CAUTION]
>
>Se una di queste attività ha esito negativo, non saranno eseguite le seguenti.\
>Le query SQL con un attributo **LIMIT** verranno eseguite ripetutamente fino all&#39;elaborazione di tutte le informazioni.

>[!NOTE]
>
>Le sezioni seguenti che descrivono le attività eseguite dal flusso di lavoro di pulizia del database sono riservate agli amministratori di database o agli utenti che hanno familiarità con il linguaggio SQL.

### Elenchi per eliminare la pulizia {#lists-to-delete-cleanup}

La prima attività eseguita dal **[!UICONTROL Database cleanup]** flusso di lavoro elimina tutti i gruppi con **deleteStatus != 0** attributo da **NmsGroup**. Vengono eliminati anche i record collegati a tali gruppi e presenti in altre tabelle.

1. Gli elenchi da eliminare vengono recuperati utilizzando la seguente query SQL:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Ogni elenco contiene diversi collegamenti ad altre tabelle. Tutti questi collegamenti vengono eliminati in blocco utilizzando la seguente query:

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   dove **$(relatedTable)** è una tabella correlata a **NmsGroup** e **$(l)** è l&#39;identificatore di elenco.

1. Quando l&#39;elenco è un elenco di tipo &#39;Elenco&#39;, la tabella associata viene eliminata utilizzando la seguente query:

   ```
   DROP TABLE grp$(l)
   ```

1. Ogni elenco **Seleziona** tipo recuperato dall&#39;operazione viene eliminato utilizzando la seguente query:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   dove **$(l)** è l&#39;identificatore elenco

### Pulizia delle consegne da eliminare o riciclare {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Questa attività elimina tutte le consegne da eliminare o riciclare.

1. Il **[!UICONTROL Database cleanup]** flusso di lavoro seleziona tutte le consegne per le quali il campo **deleteStatus** ha il valore **[!UICONTROL Yes]** o **[!UICONTROL Recycled]** e la cui data di eliminazione è precedente al periodo definito nel campo **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) della procedura guidata di distribuzione. For more on this, refer to [Deployment wizard](#deployment-wizard). Questo periodo è calcolato in relazione alla data corrente del server.
1. Per ciascun server di mid-sourcing, l&#39;attività seleziona l&#39;elenco delle consegne da eliminare.
1. Il **[!UICONTROL Database cleanup]** flusso di lavoro elimina i registri di consegna, gli allegati, le informazioni della pagina mirror e tutti gli altri dati correlati.
1. Prima di eliminare definitivamente la consegna, il flusso di lavoro elimina le informazioni collegate dalle tabelle seguenti:

   * Nella tabella di esclusione della consegna (**NmsDlvExclusion**) viene utilizzata la seguente query:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      dove **$(l)** è l&#39;identificatore della consegna.

   * Nella tabella coupon (**NmsCouponValue**), viene utilizzata la seguente query (con eliminazione di massa):

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      dove **$(l)** è l&#39;identificatore della consegna.

   * Nelle tabelle del registro di consegna (**NmsBroadlogXxx**), le eliminazioni di massa vengono eseguite in batch di 20.000 record.
   * Nelle tabelle delle proposte di offerta (**NmsPropositionXxx**), le eliminazioni di massa vengono eseguite in batch di 20.000 record.
   * Nelle tabelle del registro di monitoraggio (**NmsTrackinglogXxx**), le eliminazioni di massa vengono eseguite in batch di 20.000 record.
   * Nella tabella del frammento di consegna (**NmsDeliveryPart**), le eliminazioni di massa vengono eseguite in batch di 500.000 record. Questa tabella contiene informazioni sulla personalizzazione dei messaggi rimanenti da inviare.
   * Nella tabella del frammento di dati della pagina mirror (**NmsMirrorPageInfo**), le eliminazioni di massa vengono eseguite in batch di 20.000 record per le parti di consegna scadute e per quelle finite o annullate. Questa tabella contiene informazioni sulla personalizzazione su tutti i messaggi utilizzati per generare pagine mirror.
   * Nella tabella di ricerca della pagina mirror (**NmsMirrorPageSearch**), le eliminazioni di massa vengono eseguite in batch di 20.000 record. Questa tabella è un indice di ricerca che fornisce l’accesso alle informazioni di personalizzazione memorizzate nella tabella **NmsMirrorPageInfo** .
   * Nella tabella di registro del processo batch (**XtkJobLog**), le eliminazioni di massa vengono eseguite in batch di 20.000 record. Questa tabella contiene il registro delle consegne da eliminare.
   * Nella tabella di tracciamento URL di consegna (**NmsTrackingUrl**) viene utilizzata la seguente query:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      dove **$(l)** è l&#39;identificatore della consegna.

      Questa tabella contiene gli URL trovati nelle consegne da eliminare per attivarne il tracciamento.

1. La consegna viene eliminata dalla tabella di consegna (**NmsDelivery**):

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   dove **$(l)** è l&#39;identificatore della consegna.

#### Distribuzione tramite mid-sourcing {#deliveries-using-mid-sourcing}

Il **[!UICONTROL Database cleanup]** flusso di lavoro elimina anche le consegne sui server di mid-sourcing.

1. A questo scopo, il flusso di lavoro verifica che ogni consegna sia inattiva (in base al suo stato). Se una consegna è attiva, verrà arrestata prima di essere eliminata. Il controllo viene eseguito eseguendo la seguente query:

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   dove **$(l)** è l&#39;identificatore della consegna.

1. Se il valore dello stato è **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , o **[!UICONTROL Pause in progress]** **[!UICONTROL Paused]** (valori 51, 55, 61, 62, 71, 72, 75), la consegna viene interrotta e l&#39;attività elimina le informazioni collegate.

### Pulizia delle consegne scadute {#cleanup-of-expired-deliveries}

Questa attività interrompe le consegne il cui periodo di validità è scaduto.

1. Il **[!UICONTROL Database cleanup]** flusso di lavoro crea l&#39;elenco delle consegne scadute. Questo elenco include tutte le consegne scadute con uno stato diverso da **[!UICONTROL Finished]** , nonché quelle interrotte di recente con oltre 10.000 messaggi non elaborati. Viene utilizzata la seguente query:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   se la modalità di **consegna 1** corrisponde alla **[!UICONTROL Mass delivery]** modalità, **lo stato 51** corrisponde allo **[!UICONTROL Start pending]** stato, **lo stato 85** corrisponde allo **[!UICONTROL Stopped]** stato e il numero più elevato di registri di consegna aggiornati in massa sul server di consegna è pari a 10.000.

1. Il flusso di lavoro include quindi l&#39;elenco delle consegne scadute di recente che utilizzano il mid-sourcing. Sono escluse le consegne per le quali non sono stati ancora recuperati log di consegna tramite il server di mid-sourcing.

   Viene utilizzata la seguente query:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. La seguente query viene utilizzata per rilevare se l&#39;account esterno è ancora attivo, per filtrare le consegne per data:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. Nell&#39;elenco delle consegne scadute, i registri di consegna il cui stato è **[!UICONTROL Pending]** , passare a **[!UICONTROL Delivery cancelled]** , e tutte le consegne in questo elenco passano a **[!UICONTROL Finished]** .

   Vengono utilizzate le seguenti query:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   dove **$(curdate)** è la data corrente del server di database, **$(bl)** è l&#39;identificatore del messaggio dei registri di consegna, **$(dl)** è la consegna, lo stato di **consegna 6** corrisponde allo **[!UICONTROL Pending]** stato e lo stato di **** **[!UICONTROL Delivery cancelled]** consegna 7corrisponde allo stato .

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   dove lo stato di **consegna 95** corrisponde allo **[!UICONTROL Finished]** stato, e **$(dl)** è l&#39;identificatore della consegna.

1. Tutti i frammenti (**deliveryParts**) di consegne obsolete vengono eliminati e tutti i frammenti obsoleti di consegne di notifiche in corso vengono eliminati. L&#39;eliminazione di massa viene utilizzata per entrambe le attività.

   Vengono utilizzate le seguenti query:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   dove lo stato di **consegna 95** corrisponde allo **[!UICONTROL Finished]** stato, lo stato di **consegna 85** corrisponde allo **[!UICONTROL Stopped]** stato, e **$(curateDate)** alla data corrente del server.

### Pulizia delle pagine mirror {#cleanup-of-mirror-pages}

Con questa attività vengono eliminate le risorse Web (pagine mirror) utilizzate dalle consegne.

1. In primo luogo, l&#39;elenco delle consegne da rimuovere viene recuperato utilizzando la seguente query:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   dove **$(curateDate)** è la data corrente del server.

1. La tabella **NmsMirrorPageInfo** viene quindi eliminata, se necessario utilizzando l&#39;identificatore della consegna precedentemente recuperata. L&#39;eliminazione di massa viene utilizzata per generare le seguenti query:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   dove **$(dl)** è l&#39;identificatore della consegna.

1. Una voce viene quindi aggiunta al registro di consegna.
1. Le consegne sollecitate vengono poi identificate, per evitare di doverle rielaborare in un secondo momento. Viene eseguita la seguente query:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   dove **$(strIn)** è l&#39;elenco di identificatori di consegna.

### Pulizia delle tabelle di lavoro {#cleanup-of-work-tables}

Questa attività elimina dal database tutte le tabelle di lavoro che corrispondono alle consegne il cui stato è **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** o **[!UICONTROL Deleted]** .

1. L&#39;elenco di tabelle con nomi che iniziano con **wkDlv_** viene recuperato prima con la seguente query (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Le tabelle utilizzate dai flussi di lavoro in corso vengono quindi escluse. A tal fine, l&#39;elenco delle consegne in corso viene recuperato utilizzando la seguente query:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   dove 0 è il valore che corrisponde allo stato di **[!UICONTROL Being edited]** consegna, 85 corrisponde allo **[!UICONTROL Stopped]** stato e 100 corrisponde allo **[!UICONTROL Deleted]** stato.

1. Le tabelle non più utilizzate verranno eliminate utilizzando la seguente query:

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Pulizia dei rifiuti generati dalle importazioni {#cleanup-of-rejects-generated-by-imports-}

Questo passaggio consente di eliminare i record per i quali non sono stati elaborati tutti i dati durante l&#39;importazione.

1. L&#39;eliminazione di massa viene eseguita sulla tabella **XtkReject** con la seguente query:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   dove **$(curateDate)** è la data del server corrente dalla quale viene sottratto il periodo definito per l&#39;opzione **NmsCleanup_RejectPurgeDelay** (fare riferimento alla procedura guidata [di](#deployment-wizard)distribuzione) e **$(l)** è il numero massimo di record da eliminare in massa.

1. Tutti i rifiuti orfani vengono quindi eliminati utilizzando la seguente query:

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Pulizia delle istanze del flusso di lavoro {#cleanup-of-workflow-instances}

Questa attività elimina ogni istanza del flusso di lavoro utilizzando l&#39;identificatore (**lWorkflowId**) e la cronologia (**lHistory**). Elimina le tabelle inattive eseguendo di nuovo l&#39;attività di pulizia della tabella di lavoro. La pulizia elimina anche tutte le tabelle di lavoro orfane (wkf% e wkfhisto%) dei flussi di lavoro eliminati.

>[!NOTE]
>
>La frequenza di eliminazione della cronologia viene specificata per ogni flusso di lavoro nel campo **Cronologia in giorni** (valore predefinito: 30 giorni). Questo campo si trova nella scheda **Esecuzione** delle proprietà del flusso di lavoro. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/workflow-properties.md#execution).

1. Per recuperare l&#39;elenco dei flussi di lavoro da eliminare, viene utilizzata la seguente query:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Questa query genera l’elenco dei flussi di lavoro che verranno utilizzati per eliminare tutti i registri collegati, le attività completate e gli eventi completati, utilizzando le query seguenti:

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   dove **$(lworkflow)** è l&#39;identificatore del flusso di lavoro e **$(lhistory)** è l&#39;identificatore della cronologia.

1. Tutte le tabelle non utilizzate vengono eliminate. A tal fine, tutte le tabelle vengono raccolte grazie a una maschera di tipo **wkf%** utilizzando la seguente query (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Vengono quindi escluse tutte le tabelle utilizzate da un&#39;istanza del flusso di lavoro in sospeso. L&#39;elenco dei flussi di lavoro attivi viene recuperato utilizzando la seguente query:

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Ogni identificatore del flusso di lavoro viene quindi recuperato per trovare il nome delle tabelle utilizzate dai flussi di lavoro in corso. Questi nomi sono esclusi dall&#39;elenco delle tabelle recuperate in precedenza.
1. Le tabelle della cronologia delle attività di tipo &quot;query incrementale&quot; sono escluse utilizzando le query seguenti:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   dove **$(strcondition)** è l&#39;elenco di tabelle che corrispondono alla maschera **wkfisto%** .

1. Le tabelle rimanenti vengono eliminate utilizzando la seguente query:

   ```
   DROP TABLE wkf15487_12;
   ```

### Pulizia dei login del flusso di lavoro {#cleanup-of-workflow-logins}

Questa attività elimina gli accessi al flusso di lavoro utilizzando la seguente query:

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Pulizia delle tabelle di lavoro orfane {#cleanup-of-orphan-work-tables}

Questa attività elimina le tabelle di lavoro orfane collegate ai gruppi. La tabella **NmsGroup** memorizza i gruppi da pulire (con un tipo diverso da 0). Il prefisso dei nomi delle tabelle è **grp**. Per identificare i gruppi da eliminare, viene utilizzata la seguente query:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Pulizia dei visitatori {#cleanup-of-visitors}

Questa attività elimina i record obsoleti dalla tabella dei visitatori utilizzando l&#39;eliminazione di massa. I record obsoleti sono quelli per i quali l&#39;ultima modifica è precedente al periodo di conservazione definito nella procedura guidata di distribuzione (fare riferimento alla procedura guidata [di](#deployment-wizard)distribuzione). Viene utilizzata la seguente query:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

dove **$(tsDate)** è la data corrente del server, dalla quale viene sottratto il periodo definito per l&#39;opzione **NmsCleanup_VisitorPurgeDelay** .

### Pulizia dell&#39;NPAI {#cleanup-of-npai}

Questa attività consente di eliminare i record che corrispondono a indirizzi validi dalla tabella **NmsAddress** . La seguente query viene utilizzata per eseguire l&#39;eliminazione di massa:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

dove **lo stato 2** corrisponde allo **[!UICONTROL Valid]** stato, **$(tsDate1)** è la data del server corrente e **$(tsDate2)** corrisponde all&#39;opzione **NmsCleanup_LastCleanup** .

### Pulizia delle sottoscrizioni {#cleanup-of-subscriptions-}

Questa attività elimina tutte le sottoscrizioni eliminate dall&#39;utente dalla tabella **NmsSubscription** utilizzando l&#39;eliminazione di massa. Viene utilizzata la seguente query:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Pulizia dei registri di tracciamento {#cleanup-of-tracking-logs}

Questa attività elimina i record obsoleti dalle tabelle di registro di monitoraggio e monitoraggio Web. I record obsoleti sono quelli precedenti al periodo di conservazione definito nella procedura guidata di distribuzione (fare riferimento alla procedura guidata [di](#deployment-wizard)distribuzione).

1. Innanzitutto, l&#39;elenco delle tabelle di registro di tracciamento viene recuperato utilizzando la seguente query:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. L&#39;eliminazione di massa viene utilizzata per eliminare tutte le tabelle nell&#39;elenco delle tabelle recuperate in precedenza. Viene utilizzata la seguente query:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   dove **$(tsDate)** è la data del server corrente dalla quale viene sottratto il periodo definito per l&#39;opzione **NmsCleanup_TrackingLogPurgeDelay** .

1. La tabella delle statistiche di tracciamento viene eliminata utilizzando l’eliminazione di massa. Viene utilizzata la seguente query:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   dove **$(tsDate)** è la data del server corrente dalla quale viene sottratto il periodo definito per l&#39;opzione **NmsCleanup_TrackingStatePurgeDelay** .

### Pulizia dei registri di consegna {#cleanup-of-delivery-logs}

Questa attività consente di eliminare i registri di consegna memorizzati in varie tabelle.

1. A tal fine, l&#39;elenco degli schemi di log di consegna viene recuperato utilizzando la seguente query:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Quando si utilizza il mid-sourcing, nelle mappature di consegna non viene fatto riferimento alla tabella **NmsBroadLogMid** . Lo schema **nms:wideLogMid** viene aggiunto all&#39;elenco recuperato dalla query precedente.
1. Il flusso di lavoro di pulizia **del** database elimina quindi i dati obsoleti dalle tabelle recuperate in precedenza. Viene utilizzata la seguente query:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   dove **$(tableName)** è il nome di ogni tabella nell&#39;elenco degli schemi e **$(option)** è la data definita per l&#39;opzione **NmsCleanup_BroadLogPurgeDelay** (fare riferimento alla procedura guidata [di](#deployment-wizard)distribuzione).

1. Infine, il flusso di lavoro verifica se esiste la tabella **NmsProviderMsgId** . In tal caso, tutti i dati obsoleti vengono eliminati utilizzando la seguente query:

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   dove **$(opzione)** corrisponde alla data definita per l&#39;opzione **NmsCleanup_BroadLogPurgeDelay** (fare riferimento alla procedura guidata [di](#deployment-wizard)distribuzione).

### Pulizia della tabella NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Questa attività elimina la tabella **NmsEmailErrorState** . Il programma principale (**coalesceErrors**) definisce due date:

* **Data** di inizio: data del processo successivo che corrisponde all&#39;opzione **NmsLastErrorStatCoalesce** o alla data più recente nella tabella.
* **Data** finale: data server corrente.

Se la data di inizio è maggiore o uguale alla data di fine, non verrà eseguita alcuna procedura. In questo caso viene visualizzato il messaggio **coalesceUpToDate** .

Se la data di inizio è precedente alla data di fine, la tabella **NmsEmailErrorStat** viene pulita.

Il numero totale di errori nella tabella **NmsEmailErrorStat** , tra le date di inizio e di fine, viene recuperato utilizzando la seguente query:

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

dove **$end** e **$start** sono le date di inizio e di fine definite in precedenza.

Se il totale è maggiore di 0:

1. La seguente query viene eseguita per mantenere solo gli errori oltre una determinata soglia (pari a 20):

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. Viene visualizzato il messaggio **ColescingErrors** .
1. Viene creata una nuova connessione per eliminare tutti gli errori che si sono verificati tra le date di inizio e di fine. Viene utilizzata la seguente query:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Ogni errore viene salvato nella tabella **NmsEmailErrorStat** utilizzando la seguente query:

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   dove ogni variabile corrisponde a un valore recuperato dalla query precedente.

1. La variabile **start** viene aggiornata con i valori del processo precedente per completare il ciclo.

Ciclo continuo e arresto attività.

Le pulizie vengono eseguite sulle tabelle **NmsEmailError** e **cleanupNmsMxDomain** .

### Pulizia della tabella NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

Viene utilizzata la seguente query:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Questa query elimina tutte le righe senza record collegati in **NmsEmailErrorStat** dalla tabella **NmsEmailError** .

### Pulizia della tabella NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

Viene utilizzata la seguente query:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Questa query elimina tutte le righe senza un record collegato nella tabella **NmsEmailErrorState** dalla tabella **NmsMxDomain** .

### Pulizia delle proposte {#cleanup-of-propositions}

Se è installato il modulo **Interazione** , questa attività viene eseguita per eliminare le tabelle **NmsPropositionXxx** .

L&#39;elenco delle tabelle di proposizioni viene recuperato e l&#39;eliminazione di massa viene eseguita su ognuna di esse, utilizzando la seguente query:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

dove **$(opzione)** è la data definita per l&#39;opzione **NmsCleanup_PropositionPurgeDelay** (fare riferimento alla [procedura guidata](#deployment-wizard)di distribuzione).

### Pulizia delle tabelle di simulazione {#cleanup-of-simulation-tables}

Questa operazione elimina le tabelle di simulazione orfane (che non sono più collegate a una simulazione di offerta o a una simulazione di consegna).

1. Per recuperare l&#39;elenco delle simulazioni che richiedono la pulizia, viene utilizzata la seguente query:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Il nome delle tabelle da eliminare è composto dal prefisso **wkSimu_** seguito dall’identificatore della simulazione (ad esempio: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Pulizia della traccia di controllo {#cleanup-of-audit-trail}

Viene utilizzata la seguente query:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

dove **$(tsDate)** è la data del server corrente dalla quale viene suddiviso il periodo definito per l&#39;opzione **XtkCleanup_AuditTrailPurgeDelay** .

### Pulizia di Nmsaddress {#cleanup-of-nmsaddress}

Viene utilizzata la seguente query:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Questa query elimina tutte le voci correlate a iOS e Android.

### Aggiornamento delle statistiche e ottimizzazione dello storage {#statistics-update}

L’opzione **XtkCleanup_NoStats** consente di controllare il comportamento del passaggio di ottimizzazione dell’archiviazione del flusso di lavoro di pulizia.

Se l&#39;opzione **XtkCleanup_NoStats** non esiste o se il relativo valore è 0, verrà eseguita l&#39;ottimizzazione dell&#39;archiviazione in modalità dettagliata (VACUUM VERBOSE ANALYZE) su PostgreSQL e verranno aggiornate le statistiche su tutti gli altri database. Per verificare che questo comando sia eseguito, controllare i registri PostSQL. VACUUM emette linee nel formato: `INFO: vacuuming "public.nmsactivecontact"` e ANALYZE genera le righe nel formato: `INFO: analyzing "public.nmsactivecontact"`.

Se il valore dell&#39;opzione è 1, l&#39;aggiornamento delle statistiche non viene eseguito su alcun database. Nei registri del flusso di lavoro verrà visualizzata la seguente riga di registro: `Option 'XtkCleanup_NoStats' is set to '1'`.

Se il valore dell&#39;opzione è 2, verrà eseguita l&#39;analisi dello storage in modalità dettagliata (ANALYZE VERBOSE) su PostgreSQL e verranno aggiornate le statistiche su tutti gli altri database. Per verificare che questo comando sia eseguito, controllare i registri PostSQL. ANALYZE genera le righe nel formato: `INFO: analyzing "public.nmsactivecontact"`.

### Pulizia iscrizione (NMAC) {#subscription-cleanup--nmac-}

Questa attività elimina tutte le sottoscrizioni relative ai servizi eliminati o alle applicazioni mobili.

Per recuperare l’elenco degli schemi di trasmissione, viene utilizzata la seguente query:

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

L&#39;attività quindi recupera i nomi delle tabelle collegate al collegamento **appSubscription** ed elimina queste tabelle.

Questo flusso di lavoro di pulizia elimina anche tutte le voci in cui disabilitato = 1 che non sono state aggiornate dall’ora impostata nell’opzione **NmsCleanup_AppSubscriptionRcpPurgeDelay** .

### Pulizia delle informazioni sulla sessione {#cleansing-session-information}

Questa attività elimina le informazioni dalla tabella **sessionInfo** . Viene utilizzata la seguente query:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Pulizia degli eventi scaduti {#cleansing-expired-events}

Questa attività pulisce gli eventi ricevuti e memorizzati nelle istanze di esecuzione e gli eventi archiviati in un&#39;istanza di controllo.

### Pulizia delle reazioni {#cleansing-reactions}

Questo compito pulisce le reazioni (tabella **NmsRemaMatchRcp**) in cui le ipotesi sono state eliminate.
