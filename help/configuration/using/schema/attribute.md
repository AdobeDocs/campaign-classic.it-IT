---
product: campaign
title: Elementi e attributi - elemento attributo
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 0%

---

# elemento attributo {#attribute--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model}

attributo:==help

## Attributi {#attributes}

_operation (stringa), advanced (booleano), applyIf (stringa), autoIncrement (booleano), ownedTo (stringa)), dataPolicy (stringa), dbEnum (stringa), defOnDuplicate (booleano), default (stringa), desc (stringa), enum (stringa), expr (stringa), feature (stringa), featureDate (booleana) img (stringa), inout (stringa), label (stringa), length (stringa), localizable (booleano), name (MNTOKEN), notNull (booleano), pkgStatus (stringa), ref (stringa), required (booleano), sql (booleano), sqlDefault (stringa), sqlname (stringa), sqltable (stringa), target NTOKEN), modello (stringa), tradottoDefault (stringa), tradottoExpr (stringa), tipo (MNTOKEN), utente (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano)

## Genitori {#parents}

`<element>`

## Elementi figli {#children}

`<help>`

## Descrizione {#description}

`<attribute>` gli elementi ti consentono di definire un campo nel database.

## Uso e contesto di utilizzo {#use-and-context-of-use}

`<attribute>` gli elementi devono essere dichiarati in un `<element>` elemento.

La sequenza in cui `<attribute>` gli elementi sono definiti in un `<srcschema>` non influisce sulla sequenza di creazione del campo nel database. La sequenza di creazione sarà alfabetica.

## Descrizione attributo {#attribute-description}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo viene utilizzato principalmente per l’estensione degli schemi predefiniti.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che Adobe Campaign recupererà l’elemento senza aggiornarlo o genererà un errore se non esiste.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che Adobe Campaign aggiornerà l’elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che Adobe Campaign inserirà l’elemento senza verificare se esiste.
   * &quot;update&quot;: aggiornamento. Ciò significa che Adobe Campaign aggiornerà l’elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Questo significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **avanzato (booleano)**: quando questa opzione viene attivata (@advanced=&quot;true&quot;), consente di nascondere l&#39;attributo nell&#39;elenco dei campi disponibili, accessibili per configurare un elenco in un modulo.
* **applyIf (stringa)**: questo attributo consente di rendere i campi facoltativi. La `<attribute>` verrà preso in considerazione al momento dell&#39;aggiornamento del database quando il vincolo viene rispettato. &quot;applyIf&quot; riceve un&#39;espressione XTK.
* **autoIncrement (booleano)**: se questa opzione è attivata, il campo diventa un contatore. Questo consente di incrementare un valore (per lo più ID). (uso esterno)
* **ownedTo (stringa)**: prende il nome e lo spazio dei nomi della tabella che condivide il campo e compila lo schema in cui è dichiarato l’attributo. (utilizzato solo in un `<schema>`).
* **dataPolicy (stringa)**: consente di specificare i vincoli di approvazione per i valori consentiti nel campo SQL o XML. I valori di questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: maiuscolo
   * &quot;lowerCase&quot;: tutte le lettere minuscole
   * &quot;UpperCase&quot;: maiuscolo
   * &quot;email&quot;: indirizzo e-mail
   * &quot;telefono&quot;: numero di telefono
   * &quot;identifier&quot;: nome identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti nel `<srcschema>`.
* **defOnDuplicate (booleano)**: se questo attributo viene attivato, quando un record viene duplicato, il valore predefinito (definito in @default) viene automaticamente riapplicato al record.
* **default (string)**: ti consente di definire il valore del campo predefinito (chiamata a una funzione, valore predefinito). Questo attributo riceve un&#39;espressione XTK.
* **desc (stringa)**: ti consente di inserire una descrizione dell’attributo. Questa descrizione viene visualizzata nella barra di stato dell’interfaccia.
* **edit (stringa)**: questo attributo specifica il tipo di input che verrà utilizzato nel modulo collegato allo schema.
* **enum (stringa)**: riceve il nome dell&#39;enumerazione collegata al campo. L&#39;enumerazione può essere inserita nello stesso schema o in uno schema remoto.
* **expr (stringa)**: definisce un’espressione di precalcolo del campo. Questo attributo riceve un percorso Xpath o un&#39;espressione XTK.
* **feature (stringa)**: definisce un campo delle caratteristiche: Questi campi vengono utilizzati per estendere i dati in una tabella esistente, ma con memorizzazione in una tabella allegata. I valori accettati sono:

   * &quot;shared&quot;: il contenuto viene memorizzato in una tabella condivisa per tipo di dati
   * &quot;dedicato&quot;: il contenuto viene memorizzato in una tabella dedicata

   Le tabelle delle caratteristiche SQL vengono create automaticamente in base al tipo di caratteristica:

   * dedicato: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * condiviso: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Esistono due tipi di campi con caratteristiche: campi semplici à¹ in cui è autorizzato un singolo valore per la caratteristica e campi a scelta multipla in cui la caratteristica è collegata a un elemento di raccolta che può contenere più valori.

   Quando una caratteristica è definita in uno schema, questo schema deve avere una chiave principale basata su un singolo campo (le chiavi composite non sono autorizzate).

