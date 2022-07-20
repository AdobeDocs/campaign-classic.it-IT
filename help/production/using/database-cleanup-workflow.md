---
product: campaign
title: Flusso di lavoro di pulizia del database
description: Scopri in che modo i dati obsoleti vengono eliminati automaticamente
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 56e9fcc4240649f53239b12f1390dea041602e79
workflow-type: tm+mt
source-wordcount: '2823'
ht-degree: 0%

---

# Flusso di lavoro di pulizia del database{#database-cleanup-workflow}

![](../../assets/v7-only.svg)

## Introduzione {#introduction}

La **[!UICONTROL Database cleanup]** flusso di lavoro accessibile tramite **[!UICONTROL Administration > Production > Technical workflows]** node, consente di eliminare i dati obsoleti per evitare la crescita esponenziale del database. Il flusso di lavoro viene attivato automaticamente senza l’intervento dell’utente.

![cleanup](assets/ncs_cleanup_workflow.png)

## Configurazione {#configuration}

La pulizia del database è configurata su due livelli: nella pianificazione del flusso di lavoro e nella procedura guidata di distribuzione.

### Utilità di pianificazione dei flussi di lavoro {#the-scheduler}

>[!NOTE]
>
>Per ulteriori informazioni sulla pianificazione, consulta [questa sezione](../../workflow/using/scheduler.md).

