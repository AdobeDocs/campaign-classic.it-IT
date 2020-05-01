---
title: Elementi e attributi
seo-title: Elementi e attributi
description: Elementi e attributi
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a2cb740fe9b71435f602b738bd270fd3a0954901

---


# Elementi e attributi {#elements-and-attributes}

Quando si modifica uno schema, è disponibile un sistema di approvazione basato sullo schema di origine (xtk:srcSchema). Alcuni errori possono essere rilevati anche durante l&#39;aggiornamento del database utilizzando l&#39;aggiornamento della struttura del database. procedura guidata.

Per impostazione predefinita, negli schemi di Adobe Campaign, tutti gli attributi di tipo booleano sono &quot;false&quot;. Per attivarli, è necessario specificare l&#39;attributo nello schema e impostarne il valore su &quot;true&quot;.

## `<attribute>` element {#attribute--element}

### Modello di contenuto {#content-model}

attribute:==help

### Attributi {#attributes}

_operation (stringa), advanced (booleano), applyIf (stringa), autoIncrement (booleano), membersTo (stringa), dataPolicy (stringa), dbEnum (stringa), defOnDuplicate (booleano), default (stringa), desc (stringa), enum (stringa), expr (stringa), feature (stringa), feature (stringa), featureDate (booleano) img (stringa), inout (stringa), label (stringa), length (stringa), localizable (booleano), name (MNTOKEN), notNull (booleano), pkgStatus (stringa), ref (stringa), Required (booleano), sqlDefault (stringa), sqlname (stringa), sqltable (stringa), target (mltable) NTOKEN), template (stringa), translateDefault (stringa), translateExpr (stringa), type (MNTOKEN), user (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano)

### Genitori {#parents}

`<element>`

### Bambini {#children}

`<help>`

### Descrizione {#description}

`<attribute>` consentono di definire un campo nel database.

### Uso e contesto di utilizzo {#use-and-context-of-use}

`<attribute>` gli elementi devono essere dichiarati in un `<element>` elemento.

La sequenza in cui `<attribute>` gli elementi sono definiti in un `<srcschema>` database non influisce sulla sequenza di creazione del campo nel database. La sequenza di creazione sarà in ordine alfabetico.

### Descrizione attributo {#attribute-description}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo è utilizzato principalmente per estendere gli schemi out-of-the-box.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che Adobe Campaign recupererà l&#39;elemento senza aggiornarlo o generando un errore in caso contrario.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Questo significa che Adobe Campaign aggiornerà l&#39;elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che Adobe Campaign inserirà l&#39;elemento senza verificarne l&#39;esistenza.
   * &quot;update&quot;: update. Questo significa che Adobe Campaign aggiornerà l&#39;elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **advanced (booleano)**: quando questa opzione è attivata (@advanced=&quot;true&quot;), consente di nascondere l&#39;attributo nell&#39;elenco dei campi disponibili, accessibili per configurare un elenco in un modulo.
* **applyIf (stringa)**: questo attributo consente di rendere facoltativi i campi. L&#39; `<attribute>` elemento verrà preso in considerazione durante l&#39;aggiornamento del database quando il vincolo viene rispettato. &quot;applyIf&quot; riceve un&#39;espressione XTK.
* **autoIncrement (booleano)**: se questa opzione è attivata, il campo diventa un contatore. Questo consente di incrementare un valore (per la maggior parte ID). (uso esterno)
* **membersTo (stringa)**: prende il nome e lo spazio dei nomi della tabella che condivide il campo e compila lo schema in cui è dichiarato l&#39;attributo. (utilizzato solo in a `<schema>`).
* **dataPolicy (stringa)**: consente di specificare i vincoli di approvazione per i valori consentiti nel campo SQL o XML. I valori per questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: lettere maiuscole
   * &quot;lowerCase&quot;: Tutte le maiuscole
   * &quot;UpCase&quot;: maiuscolo
   * &quot;email&quot;: indirizzo e-mail
   * &quot;phone&quot;: numero di telefono
   * &quot;identifier&quot;: nome identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti nel `<srcschema>`.
* **defOnDuplicate (booleano)**: se questo attributo è attivato, quando un record viene duplicato, il valore predefinito (definito in @default) viene automaticamente applicato di nuovo al record.
* **default (string)**: consente di definire il valore del campo predefinito (chiamata a una funzione, valore predefinito). Questo attributo riceve un&#39;espressione XTK.
* **desc (stringa)**: consente di inserire una descrizione dell&#39;attributo. Questa descrizione viene visualizzata nella barra di stato dell&#39;interfaccia.
* **edit (stringa)**: questo attributo specifica il tipo di input che verrà utilizzato nel modulo collegato allo schema.
* **enum (stringa)**: riceve il nome dell&#39;enumerazione collegata al campo. L&#39;enumerazione può essere inserita nello stesso schema o in uno schema remoto.
* **expr (stringa)**: definisce un&#39;espressione di precalcolo dei campi. Questo attributo riceve un&#39;espressione Xpath o XTK.
* **feature (stringa)**: definisce un campo delle caratteristiche: Questi campi vengono utilizzati per estendere i dati in una tabella esistente, ma con memorizzazione in una tabella allegata. I valori accettati sono:

   * &quot;shared&quot;: il contenuto è memorizzato in una tabella condivisa per tipo di dati
   * &quot;dedicato&quot;: il contenuto è memorizzato in una tabella dedicata
   Le tabelle delle caratteristiche SQL vengono create automaticamente in base al tipo di caratteristica:

   * dedicato: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Esistono due tipi di campi di caratteristiche: campi semplici &quot;oà¹&quot; in cui è autorizzato un singolo valore per la caratteristica, e campi di scelta multipla &quot;oà¹&quot;, in cui la caratteristica è collegata a un elemento di raccolta che può contenere più valori.

   Quando una caratteristica è definita in uno schema, questo schema deve avere una chiave principale basata su un singolo campo (le chiavi composite non sono autorizzate).