* **featureDate (booleano)**: attributo collegato al campo delle caratteristiche &quot;@feature&quot;. Se il suo valore è &quot;true&quot;, ti consente di sapere quando è stato aggiornato l’ultimo valore.
* **img (stringa)**: consente di definire un percorso per un’immagine collegata a un campo (namespace + nome immagine) (esempio: img=&quot;cus:mypicture.jpg&quot;). Fisicamente, l&#39;immagine deve essere importata nel server dell&#39;applicazione.
* **label (stringa)**: etichetta collegata al campo, destinata principalmente all’utente nell’interfaccia di . Consente di evitare i vincoli di denominazione.
* **length (stringa)**: max numero di caratteri per un valore del campo SQL di tipo &quot;stringa&quot;. Se l’attributo &quot;@length&quot; non è specificato, Adobe Campaign crea automaticamente un campo per 255 caratteri.
* **localizzabile (booleano)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **nome (MNTOKEN)**: nome dell’attributo che corrisponde al nome del campo nella tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e rispettare i vincoli di denominazione XML.

   Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente al nome del campo da Adobe Campaign:

   * &quot;i&quot;: prefisso del tipo &quot;integer&quot;.
   * &quot;d&quot;: prefisso del tipo &quot;doppio&quot;.
   * &quot;s&quot;: Prefisso per il tipo di stringa di caratteri.
   * &quot;ts&quot;: prefisso del tipo &quot;date&quot;.

   Per definire completamente il nome del campo nella tabella, utilizza l’opzione &quot;@sqlname&quot; quando definisci un attributo.

* **notNull (booleano)**: consente di ridefinire il comportamento di Adobe Campaign per quanto riguarda la gestione dei record NULL nel database. Per impostazione predefinita, i campi numerici non sono nulli e i campi di tipo stringa e data possono essere nulli.
* **pkgStatus (stringa)**: durante le esportazioni dei pacchetti, i valori vengono presi in considerazione a seconda del valore del &quot;@pkgStatus&quot;:

   * &quot;always&quot;: sempre presente
   * &quot;never&quot;: mai presente
   * &quot;predefinito (o nullo)&quot;: il valore viene esportato a meno che non si tratti del valore predefinito o di un campo interno non compatibile con altre istanze.

* **ref (stringa)**: questo attributo definisce un riferimento a un `<attribute>` elemento condiviso da diversi schemi (factoring di definizione). La definizione non viene copiata nello schema corrente.
* **required (booleano)**: se questo attributo viene attivato (@required=&quot;true&quot;), il campo viene evidenziato nell’interfaccia di . Nei moduli l’etichetta del campo sarà rossa.
* **sql (booleano)**: se questo attributo viene attivato (@sql=&quot;true&quot;), forza l&#39;archiviazione dell&#39;attributo SQL, anche quando l&#39;elemento che contiene l&#39;attributo ha la proprietà xml=&quot;true&quot;.
* **sqlDefault (stringa)**: questo attributo consente di definire il valore predefinito preso in considerazione per l&#39;aggiornamento del database se l&#39;attributo @notNull è attivato. Se questo attributo viene aggiunto dopo la creazione dell&#39;attributo, il comportamento dello schema non cambierà nemmeno per i nuovi record. Per modificare lo schema e aggiornare il valore dei nuovi record, è necessario eliminare e creare nuovamente l&#39;attributo.
* **sqlname (stringa)**: del campo durante la creazione della tabella. Se @sqlname non è specificato, il valore dell&#39;attributo &quot;@name&quot; viene utilizzato per impostazione predefinita. Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente a seconda del tipo di campo.
* **template (stringa)**: questo attributo definisce un riferimento a un `<attribute>` elemento condiviso da diversi schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translateDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, il &quot;@translateDefault&quot; ti permetterà di ridefinire un&#39;espressione che corrisponda a quella definita in @default, da raccogliere dallo strumento di traduzione (uso interno).
* **translateExpr (stringa)**: se è presente un attributo &quot;@expr&quot;, l&#39;attributo &quot;@translateExpr&quot; consente di ridefinire un&#39;espressione che corrisponda a quella definita in @expr, che deve essere raccolta dallo strumento di traduzione (uso interno).
* **type (MNTOKEN)**: tipo di campo.

   I tipi di campo sono generici. A seconda del tipo di database installato, Adobe Campaign cambia il tipo definito in un valore specifico del database installato durante l&#39;aggiornamento della struttura.

   Elenco dei tipi disponibili:

   * QUALSIASI
   * bidone
   * macchia
   * booleano
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
   * stringa
   * orario
   * timespan
   * uuid

   Se l’attributo &quot;@type&quot; viene lasciato vuoto, per impostazione predefinita, Adobe Campaign collega al campo una stringa di caratteri (STRING) con una lunghezza di 100.

   Se il campo è di tipo STRING e il nome del campo non è specificato dalla presenza dell&#39;attributo &quot;@sqlname&quot;, il nome del campo nel database sarà automaticamente preceduto da un nome &#39;s&#39;. Questa modalità operativa sarà simile ai campi di tipo INTEGER (i), DOUBLE (d) e DATES (ts).

* **userEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;open&quot;. I valori dell’enumerazione possono essere definiti dall’utente nell’interfaccia di .
* **visibleIf (stringa)**: definisce una condizione sotto forma di espressione XTK per mostrare o nascondere l’attributo.

   >[!IMPORTANT]
   >
   >L’attributo è nascosto ma è comunque possibile accedervi.

* **xml (booleano)**: se questa opzione è attivata, i valori del campo non hanno un campo SQL collegato. Adobe Campaign crea un campo di tipo Testo &quot;mData&quot; per l’archiviazione dei record. Ciò significa che non è presente alcun filtro o ordinamento in questi campi.

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

Esempio con un &quot;@applyIf&quot;: l&#39;attributo &quot;contiene&quot; sarà creato solo se il numero di paesi è maggiore di 20.

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
