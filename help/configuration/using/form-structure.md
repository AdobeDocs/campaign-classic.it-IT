---
product: campaign
title: Struttura di un modulo
description: Struttura di un modulo
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: e61f2b63-06d3-4b8c-867f-1c729176d2da
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 0%

---

# Struttura di un modulo{#form-structure}

La descrizione di un modulo è un documento XML strutturato che osserva la grammatica dello schema del modulo **xtk:form**.

Il documento XML del modulo di input deve contenere gli attributi `<form>` root con gli attributi **name** e **namespace** per compilare il nome e lo spazio dei nomi del modulo.

```
<form name="form_name" namespace="name_space">
...
</form>
```

Per impostazione predefinita, un modulo è associato allo schema dati con lo stesso nome e lo stesso spazio dei nomi. Per associare un modulo a un nome diverso, imposta l&#39;attributo **entity-schema** dell&#39;elemento `<form>` sul nome della chiave dello schema. Per illustrare la struttura di un modulo di input, descriviamo un’interfaccia utilizzando lo schema di esempio &quot;cus:recipient&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

Il modulo di input basato sullo schema di esempio:

![](assets/d_ncs_integration_form_exemple1.png)

```
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

La descrizione dei controlli di modifica inizia dall&#39;elemento `<form>` principale. Un controllo di modifica viene immesso in un elemento **`<input>`** con l&#39;attributo **xpath** contenente il percorso del campo nel relativo schema.

Il controllo edit si adatta automaticamente al tipo di dati corrispondente e utilizza l’etichetta definita nello schema.

>[!NOTE]
>
>Puoi sovraccaricare l&#39;etichetta definita nel relativo schema dati aggiungendo l&#39;attributo **label** all&#39;elemento `<input>` :\
>`<input label="E-mail address" xpath="@name" />`

Per impostazione predefinita, ogni campo viene visualizzato su una singola riga e occupa tutto lo spazio disponibile a seconda del tipo di dati.

## Formattazione {#formatting}

Il layout dei controlli è simile al layout utilizzato nelle tabelle HTML, con la possibilità di dividere un controllo in più colonne, elementi di interlacciamento o di specificare l&#39;occupazione dello spazio disponibile. Tenere tuttavia presente che la formattazione consente solo di suddividere l&#39;area per proporzioni; non è possibile specificare dimensioni fisse per un oggetto.

Per visualizzare i controlli dell&#39;esempio precedente in due colonne:

![](assets/d_ncs_integration_form_exemple2.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

L&#39;elemento **`<container>`** con l&#39;attributo **colcount** consente di forzare la visualizzazione dei controlli figlio su due colonne.

L&#39;attributo **colspan** di un controllo estende il controllo in base al numero di colonne inserite nel relativo valore:

![](assets/d_ncs_integration_form_exemple3.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

Compilando l&#39;attributo **type=&quot;frame&quot;**, il contenitore aggiunge un frame intorno ai controlli figlio con l&#39;etichetta contenuta nell&#39;attributo **label** :

![](assets/d_ncs_integration_form_exemple4.png)

```
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

Un elemento **`<static>`** può essere utilizzato per formattare il modulo di input:

![](assets/d_ncs_integration_form_exemple5.png)

```
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and e-mail address." colspan="2"/>
</form>
```

Il tag **`<static>`** con il tipo **separatore** consente di aggiungere una barra separatore con un&#39;etichetta contenuta nell&#39;attributo **label**.

È stato aggiunto un testo della guida utilizzando il tag `<static>` con tipo di guida. Il contenuto del testo viene immesso nell&#39;attributo **label** .

## Contenitori {#containers}

I contenitori consentono di raggruppare un set di controlli. Sono rappresentati dall’elemento **`<container>`** . Sono stati utilizzati in precedenza per formattare i controlli su più colonne.

L&#39;attributo **xpath** su un `<container>` consente di semplificare il riferimento ai controlli figlio. Il riferimento ai controlli è quindi relativo all&#39;elemento padre `<container>`.