* **featureDate (booleano)**: attributo collegato al campo delle caratteristiche &quot;@feature&quot;. Se il valore è &quot;true&quot;, è possibile verificare l’ultimo aggiornamento del valore.
* **img (stringa)**: consente di definire un percorso per un’immagine collegata a un campo (namespace + nome immagine) (esempio: img=&quot;cus:mypicture.jpg&quot;). Fisicamente, l&#39;immagine deve essere importata nel server dell&#39;applicazione.
* **label (stringa)**: etichetta collegata al campo, destinata principalmente all&#39;utente nell&#39;interfaccia. Consente di evitare i vincoli di denominazione.
* **length (stringa)**: max numero di caratteri per un valore del campo SQL di tipo &quot;stringa&quot;. Se l&#39;attributo &quot;@length&quot; non è specificato, Adobe Campaign crea automaticamente un campo per 255 caratteri.
* **localizzabile (booleano)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **name (MNTOKEN)**: nome dell&#39;attributo che corrisponderà al nome del campo nella tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e conforme ai vincoli di denominazione XML.

   Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente al nome del campo da Adobe Campaign:

   * &quot;i&quot;: prefisso per il tipo &#39;integer&#39;.
   * &quot;d&quot;: per il tipo &#39;double&#39;.
   * &quot;s&quot;: per il tipo di stringa del carattere.
   * &quot;t&quot;: per il tipo &#39;date&#39;.
   Per definire completamente il nome del campo nella tabella, utilizzate l&#39;opzione &quot;@sqlname&quot; quando definite un attributo.

* **notNull (booleano)**: consente di ridefinire il comportamento di Adobe Campaign per quanto riguarda la gestione dei record NULL nel database. Per impostazione predefinita, i campi numerici non sono null e i campi stringa e tipo data possono essere null.
* **pkgStatus (stringa)**: durante le esportazioni del pacchetto, i valori vengono presi in considerazione a seconda del valore di &quot;@pkgStatus&quot;:

   * &quot;always&quot;: always present
   * &quot;never&quot;: never
   * &quot;default (or nothing)&quot;: il valore viene esportato tranne se è il valore predefinito o se non è un campo interno che non sarebbe compatibile con altre istanze.

* **ref (stringa)**: questo attributo definisce un riferimento a un `<attribute>` elemento condiviso da più schemi (factoring di definizione). La definizione non viene copiata nello schema corrente.
* **obbligatorio (booleano)**: se questo attributo è attivato (@requirements=&quot;true&quot;), il campo è evidenziato nell&#39;interfaccia. L&#39;etichetta del campo sarà rossa nei moduli.
* **sql (booleano)**: se questo attributo è attivato (@sql=&quot;true&quot;), forza l&#39;archiviazione dell&#39;attributo SQL, anche quando l&#39;elemento che contiene l&#39;attributo ha la proprietà xml=&quot;true&quot;.
* **sqlDefault (stringa)**: questo attributo consente di definire il valore predefinito preso in considerazione per l&#39;aggiornamento del database se l&#39;attributo @notNull è attivato. Se questo attributo viene aggiunto dopo la creazione dell&#39;attributo, il comportamento dello schema non verrà modificato nemmeno per i nuovi record. Per modificare lo schema e aggiornare il valore dei nuovi record, è necessario eliminare e creare nuovamente l&#39;attributo.
* **sqlname (stringa)**: del campo durante la creazione della tabella. Se @sqlname non è specificato, per impostazione predefinita viene utilizzato il valore dell&#39;attributo &quot;@name&quot;. Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente a seconda del tipo di campo.
* **template (stringa)**: questo attributo definisce un riferimento a un `<attribute>` elemento condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translateDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, l&#39;attributo &quot;@translateDefault&quot; consentirà di ridefinire un&#39;espressione che corrisponda a quella definita in @default, che verrà raccolta dallo strumento di traduzione (uso interno).
* **translateExpr (stringa)**: se è presente un attributo &quot;@expr&quot;, l&#39;attributo &quot;@translateExpr&quot; consente di ridefinire un&#39;espressione che corrisponda a quella definita in @expr, da raccogliere con lo strumento di traduzione (uso interno).
* **type (MNTOKEN)**: tipo di campo.

   I tipi di campo sono generici. A seconda del tipo di database installato, Adobe Campaign modifica il tipo definito in un valore specifico per il database installato durante l&#39;aggiornamento della struttura.

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * string
   * time
   * periodo
   * uuid
   Se l&#39;attributo &quot;@type&quot; viene lasciato vuoto, per impostazione predefinita Adobe Campaign collega al campo una stringa di caratteri (STRING) con una lunghezza pari a 100.

   Se il campo è di tipo STRING e il nome del campo non è specificato dalla presenza dell&#39;attributo &quot;@sqlname&quot;, il nome del campo nel database sarà automaticamente preceduto da un nome &#39;s&#39;. Questa modalità operativa sarà simile a quella dei campi INTEGER (i), DOUBLE (d) e DATES (ts).

* **userEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;open&quot;. I valori dell&#39;enumerazione possono essere definiti dall&#39;utente nell&#39;interfaccia.
* **visibleIf (stringa)**: definisce una condizione sotto forma di espressione XTK per mostrare o nascondere l&#39;attributo.

   >[!IMPORTANT]
   >
   >L&#39;attributo è nascosto, ma è comunque possibile accedervi.

* **xml (booleano)**: se questa opzione è attivata, i valori del campo non hanno un campo SQL collegato. Adobe Campaign crea un campo &quot;mData&quot; di tipo Testo per l&#39;archiviazione dei record. Ciò significa che non è possibile filtrare o ordinare i campi.

### Esempi {#examples}

Esempio di valori di enumerazione i cui valori sono memorizzati nel database:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Dichiarazione di un campo XML con &quot;@datapolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Esempio con un &quot;@applyIf&quot;: l&#39;attributo &quot;contains&quot; sarà creato solo se il numero di paesi è maggiore di 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Esempio con &quot;@feature&quot; di tipo &quot;condiviso&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Esempio con &quot;@feature&quot; di tipo &quot;dedicato&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```

## `<compute-string>` element {#compute-string--element}

### Modello di contenuto {#content-model-1}

compute-string:==EMPTY

### Attributi {#attributes-1}

@expr

### Genitori {#parents-1}

`<element>`

### Bambini {#children-1}

None

### Descrizione {#description-1}

L&#39; `<compute-string>` elemento consente di generare una stringa basata su un&#39;espressione XTK per visualizzare un&#39;etichetta &quot;predefinita&quot; nell&#39;interfaccia in base a diversi valori.

