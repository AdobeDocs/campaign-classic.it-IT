---
title: Configurazioni generali
seo-title: Configurazioni generali
description: Configurazioni generali
seo-description: null
page-status-flag: never-activated
uuid: 317a145d-36b0-40fe-a272-ad5e35b0b190
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: f4b1c108-7f71-4aa1-8394-a7f660834c9c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2822'
ht-degree: 0%

---


# Configurazioni generali{#general-configurations}

Questa sezione descrive la configurazione da eseguire in  Adobe Campaign v7 se state eseguendo la migrazione da una v5.11 o una v6.02.

Inoltre:

* Se effettuate la migrazione dalla v5.11, dovete anche completare la configurazione dettagliata nelle configurazioni [Specifiche nella sezione v5.11](../../migration/using/specific-configurations-in-v5-11.md) .
* Se effettuate la migrazione dalla v6.02, dovete anche completare la configurazione dettagliata nelle configurazioni [Specifiche nella sezione v6.02](../../migration/using/specific-configurations-in-v6-02.md) .

## Fusi orari {#time-zones}

### Modalità fuso orario multiplo {#multi-time-zone-mode}

Nella release v6.02, la modalità &quot;fuso orario multiplo&quot; era disponibile solo per i motori di database PostSQL. Ora è disponibile indipendentemente dal tipo di motore di database utilizzato. Consigliamo vivamente di trasformare la base in una base &quot;multi-timezone&quot;.

Per utilizzare la modalità TIMESTAMP WITH TIMEZONE, è inoltre necessario aggiungere l&#39;opzione **-userTimestamptz:1** alla riga di comando postupgrade.

>[!IMPORTANT]
>
>Se il parametro **-usetimestamptz:1** viene utilizzato con un motore di database incompatibile, il database sarà danneggiato e sarà necessario ripristinare un backup del database ed eseguire nuovamente il comando precedente.

