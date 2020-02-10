---
title: Utilizzo dei pacchetti di dati
seo-title: Utilizzo dei pacchetti di dati
description: Utilizzo dei pacchetti di dati
seo-description: null
page-status-flag: never-activated
uuid: 867b2702-dbc4-4b71-a385-a2c7fd09d25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 42867665-d0ca-486e-9110-91716c0d5c57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Utilizzo dei pacchetti di dati{#working-with-data-packages}

## Informazioni sui pacchetti di dati {#about-data-packages}

Adobe Campaign consente di esportare o importare la configurazione della piattaforma e i dati attraverso un sistema di pacchetti. I pacchetti possono contenere diversi tipi di configurazioni, elementi, filtrati o meno.

I pacchetti di dati consentono la visualizzazione delle entità del database Adobe Campaign tramite file in formato XML. Ogni entità contenuta in un pacchetto è rappresentata da tutti i suoi dati.

Il principio dei pacchetti **di** dati è esportare una configurazione di dati e integrarla in un altro sistema Adobe Campaign. Per ulteriori informazioni su come mantenere un insieme coerente di pacchetti di dati, consulta questa [nota tecnica](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_How_to_maintain_a_consistent_set_of_data_packages.pdf).

### Tipi di pacchetti {#types-of-packages}

Esistono tre tipi di pacchetti esportabili: pacchetti utente, pacchetti di piattaforma e pacchetti di amministrazione.

* **Pacchetto** utente: consente di selezionare l&#39;elenco delle entità da esportare. Questo tipo di pacchetto gestisce le dipendenze e verifica gli errori.
* **Pacchetto** piattaforma: include tutte le risorse tecniche aggiunte (non standard): schemi, codice JavaScript, ecc.

   ![](assets/ncs_datapackage_package_platform.png)

* **Pacchetto** amministratore: include tutti i modelli e gli oggetti business aggiunti (non standard): modelli, librerie ecc.

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>I tipi di **piattaforma** e **amministratore** contengono un elenco predefinito di entità da esportare. Ogni entità è collegata a condizioni di filtraggio che consentono di rimuovere le risorse pronte all&#39;uso del pacchetto creato.

## Struttura dei dati {#data-structure}

La descrizione di un pacchetto di dati è un documento XML strutturato conforme alla grammatica dello schema di dati **xrk:navtree** .

Esempio di pacchetto dati:

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

Il documento XML deve iniziare e terminare con l&#39; **`<package>`** elemento . Tutti **`<entities>`** gli elementi successivi distribuiscono i dati per tipo di documento.

Un **`<entities>`** elemento contiene i dati del pacchetto nel formato dello schema dati immesso nell&#39;attributo **schema** .

I dati contenuti in un pacchetto non devono contenere chiavi interne non compatibili tra le basi, come chiavi generate automaticamente (opzione **autopk** ).

Nel nostro esempio, i join sui collegamenti &quot;cartella&quot; e &quot;società&quot; sono stati sostituiti dai cosiddetti tasti &quot;di alto livello&quot; sulle tabelle di destinazione:

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

L&#39; **`operation`** attributo con il valore &quot;none&quot; definisce un collegamento di riconciliazione.

Un pacchetto di dati può essere costruito manualmente da qualsiasi editor di testo. È sufficiente assicurarsi che la struttura del documento XML sia conforme allo schema di dati &quot;xtk:navtree&quot;. La console di Adobe Campaign dispone di un modulo di esportazione e importazione di pacchetti di dati.

## Esportazione di pacchetti {#exporting-packages}

### Informazioni sull&#39;esportazione dei pacchetti {#about-package-export}

I pacchetti possono essere esportati in tre modi diversi:

* Consente di **[!UICONTROL Package Export Wizard]** esportare un set di oggetti in un singolo pacchetto. Per ulteriori informazioni, consultate [Esportazione di un set di oggetti in un pacchetto](#exporting-a-set-of-objects-in-a-package)
* Un **singolo oggetto** può essere esportato direttamente in un pacchetto facendo clic con il pulsante destro del mouse su di esso e selezionando **[!UICONTROL Actions > Export in a package]**.
* **Le definizioni** dei pacchetti consentono di creare una struttura di pacchetti in cui aggiungere gli oggetti che verranno esportati in un secondo momento in un pacchetto. Per ulteriori informazioni, consultate [Gestione delle definizioni dei pacchetti](#managing-package-definitions)

Una volta esportato un pacchetto, potrete importarlo e tutte le entità aggiunte in un&#39;altra istanza di Campaign.

### Esportazione di un set di oggetti in un pacchetto {#exporting-a-set-of-objects-in-a-package}

La procedura guidata di esportazione del pacchetto è accessibile dal **[!UICONTROL Tools > Advanced > Export package...]** menu della console client Adobe Campaign.

![](assets/ncs_datapackage_typepackage.png)

Per i tre tipi di pacchetti, la procedura guidata offre i seguenti passaggi:

1. Elenca le entità da esportare per tipo di documento:

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >Se esportate una cartella **[!UICONTROL Offer category]**, **[!UICONTROL Offer environment]** o **[!UICONTROL Program]** digitate, non selezionate mai la cartella **[!UICONTROL Plan]** xtk:folder **** in quanto potreste perdere alcuni dati. Selezionate l&#39;entità che corrisponde alla cartella: **nms:offerCategory** per le categorie di offerte, **nms:offerEnv** per gli ambienti di offerte, **nms:program** e **nms:plan** per i piani.

   Gestione elenchi consente di aggiungere o eliminare entità per l&#39;esportazione dalla configurazione. Fate clic **[!UICONTROL Add]** per selezionare una nuova entità.

   Il **[!UICONTROL Detail]** pulsante modifica la configurazione selezionata.

   >[!NOTE]
   >
   >Il meccanismo di dipendenza controlla la sequenza di esportazione delle entità. Per ulteriori informazioni, vedere [Gestione delle dipendenze](#managing-dependencies).

1. La schermata di configurazione dell&#39;entità definisce la query del filtro sul tipo di documento da estrarre.

   È necessario configurare la clausola di filtraggio per l&#39;estrazione dei dati.

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >L&#39;editor di query viene presentato in [questa sezione](../../platform/using/about-queries-in-campaign.md).

1. Fare clic **[!UICONTROL Next]** e selezionare le colonne di ordinamento per ordinare i dati durante l&#39;estrazione:

   ![](assets/ncs_datapackage_export5.png)

1. Visualizzare l&#39;anteprima dei dati da estrarre prima di eseguire l&#39;esportazione.

   ![](assets/ncs_datapackage_export6.png)

1. L’ultima pagina della procedura guidata di esportazione del pacchetto consente di avviare l’esportazione. I dati saranno memorizzati nel file indicato nel **[!UICONTROL File]** campo.

   ![](assets/ncs_datapackage_export7.png)

### Gestione delle dipendenze {#managing-dependencies}

Il meccanismo di esportazione consente ad Adobe Campaign di tenere traccia dei collegamenti tra i vari elementi esportati.

Tale meccanismo è definito da due regole:

* gli oggetti collegati a un collegamento con un&#39;integrità **propria** o di tipo **proprietario** vengono esportati nello stesso pacchetto dell&#39;oggetto esportato.
* gli oggetti collegati a un collegamento con un collegamento **neutro** o **definire** l&#39;integrità del tipo (collegamento definito) devono essere esportati separatamente.

>[!NOTE]
>
>I tipi di integrità collegati agli elementi dello schema sono definiti in [questa sezione](../../configuration/using/database-mapping.md#links--relation-between-tables).

#### Esportazione di una campagna {#exporting-a-campaign}

Di seguito è riportato un esempio di come esportare una campagna. La campagna marketing da esportare contiene un&#39;attività (etichetta: &quot;MyTask&quot;) e un flusso di lavoro (etichetta: &quot;CampaignWorkflow&quot;) in una cartella &quot;MyWorkflow&quot; (nodo: Amministrazione/Produzione/Flussi di lavoro tecnici/Processi campagna/MyWorkflow).

L’attività e il flusso di lavoro vengono esportati nello stesso pacchetto della campagna, poiché gli schemi corrispondenti sono collegati da collegamenti con un’integrità del tipo &quot;propria&quot;.

Contenuto pacchetto:

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

L&#39;affiliazione a un tipo di pacchetto è definita in uno schema con l&#39;attributo **@pkgAdmin e @pkgPlatform** . Entrambi questi attributi ricevono un&#39;espressione XTK che definisce le condizioni di affiliazione al pacchetto.

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

Infine, l&#39;attributo **@pkgStatus** consente di definire le regole di esportazione per questi elementi o attributi. A seconda del valore dell’attributo, l’elemento o l’attributo si trova nel pacchetto esportato. I tre valori possibili per questo attributo sono:

* **never**: non esporta il campo o il collegamento
* **always**: forza l&#39;esportazione per questo campo
* **preCreate**: autorizza la creazione dell&#39;entità collegata

>[!NOTE]
>
>Il valore **preCreate** è ammesso solo per gli eventi dei tipi di collegamento. Consente di creare o indirizzare un&#39;entità non ancora caricata nel pacchetto esportato.

## Gestione delle definizioni dei pacchetti {#managing-package-definitions}

### Informazioni sulle definizioni dei pacchetti {#about-package-definitions}

Le definizioni dei pacchetti consentono di creare una struttura di pacchetti in cui aggiungere entità che verranno esportate in un secondo momento in un singolo pacchetto. Potrete quindi importare il pacchetto e tutte le entità aggiunte in un&#39;altra istanza di Campaign.

**Argomenti correlati:**

* [Creazione di una definizione di pacchetto](#creating-a-package-definition)
* [Aggiunta di entità a una definizione di pacchetto](#adding-entities-to-a-package-definition)
* [Configurazione della generazione delle definizioni dei pacchetti](#configuring-package-definitions-generation)
* [Esportazione di pacchetti da una definizione di pacchetto](#exporting-packages-from-a-package-definition)

### Creazione di una definizione di pacchetto {#creating-a-package-definition}

Le definizioni dei pacchetti sono accessibili dal **[!UICONTROL Administration > Configuration > Package management > Package definitions]** menu.

Per creare una definizione di pacchetto, fate clic sul **[!UICONTROL New]** pulsante, quindi compilate le informazioni generali sulla definizione del pacchetto.

![](assets/packagedefinition_create.png)

Potete quindi aggiungere entità alla definizione del pacchetto ed esportarla in un pacchetto di file XML.

**Argomenti correlati:**

* [Aggiunta di entità a una definizione di pacchetto](#adding-entities-to-a-package-definition)
* [Configurazione della generazione delle definizioni dei pacchetti](#configuring-package-definitions-generation)
* [Esportazione di pacchetti da una definizione di pacchetto](#exporting-packages-from-a-package-definition)

### Aggiunta di entità a una definizione di pacchetto {#adding-entities-to-a-package-definition}

Nella **[!UICONTROL Content]** scheda, fate clic sul **[!UICONTROL Add]** pulsante per selezionare le entità da esportare con il pacchetto. Le procedure ottimali per la selezione delle entità sono illustrate nella sezione [Esportazione di un set di oggetti in una sezione di pacchetto](#exporting-a-set-of-objects-in-a-package) .

![](assets/packagedefinition_addentities.png)

Le entità possono essere aggiunte a una definizione di pacchetto direttamente dalla loro posizione nell&#39;istanza. A questo scopo, effettuate le seguenti operazioni:

1. Fare clic con il pulsante destro del mouse sull&#39;entità desiderata, quindi selezionare **[!UICONTROL Actions > Export in a package]**.

   ![](assets/packagedefinition_singleentity.png)

1. Selezionate **[!UICONTROL Add to a package definition]**, quindi selezionate la definizione del pacchetto a cui desiderate aggiungere l&#39;entità.

   ![](assets/packagedefinition_packageselection.png)

1. L&#39;entità viene aggiunta alla definizione del pacchetto, verrà esportata con il pacchetto (consultate [Esportazione di pacchetti da una definizione](#exporting-packages-from-a-package-definition)di pacchetto).

   ![](assets/packagedefinition_entityadded.png)

### Configurazione della generazione delle definizioni dei pacchetti {#configuring-package-definitions-generation}

La generazione del pacchetto può essere configurata dalla **[!UICONTROL Content]** scheda di definizione del pacchetto. A tale scopo, fare clic sul **[!UICONTROL Generation parameters]** collegamento.

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**: include la definizione attualmente utilizzata nella definizione del pacchetto.
* **[!UICONTROL Include an installation script]**: consente di aggiungere uno script javascript da eseguire durante l&#39;importazione del pacchetto. Quando è selezionata questa opzione, nella schermata di definizione del pacchetto viene aggiunta una **[!UICONTROL Script]** scheda.
* **[!UICONTROL Include default values]**: aggiunge al pacchetto i valori di tutti gli attributi delle entità.

   Questa opzione non è selezionata per impostazione predefinita, per evitare esportazioni troppo lunghe. Ciò significa che gli attributi delle entità con valori predefiniti (&#39;stringa vuota&#39;, &#39;0&#39; e &#39;false&#39; se non altrimenti definiti nello schema) non saranno aggiunti al pacchetto e quindi non saranno esportati.

   >[!CAUTION]
   >
   >Se si deseleziona questa opzione, è possibile che vengano unite le versioni locali e importate.
   >
   >Se l&#39;istanza in cui viene importato il pacchetto contiene entità identiche a quelle del pacchetto (ad esempio con lo stesso ID esterno), i loro attributi non saranno aggiornati. Ciò può verificarsi se gli attributi della precedente istanza hanno valori predefiniti, in quanto non sono inclusi nel pacchetto.
   >
   >In tal caso, la selezione dell&#39; **[!UICONTROL Include default values]** opzione impedirebbe l&#39;unione delle versioni, poiché tutti gli attributi dell&#39;istanza precedente venivano esportati con il pacchetto.

### Esportazione di pacchetti da una definizione di pacchetto {#exporting-packages-from-a-package-definition}

Per esportare un pacchetto dalla definizione di un pacchetto, effettuate le seguenti operazioni:

1. Selezionate la definizione del pacchetto da esportare, quindi fate clic sul **[!UICONTROL Actions]** pulsante e selezionate **[!UICONTROL Export the package]**.
1. Per impostazione predefinita viene selezionato un file XML corrispondente al pacchetto esportato. Viene denominato in base allo spazio dei nomi e al nome della definizione del pacchetto.
1. Una volta definiti il nome e la posizione del pacchetto, fate clic sul **[!UICONTROL Start]** pulsante per avviare l&#39;esportazione.

   ![](assets/packagedefinition_packageexport.png)

## Importazione di pacchetti {#importing-packages}

### Informazioni sull&#39;importazione di pacchetti {#about-package-import}

La procedura guidata di importazione dei pacchetti è accessibile dal menu principale **[!UICONTROL Tools > Advanced > Package import...]** della console client Adobe Campaign.

Puoi importare un pacchetto da un&#39;esportazione eseguita in precedenza, ad esempio da un&#39;altra istanza di Adobe Campaign, o da un pacchetto standard, a seconda dei termini della licenza.

![](assets/ncs_datapackage_import.png)

### Installazione di un pacchetto da un file {#installing-a-package-from-a-file}

Per importare un pacchetto di dati esistente, selezionate il file XML e fate clic su **[!UICONTROL Open]**.

![](assets/ncs_datapackage_import_1.png)

Il contenuto del pacchetto da importare viene visualizzato nella sezione centrale dell&#39;editor.

Fate clic su **[!UICONTROL Next]** e **[!UICONTROL Start]** per avviare l&#39;importazione.

![](assets/ncs_datapackage_import_2.png)

### Installazione di un pacchetto standard {#installing-a-standard-package}

I pacchetti standard vengono installati quando Adobe Campaign è configurato. A seconda delle autorizzazioni e del modello di distribuzione, potete importare nuovi pacchetti standard se acquisite nuove opzioni o componenti aggiuntivi o se effettuate l’aggiornamento a una nuova offerta.

Fate riferimento al contratto di licenza per verificare quali pacchetti è possibile installare.

Per ulteriori informazioni sui pacchetti standard, consultate [questa pagina](../../installation/using/installing-campaign-standard-packages.md).