### Uso e contesto di utilizzo {#use-and-context-of-use-1}

Quando non `<compute-string>` viene definito alcun elemento, per impostazione predefinita viene immesso un `<compute-string>` elemento con i valori della chiave primaria nello schema.

### Descrizione attributo {#attribute-description-1}

* **expr (stringa)**: Espressione XTK e/o Xpath

### Esempi {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Risultato della stringa calcolata su un destinatario: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` element {#condition--element}

### Modello di contenuto {#content-model-2}

condizione:==EMPTY

### Attributi {#attributes-2}

* @boolOperator (stringa)
* @enabledIf (stringa)
* @expr (stringa)

### Genitori {#parents-2}

`<sysfilter>`

### Bambini {#children-2}

None

### Descrizione {#description-2}

Questo elemento consente di definire una condizione di filtro.

### Uso e contesto di utilizzo {#use-and-context-of-use-2}

Un `<sysfiler>` elemento può contenere diverse condizioni di filtraggio.

### Descrizione attributo {#attribute-description-2}

* **boolOperator (stringa)**: se più `<conditions>` sono definiti all&#39;interno dello stesso `<sysfilter>` elemento, questo attributo consente di combinarli. Per impostazione predefinita, il collegamento logico è compreso tra `<condition>` gli elementi è &quot;AND&quot;. L&#39;attributo &quot;@boolOperator&quot; consente di combinare collegamenti di tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (stringa)**: test di attivazione della condizione.
* **expr (stringa)**: un&#39;espressione XTK.

### Esempi {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` element {#dbindex--element}

### Modello di contenuto {#content-model-3}

dbindex:==keyfield

### Attributi {#attributes-3}

* @_operation (stringa)
* @applyIf (stringa)
* @label (stringa)
* @name (MNTOKEN)
* @univoche (booleano)

### Genitori {#parents-3}

`<element>`

### Bambini {#children-3}

`<keyfield>`

### Descrizione {#description-3}

Questo elemento consente di definire un indice collegato a una tabella.

### Uso e contesto di utilizzo {#use-and-context-of-use-3}

È possibile definire diversi indici. Un indice può fare riferimento a uno o più campi della tabella. La dichiarazione dell&#39;indice in genere segue la definizione dell&#39;elemento dello schema principale.

L&#39;ordine degli `<keyfield>` elementi definiti in un `<dbindex>` articolo è molto importante. Il primo `<keyfield>` deve essere il criterio di indicizzazione su cui si basano principalmente le query.

Il nome dell&#39;indice nel database viene calcolato concatenando il nome della tabella e il nome dell&#39;indice. Ad esempio: Nome tabella &quot;Sample&quot;, spazio dei nomi &quot;Cus&quot;, nome indice &quot;MyIndex&quot;-> nome del campo indice durante la creazione dell&#39;indice durante la query: &quot;CusSample_myIndex&quot;.

### Descrizione attributo {#attribute-description-3}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo è utilizzato principalmente per estendere gli schemi out-of-the-box.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che Adobe Campaign recupererà l&#39;elemento senza aggiornarlo o generando un errore in caso contrario.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Questo significa che Adobe Campaign aggiornerà l&#39;elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che Adobe Campaign inserirà l&#39;elemento senza verificarne l&#39;esistenza.
   * &quot;update&quot;: update. Questo significa che Adobe Campaign aggiornerà l&#39;elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **applyIf (stringa)**: condizione per tenere conto dell&#39;indice - riceve un&#39;espressione XTK.
* **label (stringa)**: index label.
* **name (MNTOKEN)**: nome di indice univoco.
* **univoco (booleano)**: se questa opzione è attivata (@univoche=&quot;true&quot;), l&#39;attributo garantisce l&#39;univocità dell&#39;indice in tutti i campi.

### Esempi {#examples-3}

Creazione di un indice nel campo &quot;id&quot;. (l&#39;attributo &quot;@Unique&quot; sull&#39; `<dbindex>` elemento attiva l&#39;aggiunta della parola chiave SQL &quot;UNIQUE&quot; quando l&#39;indice viene creato nel database (query)).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Creazione di un indice composito nei campi &quot;@mail&quot; e &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

## `<element>` element {#element--element}

### Modello di contenuto {#content-model-4}

element:==(attribute | stringa di calcolo | dbindex | Default | element | help | join | Tasto | sysFilter | translateDefault)

### Attributi {#attributes-4}

_operation (stringa), advanced (booleano), aggregate (stringa), applyIf (stringa), autopk (booleano), appartieneTo (stringa), convDate (stringa), dataPolicy (stringa), dataSource (stringa), dbEnum (stringa), defOnDuplicate (booleano), predefinito (stringa), desc (stringa), displayAsField (booleano) NotSupportDiff (booleano), edit (stringa), emptyKeyValue (stringa), enum (stringa), enumImage (stringa), espandereSchemaTarget (stringa), expr (stringa), externalJoin (booleano), feature (stringa), featureDate (booleano), filterPath (stringa), folderLink (stringa), folderModel (stringa), folderProcess stringa), fullLoad (booleano), gerarchico (booleano), gerarchicoPath (stringa), img (stringa), inout (stringa), integrità (stringa), etichetta (stringa), etichettaSingolare (stringa), lunghezza (stringa), localizzabile (booleano), nome (MNTOKEN), noDbIndex (booleano), noKey (booleano) Boolean, overflowtable (booleano), pkSequence (stringa), pkgStatus (stringa), ref (stringa), obbligatorio (booleano), revAdvanced (booleano), revCardinality (stringa), revDesc (stringa), revExternalJoin (booleano), revIntegrity (stringa), revLabel (stringa), revLink (stringa), revTarget revVisibleIf (stringa), sql (booleano), sqlname (stringa), sqltable (stringa), tableSpace (stringa), tableSpaceIndex (stringa), target (MNTOKEN), template (stringa), temporaryTable (booleano), translateDefault (stringa), translateExpr (stringa), type (MNTOKEN), unbound (non bound) booleano), utente (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano), xmlChildren (booleano)

### Genitori {#parents-4}

`<srcschema>`

`<element>`

### Bambini {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### Descrizione {#description-4}

Adobe Campaign offre quattro tipi di `<element>` elementi:

