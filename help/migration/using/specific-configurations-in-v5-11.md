---
title: Configurazioni specifiche nella versione v5.11
seo-title: Configurazioni specifiche nella versione v5.11
description: Configurazioni specifiche nella versione v5.11
seo-description: null
page-status-flag: never-activated
uuid: d6920beb-a766-4aec-8a8e-d32e47b545a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: fc280640-528d-44de-87d8-52f443772abd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 3%

---


# Configurazioni specifiche nella versione v5.11{#specific-configurations-in-v5-11}

In questa sezione viene descritta la configurazione aggiuntiva necessaria per la migrazione dalla versione 5.11. È inoltre necessario configurare le impostazioni dettagliate nella sezione Configurazioni [](../../migration/using/general-configurations.md) generali.

## Applicazioni web {#web-applications}

Durante la migrazione verrà visualizzato automaticamente il seguente avviso:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Alcuni componenti delle applicazioni Web, ad esempio i vari campi formula, hanno gli attributi @id. Questi vengono utilizzati nel codice XML delle applicazioni Web e non vengono più generati allo stesso modo. Non sono visibili nell&#39;interfaccia e normalmente non è necessario utilizzarli. Tuttavia, in alcuni casi, gli attributi @id possono essere stati utilizzati per personalizzare il rendering delle applicazioni Web, ad esempio tramite un foglio di stile o utilizzando codice JavaScript.

Durante la migrazione, è **necessario** controllare il percorso del file di registro specificato nell&#39;avviso:

* **Il file non è vuoto**: contiene avvisi che riguardano incoerenze registrate prima della migrazione e che ancora esistono. Può trattarsi di codice JavaScript in un&#39;applicazione Web che fa riferimento a un ID non esistente. Ogni errore deve essere controllato e corretto.
* **Il file è vuoto**: ciò significa che  Adobe Campaign non ha rilevato alcun problema.

A prescindere dal fatto che il file sia vuoto o meno, dovete verificare che questi ID non siano utilizzati per la configurazione altrove (e, in questo caso, adattare la configurazione).

## Flussi di lavoro {#workflows}