Per impostazione predefinita, la **[!UICONTROL Database cleanup]** il flusso di lavoro è configurato per iniziare ogni giorno alle 4 del mattino. La pianificazione consente di modificare la frequenza di attivazione del flusso di lavoro. Sono disponibili le seguenti frequenze:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![schedulatore](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Al fine di **[!UICONTROL Database cleanup]** per avviare il flusso di lavoro alla data e all’ora definite nella pianificazione, è necessario avviare il motore del flusso di lavoro (wfserver).

### Procedura guidata di distribuzione {#deployment-wizard}

La **[!UICONTROL Deployment wizard]**, accessibile tramite **[!UICONTROL Tools > Advanced]** consente di configurare per quanto tempo vengono salvati i dati. I valori sono espressi in giorni. Se tali valori non vengono modificati, il flusso di lavoro utilizza i valori predefiniti.

![](assets/ncs_cleanup_deployment-wizard.png)

I campi **[!UICONTROL Purge of data]** la finestra coincide con le seguenti opzioni. Vengono utilizzati da alcune delle attività eseguite da **[!UICONTROL Database cleanup]** flusso di lavoro:

* Tracciamento consolidato: **NmsCleanup_TrackingStatePurgeDelay** (fare riferimento a [Pulizia dei registri di tracciamento](#cleanup-of-tracking-logs))
* Log di consegna: **NmsCleanup_BroadLogPurgeDelay** (fare riferimento a [Pulizia dei registri di consegna](#cleanup-of-delivery-logs))
* Registri di tracciamento: **NmsCleanup_TrackingLogPurgeDelay** (fare riferimento a [Pulizia dei registri di tracciamento](#cleanup-of-tracking-logs))
* Consegne eliminate: **NmsCleanup_RecycledDeliveryPurgeDelay** (fare riferimento a [Pulizia delle consegne da eliminare o riciclare](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Rifiuti di importazione: **NmsCleanup_RejectsPurgeDelay** (fare riferimento a [Pulizia dei rifiuti prodotti dalle importazioni](#cleanup-of-rejects-generated-by-imports-))
* Profili dei visitatori: **NmsCleanup_VisitorPurgeDelay** (fare riferimento a [Pulizia dei visitatori](#cleanup-of-visitors))
* Proposte di offerta: **NmsCleanup_PropositionPurgeDelay** (fare riferimento a [Pulizia delle proposte](#cleanup-of-propositions))

   >[!NOTE]
   >
   >La **[!UICONTROL Offer propositions]** è disponibile solo quando il campo **Interazione** modulo installato.

* Eventi: **NmsCleanup_EventPurgeDelay** (fare riferimento a [Pulizia degli eventi scaduti](#cleansing-expired-events))
* Eventi archiviati: **NmsCleanup_EventHistoPurgeDelay** (fare riferimento a [Pulizia degli eventi scaduti](#cleansing-expired-events))

   >[!NOTE]
   >
   >La **[!UICONTROL Events]** e **[!UICONTROL Archived events]** i campi sono disponibili solo se **Centro messaggi** modulo installato.

* Audit trail: **XtkCleanup_AuditTrailPurgeDelay** (fare riferimento a [Pulizia della pista di controllo](#cleanup-of-audit-trail))

Tutte le attività eseguite da **[!UICONTROL Database cleanup]** il flusso di lavoro è descritto nella sezione seguente.

## Attività eseguite dal flusso di lavoro di pulizia del database {#tasks-carried-out-by-the-database-cleanup-workflow}

Alla data e all’ora definite nella pianificazione del flusso di lavoro (consulta [Programmatore](#the-scheduler)), il motore del flusso di lavoro avvia il processo di pulizia del database. La pulizia del database si connette al database ed esegue le attività nella sequenza riportata di seguito.

>[!IMPORTANT]
>
>Se una di queste attività ha esito negativo, quelle successive non vengono eseguite.
>
>Query SQL con un **LIMITE** vengono eseguiti ripetutamente fino a quando tutte le informazioni non vengono elaborate.


### Elenchi da eliminare {#lists-to-delete-cleanup}

La prima attività eseguita da **[!UICONTROL Database cleanup]** il flusso di lavoro elimina tutti i gruppi con **deleteStatus != 0** attributo dal **NmsGroup**. Vengono inoltre eliminati i record collegati a tali gruppi e presenti in altre tabelle.

1. Gli elenchi da eliminare vengono recuperati utilizzando la seguente query SQL:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Ogni elenco include diversi collegamenti ad altre tabelle. Tutti questi collegamenti vengono eliminati in blocco utilizzando la seguente query:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   dove `$(relatedTable)` è una tabella correlata a **NmsGroup** e `$(l)` è l&#39;identificatore dell&#39;elenco.

1. Quando l’elenco è un elenco di tipo &quot;Elenco&quot;, la tabella associata viene eliminata utilizzando la seguente query:

   ```sql
   DROP TABLE grp$(l)
   ```

1. Ogni **Seleziona** l&#39;elenco dei tipi recuperato dall&#39;operazione viene eliminato utilizzando la seguente query:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   dove `$(l)` è l&#39;identificatore dell&#39;elenco

### Pulizia delle consegne da eliminare o riciclare {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Questa attività elimina tutte le consegne da eliminare o riciclare.

1. La **[!UICONTROL Database cleanup]** seleziona tutte le consegne per le quali il **deleteStatus** il campo ha il valore **[!UICONTROL Yes]** o **[!UICONTROL Recycled]** e la cui data di cancellazione è precedente al periodo definito nel **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) della procedura guidata di distribuzione. Per ulteriori informazioni, consulta [Procedura guidata di distribuzione](#deployment-wizard). Questo periodo è calcolato in relazione alla data corrente del server.
1. Per ogni server di mid-sourcing, l&#39;attività seleziona l&#39;elenco delle consegne da eliminare.
1. La **[!UICONTROL Database cleanup]** il flusso di lavoro elimina i registri di consegna, gli allegati, le informazioni della pagina speculare e tutti gli altri dati correlati.
1. Prima di eliminare definitivamente la consegna, il flusso di lavoro elimina le informazioni collegate dalle tabelle seguenti:

   * Nella tabella di esclusione della consegna (**NmsDlvExclusion**), viene utilizzata la seguente query:

      ```sql
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      dove **$(l)** è l’identificatore della consegna.

   * Nella tabella delle cedole (**NmsCouponValue**), viene utilizzata la seguente query (con eliminazioni di massa):

      ```sql
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      dove `$(l)` è l’identificatore della consegna.

   * Nelle tabelle dei registri di consegna (**NmsBroadlogXxx**), le eliminazioni di massa vengono eseguite in batch di 20.000 record.
   * Nelle tabelle delle proposte di offerta (**NmsPropositionXxx**), le eliminazioni di massa vengono eseguite in batch di 20.000 record.
   * Nelle tabelle dei registri di tracciamento (**NmsTrackinglogXxx**), le eliminazioni di massa vengono eseguite in batch di 20.000 record.
   * Nella tabella dei frammenti di consegna (**NmsDeliveryPart**), le eliminazioni di massa vengono eseguite in batch di 500.000 record. Questa tabella contiene informazioni di personalizzazione sui messaggi rimanenti da consegnare.
   * Nella tabella dei frammenti di dati della pagina speculare (**NmsMirrorPageInfo**), le eliminazioni di massa vengono eseguite in batch di 20.000 record per le parti di consegna scadute e per quelle finite o annullate. Questa tabella contiene informazioni di personalizzazione su tutti i messaggi utilizzati per generare pagine mirror.
   * Nella tabella di ricerca della pagina speculare (**NmsMirrorPageSearch**), le eliminazioni di massa vengono eseguite in batch di 20.000 record. Questa tabella è un indice di ricerca che fornisce accesso alle informazioni di personalizzazione memorizzate in **NmsMirrorPageInfo** tabella.
   * Nella tabella del registro del processo batch (**XtkJobLog**), le eliminazioni di massa vengono eseguite in batch di 20.000 record. Questa tabella contiene il registro delle consegne da eliminare.
   * Nella tabella di tracciamento degli URL di consegna (**NmsTrackingUrl**), viene utilizzata la seguente query:

      ```sql
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      dove `$(l)` è l’identificatore della consegna.

      Questa tabella contiene gli URL trovati nelle consegne da eliminare per abilitarne il tracciamento.

1. La consegna viene eliminata dalla tabella di consegna (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   dove `$(l)` è l’identificatore della consegna.

#### Consegne tramite mid-sourcing {#deliveries-using-mid-sourcing}

La **[!UICONTROL Database cleanup]** il flusso di lavoro elimina anche le consegne sui server di mid-sourcing.

1. A questo scopo, il flusso di lavoro controlla che ogni consegna sia inattiva (in base al suo stato). Se una consegna è attiva, verrà interrotta prima di essere eliminata. Il controllo viene eseguito eseguendo la seguente query:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   dove **$(l)** è l’identificatore della consegna.

1. Se il valore dello stato è **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** oppure **[!UICONTROL Paused]** (valori 51, 55, 61, 62, 71, 72, 75), la consegna viene interrotta e l&#39;attività elimina le informazioni collegate.

### Pulizia delle consegne scadute {#cleanup-of-expired-deliveries}

Questa attività interrompe le consegne il cui periodo di validità è scaduto.

1. La **[!UICONTROL Database cleanup]** crea l’elenco delle consegne scadute. Questo elenco include tutte le consegne scadute con uno stato diverso da **[!UICONTROL Finished]** , così come ha interrotto di recente le consegne con oltre 10.000 messaggi non elaborati. Viene utilizzata la seguente query:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   dove `delivery mode 1` corrisponde a **[!UICONTROL Mass delivery]** modalità, `state 51` corrisponde a **[!UICONTROL Start pending]** stato, `state 85` corrisponde a **[!UICONTROL Stopped]** e il numero più alto di log di consegna aggiornati in massa sul server di consegna è uguale a 10.000.

1. Il flusso di lavoro include quindi l’elenco delle consegne scadute di recente che utilizzano il mid-sourcing. Sono escluse le consegne per le quali non sono ancora stati recuperati log di consegna tramite il server di mid-sourcing .

   Viene utilizzata la seguente query:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. La seguente query viene utilizzata per rilevare se l’account esterno è ancora attivo o meno, per filtrare le consegne per data:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. Nell’elenco delle consegne scadute, registri di consegna il cui stato è **[!UICONTROL Pending]** , passa a **[!UICONTROL Delivery cancelled]** e tutte le consegne in questo elenco passano a **[!UICONTROL Finished]** .

   Vengono utilizzate le seguenti query:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   dove `$(curdate)`è la data corrente del server di database, `$(bl)` è l’identificatore del messaggio dei registri di consegna, `$(dl)` è l’identificatore di consegna, `delivery status 6` corrisponde a **[!UICONTROL Pending]** lo stato e `delivery status 7` corrisponde a **[!UICONTROL Delivery cancelled]** stato.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   dove `delivery state 95` corrisponde a **[!UICONTROL Finished]** lo stato e `$(dl)` è l’identificatore della consegna.

1. Tutti i frammenti (**deliveryParts**) delle consegne obsolete vengono eliminate e tutti i frammenti obsoleti delle consegne di notifica in corso vengono eliminati. L&#39;eliminazione di massa viene utilizzata per entrambe queste attività.

   Vengono utilizzate le seguenti query:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   dove `delivery state 95` corrisponde a **[!UICONTROL Finished]** status, `delivery state 85` corrisponde a **[!UICONTROL Stopped]** lo stato e `$(curDate)` è la data corrente del server.

### Pulizia delle pagine mirror {#cleanup-of-mirror-pages}

Questa attività elimina le risorse web (pagine mirror) utilizzate dalle consegne.

1. Innanzitutto, l’elenco delle consegne da eliminare viene recuperato utilizzando la seguente query:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   dove `$(curDate)` è la data corrente del server.

1. La **NmsMirrorPageInfo** viene quindi eliminata, se necessario utilizzando l’identificatore della consegna recuperata in precedenza. L’eliminazione di massa viene utilizzata per generare le query seguenti:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   dove `$(dl)` è l’identificatore della consegna.

1. Viene quindi aggiunta una voce al registro di consegna.
1. Vengono quindi individuate le consegne sollecitate, per evitare di doverle rielaborare in un secondo momento. Viene eseguita la seguente query:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   dove `$(strIn)` è l’elenco degli identificatori di consegna.

### Pulizia delle tabelle di lavoro {#cleanup-of-work-tables}

Questa attività elimina dal database tutte le tabelle di lavoro che corrispondono alle consegne il cui stato è **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** o **[!UICONTROL Deleted]** .

1. Elenco delle tabelle con nomi che iniziano con **wkDlv_** viene recuperato prima con la seguente query (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Le tabelle utilizzate dai flussi di lavoro in corso vengono quindi escluse. A questo scopo, l’elenco delle consegne in corso viene recuperato utilizzando la seguente query:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   dove `0` è il valore che corrisponde al **[!UICONTROL Being edited]** stato della consegna, `85` corrisponde a **[!UICONTROL Stopped]** lo stato e `100` corrisponde a **[!UICONTROL Deleted]** stato.

1. Le tabelle non più utilizzate verranno eliminate utilizzando la seguente query:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Pulizia dei rifiuti prodotti dalle importazioni {#cleanup-of-rejects-generated-by-imports-}

Questo passaggio ti consente di eliminare i record per i quali non sono stati elaborati tutti i dati durante l’importazione.

1. L&#39;eliminazione di massa viene effettuata sul **XtkReject** tabella con la seguente query:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   dove `$(curDate)` è la data corrente del server da cui sottraggiamo il periodo definito per il **NmsCleanup_RejectsPurgeDelay** (fai riferimento a [Procedura guidata di distribuzione](#deployment-wizard)) e `$(l)` è il numero massimo di record da eliminare in massa.

1. Tutti i rifiuti orfani vengono quindi eliminati utilizzando la seguente query:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Pulizia delle istanze del flusso di lavoro {#cleanup-of-workflow-instances}

Questa attività elimina ogni istanza del flusso di lavoro utilizzando il relativo identificatore (**lWorkflowId**) e la cronologia (**Cronologia**). Elimina le tabelle inattive eseguendo nuovamente l&#39;attività di pulizia della tabella di lavoro. La pulizia elimina anche tutte le tabelle di lavoro orfane (wkf% e wkfhisto%) dei flussi di lavoro eliminati.

>[!NOTE]
>
>La frequenza di eliminazione della cronologia viene specificata per ogni flusso di lavoro nel **Storia nei giorni** (valore predefinito 30 giorni). Questo campo si trova nella **Esecuzione** scheda delle proprietà del flusso di lavoro. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/workflow-properties.md#execution).

1. Per recuperare l’elenco dei flussi di lavoro da eliminare, viene utilizzata la seguente query:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Questa query genera l’elenco dei flussi di lavoro che verranno utilizzati per eliminare tutti i registri collegati, le attività completate e gli eventi completati, utilizzando le query seguenti:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   dove `$(lworkflow)` è l’identificatore del flusso di lavoro e `$(lhistory)` è l&#39;identificatore della cronologia.

1. Tutte le tabelle non utilizzate vengono eliminate. A tal fine, tutte le tabelle vengono raccolte grazie a un **wkf%** digita la maschera utilizzando la seguente query (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Vengono quindi escluse tutte le tabelle utilizzate da un’istanza di flusso di lavoro in sospeso. L’elenco dei flussi di lavoro attivi viene recuperato utilizzando la seguente query:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Ogni identificatore del flusso di lavoro viene quindi recuperato per trovare il nome delle tabelle utilizzate dai flussi di lavoro in corso. Questi nomi sono esclusi dall&#39;elenco delle tabelle precedentemente recuperate.
1. Le tabelle della cronologia delle attività di tipo &quot;query incrementale&quot; sono escluse utilizzando le seguenti query:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   dove `$(strcondition)` è l’elenco delle tabelle che corrispondono al **wkfhisto%** maschera.

1. Le tabelle rimanenti vengono eliminate utilizzando la seguente query:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Pulizia degli accessi al flusso di lavoro {#cleanup-of-workflow-logins}

Questa attività elimina gli accessi al flusso di lavoro utilizzando la seguente query:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Pulizia delle tabelle di lavoro orfane {#cleanup-of-orphan-work-tables}

Questa attività elimina le tabelle di lavoro orfane collegate ai gruppi. La **NmsGroup** in tabella vengono memorizzati i gruppi da pulire (con un tipo diverso da 0). Il prefisso dei nomi delle tabelle è **grp**. Per identificare i gruppi da pulire, viene utilizzata la seguente query:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Pulizia dei visitatori {#cleanup-of-visitors}

Questa attività elimina i record obsoleti dalla tabella dei visitatori utilizzando l’eliminazione di massa. I record obsoleti sono quelli per i quali l&#39;ultima modifica è precedente al periodo di conservazione definito nella procedura guidata di distribuzione (fare riferimento a [Procedura guidata di distribuzione](#deployment-wizard)). Viene utilizzata la seguente query:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

dove `$(tsDate)` è la data corrente del server, dalla quale sottrarremo il periodo definito per il **NmsCleanup_VisitorPurgeDelay** opzione .

### Pulizia di NPAI {#cleanup-of-npai}

Questa attività ti consente di eliminare i record che corrispondono a indirizzi validi dalla **NmsAddress** tabella. La seguente query viene utilizzata per eseguire l&#39;eliminazione di massa:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

dove `status 2` corrisponde a **[!UICONTROL Valid]** status, `$(tsDate1)` è la data corrente del server, e `$(tsDate2)` corrisponde a **NmsCleanup_LastCleanup** opzione .

### Pulizia degli abbonamenti {#cleanup-of-subscriptions-}

Questa attività elimina tutte le sottoscrizioni eliminate dall&#39;utente dal **NmsSubscription** tabella, con eliminazione di massa. Viene utilizzata la seguente query:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Pulizia dei registri di tracciamento {#cleanup-of-tracking-logs}

Questa attività elimina i record obsoleti dalle tabelle di registro di tracking e di webtracking. I record obsoleti sono quelli precedenti al periodo di conservazione definito nella procedura guidata di distribuzione (fare riferimento a [Procedura guidata di distribuzione](#deployment-wizard)).

1. Innanzitutto, l&#39;elenco delle tabelle di log di tracking viene recuperato utilizzando la seguente query:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. L&#39;eliminazione di massa viene utilizzata per eliminare tutte le tabelle nell&#39;elenco delle tabelle recuperate in precedenza. Viene utilizzata la seguente query:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   dove `$(tsDate)` è la data corrente del server da cui sottraggiamo il periodo definito per il **NmsCleanup_TrackingLogPurgeDelay** opzione .

1. La tabella delle statistiche di tracciamento viene eliminata utilizzando l’eliminazione di massa. Viene utilizzata la seguente query:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   dove `$(tsDate)` è la data corrente del server da cui sottraggiamo il periodo definito per il **NmsCleanup_TrackingStatePurgeDelay** opzione .

### Pulizia dei registri di consegna {#cleanup-of-delivery-logs}

Questa attività ti consente di eliminare i registri di consegna memorizzati in varie tabelle.

1. A questo scopo, l’elenco degli schemi di log di consegna viene recuperato utilizzando la seguente query:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Quando si utilizza l&#39;mid-sourcing, la funzione **NmsBroadLogMid** nelle mappature di consegna non viene fatto riferimento alla tabella. La **nms:wideLogMid** lo schema viene aggiunto all&#39;elenco recuperato dalla query precedente.
1. La **Pulizia del database** quindi elimina i dati obsoleti dalle tabelle recuperate in precedenza. Viene utilizzata la seguente query:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   dove `$(tableName)` è il nome di ciascuna tabella dell’elenco degli schemi, e `$(option)` è la data definita per **NmsCleanup_BroadLogPurgeDelay** (fai riferimento a [Procedura guidata di distribuzione](#deployment-wizard)).

1. Infine, il flusso di lavoro controlla se il **NmsProviderMsgId** tabella esistente. In tal caso, tutti i dati obsoleti vengono eliminati utilizzando la seguente query:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   dove `$(option)` corrisponde alla data definita per **NmsCleanup_BroadLogPurgeDelay** (fai riferimento a [Procedura guidata di distribuzione](#deployment-wizard)).

### Pulizia della tabella NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Questa attività pulisce la **NmsEmailErrorState** tabella. Il programma principale (**coalesceErrors**) definisce due date:

* **Data di inizio**: data del processo successivo che corrisponde alla **NmsLastErrorStatCoalesce** o la data più recente nella tabella.
* **Data di fine**: data corrente del server.

Se la data di inizio è maggiore o uguale alla data di fine, non verrà eseguita alcuna procedura. In questo caso, il **coalesceUpToDate** viene visualizzato un messaggio.

Se la data di inizio è precedente alla data di fine, la **NmsEmailErrorState** il tavolo è pulito.

Numero totale di errori nel **NmsEmailErrorState** tra le date di inizio e di fine viene recuperata utilizzando la seguente query:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

dove `$end` e `$start` sono le date di inizio e di fine definite in precedenza.

Se il totale è maggiore di 0:

1. Viene eseguita la seguente query per mantenere solo gli errori oltre una determinata soglia (che è uguale a 20):

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. La **coalescingErrors** viene visualizzato il messaggio.
1. Viene creata una nuova connessione per eliminare tutti gli errori che si sono verificati tra le date di inizio e di fine. Viene utilizzata la seguente query:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Ogni errore viene salvato nel **NmsEmailErrorState** tabella utilizzando la seguente query:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   dove ogni variabile corrisponde a un valore recuperato dalla query precedente.

1. La **start** viene aggiornata con i valori del processo precedente per completare il ciclo.

Il ciclo e l&#39;attività si fermano.

Le operazioni di pulizia vengono eseguite in **NmsEmailError** e **cleanupNmsMxDomain** tabelle.

### Pulizia della tabella NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

Viene utilizzata la seguente query:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Questa query elimina tutte le righe senza record collegati nel **NmsEmailErrorState** dal **NmsEmailError** tabella.

### Pulizia della tabella NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

Viene utilizzata la seguente query:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Questa query elimina tutte le righe senza un record collegato nel **NmsEmailErrorState** dalla tabella **NmsMxDomain** tabella.

### Pulizia delle proposte {#cleanup-of-propositions}

Se la **Interazione** il modulo è installato, questa attività viene eseguita per eliminare il **NmsPropositionXxx** tabelle.

L&#39;elenco delle tabelle delle proposte viene recuperato e l&#39;eliminazione di massa viene eseguita su ognuna di esse, utilizzando la seguente query:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

dove `$(option)` è la data definita per **NmsCleanup_PropositionPurgeDelay** (fai riferimento a [Procedura guidata di distribuzione](#deployment-wizard)).

### Pulizia delle tabelle di simulazione {#cleanup-of-simulation-tables}

Questa attività pulisce le tabelle di simulazione orfane (che non sono più collegate a una simulazione di offerta o a una simulazione di consegna).

1. Per recuperare l’elenco delle simulazioni che richiedono la pulizia, viene utilizzata la seguente query:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Il nome delle tabelle da eliminare è costituito dal **wkSimu_** Prefisso seguito dall’identificatore della simulazione (ad esempio: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Pulizia della pista di controllo {#cleanup-of-audit-trail}

Viene utilizzata la seguente query:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

dove **$(tsDate)** è la data corrente del server a partire dalla quale il periodo definito per **XtkCleanup_AuditTrailPurgeDelay** viene sottratta.

### Pulizia di Nmsaddress {#cleanup-of-nmsaddress}

Viene utilizzata la seguente query:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Questa query elimina tutte le voci relative ad iOS e Android.

### Aggiornamento delle statistiche e ottimizzazione dello storage {#statistics-update}

La **XtkCleanup_NoStats** consente di controllare il comportamento della fase di ottimizzazione dello storage del flusso di lavoro di pulizia.

Se la **XtkCleanup_NoStats** l&#39;opzione non esiste o, se il valore è 0, esegue l&#39;ottimizzazione dello storage in modalità dettagliata (VACUUM VERBOSE ANALYZE) su PostgreSQL e aggiorna le statistiche su tutti gli altri database. Per verificare che questo comando sia eseguito, controlla i log PostgreSQL. VACUUM genera linee nel formato: `INFO: vacuuming "public.nmsactivecontact"` e ANALYZE genera le linee nel formato: `INFO: analyzing "public.nmsactivecontact"`.

Se il valore dell&#39;opzione è 1, l&#39;aggiornamento delle statistiche non viene eseguito su alcun database. Nei registri del flusso di lavoro viene visualizzata la seguente riga di registro: `Option 'XtkCleanup_NoStats' is set to '1'`.

Se il valore dell&#39;opzione è 2, questo eseguirà l&#39;analisi dello storage in modalità dettagliata (ANALYZE VERBOSE) su PostgreSQL e aggiornerà le statistiche su tutti gli altri database. Per verificare che questo comando sia eseguito, controlla i log PostgreSQL. ANALYZE genera linee nel formato seguente: `INFO: analyzing "public.nmsactivecontact"`.

### Pulizia sottoscrizione (NMAC) {#subscription-cleanup--nmac-}

Questa attività elimina tutti gli abbonamenti relativi ai servizi eliminati o alle applicazioni mobili.

Per recuperare l’elenco degli schemi di registro di trasmissione, viene utilizzata la seguente query:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

L&#39;attività recupera quindi i nomi delle tabelle collegate al **appSubscription** collega ed elimina queste tabelle.

Questo flusso di lavoro di pulizia elimina anche tutte le voci in cui idisabled = 1 che non sono state aggiornate dall&#39;ora impostata nel **NmsCleanup_AppSubscriptionRcpPurgeDelay** opzione .

### Pulizia delle informazioni sulla sessione {#cleansing-session-information}

Questa attività elimina le informazioni dal **sessionInfo** tabella, viene utilizzata la seguente query:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Pulizia degli eventi scaduti {#cleansing-expired-events}

Questa attività pulisce gli eventi ricevuti e memorizzati nelle istanze di esecuzione e gli eventi archiviati in un&#39;istanza di controllo.

### Pulizia delle reazioni {#cleansing-reactions}

Questo compito pulisce le reazioni (tabella **NmsRemaMatchRcp**) in cui sono state soppresse le ipotesi.