* Radice `<element>` : definisce il nome della tabella SQL che corrisponde allo schema.
* Struttura `<element>` : definisce un gruppo di `<element>` elementi o di `<attribute>` elementi.
* Collegamento `<element>` : definisce un collegamento. Questi elementi devono includere l&#39;attributo &quot;@type=link&quot;.
* XML `<element>` : definisce un campo di tipo Testo &quot;mData&quot;. Questo elemento deve includere l&#39;attributo &quot;@type=xml&quot;.

### Descrizione attributo {#attribute-description-4}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo è utilizzato principalmente per estendere gli schemi out-of-the-box.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che Adobe Campaign recupererà l&#39;elemento senza aggiornarlo o generando un errore in caso contrario.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Questo significa che Adobe Campaign aggiornerà l&#39;elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che Adobe Campaign inserirà l&#39;elemento senza verificarne l&#39;esistenza.
   * &quot;update&quot;: update. Questo significa che Adobe Campaign aggiornerà l&#39;elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **advanced (booleano)**: quando questa opzione è attivata (@advanced=&quot;true&quot;), consente di nascondere l&#39;attributo nell&#39;elenco dei campi disponibili, accessibili per configurare un elenco in un modulo.
* **aggregate (stringa)**: consente di copiare la definizione di un `<element>` altro schema. Questo attributo riceve una dichiarazione dello schema sotto forma di &quot;namespace:name&quot;.
* **applyIf (stringa)**: condizione per l’applicazione dell’indice. Questo attributo riceve un&#39;espressione XTK.
* **autopk (booleano)**: se questa opzione è attivata (autopk=&quot;true&quot;), viene automaticamente definita una chiave univoca. Questa opzione può essere utilizzata solo sull&#39;elemento principale dello schema. Attenzione, Adobe Campaign garantisce solo che la chiave generata sia univoca. Non è garantito che i valori chiave siano consecutivi e incrementali.
* **dataPolicy (stringa)**: consente di specificare i vincoli di approvazione per i valori consentiti nel campo SQL. I valori per questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: lettere maiuscole
   * &quot;lowerCase&quot;: Tutte le maiuscole
   * &quot;UpCase&quot;: maiuscolo
   * &quot;email&quot;: indirizzo e-mail
   * &quot;phone&quot;: numero di telefono
   * &quot;identifier&quot;: nome identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti nel `<srcschema>`.
* **defOnDuplicate (booleano)**: se questo attributo è attivato, quando un record viene duplicato, il valore predefinito (definito in @default) viene automaticamente applicato di nuovo al record.
* **default (string)**: consente di definire il comportamento degli elementi (chiamata a una funzione, valore predefinito). Questo attributo riceve un&#39;espressione XTK.
* **desc (stringa)**: consente di inserire una descrizione dell’elemento. Questa descrizione viene visualizzata nella barra di stato dell&#39;interfaccia.
* **displayAsField (booleano)**: se questo attributo è attivato, un tipo di &quot;collegamento&quot; `<element>` verrà visualizzato come campo nella vista struttura degli schemi (scheda &quot;Struttura&quot;). In questo modo, è possibile visualizzare un collegamento come campo locale e modificarne il comportamento durante una query. Quando l&#39;elemento viene trovato nella SELEZIONE di una query, verrà utilizzato il valore della destinazione del collegamento. Quando l&#39;elemento viene trovato nella posizione WHERE di una query, verrà utilizzata la chiave sottostante del collegamento.
* **edit (stringa)**: questo attributo specifica il tipo di input che verrà utilizzato nel modulo collegato allo schema.
* **enum (stringa)**: riceve il nome dell&#39;enumerazione collegata al campo. L&#39;enumerazione può essere inserita nello stesso schema o in uno schema remoto.
* **expr (stringa)**: questo attributo definisce un campo calcolato per il quale non è memorizzata alcuna definizione nella tabella. Riceve un&#39;espressione Xpath o XTK (stringa).
* **externalJoin (booleano)**: join esterno in un elemento di tipo &quot;collegamento&quot;.
* **feature (stringa)**: definisce un campo delle caratteristiche: Questi campi vengono utilizzati per estendere i dati in una tabella esistente, ma con memorizzazione in una tabella allegata. I valori accettati sono:

   * &quot;shared&quot;: il contenuto è memorizzato in una tabella condivisa per tipo di dati
   * &quot;dedicato&quot;: il contenuto è memorizzato in una tabella dedicata
   Le tabelle delle caratteristiche SQL vengono create automaticamente in base al tipo di caratteristica:

   * dedicato: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Esistono due tipi di campi di caratteristiche: campi semplici in cui è autorizzato un singolo valore sui campi caratteristici e a scelta multipla, in cui la caratteristica è collegata a un elemento di raccolta che può contenere più valori.

   Quando una caratteristica è definita in uno schema, questo schema deve avere una chiave principale basata su un singolo campo (le chiavi composite non sono autorizzate).

* **featureDate (booleano)**: attributo collegato al campo delle caratteristiche &quot;@feature&quot;. Se il valore è &quot;true&quot;, è possibile verificare l’ultimo aggiornamento del valore.
* **filterPath (stringa)**: questo attributo riceve un Xpath e consente di definire un filtro per un campo.
* **folderLink (stringa)**: questo attributo riceve il nome del collegamento che consente di recuperare i file contenenti entità.
* **folderModel (stringa)**: definisce il tipo di cartella che consente l&#39;archiviazione delle entità. Questo attributo è definito solo se è presente &quot;@folderLink&quot;.
* **folderProcess (stringa)**: definisce il collegamento in cui vengono memorizzate le istanze del modello di entità. Questo attributo è definito solo se è presente &quot;@folderLink&quot;.
* **fullLoad (booleano)**: questo attributo forza la visualizzazione di tutti i record in una tabella durante la selezione del campo in un modulo.
* **img (stringa)**: riceve il percorso di un’immagine collegata a un elemento. Il valore di questo attributo è di tipo &quot;namespace:image name&quot;. Ad esempio: img=&quot;cus:myImage.jpg&quot;. Fisicamente, l&#39;immagine deve essere importata nel server dell&#39;applicazione.
* **integrità (stringa)**: integrità referenziale dell&#39;occorrenza della tabella di origine verso la tabella di destinazione.

   I valori accessibili sono:

   * &quot;define&quot;: Adobe Campaign non elimina l&#39;entità se vi viene fatto riferimento tramite il collegamento
   * &quot;normal&quot;: l&#39;eliminazione dell&#39;occorrenza di origine inizializza le chiavi del collegamento sull&#39;occorrenza di destinazione (modalità predefinita). Questo tipo di integrità inizializza tutte le chiavi esterne
   * &quot;own&quot;: l&#39;eliminazione dell&#39;occorrenza di origine attiva l&#39;eliminazione dell&#39;occorrenza di destinazione
   * &quot;owncopy&quot;: simili a &quot;own&quot; (in caso di cancellazione) o a duplicati (in caso di duplicazione)
   * &quot;neutro&quot;: non fa nulla