Esempio di contenitore senza &quot;xpath&quot;:

```
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

Esempio con l’aggiunta di &quot;xpath&quot; all’elemento denominato &quot;location&quot;:

```
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### Tipi di contenitore {#types-of-container}

I contenitori vengono utilizzati per creare controlli complessi utilizzando un set di campi formattati nelle pagine.

#### Contenitore di schede {#tab-container}

Un contenitore a schede formatta i dati in pagine accessibili dalle schede.

![](assets/d_ncs_integration_form_exemple6.png)

```
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    ...
  </container>
</container>
```

Il contenitore principale è definito dall&#39;attributo **type=&quot;notebook&quot;** . Le schede sono dichiarate nei contenitori secondari e l&#39;etichetta delle schede è compilata dall&#39;attributo **label** .

>[!NOTE]
>
>Una funzione **style=&quot;down|up**(per impostazione predefinita)**&quot;** forza il posizionamento verticale delle etichette di tabulazione sotto o sopra il controllo. Questa funzione è facoltativa.
>![](assets/d_ncs_integration_form_exemple7.png)
>`<container style="down" type="notebook">  ... </container>`

#### Elenco icone {#icon-list}

Questo contenitore presenta una barra delle icone verticale che consente di selezionare le pagine da visualizzare.

![](assets/d_ncs_integration_form_exemple8.png)

```
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    ...
  </container>
</container>
```

Il contenitore principale è definito dall&#39;attributo **type=&quot;iconbox&quot;** . Le pagine associate alle icone vengono dichiarate nei contenitori secondari. L’etichetta delle icone viene compilata dall’attributo **label** .

L’icona di una pagina viene compilata dall’attributo `img="<image>"` , dove `<image>` è il nome dell’immagine corrispondente alla chiave costituita dal nome e dallo spazio dei nomi (ad esempio, &quot;xtk:properties.png&quot;).

Le immagini sono disponibili dal nodo **[!UICONTROL Administration > Configuration > Images]** .

#### Contenitore Visibilità {#visibility-container}

È possibile mascherare un set di controlli tramite una condizione dinamica.

Questo esempio illustra la visibilità dei controlli sul valore del campo &quot;Genere&quot;:

```
<container type="visibleGroup" visibleIf="@gender=1">
  ...
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  ...
</container>
```

Un contenitore di visibilità è definito dall&#39;attributo **type=&quot;visibleGroup&quot;**. L&#39;attributo **visibleIf** contiene la condizione di visibilità.

Esempi di sintassi della condizione:

* **visibleIf=&quot;@email=&#39;peter.martinezATneeolane.net&#39;&quot;**: verifica l&#39;uguaglianza nei dati di tipo stringa. Il valore di confronto deve essere tra virgolette.
* **visibleIf=&quot;@gender >= 1 e @gender != 2&quot;**: su un valore numerico.
* **visibleIf=&quot;@boolean1=true o @boolean2=false&quot;**: test su campi booleani.

#### Abilitazione del contenitore {#enabling-container}

Questo contenitore consente di abilitare o disabilitare un set di dati da una condizione dinamica. La disattivazione di un controllo ne impedisce la modifica. L&#39;esempio seguente illustra l&#39;abilitazione dei controlli dal valore del campo &quot;Genere&quot;:

```
<container type="enabledGroup" enabledIf="@gender=1">
  ...
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  ...
</container>
```

Un contenitore di abilitazione è definito dall&#39;attributo **type=&quot;enabledGroup&quot;** . L&#39;attributo **enabledIf** contiene la condizione di attivazione.

## Modifica di un collegamento {#editing-a-link}

Ricorda che nello schema dati è dichiarato un collegamento come segue:

```
<element label="Company" name="company" target="cus:company" type="link"/>
```

Il controllo di modifica del collegamento nel relativo modulo di input è il seguente:

![](assets/d_ncs_integration_form_exemple9.png)

```
<input xpath="company"/>
```

La selezione di Target è accessibile tramite il campo di modifica. L’ingresso è assistito dal tipo avanti in modo che un elemento di destinazione possa essere facilmente trovato dai primi caratteri immessi. La ricerca si basa quindi sulla **stringa di calcolo** definita nello schema di destinazione. Se lo schema non esiste dopo la convalida nel controllo, viene visualizzato un messaggio di conferma della creazione rapida del target. La conferma crea un nuovo record nella tabella di destinazione e lo associa al collegamento.

Un elenco a discesa viene utilizzato per selezionare un elemento di destinazione dall’elenco di record già creati.

L’icona **[!UICONTROL Modify the link]** (cartella) avvia un modulo di selezione con l’elenco degli elementi di destinazione e una zona filtro:

![](assets/d_ncs_integration_form_exemple10.png)

L’icona **[!UICONTROL Edit link]** (lente di ingrandimento) avvia il modulo di modifica dell’elemento collegato. Il modulo utilizzato viene dedotto per impostazione predefinita sulla chiave dello schema di destinazione. L’attributo **form** consente di forzare il nome del modulo di modifica (ad esempio &quot;cus:company2&quot;).

Puoi limitare la scelta degli elementi di destinazione aggiungendo l’elemento **`<sysfilter>`** dalla definizione del collegamento nel modulo di input:

```
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

Puoi anche ordinare l’elenco con l’elemento **`<orderby>`** :

```
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### Proprietà di controllo {#control-properties}

* **noAutoComplete**: disabilita type-ahead (con il valore &quot;true&quot;)
* **createMode**: crea il collegamento al volo, se non esiste. I valori possibili sono:

   * **Nessuno**: disabilita la creazione. Se il collegamento non esiste, viene visualizzato un messaggio di errore
   * **in linea**: crea il collegamento con il contenuto del campo di modifica
   * **edizione**: visualizza il modulo di modifica sul collegamento. Quando il modulo viene convalidato, i dati vengono salvati (modalità predefinita)

* **noZoom**: nessun modulo di modifica sul collegamento (con il valore &quot;true&quot;)
* **modulo**: sovraccarica il modulo di modifica dell’elemento di destinazione

## Elenco di collegamenti {#list-of-links}

Un collegamento inserito nello schema dati come elemento di raccolta (unbound=&quot;true&quot;) deve passare attraverso un elenco per visualizzare tutti gli elementi associati ad esso.

Il principio consiste nel visualizzare l’elenco degli elementi collegati con il caricamento ottimizzato dei dati (download per batch di dati, esecuzione dell’elenco solo se visibile).

Esempio di collegamento di una raccolta in uno schema:

```
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
...
</element>
```

L’elenco nel relativo modulo di immissione:

![](assets/d_ncs_integration_form_exemple11.png)

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Il controllo elenco è definito dall&#39;attributo **type=&quot;linklist&quot;** . Il percorso dell&#39;elenco deve fare riferimento al collegamento della raccolta.

Le colonne sono dichiarate tramite gli elementi **`<input>`** dell’elenco. L&#39;attributo **xpath** fa riferimento al percorso del campo nello schema di destinazione.

Una barra degli strumenti con un’etichetta (definita sul collegamento nello schema) viene automaticamente posizionata sopra l’elenco.

L’elenco può essere filtrato tramite il pulsante **[!UICONTROL Filters]** e configurato per aggiungere e ordinare le colonne.

I pulsanti **[!UICONTROL Add]** e **[!UICONTROL Delete]** consentono di aggiungere ed eliminare elementi della raccolta sul collegamento. Per impostazione predefinita, l’aggiunta di un elemento avvia il modulo di modifica dello schema di destinazione.