>[!NOTE]
>
>È possibile modificare il fuso orario dopo la migrazione tramite la console (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** nodo).
>
>Per ulteriori informazioni sulla gestione del fuso orario, consulta [questa sezione](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Se durante l&#39;aggiornamento successivo viene visualizzato un errore **ORA 01805** , i file del fuso orario Oracle tra il server dell&#39;applicazione e il server del database non sono sincronizzati. Per sincronizzarli nuovamente, effettuate le seguenti operazioni:

1. Per identificare il file del fuso orario utilizzato, eseguire il comando seguente:

   ```
   select * from v$timezone_file
   ```

   I file del fuso orario si trovano in genere nella cartella **ORACLE_HOME/oracore/zoneinfo/** .

1. Verificate che i file del fuso orario siano identici su entrambi i server.

Per maggiori informazioni, visita: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Un disallineamento del fuso orario tra client e server può anche causare dei ritardi. Per questo motivo, si consiglia di utilizzare la stessa versione di Oracle library sui lati client e server, entrambi i fusi orari devono essere identici.

Per verificare se entrambi i lati si trovano negli stessi fusi orari:

1. Controllare la versione del file del fuso orario sul lato client eseguendo il comando seguente:

   ```
   genezi -v
   ```

   genezi è un file binario trovato nella directory archivio **$ORACLE_HOME/bin** .

1. Controllare la versione del file del fuso orario sul lato server eseguendo il comando seguente:

   ```
   select * from v$timezone_file
   ```

1. Per modificare il file del fuso orario sul lato client, utilizzate la variabile di ambiente **ORA_TZFILE** .

## Sicurezza {#security}

### Zone di protezione {#security-zones}

>[!IMPORTANT]
>
>Per motivi di sicurezza, la piattaforma Adobe Campaign  non è più accessibile per impostazione predefinita: è necessario configurare le aree di protezione e quindi raccogliere gli indirizzi IP dell&#39;operatore.

 Adobe Campaign v7 prevede il concetto di zone **di** sicurezza. Ogni utente deve essere associato a una zona per accedere a un&#39;istanza e l&#39;indirizzo IP dell&#39;utente deve essere incluso negli indirizzi o negli intervalli di indirizzi definiti nella zona di protezione. È possibile configurare le aree di protezione nel file di configurazione  server Adobe Campaign. La zona di protezione a cui è associato un utente deve essere definita nella console (**[!UICONTROL Administration > Access management > Operators]**).

**Prima della migrazione**, chiedi all’amministratore di rete di aiutarti a definire le zone di sicurezza da attivare dopo la migrazione.

**Dopo l&#39;aggiornamento** successivo (prima del riavvio del server), è necessario configurare le aree di protezione.

La configurazione dell&#39;area di protezione è disponibile in [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones).

### Password utente {#user-passwords}

In v7, la connessione dell’operatore **interno** e **amministratore** deve essere protetta da una password. Si consiglia vivamente di assegnare password a questi account e a tutti gli account degli operatori, **prima della migrazione**. Se non avete specificato una password **interna**, non potrete connettervi. Per assegnare una password a **internal**, immettete il comando seguente:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La password **interna** deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consultare [questa sezione](../../installation/using/campaign-server-configuration.md#internal-identifier) e [questa sezione](../../platform/using/access-management.md#about-permissions).

### Nuove funzioni in v7 {#new-features-in-v7}

* Gli utenti senza autorizzazioni non possono più connettersi a  Adobe Campaign. Le autorizzazioni devono essere aggiunte manualmente, ad esempio creando un&#39;autorizzazione denominata **connect**.

   Gli utenti interessati da questa modifica vengono identificati ed elencati durante il post aggiornamento.

* Il tracciamento non funziona più se la password è vuota. In questo caso, un messaggio di errore vi consentirà di saperlo e vi chiederà di riconfigurarlo.
* Le password utente non sono più memorizzate nello schema **xtk:sessionInfo** .
* Le autorizzazioni di amministrazione sono ora necessarie per utilizzare le funzioni **xtk:builder:ValuteJavaScript** e **xtk:builder:ValuteJavaScriptTemplate** .

Alcuni schemi predefiniti sono stati modificati e ora sono accessibili solo per impostazione predefinita, con accesso in scrittura per gli operatori con l&#39;autorizzazione **amministratore** :

* ncm:pubblicare
* nl:monitoraggio
* nms:calendario
* xtk:builder
* xtk:connessioni
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusione
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:stringhe
* xtk:xslt

### Parametro sessionToken {#sessiontoken-parameter}

In v5, il parametro del token **di** sessione funzionava su entrambi i lati client (elenco di schermate del tipo di panoramica, editor di collegamenti, ecc.) e lato server (applicazioni Web, rapporti, jsp, jssp, ecc.). In v7, funziona solo sul lato server. Se desiderate tornare alla funzionalità completa come in v5, dovete modificare i collegamenti utilizzando questo parametro e passare tramite la pagina di connessione:

Esempio di collegamento:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Nuovo collegamento mediante la pagina di connessione:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Se utilizzate un operatore collegato a una maschera IP affidabile, verificate che disponga dei diritti minimi e che si trovi in una zona di sicurezza in modalità **sessionTokenOnly** .

### Funzioni SQL {#sql-functions}

Le chiamate di funzione SQL sconosciute non vengono più inviate naturalmente al server. Attualmente, tutte le funzioni SQL devono essere aggiunte allo schema **xtk:funcList** (per ulteriori informazioni, consultare [questa sezione](../../configuration/using/adding-additional-sql-functions.md)). Durante la migrazione, durante l&#39;aggiornamento successivo viene aggiunta un&#39;opzione che consente di mantenere la compatibilità con le vecchie funzioni SQL non dichiarate. Se si desidera continuare a utilizzare queste funzioni, verificare che l&#39;opzione **XtkPassUnknownSQLFunctionsToRDBMS** sia effettivamente definita a livello di **[!UICONTROL Administration > Platform > Options]** nodo.

>[!IMPORTANT]
>
>Raccomandiamo vivamente di non utilizzare questa opzione a causa dei rischi per la sicurezza che introduce.

### JSSP {#jssp}

Se desiderate autorizzare l&#39;accesso a determinate pagine tramite il protocollo HTTP (non HTTPS), ad esempio nelle app Web, indipendentemente dalla configurazione eseguita nelle aree di protezione, dovete specificare il parametro **httpAllowed=&quot;true&quot;** nella regola di inoltro corrispondente.

Se utilizzate JSSP anonimi, dovete aggiungere il parametro **httpAllowed=&quot;true&quot;** in una regola relay per il vostro JSSP (**[!UICONTROL serverConf.xml]** file):

Ad esempio:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blocklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Sintassi {#syntax}

### JavaScript {#javascript}

 Adobe Campaign v7 integra un interprete JavaScript più recente. Tuttavia, questo aggiornamento potrebbe causare il malfunzionamento di alcuni script. Poiché il motore precedente era più permissivo, alcune sintassi funzionerebbe, che non è più il caso con la nuova versione del motore.

La **[!UICONTROL myObject.@attribute]** sintassi ora è valida solo per gli oggetti XML. Questa sintassi può essere utilizzata per personalizzare le consegne e la gestione dei contenuti. Se avete utilizzato questo tipo di sintassi su un oggetto non XML, le funzioni di personalizzazione non funzioneranno più.

Per tutti gli altri tipi di oggetto, la sintassi è ora **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. Ad esempio, un oggetto non XML che utilizzava la sintassi seguente: **[!UICONTROL employee.@sn]**, deve ora usare la sintassi seguente: **[!UICONTROL employee`[`&quot;Sn&quot;`]`]**.

* Sintassi precedente:

   ```
   employee.@sn
   ```

* Nuova sintassi:

   ```
   employee["sn"]
   ```

Per modificare un valore in un oggetto XML, è ora necessario iniziare aggiornando il valore prima di aggiungere il nodo XML:

* Codice JavaScript precedente:

   ```
   var cellStyle = node.style.copy();
   this.styles.appendChild(cellStyle);
   cellStyle.@width = column.@width;
   ```

* Nuovo codice JavaScript:

   ```
   var cellStyle = node.style.copy();
   cellStyle.@width = column.@width;
   this.styles.appendChild(cellStyle);
   ```

Non è più possibile utilizzare un attributo XML come chiave di tabella.

* Sintassi precedente:

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* Nuova sintassi:

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

Per rafforzare la sicurezza dell’istanza, in  Adobe Campaign v7 è stata introdotta una nuova sintassi che sostituisce la sintassi basata su SQLData. Se utilizzate questi elementi di codice con questa sintassi, dovete modificarli. I principali elementi in questione sono:

* Filtraggio per sottoquery: la nuova sintassi si basa sull&#39; `<subQuery>` elemento per definire una sottoquery
* Aggregati: la nuova sintassi è &quot;funzione di aggregazione(raccolta)&quot;
* Filtraggio per join: la nuova sintassi è `[schemaName:alias:xPath]`

Lo schema queryDef (xtk:queryDef) è stato modificato:

* è disponibile un nuovo `<subQuery>` elemento per sostituire SELECT incluso in SQLData
* per l&#39;attributo @setOperator vengono introdotti due nuovi valori, &quot;IN&quot; e &quot;NOT IN&quot;
* un nuovo `<where>` elemento, secondario dell’ `<node>` elemento: questo consente di effettuare &quot;sottoselezioni&quot; in SELECT

Quando si utilizza un attributo &quot;@expr&quot;, è possibile che sia presente SQLData. È possibile eseguire una ricerca per i seguenti termini: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

 le istanze di Adobe Campaign v7 sono protette per impostazione predefinita. La sicurezza viene in termini di definizioni delle zone di protezione nel **[!UICONTROL serverConf.xml]** file: l&#39;attributo **allowSQLInjection** gestisce la protezione della sintassi SQL.

Se si verifica un errore SQLData durante l&#39;esecuzione post-aggiornamento, è necessario modificare questo attributo per consentire temporaneamente l&#39;utilizzo di sintassi basate su SQLData, consentendo di riscrivere il codice. Per eseguire questa operazione, è necessario modificare l&#39;opzione seguente nel file **serverConf.xml** :

```
allowSQLInjection="true"
```

Quindi, riavviate il postaggiornamento con il seguente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

È necessario configurare le aree di protezione (fare riferimento a [Protezione](#security)), quindi riattivare la protezione modificando l&#39;opzione:

```
allowSQLInjection="false"
```

Di seguito sono riportati alcuni esempi comparativi tra la vecchia e la nuova sintassi.

**Filtraggio per sottoquery**

* Sintassi precedente:

   ```
   <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
   ```

* Nuova sintassi:

   ```
   <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
     <subQuery schema="xtk:operatorGroup">
        <select>
          <node expr="[@operator-id]" />
        </select>
        <where>
          <condition expr="[@group-id]=$long(../@owner-id)"/>
        </where>
      </subQuery>
   </condition>
   ```

* Sintassi precedente:

   ```
   <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
       <where>
         <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

* Nuova sintassi:

   ```
   <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
       <where>
         <condition expr="@email" setOperator="IN" internalId="1">
           <subQuery schema="nms:recipient">
             <select><node expr="@email"/></select>
             <where><condition expr="[@folder-id]=$(folderId)"/></where>
             <groupBy><node expr="@email"/></groupBy>
             <having><condition expr="count(@email)>1"/></having>
           </subQuery>
         </condition>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

**L&#39;aggregato**

Aggregate, funzione (raccolta)

* Sintassi precedente:

   ```
   <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
   ```

* Nuova sintassi:

   ```
   <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
   ```

   >[!NOTE]
   >
   >I giunti vengono eseguiti automaticamente per le funzioni aggregate. Non è più necessario specificare la condizione WHERE O0.iOperationId=iOperationId.
   >
   >Non è più possibile utilizzare la funzione &quot;count(*)&quot;. È necessario utilizzare &quot;countall()&quot;.

* Sintassi precedente:

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* Nuova sintassi:

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**Filtri per giunzioni**

`[schemaName:alias:xPath]`

L&#39;alias è facoltativo

* Sintassi precedente:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* Nuova sintassi:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**Suggerimenti e trucchi**

In un `<subQuery>` elemento, per fare riferimento a un campo &quot;campo&quot; dell&#39; `<queryDef>` elemento principale, utilizzate la sintassi seguente: `[../@field]`

Esempio:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## Conflitti {#conflicts}

La migrazione viene eseguita tramite un post-aggiornamento e possono verificarsi conflitti in rapporti, moduli o applicazioni Web. Questi conflitti possono essere risolti dalla console.

Dopo la sincronizzazione delle risorse, il comando **postupgrade** consente di rilevare se la sincronizzazione genera errori o avvisi.

### Visualizzare il risultato della sincronizzazione {#view-the-synchronization-result}

Il risultato della sincronizzazione può essere visualizzato in due modi:

* Nell&#39;interfaccia della riga di comando, gli errori vengono generati da una tripla freccia **>>** e la sincronizzazione viene arrestata automaticamente. Le avvertenze vengono materializzate da una doppia freccia **>>** e devono essere risolte una volta completata la sincronizzazione. Alla fine del post aggiornamento, nel prompt dei comandi viene visualizzato un riepilogo. Ad esempio:

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se l&#39;avviso riguarda un conflitto di risorse, l&#39;operatore deve prestare attenzione a risolverlo.

* Il risultato della sincronizzazione è **postupgrade_`<server version number>`_time del file postupgrade`>`.log** . È disponibile per impostazione predefinita nella seguente directory: **directory di installazione/var/`<instance>`postupgrade**. Gli errori e gli avvisi sono indicati dagli attributi **error** e **warning** .

### Risoluzione di un conflitto {#resolve-a-conflict}

La risoluzione dei conflitti deve essere eseguita solo dagli operatori avanzati e da quelli ai quali sono stati concessi diritti di amministratore.

Per risolvere un conflitto, eseguire il seguente processo:

1. Nella struttura ad albero  Adobe Campaign, posizionare il cursore **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Selezionare il conflitto da risolvere nell&#39;elenco.

Esistono tre modi possibili per risolvere un conflitto:

* **[!UICONTROL Declared as resolved]**: richiede l&#39;intervento preventivo dell&#39;operatore.
* **[!UICONTROL Accept the new version]**: consigliato se le risorse fornite con  Adobe Campaign non sono state modificate dall&#39;utente.
* **[!UICONTROL Keep the current version]**: indica che l&#39;aggiornamento viene rifiutato.

   >[!IMPORTANT]
   Se si seleziona questa modalità di risoluzione, si rischia di perdere le patch nella nuova versione. Si raccomanda pertanto vivamente che tale opzione non sia utilizzata o riservata solo agli operatori esperti.

Se scegliete di risolvere manualmente il conflitto, procedete come segue:

1. Nella sezione inferiore della finestra, cercare le entità **`_conflict_ string`** con conflitti. L&#39;entità installata con la nuova versione contiene il **nuovo** argomento, l&#39;entità che corrisponde alla versione precedente contiene l&#39; **argomento cus** .

   ![](assets/s_ncs_production_conflict002.png)

1. Eliminate la versione che non desiderate mantenere. Eliminare l&#39;entità **`_conflict_argument_ string`** che si sta tenendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vai al conflitto che avresti risolto. Fate clic sull&#39; **[!UICONTROL Actions]** icona e selezionate **[!UICONTROL Declare as resolved]**.
1. Salvare le modifiche: il conflitto ora è risolto.

## Tomcat {#tomcat}

Il server Tomcat integrato in  Adobe Campaign v7 ha modificato la versione (Tomcat 7). Anche la sua cartella di installazione (tomcat-6) è cambiata (tomcat 7). Dopo l&#39;aggiornamento, accertatevi che i percorsi colleghino alla cartella aggiornata (nel **[!UICONTROL serverConf.xml]** file):

```
$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
```

## Interazione {#interaction}

### Prerequisiti {#prerequisites}

**Prima dell&#39;aggiornamento** successivo, è necessario eliminare tutti i riferimenti allo schema dalla versione 6.02 che non saranno più presenti nella versione v7.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Contenuto offerta {#offer-content}

In v7, il contenuto dell’offerta è stato spostato. In v6.02 il contenuto era in ogni schema di rappresentazione (**nms:emailOfferView**). In v7, il contenuto è ora nello schema delle offerte. Dopo l&#39;aggiornamento successivo, il contenuto non sarà quindi visibile nell&#39;interfaccia. Dopo l&#39;aggiornamento, è necessario ricreare il contenuto dell&#39;offerta o sviluppare uno script che sposta automaticamente il contenuto dallo schema di rappresentazione allo schema dell&#39;offerta.

>[!IMPORTANT]
Se alcune consegne che utilizzano offerte configurate devono essere inviate dopo la migrazione, dovete eliminare e ricreare tutte queste consegne in v7. In caso contrario, viene offerta una &quot;modalità di compatibilità&quot;. Questa modalità non è consigliata perché non si desidera utilizzare tutte le nuove funzioni di Interaction v7. Si tratta di una modalità transitoria che consente di completare le campagne in corso prima della migrazione effettiva alla versione 6.1. Per maggiori informazioni su questa modalità, contattateci.

Un esempio di script di movimento (**interactiveTo610_full_XX.js**) è disponibile nella cartella **Migrazione** all’interno della cartella  Adobe Campaign v7. Questo file mostra un esempio di script per un client che utilizza una singola rappresentazione e-mail per offerta (i **[!UICONTROL htmlSource]** campi e **[!UICONTROL textSource]** ). Il contenuto presente nella tabella **NmsEmailOfferView** è stato spostato nella tabella delle offerte.

>[!NOTE]
L&#39;utilizzo di questo script non consente di trarre vantaggio dalle opzioni &quot;content management&quot; e &quot;rendering delle funzioni&quot;. Per beneficiare di queste funzioni, è necessario ripensare le offerte del catalogo, in particolare i contenuti delle offerte e gli spazi di configurazione.

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### Test e configurazione {#tests-and-configuration}

Di seguito viene illustrata la procedura da seguire dopo aver spostato il contenuto dell&#39;offerta se disponete di un solo ambiente. In questo caso prendiamo ad esempio &quot;ENV&quot;.

1. In tutti gli spazi di ambiente &quot;ENV&quot;, aggiornate l&#39;elenco dei campi utilizzati. Ad esempio, per uno spazio di offerta che utilizza solo l’ **[!UICONTROL htmlSource]**, è necessario aggiungere l’ **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. Nel **[!UICONTROL Type of Environment]** campo all&#39;interno della **[!UICONTROL General]** scheda, selezionare **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Create un ambiente di progettazione (&quot;ENV_DESIGN&quot;, ad esempio) e collegatelo all’ambiente online ENV.

   ![](assets/migration_interaction_4.png)

1. Distribuire tutti gli spazi di offerta dell&#39;ambiente ENV (clic con il pulsante destro del mouse > **[!UICONTROL Actions > Deploy]**) e selezionare l&#39;ambiente &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Esegue le stesse operazioni per tutte le offerte di ambiente &quot;ENV&quot;.
1. Attiva tutte le offerte di ambiente &quot;ENV_DESIGN&quot; sui canali pertinenti.
1. Test per rendere disponibile un&#39;offerta. Se non si verificano problemi, eseguite le attività in sospeso nell’attività del flusso di lavoro più recente **[!UICONTROL Offer notification]** (offerMgt) per rendere attive tutte le offerte.

   ![](assets/migration_interaction_6.png)

1. Eseguire test completi.

   >[!NOTE]
   I nomi delle categorie e delle offerte online vengono modificati dopo essere andati in diretta. Sul canale in entrata, aggiornate tutti i riferimenti a offerte e categorie.

## Rapporti {#reports}

### Rapporti standard {#standard-reports}

Tutti i report standard attualmente utilizzano il motore di rendering v6.x. Se avevate aggiunto JavaScript in questi rapporti, alcuni elementi potrebbero non funzionare più. In effetti, la vecchia versione di JavaScript non è compatibile con il motore di rendering v6.x. È quindi necessario controllare il codice JavaScript e adattarlo in un secondo momento. È necessario verificare ogni rapporto, in particolare la funzione di esportazione.

### Rapporti personalizzati {#personalized-reports}

Se desiderate avere il banner blu dalla release v7 (che consenta di accedere agli universi), dovete ripubblicare i rapporti. In caso di problemi, potete forzare il motore di rendering v6.0. Per eseguire questa operazione, andate all&#39; **[!UICONTROL Properties]** interno del rapporto, fate clic su **[!UICONTROL Rendering]** e scegliete il motore di **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering.

![](assets/migration_reports_1.png)

Se desiderate beneficiare delle nuove funzionalità del rapporto, dovete selezionare il motore di rendering v.6.x. In questo caso, controllare tutti gli script e modificarli se necessario. Per quanto riguarda l&#39;esportazione PDF, se avevate aggiunto script specifici per OpenOffice, questo non funzionerà più con il nuovo motore di esportazione PDF (PhantomJS).

## Applicazioni web {#web-applications}

Esistono due famiglie di applicazioni Web:

* applicazioni web identificate (viste insieme, moduli di approvazione, sviluppi interni extranet),
* applicazioni Web anonime (moduli Web o per questionari).

### Applicazioni Web identificate {#identified-web-applications}

Come per i report (vedere [Rapporti](#reports)), se hai aggiunto JavaScript, devi controllare e adattare se necessario. Se desiderate usufruire del banner blu v7 (contenente gli universi), dovete ripubblicare l’applicazione Web. Se il codice JavaScript funziona correttamente, potete selezionare il motore di rendering v6.x. In caso contrario, potete utilizzare il motore di rendering v6.0 mentre adattate il codice, quindi utilizzare il motore di rendering v6.x.

>[!NOTE]
I passaggi per selezionare il motore di rendering sono gli stessi per la selezione dei report. Consultate Rapporti [](#personalized-reports)personalizzati.

I metodi di connessione dell’applicazione Web sono stati modificati in v7. Se si verificano problemi di connessione nelle applicazioni Web identificate, è necessario attivare temporaneamente le opzioni **allowUserPassword** e **sessionTokenOnly** nel file **serverConf.xml** . Dopo l’aggiornamento, modificate i seguenti valori di opzione:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Quindi, riavviate il postaggiornamento con il seguente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Verificate le applicazioni Web nel motore di rendering v6.x prima di pubblicarle. Quindi disattivate queste due opzioni.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Applicazioni Web anonime {#anonymous-web-applications}

In caso di problemi, ripubblicate l’applicazione Web. Se il problema persiste, potete selezionare il motore di rendering v6.0. Se non avete aggiunto JavaScript, potete selezionare il motore di rendering v6.x e trarre vantaggio dalle sue nuove funzioni.

>[!NOTE]
I passaggi per selezionare il motore di rendering sono gli stessi per la selezione dei report. Consultate Rapporti [](#personalized-reports)personalizzati.

## Cappello rosso {#red-hat}

Se gli schemi out-of-the-box sono stati eliminati in v6.02 o v5.11, dopo l’aggiornamento potrebbe non essere più possibile modificare gli schemi. In questo caso, eseguite il comando:

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