* **label (stringa)**: etichetta dell&#39;elemento.
* **labelSingular (stringa)**: etichetta (forma singolare) dell&#39;elemento utilizzato in alcune parti dell&#39;interfaccia.
* **length (stringa)**: max numero di caratteri autorizzati per un valore del campo SQL di tipo &quot;stringa&quot;.
* **localizzabile (booleano)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **name (MNTOKEN)**: nome interno dell&#39;elemento che corrisponde al nome della tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e deve essere conforme ai vincoli di denominazione collegati a XML.

   Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente al nome del campo da Adobe Campaign.

   * &quot;i&quot;: prefisso per il tipo &#39;integer&#39;.
   * &quot;d&quot;: per il tipo &#39;double&#39;.
   * &quot;s&quot;: per il tipo di stringa del carattere.
   * &quot;t&quot;: per il tipo &#39;date&#39;.
   Per definire il nome della tabella in modo autonomo, è necessario utilizzare l&#39;attributo &quot;@sqltable&quot; nella definizione dell&#39;elemento dello schema principale.

* **noDbIndex (booleano)**: consente di specificare che l&#39;elemento non verrà indicizzato.
* **ordered (booleano)**: se l&#39;attributo è attivato (ordered=&quot;true&quot;), Adobe Campaign mantiene la sequenza di dichiarazione dell&#39;elemento in un elemento di raccolta XML.
* **pkSequence (stringa)**: riceve il nome della sequenza da utilizzare per il calcolo di una chiave incrementale automatica. Questo attributo può essere utilizzato solo se è definita una chiave automatica incrementale sull&#39;elemento principale dello schema.
* **pkgStatus (stringa)**: durante le esportazioni del pacchetto, i valori saranno presi in considerazione in funzione del valore di questo attributo:

   * &quot;always&quot;: l&#39;elemento sarà sempre presente
   * &quot;never&quot;: l&#39;elemento non sarà mai presente
   * &quot;default (or nothing)&quot;: l&#39;elemento viene esportato a meno che non sia l&#39;elemento predefinito o che non sia un campo interno e non sia compatibile con altre istanze

* **ref (stringa)**: questo attributo definisce un riferimento a un elemento >element> condiviso da più schemi (factoring di definizione). La definizione non viene copiata nello schema corrente.
* **obbligatorio (booleano)**: se questo attributo è attivato (@requirements=&quot;true&quot;), il campo è evidenziato nell&#39;interfaccia. L&#39;etichetta del campo sarà rossa nei moduli.
* **revAdvanced (booleano)**: quando attivato, questo attributo specifica che il collegamento opposto è un collegamento &quot;avanzato&quot;.
* **revCardinality (stringa)**: questo attributo definisce la cardinalità di un collegamento tra due tabelle. Viene utilizzato in un tipo di &quot;collegamento&quot; `<element>`.

   I valori possibili sono:

   * &quot;single&quot; : Collegamento semplice di tipo 1-1
   * &quot;unbound&quot;: Collegamento raccolta tipi 1-N
   Per impostazione predefinita, se l&#39;attributo non è specificato durante la creazione del collegamento, la cardinalità sarà di 1-N.

* **revDesc (stringa)**: questo attributo riceve una descrizione collegata al collegamento opposto.
* **revExternalJoin (booleano)**: quando attivato, questo attributo consente di forzare il join esterno sul collegamento opposto.
* **revIntegrity (stringa)**: questo attributo definisce l&#39;integrità dello schema di destinazione. Gli stessi valori dell&#39;attributo &quot;@integrità&quot; sono autorizzati. Per impostazione predefinita, Adobe Campaign assegna il valore &quot;normale&quot; a questo attributo.
* **revLabel (stringa)**: etichetta del collegamento opposto.
* **revLink (stringa)**: nome del collegamento opposto. Se il valore è &quot;_NONE_&quot;, nello schema di destinazione non verrà creato alcun collegamento opposto.
* **revTarget (stringa)**: destinazione del collegamento opposto.
* **sql (booleano)**: se questo attributo è attivato (@sql=&quot;true&quot;), forza l&#39;archiviazione dell&#39;elemento SQL, anche se l&#39;elemento ha la proprietà xml=&quot;true&quot;.
* **sqlname (stringa)**: nome del campo durante la creazione della tabella. Se &quot;@sqlname&quot; non è specificato, il valore dell&#39;attributo &quot;@name&quot; viene utilizzato per impostazione predefinita. Durante la scrittura dello schema nella tabella, i prefissi vengono aggiunti automaticamente in base al tipo di campo.
* **sqltable (stringa)**: per l&#39;elemento principale dello schema, questo attributo sovraccarica il nome della tabella SQL generata per impostazione predefinita. Se &quot;@sqltable&quot; non è specificato, il nome predefinito sarà strutturato come segue: namespace (prima lettera maiuscola) seguito dal valore dello SrcSchema &quot;@name&quot;.
* **tableSpace (stringa)**: questo attributo consente di specificare una nuova tablespace di memorizzazione dei dati per una tabella (valida nella directory principale `<element>`).
* **tableSpaceIndex (stringa)**: questo attributo consente di specificare una nuova tablespace di memorizzazione dell&#39;indice per una tabella (valida per la directory principale `<element>`).
* **target (MNTOKEN)**: riceve il nome dello schema di destinazione durante la creazione di un collegamento tra tabelle. Questo attributo è attivo solo per gli elementi di tipo &quot;link&quot;.
* **template (stringa)**: questo attributo definisce un riferimento a un `<element>` elemento condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translateDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, l&#39;attributo &quot;@translateDefault&quot; consentirà di ridefinire un&#39;espressione che corrisponda a quella definita in @default, che verrà raccolta dallo strumento di traduzione (uso interno).
* **translateExpr (stringa)**: se viene trovato un attributo &quot;@expr&quot;, l&#39;attributo &quot;@translateExpr&quot; consente di ridefinire un&#39;espressione che corrisponda a quella definita in &quot;@expr&quot; e che verrà raccolta dallo strumento di traduzione (uso interno).
* **type (MNTOKEN)**: definisce il tipo di dati memorizzato nell&#39;elemento.

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * string
   * time
   * periodo
   * uuid