Poiché il nome della directory di installazione di Adobe Campaign  è cambiato, alcuni flussi di lavoro potrebbero non funzionare dopo la migrazione. Se un flusso di lavoro fa riferimento alla directory nl5 in una delle sue attività, si verificherà un errore. Sostituisci questo riferimento con **build**. È possibile eseguire una query SQL per identificare i flussi di lavoro seguenti (esempio PostgreSQL):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Facilità di utilizzo {#user-friendliness}

La home page  Adobe Campaign v5.11 non è più disponibile.

Sebbene non sia consigliato, esistono alcune soluzioni per mantenere interfacce specifiche da  Adobe Campaign v5.11. Per maggiori informazioni, contattateci.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL è supportato solo in v7 come motore di database principale quando si esegue la migrazione dalla versione 6.02 o 5.11 utilizzando questo motore.

MySQL non gestisce i timezones per impostazione predefinita. Per abilitare la gestione del fuso orario, eseguite il comando seguente:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Per ulteriori informazioni, consultate la pagina [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) .

Se sono state apportate modifiche alla struttura del database, durante la configurazione, ad esempio (creazione di indici specifici, creazione di viste SQL, ecc.), durante la migrazione devono essere prese alcune precauzioni. In effetti, alcune modifiche possono essere generate da incompatibilità con la procedura di migrazione. Ad esempio, la creazione di viste SQL contenenti campi **Timestamp** non è compatibile con l&#39;opzione **usetimestamptz** . Vi consigliamo pertanto di seguire le raccomandazioni seguenti:

1. Prima di avviare la migrazione, eseguire il backup del database.
1. Eliminare le modifiche SQL.
1. Eseguite l&#39;aggiornamento successivo in base alla procedura descritta nella sezione [Prerequisiti per la migrazione a  Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
   >[!NOTE]
   >
   >È fondamentale seguire i passaggi di migrazione descritti nella sezione [Prerequisiti per la migrazione a  Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
1. Reintegrare le modifiche SQL.

In questo esempio è stata creata una visualizzazione **NmcTrackingLogMessages** con un campo **Timestamp** denominato **tslog**. In questo caso, la procedura di migrazione non riesce e viene visualizzato il seguente messaggio di errore:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Per essere certi che il post-aggiornamento funzioni, è necessario eliminare la vista prima della migrazione e ricrearla dopo la migrazione, adattandola alla modalità TIMESTAMP WITH TIMEZONE.

## Tracking {#tracking}

La formula di tracciamento è stata modificata. Durante la migrazione, la vecchia formula (v5) viene sostituita dalla nuova (v7). Se utilizzate una formula personalizzata in  Adobe Campaign v5, questa configurazione deve essere adattata  Adobe Campaign v7 (opzioni **NmsTracking_ClickFormula** e **NmsTracking_OpenFormula** ).

È stata modificata anche la gestione del tracciamento Web. Una volta eseguita la migrazione alla versione v7, è necessario avviare la procedura guidata di distribuzione per completare la configurazione del tracciamento Web.

![](assets/migration_web_tracking.png)

Sono disponibili tre modalità:

* **Tracciamento** Web della sessione: Se il **[!UICONTROL Leads]** pacchetto non è stato installato, questa opzione è selezionata per impostazione predefinita. Questa opzione è la più ideale in termini di prestazioni e consente di limitare le dimensioni dei registri di tracciamento.
* **Tracciamento Web permanente**
* **Tracciamento** Web anonimo: Se il **[!UICONTROL Leads]** pacchetto è installato, questa opzione è selezionata per impostazione predefinita. È l&#39;opzione che richiede più risorse. Come sopra, la colonna **sSourceId** deve essere indicizzata (nella tabella di tracciamento e nella tabella **CrmIncomingLead** ).

>[!NOTE]
>
>Per ulteriori informazioni su queste tre modalità, consulta [questa sezione](../../configuration/using/about-web-tracking.md).

##  struttura ad albero Adobe Campaign v7 {#campaign-vseven-tree-structure}

Durante la migrazione, la struttura ad albero viene automaticamente riorganizzata in base agli standard v7. Le nuove cartelle vengono aggiunte, le cartelle obsolete vengono eliminate e il relativo contenuto viene inserito nella cartella &quot;Per spostare&quot;. Tutti gli elementi in questa cartella devono essere controllati dopo la migrazione, e il consulente deve decidere di tenerli o di eliminarli. Gli articoli da conservare devono essere spostati nel posto giusto.

È stata aggiunta un&#39;opzione per disattivare la migrazione automatica della struttura di navigazione. Questa operazione è ora manuale. Le cartelle obsolete non vengono eliminate e non vengono aggiunte nuove cartelle. Questa opzione deve essere utilizzata solo se la struttura di navigazione out-of-the-box v5 ha subito troppe modifiche. Aggiungere l’opzione alla console prima di eseguire la migrazione nel **[!UICONTROL Administration > Options]** nodo:

* Nome interno: NlMigration_KeepFolderStructure
* Tipo di dati: Integer
* Valore (testo): 3

Se utilizzate questa opzione, dopo la migrazione dovrete eliminare le cartelle obsolete, aggiungere le nuove cartelle ed eseguire tutti i controlli necessari.

**Elenco delle nuove cartelle**:

Dopo la migrazione è necessario aggiungere le seguenti cartelle:

| Nome interno | Etichetta | Condizione |
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
| nmsOperations | Campagne | Campagna installata |

**Elenco di cartelle** obsolete:

Le cartelle obsolete da eliminare dopo la migrazione sono le seguenti:

>[!NOTE]
>
>È necessario controllare l&#39;intero contenuto delle cartelle obsolete e per ogni elemento il consulente decide se conservarlo o eliminarlo. Gli elementi da conservare devono essere spostati nel luogo appropriato.

| Nome interno | Etichetta | Condizione |
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
| nmsAdminPlan | Amministrazione | Campagna installata |
| nmsResourcePlan | Resources | Campagna installata |
| nmsResourcesModels | Modelli | Campagna installata |
| nmsRootPlan | Gestione delle campagne | Campagna installata |
| nmsOperator | Operatori marketing | MRM installato |