Il pulsante **[!UICONTROL Detail]** viene aggiunto automaticamente quando l&#39;attributo **zoom=&quot;true&quot;** viene completato sul tag **`<input>`** dell&#39;elenco: consente di avviare il modulo di modifica della riga selezionata.

È possibile applicare filtri e ordinamento quando l’elenco viene caricato:

```
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

### Tabella delle relazioni {#relationship-table}

Una tabella di relazione consente di collegare due tabelle con cardinalità N-N. La tabella delle relazioni contiene solo i collegamenti alle due tabelle.

L’aggiunta di un elemento all’elenco dovrebbe pertanto consentire di completare un elenco da uno dei due collegamenti presenti nella tabella delle relazioni.

Esempio di tabella di relazione in uno schema:

```
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

Per il nostro esempio, iniziamo con il modulo di input dello schema &quot;cus:recipient&quot;. L’elenco deve visualizzare le associazioni con abbonamenti ai servizi e deve consentire di aggiungere un abbonamento selezionando un servizio esistente.

![](assets/d_ncs_integration_form_exemple12.png)

```
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

L&#39;attributo **xpathChoiceTarget** consente di avviare un modulo di selezione dal collegamento inserito. La creazione del record della tabella delle relazioni aggiornerà automaticamente il collegamento al destinatario corrente e al servizio selezionato.

>[!NOTE]
>
>L&#39;attributo **xpathEditTarget** consente di forzare la modifica della riga selezionata sul collegamento inserito.

### Proprietà elenco {#list-properties}

* **noToolbar**: nasconde la barra degli strumenti (con valore &quot;true&quot;)
* **toolbarCaption**: sovraccarica l’etichetta della barra degli strumenti
* **toolbarAlign**: modifica la geometria verticale o orizzontale della barra degli strumenti (valori possibili: &quot;verticale&quot;|&quot;orizzontale&quot;)
* **img**: visualizza l’immagine associata all’elenco
* **modulo**: sovraccarica il modulo di modifica dell’elemento di destinazione
* **zoom**: aggiunge il  **[!UICONTROL Zoom]** pulsante per modificare l’elemento di destinazione
* **xpathEditTarget**: imposta la modifica del collegamento inserito
* **xpathChoiceTarget**: inoltre, avvia il modulo di selezione sul collegamento inserito

## Controlli dell&#39;elenco di memoria {#memory-list-controls}

Gli elenchi di memoria consentono di modificare gli elementi della raccolta utilizzando il precaricamento dei dati dell’elenco. Impossibile filtrare o configurare l&#39;elenco.

Questi elenchi vengono utilizzati su elementi di raccolta mappati XML o su collegamenti a basso volume.

### Elenco a colonne {#column-list}

Questo controllo visualizza un elenco di colonne modificabili con una barra degli strumenti contenente i pulsanti Aggiungi ed Elimina .

![](assets/d_ncs_integration_form_exemple13.png)

```
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Il controllo elenco deve essere compilato con l&#39;attributo **type=&quot;list&quot;** e il percorso dell&#39;elenco deve fare riferimento all&#39;elemento raccolta.

Le colonne sono dichiarate nei tag secondari **`<input>`** dell’elenco. L&#39;etichetta e la dimensione della colonna possono essere forzate con gli attributi **label** e **colSize** .

>[!NOTE]
>
>Le frecce di ordinamento vengono aggiunte automaticamente quando l&#39;attributo **ordered=&quot;true&quot;** viene aggiunto all&#39;elemento di raccolta nello schema dati.

I pulsanti della barra degli strumenti possono essere allineati orizzontalmente:

![](assets/d_ncs_integration_form_exemple14.png)

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

L&#39;attributo **toolbarCaption** forza l&#39;allineamento orizzontale della barra degli strumenti e immette il titolo sopra l&#39;elenco.

#### Zoom in un elenco {#zoom-in-a-list}

L’inserimento e la modifica dei dati in un elenco possono essere immessi in un modulo di modifica separato.

![](assets/d_ncs_integration_form_exemple15.png)

