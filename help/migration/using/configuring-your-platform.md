---
product: campaign
title: Adatta la configurazione
description: Scopri come adattare la configurazione prima e dopo una migrazione a Campaign v7
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 3%

---

# Adatta la configurazione{#configuring-your-platform}

![](../../assets/v7-only.svg)

Alcune modifiche principali in Adobe Campaign v7 richiedono una configurazione specifica. Queste configurazioni possono essere necessarie prima o dopo la migrazione.

La configurazione dettagliata da eseguire in Adobe Campaign v7 durante la migrazione da Campaign v5 o v6 è disponibile in [questa pagina](general-configurations.md).


Durante la migrazione, il **NmsRecipient** la tabella viene ricreata dalla definizione degli schemi. Eventuali modifiche apportate alla struttura SQL di questa tabella al di fuori di Adobe Campaign andranno perse.

Esempio di elementi da controllare:

* Se hai aggiunto una colonna (o un indice) nel **NmsRecipient** tabella ma non dettagliata nello schema, questa non verrà salvata.
* La **tablespace** l&#39;attributo recupera i valori per impostazione predefinita, ovvero quelli definiti nella procedura guidata di distribuzione.
* Se hai aggiunto una visualizzazione di riferimento al **NmsRecipient** prima di eseguire la migrazione, è necessario eliminarla.


## Prima della migrazione {#before-the-migration}

Durante la migrazione ad Adobe Campaign v7, è necessario configurare i seguenti elementi. Questi elementi devono essere affrontati prima di avviare il **postupgrade**.

