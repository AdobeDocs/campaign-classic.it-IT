---
product: campaign
title: Configurazioni generali
description: Configurazioni generali
audience: migration
content-type: reference
topic-tags: configuration
hide: true
hidefromtoc: true
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '2625'
ht-degree: 0%

---

# Configurazioni generali{#general-configurations}

![](../../assets/v7-only.svg)

Questa sezione descrive la configurazione da eseguire in Adobe Campaign v7 durante la migrazione da a v5.11 o a v6.02.

Inoltre:

* Se effettui la migrazione dalla versione v5.11, devi anche completare la configurazione dettagliata in [questa sezione](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* Se effettui la migrazione dalla versione v6.02, devi anche completare la configurazione dettagliata in [questa sezione](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## Fusi orari {#time-zones}

### Modalità a più fusi orari {#multi-time-zone-mode}

Nella versione 6.02, la modalità &quot;fuso orario multiplo&quot; era disponibile solo per i motori di database PostgreSQL. Ora viene offerto indipendentemente dal tipo di motore di database utilizzato. Ti consigliamo vivamente di trasformare la tua base in una base &quot;multi-fuso orario&quot;.

Per utilizzare la modalità TIMESTAMP WITH TIMEZONE, è necessario aggiungere anche la **-userTimestamptz:1** alla riga di comando post aggiornamento.

>[!IMPORTANT]
>
>Se la **-usetimestamptz:1** Il parametro viene utilizzato con un motore di database incompatibile, il database sarà danneggiato e sarà necessario ripristinare un backup del database ed eseguire nuovamente il comando precedente.

>[!NOTE]
>
>È possibile modificare il fuso orario dopo la migrazione tramite la console (**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** node).
>
>Per ulteriori informazioni sulla gestione del fuso orario, consulta [questa sezione](../../installation/using/time-zone-management.md).

###  Oracle {#oracle}

Se ottieni un **ORA 01805** errore durante l&#39;aggiornamento successivo, ciò significa che i file del fuso orario Oracle tra l&#39;application server e il database server non sono sincronizzati. Per sincronizzarli nuovamente, esegui i seguenti passaggi:

1. Per identificare il file del fuso orario utilizzato, esegui il comando seguente:

   ```
   select * from v$timezone_file
   ```

   I file del fuso orario si trovano in genere nel **ORACLE_HOME/oracore/zoneinfo/** cartella.

1. Assicurati che i file del fuso orario siano identici su entrambi i server.

Per ulteriori informazioni, visita: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Un disallineamento del fuso orario tra client e server può anche causare alcuni ritardi. È pertanto consigliabile utilizzare la stessa versione della libreria Oracle sul lato client e server, entrambi i fusi orari devono essere uguali.

Per verificare se entrambe le parti si trovano negli stessi fusi orari:

1. Controllare la versione del file del fuso orario sul lato client eseguendo il seguente comando:

   ```
   genezi -v
   ```

   genezi è un binario trovato in **$ORACLE_HOME/bin** archivio.

1. Controllare la versione del file del fuso orario sul lato server eseguendo il seguente comando:

   ```
   select * from v$timezone_file
   ```

1. Per modificare il file del fuso orario sul lato client, utilizza il **ORA_TZFILE** variabile di ambiente.

## Sicurezza {#security}

### Zone di sicurezza {#security-zones}

>[!IMPORTANT]
>
>Per motivi di sicurezza, la piattaforma Adobe Campaign non è più accessibile per impostazione predefinita: devi configurare le aree di protezione e quindi raccogliere gli indirizzi IP dell’operatore.

Adobe Campaign v7 prevede il concetto di **zone di sicurezza**. Per accedere a un&#39;istanza, ogni utente deve essere associato a una zona e l&#39;indirizzo IP dell&#39;utente deve essere incluso negli indirizzi o negli intervalli di indirizzi definiti nella zona di sicurezza. È possibile configurare le aree di protezione nel file di configurazione del server Adobe Campaign. La zona di sicurezza a cui è associato un utente deve essere definita nella console (**[!UICONTROL Administration > Access management > Operators]**).

**Prima della migrazione**, chiedi all’amministratore di rete di aiutarti a definire le aree di sicurezza da attivare dopo la migrazione.

**Dopo l&#39;aggiornamento** (prima del riavvio del server), è necessario configurare le aree di protezione.

La configurazione dell&#39;area di sicurezza si trova in [questa sezione](../../installation/using/security-zones.md).

### Password utente {#user-passwords}

Nella versione v7, **interno** e **admin** la connessione dell&#39;operatore deve essere protetta da una password. Si consiglia vivamente di assegnare password a questi account e a tutti gli account dell&#39;operatore, **prima della migrazione**. Se non hai specificato una password per **interno**, non sarà possibile connettersi. Per assegnare una password a **interno**, immetti il comando seguente:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>La **interno** La password deve essere identica per tutti i server di tracciamento. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier) e [questa sezione](../../platform/using/access-management.md).

### Nuove funzioni in v7 {#new-features-in-v7}

* Gli utenti senza autorizzazioni non possono più connettersi ad Adobe Campaign. Le loro autorizzazioni devono essere aggiunte manualmente, ad esempio creando un’autorizzazione denominata **connect**.

   Gli utenti interessati da questa modifica vengono identificati ed elencati durante il post aggiornamento.

* Il tracciamento non funziona più se la password è vuota. In questo caso, ti verrà visualizzato un messaggio di errore che ti informa e ti chiederà di riconfigurarlo.
* Le password utente non vengono più memorizzate nel **xtk:sessionInfo** schema.
* Le autorizzazioni di amministrazione sono ora necessarie per utilizzare il **xtk:builder:ValutaJavaScript** e **xtk:builder:ValutaModelloJavaScript** funzioni.

Alcuni schemi predefiniti sono stati modificati e ora sono accessibili per impostazione predefinita solo con accesso in scrittura per gli operatori con il **admin** autorizzazione:

* ncm:pubblicazione
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

### Parametro Sessiontoken {#sessiontoken-parameter}

Nella versione v5, il **sessiontoken** Il parametro funzionava su entrambi i lati del client (elenco delle schermate del tipo di panoramica, editor collegamenti, ecc.) e lato server (applicazioni web, report, jsp, jssp, ecc.). In v7, funziona solo sul lato server. Se desideri tornare alla funzionalità completa come in v5, devi modificare i collegamenti utilizzando questo parametro e passare tramite la pagina di connessione:

Esempio di collegamento:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Nuovo collegamento tramite la pagina di connessione:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Se utilizzi un operatore collegato a una maschera IP attendibile, verifica che disponga dei diritti minimi e che si trovi in una zona di sicurezza in **sessionTokenOnly** modalità.

### Funzioni SQL {#sql-functions}

Le chiamate alla funzione SQL sconosciute non vengono più inviate naturalmente al server. Attualmente, tutte le funzioni SQL devono essere aggiunte al **xtk:funcList** schema (per ulteriori informazioni, consulta [questa sezione](../../configuration/using/adding-additional-sql-functions.md)). Durante la migrazione, durante l&#39;aggiornamento successivo viene aggiunta un&#39;opzione che consente di mantenere la compatibilità con le vecchie funzioni SQL non dichiarate. Se desideri continuare a utilizzare queste funzioni, controlla che la **XtkPassUnknownSQLFunctionsToRDBMS** l&#39;opzione è effettivamente definita nella **[!UICONTROL Administration > Platform > Options]** a livello di nodo.

>[!IMPORTANT]
>
>Sconsigliamo vivamente di non utilizzare questa opzione a causa dei rischi per la sicurezza che introduce.

### JSSP {#jssp}

Se si desidera autorizzare l&#39;accesso a determinate pagine tramite il protocollo HTTP (non HTTPS), ad esempio nelle app Web, indipendentemente dalla configurazione eseguita nelle aree di protezione, è necessario specificare il **httpAllowed=&quot;true&quot;** nella regola relay corrispondente.

Se utilizzi JSSP anonimi, devi aggiungere la **httpAllowed=&quot;true&quot;** in una regola relè per il tuo JSSP (**[!UICONTROL serverConf.xml]** file):

Ad esempio:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Sintassi {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7 integra un interprete JavaScript più recente. Tuttavia, questo aggiornamento può causare il malfunzionamento di alcuni script. Poiché il motore precedente era più permissivo, alcune sintassi funzionerebbero, il che non è più il caso con la nuova versione del motore.

La **[!UICONTROL myObject.@attribute]** la sintassi è ora valida solo per gli oggetti XML. Questa sintassi può essere utilizzata per personalizzare le consegne e la gestione dei contenuti. Se hai utilizzato questo tipo di sintassi su un oggetto non XML, le funzioni di personalizzazione non funzioneranno più.

Per tutti gli altri tipi di oggetti, la sintassi è ora **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. Ad esempio, un oggetto non XML che utilizza la sintassi seguente: **[!UICONTROL employee.@sn]**, ora deve utilizzare la sintassi seguente: **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* Sintassi precedente:

   ```
   employee.@sn
   ```

* Nuova sintassi:

   ```
   employee["sn"]
   ```

Per modificare un valore in un oggetto XML, è necessario iniziare aggiornando il valore prima di aggiungere il nodo XML:

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

Per rafforzare la sicurezza dell’istanza, in Adobe Campaign v7 è stata introdotta una nuova sintassi per sostituire la sintassi basata su SQLData. Se utilizzi questi elementi di codice con questa sintassi, devi modificarli. I principali elementi in questione sono i seguenti:

* Filtraggio per sottoquery: la nuova sintassi si basa sul `<subQuery>`  per definire una sottoquery
* Aggregati: la nuova sintassi è &quot;aggregate function(collection)&quot;
* Filtraggio per join: la nuova sintassi è `[schemaName:alias:xPath]`

Lo schema queryDef (xtk:queryDef) è stato modificato:

* nuovo `<subQuery>`  è disponibile per sostituire SELECT incluso in SQLData
* per l&#39;attributo @setOperator vengono introdotti due nuovi valori, &quot;IN&quot; e &quot;NOT IN&quot;
* nuovo `<where>`  che è un elemento secondario di `<node>` elemento: questo consente di effettuare &quot;selezioni secondarie&quot; in SELECT

Quando si utilizza un attributo &quot;@expr&quot;, è possibile che SQLData sia presente. È possibile eseguire una ricerca per i seguenti termini: &quot;SQLData&quot;, &quot;aliasSqlTable&quot;, &quot;sql&quot;.

Le istanze Adobe Campaign v7 sono protette per impostazione predefinita. La sicurezza viene fornita in termini di definizioni delle zone di sicurezza **[!UICONTROL serverConf.xml]** file: la **allowSQLInjection** l&#39;attributo gestisce la protezione della sintassi SQL.

Se si verifica un errore SQLData durante l&#39;esecuzione del post aggiornamento, è necessario modificare questo attributo per consentire temporaneamente l&#39;utilizzo di sintassi basate su SQLData, consentendo di riscrivere il codice. Per eseguire questa operazione, è necessario modificare l’opzione seguente nel **serverConf.xml** file:

```
allowSQLInjection="true"
```

Pertanto, riavvia il post aggiornamento con il seguente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

È necessario configurare le aree di protezione (consulta [Sicurezza](#security)), quindi riattiva la protezione modificando l&#39;opzione :

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

Funzione di aggregazione (raccolta)

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
   >I giunti vengono eseguiti automaticamente per le funzioni di aggregazione. Non è più necessario specificare la condizione WHERE O0.iOperationId=iOperationId.
   >
   >Non è più possibile utilizzare &quot;count(&#42;)&quot;. È necessario utilizzare &quot;counheight()&quot;.

* Sintassi precedente:

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* Nuova sintassi:

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**Filtri per join**

`[schemaName:alias:xPath]`

L’alias è facoltativo

* Sintassi precedente:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* Nuova sintassi:

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**Suggerimenti**

In una `<subQuery>` per fare riferimento a un campo &quot;field&quot; del `<queryDef>`   utilizza la sintassi seguente: `[../@field]`

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

La migrazione viene eseguita tramite un aggiornamento successivo e possono comparire conflitti in rapporti, moduli o applicazioni web. Questi conflitti possono essere risolti dalla console.

Dopo la sincronizzazione della risorsa, la **postupgrade** consente di rilevare se la sincronizzazione genera errori o avvisi.

### Visualizza il risultato della sincronizzazione {#view-the-synchronization-result}

Il risultato della sincronizzazione può essere visualizzato in due modi:

* Nell&#39;interfaccia della riga di comando, gli errori vengono materializzati da una tripla freccia **>>** e la sincronizzazione viene interrotta automaticamente. Le avvertenze sono materializzate da una doppia freccia **>>** e deve essere risolto una volta completata la sincronizzazione. Al termine del post aggiornamento, nel prompt dei comandi viene visualizzato un riepilogo. Ad esempio:

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Se l&#39;avviso riguarda un conflitto di risorse, è necessario prestare attenzione all&#39;operatore per risolverlo.

* La **postupgrade_`<server version number>`_ora del post aggiornamento`>`.log** il file contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **directory di installazione/var/`<instance>`postupgrade**. Gli errori e le avvertenze sono indicati dal **errore** e **avviso** attributi.

### Risolvere un conflitto {#resolve-a-conflict}

La risoluzione dei conflitti deve essere eseguita solo dagli operatori avanzati e da quelli ai quali sono stati concessi i diritti di amministratore.

Per risolvere un conflitto, applicare il seguente processo:

1. Nella struttura ad albero di Adobe Campaign, posiziona il cursore sopra **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. Selezionare il conflitto da risolvere nell&#39;elenco.

Esistono tre modi possibili per risolvere un conflitto:

* **[!UICONTROL Declared as resolved]**: richiede prima l&#39;intervento dell&#39;operatore.
* **[!UICONTROL Accept the new version]**: consigliato se l’utente non ha modificato le risorse fornite con Adobe Campaign.
* **[!UICONTROL Keep the current version]**: significa che l&#39;aggiornamento viene rifiutato.

   >[!IMPORTANT]
   >
   >Se si seleziona questa modalità di risoluzione, si rischia di perdere le patch nella nuova versione. Si raccomanda pertanto vivamente che questa opzione non sia utilizzata o riservata solo agli operatori esperti.

Se si sceglie di risolvere manualmente il conflitto, procedere come segue:

1. Nella sezione inferiore della finestra, cerca il **`_conflict_ string`** per individuare le entità con conflitti. L&#39;entità installata con la nuova versione contiene il **nuovo** l&#39;entità che corrisponde alla versione precedente contiene l&#39; **muco** argomento.

   ![](assets/s_ncs_production_conflict002.png)

1. Elimina la versione che non desideri mantenere. Elimina **`_conflict_argument_ string`** dell&#39;entità che si sta tenendo.

   ![](assets/s_ncs_production_conflict003.png)

1. Vai al conflitto che avresti risolto. Fai clic sul pulsante **[!UICONTROL Actions]** e seleziona **[!UICONTROL Declare as resolved]**.
1. Salva le modifiche: il conflitto è ora risolto.

## Tomcat {#tomcat}

Il server Tomcat integrato in Adobe Campaign v7 è stato modificato. Anche la sua cartella di installazione (tomcat-6) è quindi cambiata (tomcat 7). Dopo l’aggiornamento, assicurati di verificare che i percorsi si colleghino alla cartella aggiornata (nel **[!UICONTROL serverConf.xml]** file):

```
$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
```

## Interazione {#interaction}

### Prerequisiti {#prerequisites}

**Prima dell’aggiornamento successivo**, devi eliminare tutti i riferimenti di schema dalla versione 6.02 che non esisteranno più nella versione 7.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Contenuto dell’offerta {#offer-content}

In v7, il contenuto dell’offerta è stato spostato. Nella versione 6.02 il contenuto era in ogni schema di rappresentazione (**nms:emailOfferView**). In v7, il contenuto è ora nello schema delle offerte. Dopo l’aggiornamento, il contenuto non sarà quindi visibile nell’interfaccia di . Dopo l’aggiornamento, devi ricreare il contenuto dell’offerta o sviluppare uno script che sposta automaticamente il contenuto dallo schema di rappresentazione allo schema di offerta.

>[!IMPORTANT]
>
>Se alcune consegne che utilizzano offerte configurate dovevano essere inviate dopo la migrazione, devi eliminare e ricreare tutte queste consegne nella versione v7. Se non è possibile farlo, viene offerta una &quot;modalità di compatibilità&quot;. Questa modalità non è consigliata perché non beneficerai di tutte le nuove funzioni di Interaction v7. Questa è una modalità transitoria che ti consente di completare le campagne in corso prima della migrazione effettiva alla versione 6.1. Per ulteriori informazioni su questa modalità, contattateci.

Un esempio di script di spostamento (**actionsTo610_full_XX.js**) è disponibile nella **Migrazione** nella cartella Adobe Campaign v7. Questo file mostra un esempio di script per un client che utilizza una singola rappresentazione e-mail per offerta (il **[!UICONTROL htmlSource]** e **[!UICONTROL textSource]** campi). Il contenuto presente nel **NmsEmailOfferView** La tabella è stata spostata nella tabella delle offerte.

>[!NOTE]
>
>L’utilizzo di questo script non consente di trarre vantaggio dalle opzioni &quot;content management&quot; (gestione dei contenuti) e &quot;rendering delle funzioni&quot; (funzioni di rendering). Per usufruire di queste funzioni, è necessario ripensare le offerte del catalogo, in particolare i contenuti delle offerte e gli spazi di configurazione.

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

Segui la procedura da seguire dopo aver spostato il contenuto dell’offerta se disponi di un solo ambiente. In questo caso prendiamo &quot;ENV&quot; come esempio.

1. In tutti gli spazi di offerta dell’ambiente &quot;ENV&quot;, aggiorna l’elenco dei campi utilizzati. Ad esempio, per uno spazio di offerta che utilizza solo il **[!UICONTROL htmlSource]**, devi aggiungere la **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. In **[!UICONTROL Type of Environment]** all&#39;interno del campo **[!UICONTROL General]** scheda , seleziona **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Crea un ambiente di progettazione (&quot;ENV_DESIGN&quot;, ad esempio) e collegalo all’ambiente online ENV.

   ![](assets/migration_interaction_4.png)

1. Distribuire tutti gli spazi di offerta dell’ambiente &quot;ENV&quot; (clic con il pulsante destro del mouse > **[!UICONTROL Actions > Deploy]**) e seleziona l’ambiente &quot;ENV_DESIGN&quot;.

   ![](assets/migration_interaction_5.png)

1. Fai lo stesso per tutte le offerte di ambiente &quot;ENV&quot;.
1. Attiva tutte le offerte di ambiente &quot;ENV_DESIGN&quot; sui canali pertinenti.
1. Prova a rendere attiva un’offerta. Se non si verificano problemi, eseguire le attività in sospeso nell&#39;ultima attività del flusso di lavoro **[!UICONTROL Offer notification]** (offerMgt) per rendere live tutte le offerte.

   ![](assets/migration_interaction_6.png)

1. Esegui test completi.

   >[!NOTE]
   >
   >I nomi delle categorie e delle offerte online vengono modificati dopo essere stati pubblicati. Sul canale in entrata, aggiorna tutti i riferimenti a offerte e categorie.

## Rapporti {#reports}

### Rapporti standard {#standard-reports}

Tutti i report standard attualmente utilizzano il motore di rendering v6.x. Se hai aggiunto JavaScript a questi rapporti, alcuni elementi potrebbero non funzionare più. Infatti, la vecchia versione di JavaScript non è compatibile con il motore di rendering v6.x. Devi quindi controllare il codice JavaScript e successivamente adattarlo. È necessario verificare ogni rapporto, in particolare la funzione di esportazione.

### Rapporti personalizzati {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
Se desideri sfruttare le nuove funzionalità del rapporto, devi ripubblicare i rapporti. In questo caso, controlla tutti gli script e modificali se necessario. Per quanto riguarda l’esportazione di PDF, se hai aggiunto uno script specifico per Open Office, questo non funzionerà più con il nuovo motore di esportazione di PDF (PhantomJS).

## Applicazioni web {#web-applications}

Ci sono due famiglie di applicazioni web:

* applicazioni web identificate (insieme, moduli di approvazione, sviluppi interni extranet),
* applicazioni web anonime (moduli web o questionario).

### Applicazioni web identificate {#identified-web-applications}

Come per le relazioni ([ulteriori informazioni](#reports)), se hai aggiunto JavaScript, devi controllarlo e adattarlo se necessario. Se desideri sfruttare il banner blu v7 (contenente le schede blu), devi ripubblicare l’applicazione web.

I metodi di connessione dell&#39;applicazione Web sono stati modificati nella versione v7. In caso di problemi di connessione nelle applicazioni Web identificate, è necessario attivare temporaneamente la **allowUserPassword** e **sessionTokenOnly** nelle opzioni **serverConf.xml** file. Dopo l’aggiornamento, modifica i seguenti valori di opzione:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Pertanto, riavvia il post aggiornamento con il seguente comando:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Verifica le tue applicazioni web nel motore di rendering v6.x prima di pubblicarle. Quindi disattiva queste due opzioni.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Applicazioni web anonime {#anonymous-web-applications}

In caso di problemi, ripubblica l&#39;applicazione web.