* **unbound (booleano)**: se l&#39;attributo è attivato (unbound=&quot;true&quot;), il collegamento viene dichiarato come elemento di raccolta per una cardinalità 1-N.
* **userEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;open&quot;. I valori di enumerazione possono essere definiti dall&#39;utente nell&#39;interfaccia.
* **xml (booleano)**: se questa opzione è attivata, tutti i valori definiti nell&#39;elemento sono memorizzati in XML in un campo di tipo TESTO &quot;mData&quot;. Ciò significa che non verranno applicati filtri o ordinamento a questi campi.
* **xmlChildren (booleano)**: forza l&#39;archiviazione per ciascun figlio ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` element {#enumeration--element}

### Modello di contenuto {#content-model-5}

enumerazione:==(help| valore)

### Attributi {#attributes-5}

* @basetype (stringa)
* @default (stringa)
* @desc (stringa)
* @label (stringa)
* @name (stringa)
* @template (stringa)

### Genitori {#parents-5}

`<srcschema>`

### Bambini {#children-5}

* `<help>`
* `<value>`

### Descrizione {#description-5}

Questo elemento consente di definire un&#39;enumerazione di valori. Un&#39;enumerazione appartiene allo schema in cui è definita, ma è accessibile tramite un altro schema.

### Uso e contesto di utilizzo {#use-and-context-of-use-4}

Le enumerazioni sono definite all&#39;inizio di uno schema (prima della definizione dell&#39;elemento principale).

### Descrizione attributo {#attribute-description-5}

* **basetype (stringa)**: tipo dei valori memorizzati nell&#39;enumerazione.

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * string
   * time
   * periodo
   * uuid

* **default (string)**: Valore predefinito. Il valore predefinito può anche essere uno dei valori definiti nell&#39;enumerazione.
* **desc (stringa)**: descrizione dell&#39;enumerazione.
* **label (stringa)**: etichetta di enumerazione.
* **name (stringa)**: nome interno dell&#39;enumerazione.
* **template (stringa)**: questo attributo definisce un riferimento a un `<enumeration>` elemento condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.

### Esempi {#examples-4}

Esempio di valori di enumerazione i cui valori sono memorizzati nel database:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definizione di un&#39;enumerazione con un valore predefinito:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` element {#help--element}

### Modello di contenuto {#content-model-6}

help:==EMPTY

### Attributi {#attributes-6}

None

### Genitori {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Bambini {#children-6}

None

### Descrizione {#description-6}

Questo elemento consente di descrivere un `<element>` elemento o un `<attribute>` elemento. Può contenere solo testo ed è memorizzato in XML nel database.

### Descrizione attributo {#attribute-description-6}

Questo elemento non ha attributi.

### Esempi {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` element {#join--element}

### Modello di contenuto {#content-model-7}

join:==EMPTY

### Attributi {#attributes-7}

* @dstFilterExpr (stringa)
* @xpath-dst (stringa)
* @xpath-src (stringa)

### Genitori {#parents-7}

`<element>`

### Bambini {#children-7}

None

### Descrizione {#description-7}

Consente di definire i campi che creano un join tra tabelle SQL.

### Uso e contesto di utilizzo {#use-and-context-of-use-5}

Un `<join>` elemento può essere utilizzato solo se l&#39; `<element>` elemento padre è di tipo &#39;link&#39;. Ciò significa che l&#39;elemento padre deve avere dichiarato l&#39;attributo &quot;@type=link&quot;.

Non è necessario specificare il nome e lo spazio dei nomi della tabella remota nell&#39; `<join>` elemento . Devono essere specificati nel padre `<element>`.

Per convenzione, i collegamenti sono definiti alla fine dello schema.

Se l&#39; `<join>` elemento non viene specificato quando l&#39;elemento del tipo di collegamento è definito, il collegamento viene posizionato automaticamente sulle chiavi primarie di entrambe le tabelle.

### Descrizione attributo {#attribute-description-7}

* **dstFilterExpr (stringa)**: questo attributo consente di limitare il numero di valori idonei nella tabella remota.
* **xpath-dst (stringa)**: questo attributo riceve un attributo Xpath (@name attributo della tabella remota).
* **xpath-src (stringa)**: questo attributo riceve un attributo Xpath (@name nello schema corrente).

### Esempi {#examples-6}

Collegamento tra il campo &#39;email&#39; della tabella corrente e il campo &quot;@anima-id&quot; della tabella remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Collegamento filtrato alla tabella &quot;cus:Country&quot; in base al contenuto del campo &quot;@country&quot; che deve contenere il valore &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` element {#key--element}

### Modello di contenuto {#content-model-8}

key:==keyfield

### Attributi {#attributes-8}

* @allowEmptyPart (booleano)
* @applyIf (stringa)
* @internal (booleano)
* @label (stringa)
* @name (MNTOKEN)
* @noDbIndex (booleano)

### Genitori {#parents-8}

`<element>`

### Bambini {#children-8}

`<keyfield>`

### Descrizione {#description-8}

Questo elemento consente di definire una chiave per identificare un record nella tabella.

Una tabella deve avere almeno una chiave.

### Uso e contesto di utilizzo {#use-and-context-of-use-6}

Come regola, le chiavi sono dichiarate dopo l&#39;elemento principale dello schema e gli indici.

Una chiave è nota come composita se include più campi (ad esempio, più `<keyfield>` elementi secondari). Non utilizzate una chiave composita per definire una chiave primaria.

Se l&#39;elemento principale dello schema contiene l&#39;attributo &quot;@autopk=true&quot;, la chiave primaria è univoca. È possibile avere una sola chiave primaria per schema.