* Timezoni

   Durante una migrazione da una piattaforma v5.11, devi specificare il fuso orario da utilizzare durante il post aggiornamento.

   Se desideri utilizzare la modalità &quot;multi-fuso orario&quot;, consulta [questa sezione](../../migration/using/general-configurations.md#time-zones).

   Se utilizzi Oracle come database, verifica che i file del fuso orario Oracle siano stati sincronizzati correttamente tra l&#39;application server e il database server. [Ulteriori informazioni](../../migration/using/general-configurations.md#oracle)

* Zone di sicurezza

   Per motivi di sicurezza, la piattaforma Adobe Campaign non è più accessibile per impostazione predefinita: devi configurare le aree di protezione, che richiede la raccolta degli indirizzi IP dell’utente prima della migrazione. [Ulteriori informazioni](../../migration/using/general-configurations.md#security)

* Sintassi

   Alcuni codici JavaScript potrebbero non essere più accettati nella versione v7, a causa dell&#39;utilizzo di un nuovo interprete. [Ulteriori informazioni](../../migration/using/general-configurations.md#javascript).

   Analogamente, in Adobe Campaign v7 viene introdotta una nuova sintassi per sostituire la sintassi basata su SQLData. Se utilizzi elementi di codice con questa sintassi, devi adattarli. [Ulteriori informazioni](../../migration/using/general-configurations.md#sqldata)

* Password

   È necessario configurare le **Amministratore** e **Interno** password. [Ulteriori informazioni](../../migration/using/before-starting-migration.md#user-passwords)

* Struttura ad albero

   Se esegui la migrazione da una piattaforma v5.11, devi riorganizzare le cartelle della struttura ad albero in base alle norme Adobe Campaign v6. [Ulteriori informazioni](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interazione

   Se effettui la migrazione da Campaign v6.02 e utilizzi il  **Interazione** modulo , devi eliminare tutti i riferimenti di schema 6.02 che non esistono più in v7. [Ulteriori informazioni](../../migration/using/general-configurations.md#interaction)

## Dopo la migrazione {#after-the-migration}

Dopo l&#39;esecuzione **postupgrade**, controlla e configura i seguenti elementi:

* Pagine specchiate

   Il blocco di personalizzazione della pagina speculare è stato modificato con v6.x. Questa nuova versione migliora la sicurezza durante l’accesso a queste pagine.

   Se hai utilizzato il blocco di personalizzazione v5 nei messaggi, la visualizzazione della pagina speculare avrà esito negativo. Adobe consiglia vivamente di utilizzare il nuovo blocco di personalizzazione quando si inserisce una pagina speculare nei messaggi.

   Tuttavia, come soluzione temporanea (e dato che le pagine mirror sono ancora in tempo reale), puoi tornare al vecchio blocco di personalizzazione per evitare questo problema modificando l’opzione **[!UICONTROL XtkAcceptOldPasswords]** e impostarlo su **[!UICONTROL 1]**. Questo non influisce sull’utilizzo del nuovo blocco di personalizzazione v6.x.

* Sintassi

   Se si verificano errori relativi alla sintassi, durante il post aggiornamento devi attivare temporaneamente il **allowSQLInjection** in **serverConf.xml** file , poiché questo ti dà il tempo di riscrivere il codice. Una volta adattato il codice, assicurati di riattivare la sicurezza. [Ulteriori informazioni](../../migration/using/general-configurations.md#sqldata)

* Conflitti

   La migrazione viene eseguita tramite un aggiornamento successivo e possono comparire conflitti in rapporti, moduli o applicazioni web. Questi conflitti possono essere risolti dalla console. [Ulteriori informazioni](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Se hai personalizzato la cartella di installazione, accertati che sia stata aggiornata correttamente dopo la migrazione. [Ulteriori informazioni](../../migration/using/general-configurations.md#tomcat)

* Rapporti

   Tutti i report predefiniti al momento utilizzano il motore di rendering v6.x. Se hai aggiunto codice JavaScript ai rapporti, alcuni elementi potrebbero essere interessati. [Ulteriori informazioni](../../migration/using/general-configurations.md#reports)

* Applicazioni Web

   Dopo l&#39;aggiornamento, se si verificano problemi di connessione alle applicazioni Web identificate, è necessario attivare la **allowUserPassword** e **sessionTokenOnly** nelle opzioni **serverConf.xml** file. Per evitare problemi di sicurezza, queste due opzioni devono essere riattivate dopo che il problema è stato risolto. [Ulteriori informazioni](../../migration/using/general-configurations.md#identified-web-applications)

   A seconda del tipo di applicazioni Web e della relativa configurazione, è necessario eseguire ulteriori manipolazioni per garantirne il corretto funzionamento. [Ulteriori informazioni](../../migration/using/general-configurations.md#web-applications)

   Se si esegue la migrazione da una piattaforma v5.11, è necessario eseguire configurazioni aggiuntive. [Ulteriori informazioni](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Zone di sicurezza

   Prima di avviare il server, è necessario configurare le aree di protezione. [Ulteriori informazioni](../../installation/using/security-zones.md) e [vedi qui](../../migration/using/general-configurations.md#security)

* Flussi di lavoro

   Se esegui la migrazione da una piattaforma v5.11, devi controllare la cartella dei flussi di lavoro. [Ulteriori informazioni](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Tracciamento

   Se esegui la migrazione da una piattaforma v5.11, devi configurare la modalità di tracciamento. [Ulteriori informazioni](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interazione

   Se utilizzi **Interazione**, è necessario regolare eventuali parametri dopo la migrazione. [Ulteriori informazioni](../../migration/using/general-configurations.md#interaction)

* Dashboard

   Se viene visualizzato un errore client, è necessario aggiornare le dashboard con il nuovo codice Adobe Campaign v7 oppure copiare manualmente i seguenti file dall&#39;istanza v6.02 all&#39;istanza v7:

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Configurazioni specifiche da a v5.11 a v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

Questa sezione descrive la configurazione aggiuntiva necessaria per la migrazione dalla versione v5.11. È inoltre necessario configurare le impostazioni descritte in [Configurazioni generali](../../migration/using/general-configurations.md) sezione .

### Applicazioni web {#web-applications-v5}

Durante la migrazione verrà visualizzato automaticamente il seguente avviso:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Alcuni componenti delle applicazioni web, ad esempio i vari campi formula, hanno attributi @id. Vengono utilizzati nel codice XML delle applicazioni web e non vengono più generati nello stesso modo. Non sono visibili nell’interfaccia e non devono essere normalmente utilizzati. Tuttavia, in alcuni casi, gli attributi @id possono essere stati utilizzati per personalizzare il rendering delle applicazioni web, ad esempio tramite un foglio di stile o utilizzando il codice JavaScript.

Durante la migrazione, **deve** controllare il percorso del file di registro specificato nell&#39;avviso:

* **Il file non è vuoto**: contiene avvisi che riguardano incongruenze registrate prima della migrazione e che persistono. Può essere un codice JavaScript in un&#39;applicazione web che fa riferimento a un ID inesistente. Ogni errore deve essere controllato e corretto.
* **Il file è vuoto**: questo significa che Adobe Campaign non ha rilevato alcun problema.

Che il file sia vuoto o meno, devi verificare che questi ID non siano usati per la configurazione altrove (e, in questo caso, adatta la configurazione).

### Flussi di lavoro {#workflows}

Poiché il nome della directory di installazione di Adobe Campaign è stato modificato, alcuni flussi di lavoro potrebbero non funzionare dopo la migrazione. Se un flusso di lavoro fa riferimento alla directory nl5 in una delle sue attività, si verifica un errore. Sostituisci il riferimento con **build**. È possibile eseguire una query SQL per identificare questi flussi di lavoro (esempio PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL è supportato solo in v7 come motore di database principale quando si esegue la migrazione dalla versione 6.02 o 5.11 utilizzando questo motore.

Per impostazione predefinita, MySQL non gestisce i blocchi temporali. Per abilitare la gestione del fuso orario, esegui il comando seguente:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Per ulteriori informazioni, consulta la [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) pagina.

Se sono state apportate modifiche alla struttura del database, ad esempio durante la configurazione (creazione di indici specifici, creazione di viste SQL, ecc.), è necessario prendere alcune precauzioni durante la migrazione. In effetti, alcune modifiche possono essere generate da incompatibilità con la procedura di migrazione. Ad esempio, creazione di visualizzazioni SQL contenenti **Timestamp** i campi non sono compatibili con **usetimestamptz** opzione . Vi consigliamo pertanto di seguire le raccomandazioni seguenti:

1. Prima di avviare la migrazione, esegui il backup del database.
1. Elimina le modifiche SQL.
1. Esegui il post aggiornamento
   >[!NOTE]
   >
   >Devi seguire i passaggi di migrazione descritti in [questa sezione](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrare le modifiche SQL.

In questo esempio, un **NmcTrackingLogMessages** la visualizzazione è stata creata e presenta un **Timestamp** campo denominato **tslog**. In questo caso, la procedura di migrazione non riesce e viene visualizzato il seguente messaggio di errore:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Per assicurarsi che il post aggiornamento funzioni, è necessario eliminare la visualizzazione prima della migrazione e ricrearla dopo la migrazione, adattandola alla modalità TIMESTAMP WITH TIMEZONE.

### Tracciamento {#tracking}

La formula di tracciamento è stata modificata. Durante la migrazione, la vecchia formula (v5) viene sostituita dalla nuova (v7). Se utilizzi una formula personalizzata in Adobe Campaign v5, questa configurazione deve essere adattata in Adobe Campaign v7 (**NmsTracking_ClickFormula** e **NmsTracking_OpenFormula** opzioni).

È stata modificata anche la gestione del web tracking. Una volta effettuata la migrazione alla versione v7, devi avviare la procedura guidata di distribuzione per completare la configurazione del web tracking.

![](assets/migration_web_tracking.png)

Sono disponibili tre modalità:

* **Tracciamento web della sessione**: Se la **[!UICONTROL Leads]** pacchetto non installato. Questa opzione è selezionata per impostazione predefinita. Questa opzione è la più ideale in termini di prestazioni e ti consente di limitare le dimensioni dei log di tracciamento.
* **Tracciamento Web permanente**
* **Tracciamento web anonimo**: Se la **[!UICONTROL Leads]** pacchetto installato, questa opzione è selezionata per impostazione predefinita. È l’opzione che richiede più risorse. Come sopra, **sSourceId** deve essere indicizzata (nella tabella di tracciamento e nella **CrmIncomingLead** tabella).

>[!NOTE]
>
>Per ulteriori informazioni su queste tre modalità, consulta [questa sezione](../../configuration/using/about-web-tracking.md).

### Struttura ad albero di Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante la migrazione, la struttura ad albero viene riorganizzata automaticamente in base agli standard v7. Le nuove cartelle vengono aggiunte, le cartelle obsolete vengono eliminate e il loro contenuto viene inserito nella cartella &quot;Per spostare&quot;. Tutti gli elementi in questa cartella devono essere controllati dopo la migrazione e il consulente deve decidere di mantenerli o eliminarli. Gli oggetti da conservare devono quindi essere spostati nel posto giusto.

È stata aggiunta un’opzione per disabilitare la migrazione automatica della struttura di navigazione. Questa operazione è ora manuale. Le cartelle obsolete non vengono eliminate e non vengono aggiunte nuove cartelle. Questa opzione deve essere utilizzata solo se la struttura di navigazione preconfigurata v5 è stata sottoposta a troppe modifiche. Aggiungi l’opzione alla console prima di eseguire la migrazione nella **[!UICONTROL Administration > Options]** nodo:

* Nome interno: NlMigration_KeepFolderStructure
* Tipo di dati: Intero
* Valore (testo): 1

Se utilizzi questa opzione, dopo la migrazione dovrai eliminare le cartelle obsolete, aggiungere le nuove cartelle ed eseguire tutti i controlli necessari.

**Elenco delle nuove cartelle**:

Dopo la migrazione è necessario aggiungere le seguenti cartelle:

| Nome interno | Etichetta | Elemento “condizione” |
|---|---|---|
| nmsAutoObjects | Oggetti creati automaticamente | - |
| nmsCampaignAdmin | Gestione delle campagne | - |
| nmsCampaignMgt | Gestione delle campagne | - |
| nmsCampaignRes | Gestione delle campagne | - |
| nmsModels | Modelli | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Produzione | - |
| nmsProfilProcess | Processi | - |
| xtkDashboard | Dashboard | - |
| xtkPlatformAdmin | Piattaforma | - |
| nmsLocalOrgUnit | Unità organizzative | - |
| nmsMRM | MRM | MRM installato |
| nmsOperations | Campagne | Campaign installato |

**Elenco delle cartelle obsolete**:

Le cartelle obsolete da eliminare dopo la migrazione sono le seguenti:

>[!NOTE]
>
>È necessario controllare l&#39;intero contenuto delle cartelle obsolete e per ogni elemento il consulente decide se conservarlo o eliminarlo. Gli oggetti da conservare devono essere spostati nel luogo appropriato.

| Nome interno | Etichetta | Elemento “condizione” |
|---|---|---|
| nmsAdministration | Amministrazione | - |
| nmsDeliveryMgt | Esecuzione della campagna | - |
| ncmContent | Gestione dei contenuti | Content Manager installato |
| ncmForm | Modulo di input | Content Manager installato |
| ncmImage | Immagini | Content Manager installato |
| ncmJavascript | Codici JavaScript | Content Manager installato |
| ncmJst | Modelli JavaScript | Content Manager installato |
| ncmParameters | Configurazione | Content Manager installato |
| ncmSrcSchema | Schemi di dati | Content Manager installato |
| ncmStylesheet | File di stile XSL | Content Manager installato |
| nmsAdminPlan | Amministrazione | Campaign installato |
| nmsResourcePlan | Resources | Campaign installato |
| nmsResourcesModels | Modelli | Campaign installato |
| nmsRootPlan | Gestione delle campagne | Campaign installato |
| nmsOperator | Operatori di marketing | MRM installato |


## Configurazioni specifiche dalla versione v6.02 alla versione v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

La sezione seguente descrive la configurazione aggiuntiva necessaria per la migrazione dalla versione v6.02. È inoltre necessario configurare le impostazioni descritte in [questa pagina](../../migration/using/general-configurations.md).

### Applicazioni web {#web-applications-v6}

Se stai eseguendo la migrazione dalla versione v6.02, potrebbero essere visualizzati registri di errore relativi alle applicazioni web di tipo panoramica. Esempi di messaggi di errore:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Queste applicazioni web hanno utilizzato SQLData e non sono compatibili con v7, a causa di una maggiore sicurezza. Questi errori causeranno un errore di migrazione.

Se non hai utilizzato queste applicazioni web, esegui il seguente script di pulizia ed esegui nuovamente il post aggiornamento:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Se hai modificato queste applicazioni web e desideri continuare a utilizzarle in v7, devi attivare la **allowSQLInjection** nelle diverse aree di protezione e riavvia l&#39;aggiornamento successivo. Fai riferimento a [SQLData](../../migration/using/general-configurations.md#sqldata) per ulteriori informazioni.

### Centro messaggi {#message-center}

Dopo la migrazione di un&#39;istanza di controllo del Centro messaggi, devi ripubblicare i modelli dei messaggi transazionali affinché funzionino.

In v7, i nomi dei modelli di messaggi transazionali nelle istanze di esecuzione sono cambiati. Sono attualmente preceduti dal nome dell’operatore che corrisponde all’istanza di controllo in cui sono stati creati, ad esempio **control1_template1_rt** (4) **control1** è il nome dell&#39;operatore). Se si dispone di un volume significativo di modelli, è consigliabile eliminare i vecchi modelli nelle istanze di controllo.