---
product: campaign
title: Configurare la struttura di navigazione di Campaign Explorer
feature: Application Settings
description: Scopri come configurare la struttura di navigazione di Campaign Explorer
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 0%

---

# Configurare la struttura di navigazione di Campaign Explorer{#configuration}

In qualità di utente esperto, puoi aggiungere cartelle nella struttura dell’Explorer e personalizzarla.

Ulteriori informazioni su Esplora campagne e gerarchia di navigazione [in questa sezione](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

I tipi di cartelle utilizzati dall&#39;elenco di spostamento sono descritti in un documento XML conforme alla grammatica **xtk:navtree** schema.

Il documento XML è strutturato nel modo seguente:

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

Il documento XML contiene **`<navtree>`** elemento principale con **nome** e **namespace** attributi per specificare il nome del documento e lo spazio dei nomi. Il nome e lo spazio dei nomi costituiscono la chiave di identificazione del documento.

I comandi globali dell&#39;applicazione sono dichiarati nel documento dal **`<commands>`** elemento.

La dichiarazione dei tipi di file è strutturata nel documento con i seguenti elementi: **`<model>`** e **`<nodemodel>`**.

## Comandi globali {#global-commands}

Un comando globale consente di avviare un’azione. Questa azione può essere un modulo di input o una chiamata SOAP.

I comandi globali sono accessibili dall&#39;area principale **[!UICONTROL Tools]** menu.

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

La descrizione di un comando globale viene immessa nel **`<command>`** con le seguenti proprietà:

* **nome**: nome interno del comando: il nome deve essere inserito e univoco
* **etichetta**: etichetta del comando.
* **desc**: descrizione visibile dalla barra di stato della schermata principale.
* **modulo**: modulo da avviare: il valore da immettere è la chiave di identificazione del modulo di input (ad esempio, &quot;cus:recipient&quot;)
* **diritti**: elenco di diritti denominati (separati da una virgola) che consentono l’accesso a questo comando. L’elenco dei diritti disponibili è accessibile dalla sezione **[!UICONTROL Administration > Access management > Named rights]** cartella.
* **promptLabel**: visualizza una casella di conferma prima dell’esecuzione del comando.

A **`<command>`** può contenere **`<command>`** sottoelementi. In questo caso, l’elemento padre consente di visualizzare un sottomenu costituito da questi elementi figlio.

I comandi vengono visualizzati nello stesso ordine in cui sono dichiarati nel documento XML.

Un separatore di comandi consente di visualizzare una barra di separazione tra i comandi. È identificato dal **&#39;-&#39;** valore contenuto nell&#39;etichetta del comando.

La presenza opzionale del **`<soapcall>`** con i relativi parametri di input definisce la chiamata di un metodo SOAP da eseguire. Per ulteriori informazioni sull’API SOAP, consulta [Documentazione JSAPI per Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it).

Il contesto del modulo può essere aggiornato all’inizializzazione da **`<enter>`** tag. Per ulteriori informazioni su questo tag, consulta la documentazione sui moduli di input.

**Esempio**:

* Dichiarazione di un comando globale per avviare il modulo &quot;xtk:import&quot;:

  ```
  <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Una scelta rapida da tastiera è dichiarata sul carattere &quot;I&quot; dalla presenza di **E** nell&#39;etichetta del comando.

* Esempio di sottomenu con separatore:

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

Un tipo di cartella consente di concedere l’accesso ai dati di uno schema. La visualizzazione associata alla cartella è costituita da un elenco e da un modulo di input.

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

La dichiarazione del tipo di cartella deve essere immessa in un **`<model>`** elemento. Questo elemento ti consente di definire un’organizzazione gerarchica visibile dall’elemento **[!UICONTROL Add new folder]** menu. A **`<model>`** l&#39;elemento deve contenere **`<nodemodel>`** elementi e altro **`<model>`** elementi.

Il **nome** e **etichetta** Gli attributi popolano il nome interno dell&#39;elemento e l&#39;etichetta visualizzata nella **[!UICONTROL Add new folder]** menu.

Il **`<nodemodel>`** contiene la descrizione del tipo di cartella con le seguenti proprietà:

* **nome**: nome interno
* **etichetta**: etichetta utilizzata nella **[!UICONTROL Add new folder]** e come etichetta predefinita quando si inserisce una cartella.
* **img**: immagine predefinita all’inserimento della cartella.
* **hiddenCommands**: elenco di comandi (separati da una virgola) da mascherare. Valori possibili: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; e &quot;adbdup&quot;.
* **newFolderShortCuts**: elenco di scelte rapide da tastiera nei modelli (**`<nodemodel>`** separati da una virgola) nella creazione della cartella.
* **insertRight**, **editRight**, **deleteRight**: diritti per l’inserimento, la modifica e l’eliminazione di cartelle.

Il **`<view>`** elemento sotto **`<nodemodel>`** contiene la configurazione dell’elenco associato alla vista. Lo schema dell’elenco viene immesso nel **schema** attributo del **`<view>`** elemento.

Per modificare i record dell’elenco, viene utilizzato implicitamente il modulo di input con lo stesso nome dello schema dell’elenco. Il **tipo** attributo su **`<view>`** influisce sulla visualizzazione del modulo. I valori possibili sono:

* **listdet**: visualizza il modulo nella parte inferiore dell’elenco.
* **list**: visualizza solo l’elenco. Il modulo viene avviato facendo doppio clic su o selezionando l&#39;elenco dal menu &quot;Apri&quot;.
* **modulo**: visualizza un modulo di sola lettura.
* **editForm**: visualizza un modulo in modalità di modifica.

>[!NOTE]
>
>Il nome del modulo di input può essere sovraccaricato immettendo il **modulo** attributo in **`<view>`** elemento.

La configurazione predefinita delle colonne dell’elenco viene immessa tramite **`<columns>`** elemento. Una colonna è dichiarata su un **`<node>`** elemento contenente **xpath** con il campo a cui fare riferimento nel relativo schema come valore.

**Esempio**: dichiarazione di un tipo di cartella nello schema &quot;nms:recipient&quot;.

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

Il menu di inserimento della cartella corrispondente:

![](assets/d_ncs_integration_navigation_exemple2.png)

È possibile applicare filtri e ordinamenti durante il caricamento dell’elenco:

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

Un comando di scelta rapida consente di avviare un&#39;azione quando si seleziona l&#39;elenco. L’azione può essere un modulo di input o una chiamata SOAP.

I comandi sono accessibili dalla **[!UICONTROL Action]** dell&#39;elenco o del relativo pulsante di menu.

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

La descrizione di un comando viene immessa nel **`<command>`** con le seguenti proprietà:

* **nome**: nome interno del comando: il nome deve essere inserito e univoco.
* **etichetta**: etichetta del comando.
* **desc**: descrizione visibile dalla barra di stato della schermata principale.
* **modulo**: modulo da avviare: il valore da immettere è la chiave di identificazione del modulo di input (ad esempio, &quot;cus:recipient&quot;).
* **diritti**: elenco di diritti denominati (separati da una virgola) che consentono l’accesso a questo comando. L’elenco dei diritti disponibili è accessibile dalla sezione **[!UICONTROL Administration > Access management > Named rights]** cartella.
* **promptLabel**: visualizza una casella di conferma prima dell’esecuzione del comando
* **monoSelection**: forza la selezione mono (selezione multipla per impostazione predefinita).
* **refreshView**: forza il ricaricamento dell’elenco dopo l’esecuzione del comando.
* **enabledIf**: attiva il comando a seconda dell’espressione immessa.
* **img**: immette un’immagine che consente di accedere al comando dalla barra degli strumenti dell’elenco.

A **`<command>`** può contenere **`<command>`** sottoelementi. In questo caso, l’elemento padre consente di visualizzare un sottomenu costituito da questi elementi figlio.

I comandi vengono visualizzati nello stesso ordine in cui sono dichiarati nel documento XML.

Un separatore di comandi consente di visualizzare una barra di separazione tra i comandi. È identificato dal **&#39;-&#39;** valore contenuto nell&#39;etichetta del comando.

La presenza opzionale del **`<soapcall>`** con i relativi parametri di input definisce la chiamata di un metodo SOAP da eseguire. Per ulteriori informazioni sulle API SOAP, consulta [Documentazione JSAPI per Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it).

Il contesto del modulo può essere aggiornato all’inizializzazione tramite **`<enter>`** tag. Per ulteriori informazioni su questo tag, consulta la documentazione del modulo di input.

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

1. La cartella è una vista: l’elenco mostra tutti i record associati allo schema, con la possibilità di filtrare il sistema inserito nelle proprietà della cartella.
1. La cartella è collegata: i record nell’elenco vengono filtrati in modo implicito sul collegamento della cartella.

Per una cartella collegata, il **folderLink** attributo su **`<nodemodel>`** deve essere compilato. Questo attributo contiene il nome del collegamento nella cartella configurata nello schema di dati.

Esempio di dichiarazione di una cartella collegata nello schema dati:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

La configurazione del **`<nodemodel>`** sul collegamento della cartella denominata &quot;folder&quot; (cartella) si trova quanto segue:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