I primi 1000 identificatori sono riservati, quindi se è necessario definire un intervallo di valori per le chiavi, iniziare da 1000.

### Descrizione attributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: nel caso di una chiave composita, se questo attributo è attivato, la chiave viene considerata valida se almeno una delle chiavi non è vuota. In questo caso, il valore di nozione vuoto è &quot;0&quot; (booleano o per tutti i tipi di dati numerici). Per impostazione predefinita, è necessario immettere tutte le chiavi che costituiscono una chiave composita.
* **applyIf (stringa)**: questo attributo consente di rendere la chiave facoltativa. Definisce la condizione in base alla quale verrà applicata la definizione chiave. Questo attributo riceve un&#39;espressione XTK.
* **internal (boolean)**: se è attivato, questo attributo consente ad Adobe Campaign di sapere che la chiave è primaria.
* **label (stringa)**: dell&#39;etichetta della chiave.
* **name (MNTOKEN)**: nome interno della chiave.
* **noDbIndex (booleano)**: se è attivato (noDbIndex=&quot;true&quot;), il campo corrispondente alla chiave non verrà indicizzato.

### Esempi {#examples-------}

Dichiarazione di una chiave composita che autorizza il campo &quot;@expr&quot; o &quot;alias&quot; a essere vuoto:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Dichiarazione di una chiave primaria sul campo &quot;Nome&quot; del tipo STRING in una query SQL corrispondente `<srcschema>` e:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` element {#keyfield--element}

### Modello di contenuto {#content-model-9}

keyfield:==EMPTY

### Attributi {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Genitori {#parents-9}

`<key>`  ,  `<dbindex />`

### Bambini {#children-9}

None

### Descrizione {#description-9}

Questo elemento definisce i campi da integrare in un indice o in una chiave.

### Descrizione attributo {#attribute-description-9}

* **xlink (MNTOKEN)**: consente di fare automaticamente riferimento a chiavi esterne definite nel join per una tabella di relazione (collegamento N-N).
* **xpath (MNTOKEN)**: definizione di un indice o di una chiave su un `<attribute>` elemento. Questo attributo riceve un Xpath che definisce il percorso dell&#39;attributo dello schema che definisce la chiave o l&#39;indice.

### Esempi {#examples-}

Selezione del campo &quot;sName&quot; in un indice con un percorso Xpath su &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` element {#method--element}

### Modello di contenuto {#content-model-10}

metodo:==( help | parametri)

### Attributi {#attributes-10}

* @_operation (stringa)
* @access (stringa)
* @const (booleano)
* @hidden (booleano)
* @label (stringa)
* @library (stringa)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (booleano)

### Genitori {#parents-10}

`<methods>`  ,  `<interface />`

### Bambini {#children-10}

* `<help>`
* `<parameters>`

### Descrizione {#description-10}

Questo elemento consente di definire un metodo SOAP.

### Uso e contesto di utilizzo {#use-and-context-of-use-7}

I metodi SOAP consentono i processi dell&#39;applicazione.

Il simbolo &quot;@library&quot; è necessario per dichiarare un nuovo metodo (non nativo): lo spazio dei nomi e il nome utilizzati per la libreria sono indipendenti dallo spazio dei nomi e dal nome dello schema in cui si trova la dichiarazione.

### Descrizione attributo {#attribute-description-10}

* **access (stringa)**: questo attributo definisce il controllo di accesso per l&#39;utilizzo del metodo. Se questo attributo non è presente, l&#39;identificazione è obbligatoria. I valori disponibili sono: &#39;anonimo&#39;, &#39;admin&#39; e &#39;sql&#39;.
* **const (booleano)**: se è attivato, questo attributo significa che il metodo dichiarato modificherà l&#39;entità
* **label (stringa)**: etichetta del metodo.
* **libreria (stringa)**: questo metodo non è nativo dell&#39;applicazione. Questo attributo prende il valore della libreria dei metodi in cui viene trovata la definizione del metodo (nms:mylibrary.js).
* **name (MNTOKEN)**: nome univoco del metodo.
* **static (boolean)**: se questo attributo è attivato, il metodo è considerato autonomo, tutti i parametri devono essere specificati al metodo quando viene chiamato.

### Esempi {#examples-7}

Definizione del metodo &quot;Subscribe&quot; out of the box:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` element {#methods--element}

### Modello di contenuto {#content-model-11}

methods:==method

### Attributi {#attributes-11}

None

### Genitori {#parents-11}

`<srcschema>`

### Bambini {#children-11}

method

### Descrizione {#description-11}

Questo elemento consente di definire un `<method>` elemento. È obbligatorio dichiarare un metodo.

### Descrizione attributo {#attribute-description-11}

Questo elemento non ha attributi.

### Esempi {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` element {#param--element}

### Modello di contenuto {#content-model-12}

param:==help

### Attributi {#attributes-12}

* @_operation (stringa)
* @desc (stringa)
* @enum (stringa)
* @inout (stringa)
* @label (stringa)
* @localizable (stringa)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (stringa)

### Genitori {#parents-12}

`<parameters>`

### Bambini {#children-12}

`<help>`

### Descrizione {#description-12}

Questo elemento consente di definire un parametro per richiamare un metodo SOAP.

### Descrizione attributo {#attribute-description-12}

* **desc (stringa)**: descrizione relativa all’ `<param>` elemento.
* **inout (stringa)**: questo attributo definisce se il parametro si trova o meno all&#39;input (in) o all&#39;output (out) della chiamata SOAP. Se questo attributo non è specificato, il parametro predefinito è input (&quot;@inout=in&quot;).
* **label (stringa)**: `<param>` label
* **localizzabile (stringa)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **name (MNTOKEN)**: nome interno del `<param>`
* **type (stringa)**: questo attributo definisce il tipo di `<param>` elemento

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bin
   * blob
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * string
   * time
   * periodo
   * uuid

### Esempi {#examples-9}

Definizione dell&#39;impostazione &quot;serviceName&quot; in entrata del tipo di stringa di caratteri:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` element {#parameters--element}

### Modello di contenuto {#content-model-13}

parametri:==param

### Attributi {#attributes-13}

None

### Genitori {#parents-13}

`<method>`

### Bambini {#children-13}

`<param>`

### Descrizione {#description-13}

Questo elemento definisce un gruppo di `<parameter>` elementi.

### Uso e contesto di utilizzo {#use-and-context-of-use-8}

Questo elemento è obbligatorio, anche per un singolo elemento `<param>` secondario dell&#39; `<method>` elemento.

### Descrizione attributo {#attribute-description-13}

None

### Esempi {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` element {#srcschema--element}

### Modello di contenuto {#content-model-14}

srcSchema:==(attribute | createdBy | dati | element | enumerazione | help | interfaccia | Metodi | modifiedBy)

### Attributi {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), ExtendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (booleano), mappingType (string), modifiedBy-id (long), name (string), namespace useRecycleBin (booleano), view (booleano), xtkschema (stringa)

### Genitori {#parents-14}

None

### Bambini {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Descrizione {#description-14}

L&#39;elemento `<srcschema>` principale di uno schema. È il punto di input per la definizione dello schema.

### Uso e contesto di utilizzo {#use-and-context-of-use-9}

La presentazione dello schema è disponibile in [Informazioni sul riferimento](../../configuration/using/about-schema-reference.md) allo schema e sulla struttura [](../../configuration/using/schema-structure.md)dello schema.

### Descrizione attributo {#attribute-description-14}

* **created (datetime)**: questo attributo fornisce informazioni sulla data e l&#39;ora della creazione dello schema. Presenta un modulo &quot;Data e ora&quot;. I valori visualizzati vengono prelevati dal server. L&#39;ora viene visualizzata in formato UTC.
* **createBy-id (long)**: è l&#39;identificatore dell&#39;operatore che ha creato lo schema.
* **desc (stringa)**: descrizione schema
* **entitySchema (stringa)**: schema di base su cui si basano la sintassi e l&#39;approvazione (per impostazione predefinita per Adobe Campaign: xtk:srcSchema). Quando salvi lo schema corrente, Adobe Campaign ne approva la grammatica con lo schema dichiarato nell&#39;attributo @xtkschema.
* **extensionSchema (stringa)**: riceve il nome dello schema out-of-the-box su cui si basa l&#39;estensione dello schema corrente. Il modulo è &quot;namespace:name&quot;.
* **img (stringa)**: icona collegata allo schema (può essere definita nella procedura guidata di creazione dello schema).
* **label (stringa)**: etichetta dello schema.
* **labelSingular (stringa)**: label (singolare) per la visualizzazione nell&#39;interfaccia.
* **lastModified (datetime)**: questo attributo fornisce informazioni sulla data e l&#39;ora dell&#39;ultima modifica. Presenta un modulo &quot;Data e ora&quot;. I valori visualizzati vengono prelevati dal server. L&#39;ora viene visualizzata in formato UTC.
* **libreria (booleana)**: utilizzo dello schema come libreria e non come entità. A questo schema possono pertanto fare riferimento altri schemi grazie agli attributi &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (stringa)**:

   * &quot;sql&quot;: mappatura database
   * &quot;textFile&quot;: mappatura file di testo
   * &quot;xmlFile&quot;: Mappatura file di testo in formato XML
   * &quot;binaryFile&quot;: mappatura file binaria

* **modifiedBy-id (long)**: corrisponde all&#39;identificatore dell&#39;operatore che ha modificato lo schema.
* **name (stringa)**: nome univoco dello schema.
* **namespace (stringa)**: spazio dei nomi dello schema (predefinito: nms, xtk, nl). Quando si crea un nuovo schema per un progetto, è consigliabile utilizzare uno spazio nomi dedicato.
* **useRecycleBin (booleano)**: attiva la funzione Cestino nell&#39;applicazione. I record eliminati verranno inseriti nel cestino prima dell&#39;eliminazione finale. Questa funzione è disponibile solo in modalità &quot;Consegna&quot;.
* **view (booleano)**: se è attivato (@view=&quot;true&quot;), lo schema verrà utilizzato come visualizzazione. La procedura guidata di aggiornamento della struttura del database non terrà conto dello schema. Questa opzione è utilizzata principalmente per fare riferimento a tabelle esterne.
* **xtkschema (stringa)**: nome dello schema che definisce la grammatica dello schema (xtk:srcSchema per impostazione predefinita).

### Esempi {#examples-11}

`<srcschema>` dell&#39;elemento &quot;nms:delivery&quot; fuori dallo schema box

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` element {#sysfilter--element}

### Modello di contenuto {#content-model-15}

sysFilter:==condition

### Attributi {#attributes-15}

None

### Genitori {#parents-15}

`<element>`

### Bambini {#children-15}

`<condition>`

### Descrizione {#description-15}

Questo elemento consente di definire un filtro.

### Descrizione attributo {#attribute-description-15}

Questo elemento non ha attributi.

### Esempi {#examples-12}

Definizione di un filtro con una condizione per l&#39;attributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` element {#value--element}

### Modello di contenuto {#content-model-16}

value:==help

### Attributi {#attributes-16}

* @applyIf (stringa)
* @desc (stringa)
* @enabledIf (stringa)
* @img (stringa)
* @label (stringa)
* @name (stringa)
* @value (stringa)

### Genitori {#parents-16}

`<enumeration>`

### Bambini {#children-16}

`<help>`

### Descrizione {#description-16}

Questo elemento consente di definire i valori memorizzati in un&#39;enumerazione.

### Descrizione attributo {#attribute-description-16}

* **applyIf (stringa)**: questo attributo consente di rendere facoltativo un valore di enumerazione. Riceve un&#39;espressione XTK.
* **desc (stringa)**: descrizione del valore di enumerazione.
* **enabledIf (stringa)**: condizione per attivare il valore di enumerazione.
* **img (stringa)**: immagine collegata all&#39;enumerazione nel modulo &quot;namespace:image_name&quot;. L&#39;immagine deve essere importata nel server dell&#39;applicazione.
* **label (stringa)**: dell&#39;etichetta del valore di enumerazione.
* **name (stringa)**: nome interno del valore di enumerazione.
* **value (stringa)**: del valore di enumerazione. Il tipo di valore è definito in base al tipo di enumerazione. Se l&#39;enumerazione è di tipo stringa di caratteri, può contenere solo valori di tipo stringa di caratteri.

### Esempi {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
