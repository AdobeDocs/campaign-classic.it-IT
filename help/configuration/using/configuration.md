---
title: Configurazione
seo-title: Configurazione
description: Configurazione
seo-description: null
page-status-flag: never-activated
uuid: 0f2aadc3-5199-476c-9956-6e39b899a7d0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: b781fd52-828c-4582-a546-a1fee7e5a26d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Configurazione{#configuration}

I tipi di cartelle utilizzati dall&#39;elenco di navigazione sono descritti in un documento XML che segue la grammatica dello schema **xtk:navtree** .

Il documento XML è strutturato come segue:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

Il documento XML contiene l&#39;elemento **`<navtree>`** principale con gli attributi **name** e **namespace** per specificare il nome e lo spazio dei nomi del documento. Il nome e lo spazio dei nomi costituiscono la chiave di identificazione del documento.

I comandi globali dell&#39;applicazione sono dichiarati nel documento dall&#39; **`<commands>`** elemento .

La dichiarazione dei tipi di file è strutturata nel documento con i seguenti elementi: **`<model>`** e **`<nodemodel>`**.

## Comandi globali {#global-commands}

Un comando globale consente di avviare un’azione. Questa azione può essere un modulo di input o una chiamata SOAP.

I comandi globali sono accessibili dal **[!UICONTROL Tools]** menu principale.

La struttura di configurazione del comando è la seguente:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

La descrizione di un comando globale viene inserita nell&#39; **`<command>`** elemento con le seguenti proprietà:

* **name**: nome interno del comando: il nome deve essere immesso e univoco
* **label**: dell&#39;etichetta del comando.
* **desc**: descrizione visibile dalla barra di stato della schermata principale.
* **modulo**: modulo da avviare: il valore da immettere è la chiave di identificazione del modulo di input (ad es. &quot;cus:receive&quot;)
* **diritti**: elenco di diritti denominati (separati da virgola) che consentono l&#39;accesso a questo comando. L’elenco dei diritti disponibili è accessibile dalla **[!UICONTROL Administration > Access management > Named rights]** cartella.
* **promptLabel**: visualizza una casella di conferma prima dell&#39;esecuzione del comando.

Un **`<command>`** elemento può contenere **`<command>`** elementi secondari. In questo caso, l&#39;elemento padre consente di visualizzare un sottomenu composto da questi elementi secondari.

I comandi vengono visualizzati nello stesso ordine in cui sono dichiarati nel documento XML.

Un separatore di comando consente di visualizzare una barra di separazione tra i comandi. È identificato dal valore **&#39;-&#39;** contenuto nell&#39;etichetta del comando.

La presenza facoltativa del **`<soapcall>`** tag con i relativi parametri di input definisce la chiamata di un metodo SOAP da eseguire. Per ulteriori informazioni sull&#39;API SOAP, consultate la documentazione [JSAPI per](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)Campaign.

Il contesto del modulo può essere aggiornato all&#39;inizializzazione dal **`<enter>`** tag . Per ulteriori informazioni su questo tag, consultare la documentazione relativa ai moduli di input.

**Esempio**:

* Dichiarazione di un comando globale per avviare il modulo &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Una scelta rapida da tastiera viene dichiarata sul carattere &quot;I&quot; dalla presenza di **&amp;** nell&#39;etichetta del comando.

* Esempio di sottomenu con un separatore:

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* Esecuzione di un metodo SOAP:

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## Tipo di cartella {#folder-type}

Un tipo di cartella consente di accedere ai dati di uno schema. La visualizzazione associata alla cartella è composta da un elenco e da un modulo di input.

La struttura di configurazione del tipo di cartella è la seguente:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

La dichiarazione del tipo di cartella deve essere inserita in un **`<model>`** elemento. Questo elemento consente di definire un&#39;organizzazione gerarchica visibile dal **[!UICONTROL Add new folder]** menu. Un **`<model>`** elemento deve contenere **`<nodemodel>`** elementi e altri **`<model>`** elementi.

Gli attributi **nome** ed **etichetta** popolano il nome interno dell&#39;elemento e l&#39;etichetta visualizzata nel **[!UICONTROL Add new folder]** menu.

L&#39; **`<nodemodel>`** elemento contiene la descrizione del tipo di cartella con le seguenti proprietà:

* **name**: nome interno
* **label**: etichetta utilizzata nel **[!UICONTROL Add new folder]** menu e come etichetta predefinita quando si inserisce una cartella.
* **img**: immagine predefinita nell’inserimento della cartella.
* **hiddenCommands**: elenco di comandi (separati da virgola) da mascherare. Valori possibili: &quot;insert&quot;, &quot;delete&quot;, &quot;update&quot; e &quot;duplicate&quot;.
* **newFolderShortCuts**: elenco di scelte rapide da tastiera per i modelli (**`<nodemodel>`** separate da virgola) nella creazione delle cartelle.
* **insertRight**, **editRight**, **deleteRight**: diritti per l’inserimento, la modifica e l’eliminazione di cartelle.

L&#39; **`<view>`** elemento sotto l&#39; **`<nodemodel>`** elemento contiene la configurazione dell&#39;elenco associato alla vista. Lo schema dell&#39;elenco viene immesso nell&#39;attributo **schema** dell&#39; **`<view>`** elemento.

Per modificare i record dell&#39;elenco, viene utilizzato in modo implicito il modulo di input con lo stesso nome dello schema dell&#39;elenco. L&#39;attributo **type** sull&#39; **`<view>`** elemento influisce sulla visualizzazione del modulo. I valori possibili sono:

* **list**: visualizza il modulo in fondo all&#39;elenco.
* **elenco**: visualizza l&#39;elenco da solo. Il modulo viene avviato facendo doppio clic o mediante l&#39;opzione &quot;Apri&quot; nel menu alla selezione dell&#39;elenco.
* **modulo**: visualizza un modulo di sola lettura.
* **editForm**: visualizza un modulo in modalità di modifica.

>[!NOTE]
>
>Il nome del modulo di input può essere sovraccaricato immettendo l&#39;attributo **modulo** nell&#39; **`<view>`** elemento .

La configurazione predefinita delle colonne dell&#39;elenco viene immessa tramite l&#39; **`<columns>`** elemento . Una colonna è dichiarata su un **`<node>`** elemento contenente l&#39;attributo **xpath** con il campo a cui verrà fatto riferimento nello schema come valore.

**Esempio**: dichiarazione di un tipo di cartella sullo schema &quot;nms:destinatario&quot;.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

Menu di inserimento cartella corrispondente:

![](assets/d_ncs_integration_navigation_exemple2.png)

Potete applicare il filtro e l&#39;ordinamento al caricamento dell&#39;elenco:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Comandi di scelta rapida {#shortcut-commands}

Un comando di scelta rapida consente di avviare un’azione per selezionare l’elenco. L&#39;azione può essere un modulo di input o una chiamata SOAP.

I comandi sono accessibili dal **[!UICONTROL Action]** menu dell&#39;elenco o dal pulsante del menu associato.

La struttura di configurazione del comando è la seguente:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

La descrizione di un comando viene immessa sull&#39; **`<command>`** elemento con le seguenti proprietà:

* **name**: nome interno del comando: il nome deve essere specificato e univoco.
* **label**: dell&#39;etichetta del comando.
* **desc**: descrizione visibile dalla barra di stato della schermata principale.
* **modulo**: modulo da avviare: il valore da immettere è la chiave di identificazione del modulo di input (ad es. &quot;cus:receive&quot;).
* **diritti**: elenco di diritti denominati (separati da virgola) che consentono l&#39;accesso a questo comando. L’elenco dei diritti disponibili è accessibile dalla **[!UICONTROL Administration > Access management > Named rights]** cartella.
* **promptLabel**: visualizza una casella di conferma prima dell&#39;esecuzione del comando
* **monoSelection**: forza la selezione mono (selezione multipla per impostazione predefinita).
* **refreshView**: forza il ricaricamento dell&#39;elenco dopo l&#39;esecuzione del comando.
* **enabledIf**: attiva il comando in base all&#39;espressione immessa.
* **img**: immette un&#39;immagine che consente di accedere al comando dalla barra degli strumenti dell&#39;elenco.

Un **`<command>`** elemento può contenere **`<command>`** elementi secondari. In questo caso, l&#39;elemento padre consente di visualizzare un sottomenu composto da questi elementi secondari.

I comandi vengono visualizzati nello stesso ordine in cui sono dichiarati nel documento XML.

Un separatore di comando consente di visualizzare una barra di separazione tra i comandi. È identificato dal valore **&#39;-&#39;** contenuto nell&#39;etichetta del comando.

La presenza facoltativa del **`<soapcall>`** tag con i relativi parametri di input definisce la chiamata di un metodo SOAP da eseguire. Per ulteriori informazioni sulle API SOAP, consulta la documentazione [JSAPI di](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)Campaign.

Il contesto del modulo può essere aggiornato in fase di inizializzazione tramite il **`<enter>`** tag . Per ulteriori informazioni su questo tag, consulta la documentazione del modulo di input.

**Esempio**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### Cartella collegata {#linked-folder}

Esistono due tipi di operazioni di gestione delle cartelle:

1. La cartella è una visualizzazione: l&#39;elenco visualizza tutti i record associati allo schema, con la possibilità di filtrare il sistema immesso nelle proprietà della cartella.
1. La cartella è collegata: i record elencati vengono filtrati implicitamente sul collegamento della cartella.

Per una cartella collegata, è necessario compilare l’attributo **folderLink** dell’ **`<nodemodel>`** elemento. Questo attributo contiene il nome del collegamento nella cartella configurata nello schema dati.

Esempio di dichiarazione di una cartella collegata nello schema dati:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

La configurazione della cartella **`<nodemodel>`** sul collegamento della cartella denominata &quot;cartella&quot; è la seguente:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