```
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

Il modulo di modifica viene completato dall’elemento `<form>` nella definizione dell’elenco. La sua struttura è identica a quella di un modulo di input. Il pulsante **[!UICONTROL Detail]** viene aggiunto automaticamente quando l&#39;attributo **zoom=&quot;true&quot;** viene completato sul tag **`<input>`** dell&#39;elenco. Questo attributo consente di avviare il modulo di modifica della riga selezionata.

>[!NOTE]
>
>Aggiungendo l&#39;attributo **zoomOnAdd=&quot;true&quot;** si forza la chiamata del modulo di modifica quando viene inserito un elemento elenco.

### Proprietà elenco {#list-properties-1}

* **noToolbar**: nasconde la barra degli strumenti (con valore &quot;true&quot;)
* **toolbarCaption**: sovraccarica l’etichetta della barra degli strumenti
* **toolbarAlign**: modifica il posizionamento della barra degli strumenti (valori possibili: &quot;verticale&quot;|&quot;orizzontale&quot;)
* **img**: visualizza l’immagine associata all’elenco
* **modulo**: sovraccarica il modulo di modifica dell’elemento di destinazione
* **zoom**: aggiunge il  **[!UICONTROL Zoom]** pulsante per modificare l’elemento di destinazione
* **zoomOnAdd**: avvia il modulo di modifica sull’aggiunta
* **xpathChoiceTarget**: inoltre, avvia il modulo di selezione sul collegamento inserito

## Campi non modificabili {#non-editable-fields}

Per visualizzare un campo e impedirne la modifica, utilizza il tag **`<value>`** o completa l&#39;attributo **readOnly=&quot;true&quot;** sul tag **`<input>`** .

Esempio nel campo &quot;Genere&quot;:

![](assets/d_ncs_integration_form_exemple16.png)

```
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## Pulsante di scelta {#radio-button}

Un pulsante di scelta consente di scegliere tra diverse opzioni. I tag **`<input>`** vengono utilizzati per elencare le opzioni possibili e l&#39;attributo **checkedValue** specifica il valore associato alla scelta.

Esempio nel campo &quot;Genere&quot;:

```
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## Casella di controllo {#checkbox}

Una casella di controllo riflette uno stato booleano (selezionato o meno). Per impostazione predefinita, questo controllo è utilizzato dai campi &quot;booleani&quot; (true/false). A questo pulsante può essere associata una variabile con un valore predefinito pari a 0 o 1. Questo valore può essere sovraccaricato tramite gli attributi **checkValue** .

```
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## Modifica gerarchia di navigazione {#navigation-hierarchy-edit}

Questo controllo crea una struttura ad albero in un insieme di campi da modificare.

I controlli da modificare sono raggruppati in un **`<container>`** immesso sotto il tag **`<input>`** del controllo struttura:

```
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/d_ncs_integration_form_exemple18.png)

## Campo espressione {#expression-field}

Un campo espressione aggiorna dinamicamente un campo da un’espressione; il tag **`<input>`** viene utilizzato con un attributo **xpath** per immettere il percorso del campo da aggiornare e un attributo **expr** contenente l&#39;espressione di aggiornamento.

```
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## Contesto dei moduli {#context-of-forms}

L’esecuzione di un modulo di input inizializza un documento XML contenente i dati dell’entità da modificare. Questo documento rappresenta il contesto del modulo e può essere utilizzato come area di lavoro.

### Aggiornamento del contesto {#updating-the-context}

Per modificare il contesto del modulo, utilizzare il tag `<set expr="<value>" xpath="<field>"/>`, dove `<field>` è il campo di destinazione, e `<value>` è l’espressione o il valore di aggiornamento.

Esempi di utilizzo del tag `<set>`:

