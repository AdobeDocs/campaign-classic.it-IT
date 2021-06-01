---
product: campaign
title: Configurazioni specifiche nella versione v5.11
description: Configurazioni specifiche nella versione v5.11
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 978e1249-f79b-4f5f-9a94-3bb2510785de
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 3%

---

# Configurazioni specifiche nella versione v5.11{#specific-configurations-in-v5-11}

Questa sezione descrive la configurazione aggiuntiva necessaria per la migrazione dalla versione v5.11. È inoltre necessario configurare le impostazioni descritte nella sezione [Configurazioni generali](../../migration/using/general-configurations.md) .

## Applicazioni web {#web-applications}

Durante la migrazione verrà visualizzato automaticamente il seguente avviso:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Alcuni componenti delle applicazioni web, ad esempio i vari campi formula, hanno attributi @id. Vengono utilizzati nel codice XML delle applicazioni web e non vengono più generati nello stesso modo. Non sono visibili nell’interfaccia e non devono essere normalmente utilizzati. Tuttavia, in alcuni casi, gli attributi @id possono essere stati utilizzati per personalizzare il rendering delle applicazioni web, ad esempio tramite un foglio di stile o utilizzando il codice JavaScript.

Durante la migrazione, **è necessario** controllare il percorso del file di registro specificato nell&#39;avviso:

* **Il file non è vuoto**: contiene avvisi che riguardano incongruenze registrate prima della migrazione e che persistono. Può essere un codice JavaScript in un&#39;applicazione web che fa riferimento a un ID inesistente. Ogni errore deve essere controllato e corretto.
* **Il file è vuoto**: questo significa che Adobe Campaign non ha rilevato alcun problema.

Che il file sia vuoto o meno, devi verificare che questi ID non siano usati per la configurazione altrove (e, in questo caso, adatta la configurazione).

## Flussi di lavoro {#workflows}

Poiché il nome della directory di installazione di Adobe Campaign è stato modificato, alcuni flussi di lavoro potrebbero non funzionare dopo la migrazione. Se un flusso di lavoro fa riferimento alla directory nl5 in una delle sue attività, si verifica un errore. Sostituisci questo riferimento con **build**. È possibile eseguire una query SQL per identificare questi flussi di lavoro (esempio PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Facilità di utilizzo {#user-friendliness}

La home page di Adobe Campaign v5.11 non è più disponibile.

Sebbene non sia consigliato, esistono alcune soluzioni per mantenere interfacce specifiche da Adobe Campaign v5.11. Per ulteriori informazioni, contattateci.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL è supportato solo in v7 come motore di database principale quando si esegue la migrazione dalla versione 6.02 o 5.11 utilizzando questo motore.

Per impostazione predefinita, MySQL non gestisce i blocchi temporali. Per abilitare la gestione del fuso orario, esegui il comando seguente:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Per ulteriori informazioni, consulta la pagina [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) .

Se sono state apportate modifiche alla struttura del database, ad esempio durante la configurazione (creazione di indici specifici, creazione di viste SQL, ecc.), è necessario prendere alcune precauzioni durante la migrazione. In effetti, alcune modifiche possono essere generate da incompatibilità con la procedura di migrazione. Ad esempio, la creazione di visualizzazioni SQL contenenti campi **Timestamp** non è compatibile con l&#39;opzione **usetimestamptz**. Vi consigliamo pertanto di seguire le raccomandazioni seguenti:

1. Prima di avviare la migrazione, esegui il backup del database.
1. Elimina le modifiche SQL.
1. Esegui l&#39;aggiornamento successivo in base alla procedura descritta nella sezione [Prerequisiti per la migrazione ad Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
   >[!NOTE]
   >
   >È fondamentale seguire i passaggi di migrazione descritti nella sezione [Prerequisiti per la migrazione ad Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
1. Reintegrare le modifiche SQL.

In questo esempio, è stata creata una visualizzazione **NmcTrackingLogMessages** con un campo **Timestamp** denominato **tslog**. In questo caso, la procedura di migrazione non riesce e viene visualizzato il seguente messaggio di errore:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Per assicurarsi che il post aggiornamento funzioni, è necessario eliminare la visualizzazione prima della migrazione e ricrearla dopo la migrazione, adattandola alla modalità TIMESTAMP WITH TIMEZONE.

## Tracciamento {#tracking}

La formula di tracciamento è stata modificata. Durante la migrazione, la vecchia formula (v5) viene sostituita dalla nuova (v7). Se utilizzi una formula personalizzata in Adobe Campaign v5, questa configurazione deve essere adattata in Adobe Campaign v7 (**NmsTracking_ClickFormula** e **NmsTracking_OpenFormula** ).

È stata modificata anche la gestione del web tracking. Una volta effettuata la migrazione alla versione v7, devi avviare la procedura guidata di distribuzione per completare la configurazione del web tracking.

![](assets/migration_web_tracking.png)

Sono disponibili tre modalità:

* **Tracciamento** web della sessione: Se il  **[!UICONTROL Leads]** pacchetto non è stato installato, questa opzione è selezionata per impostazione predefinita. Questa opzione è la più ideale in termini di prestazioni e ti consente di limitare le dimensioni dei log di tracciamento.
* **Tracciamento Web permanente**
* **Tracciamento** Web anonimo: Se il  **[!UICONTROL Leads]** pacchetto è installato, questa opzione è selezionata per impostazione predefinita. È l’opzione che richiede più risorse. Come sopra, la colonna **sSourceId** deve essere indicizzata (nella tabella di tracciamento e nella tabella **CrmIncomingLead**).

>[!NOTE]
>
>Per ulteriori informazioni su queste tre modalità, consulta [questa sezione](../../configuration/using/about-web-tracking.md).

## Struttura ad albero Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante la migrazione, la struttura ad albero viene riorganizzata automaticamente in base agli standard v7. Le nuove cartelle vengono aggiunte, le cartelle obsolete vengono eliminate e il loro contenuto viene inserito nella cartella &quot;Per spostare&quot;. Tutti gli elementi in questa cartella devono essere controllati dopo la migrazione e il consulente deve decidere di mantenerli o eliminarli. Gli oggetti da conservare devono quindi essere spostati nel posto giusto.

È stata aggiunta un’opzione per disabilitare la migrazione automatica della struttura di navigazione. Questa operazione è ora manuale. Le cartelle obsolete non vengono eliminate e non vengono aggiunte nuove cartelle. Questa opzione deve essere utilizzata solo se la struttura di navigazione preconfigurata v5 è stata sottoposta a troppe modifiche. Aggiungi l’opzione alla console prima di eseguire la migrazione nel nodo **[!UICONTROL Administration > Options]** :

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

**Elenco delle cartelle** obsolete:

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