* **`<set expr="'Test'" xpath="/tmp/@test" />`**: posiziona il valore &#39;Test&#39; nella posizione temporanea /tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**: aggiorna l’entità sull’attributo &quot;lastName&quot; con il valore &quot;Test&quot;
* **`<set expr="true" xpath="@boolean1" />`**: imposta il valore del campo &quot;boolean1&quot; su &quot;true&quot;
* **`<set expr="@lastName" xpath="/tmp/@test" />`**: aggiornamenti relativi al contenuto dell&#39;attributo &quot;lastName&quot;

È possibile aggiornare il contesto del modulo durante l’inizializzazione e la chiusura del modulo tramite i tag **`<enter>`** e **`<leave>`** .

```
<form name="recipient" namespace="cus">
  <enter>
    <set...
  </enter>
  ...
  <leave>
    <set...
  </leave>
</form>
```

>[!NOTE]
>
>`<enter>` e `<leave>`   I tag possono essere utilizzati sui tipi `<container>` di pagine (&quot;blocco appunti&quot; e &quot;casella di riepilogo&quot;).

### Linguaggio delle espressioni {#expression-language-}

Per eseguire test condizionali, è possibile utilizzare una macro-lingua nella definizione del modulo.

Il tag **`<if expr="<expression>" />`** esegue le istruzioni specificate sotto il tag se l’espressione è verificata:

```
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

Il tag **`<check expr="<condition>" />`** combinato con il tag **`<error>`** impedisce la convalida del modulo e visualizza un messaggio di errore se la condizione non è soddisfatta:

```
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

## Procedure guidate {#wizards}

Una procedura guidata ti guida attraverso un set di passaggi di immissione dati sotto forma di pagine. I dati immessi vengono salvati al momento della convalida del modulo.

Una procedura guidata ha la seguente struttura:

```
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Wizard example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    ...
  </container>
  ...
</form>
```

![](assets/d_ncs_integration_form_exemple19.png)

La presenza dell&#39;attributo **type=&quot;Wizard&quot;** sull&#39;elemento `<form>` consente di definire la modalità guidata nella costruzione del modulo. Le pagine vengono completate da elementi `<container>`, secondari dell’elemento `<form>`. L’elemento `<container>` di una pagina viene popolato con gli attributi title per il titolo e desc per visualizzare la descrizione sotto il titolo della pagina. I pulsanti **[!UICONTROL Previous]** e **[!UICONTROL Next]** vengono aggiunti automaticamente per consentire la navigazione tra le pagine.

Il pulsante **[!UICONTROL Finish]** salva i dati immessi e chiude il modulo.

### Metodi SOAP {#soap-methods}

L’esecuzione del metodo SOAP può essere avviata da un tag **`<leave>`** popolato alla fine di una pagina.

Il tag **`<soapcall>`** contiene la chiamata per il metodo con i seguenti parametri di input:

```
<soapCall name="<name>" service="<schema>">
  <param type="<type>" exprIn="<xpath>"/>  
  ...
</soapCall>
```

Il nome del servizio e il relativo schema di implementazione vengono immessi tramite gli attributi **name** e **service** del tag **`<soapcall>`** .

I parametri di input sono descritti sugli elementi **`<param>`** sotto il tag **`<soapcall>`** .

Il tipo di parametro deve essere specificato tramite l&#39;attributo **type** . I tipi possibili sono i seguenti:

* **stringa**: stringa di caratteri
* **booleano**: Booleano
* **byte**: Numero intero a 8 bit
* **short**: Numero intero a 16 bit
* **long**: Numero intero a 32 bit
* **short**: Numero intero a 16 bit
* **doppio**: numero a virgola mobile a doppia precisione
* **DOMElement**: nodo di tipo elemento

L&#39;attributo **exprIn** contiene la posizione dei dati da trasmettere come parametro.

**Esempio**:

```
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param type="DOMElement" exprIn="/tmp/entityList"/>         
    <param type="DOMElement" exprIn="/tmp/choiceList"/>         
    <param type="boolean"    exprIn="true"/>       
  </soapCall>
</leave>
```
