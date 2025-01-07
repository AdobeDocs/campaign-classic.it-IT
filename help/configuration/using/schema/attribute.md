---
product: campaign
title: 'Elementi e attributi: elemento attributo'
description: Elementi e attributi
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 1%

---

# elemento attribute {#attribute--element}


## Modello di contenuto {#content-model}

attributo:==guida

## Attributi {#attributes}

_operation (stringa), advanced (booleano), apply (stringa), autoIncrement (booleano), membersTo (stringa), dataPolicy (stringa), dbEnum (stringa), defOnDuplicate (booleano), default (stringa), desc (stringa), edit (stringa), enum (stringa), expr (stringa), feature (stringa), featureDate (booleano), img (stringa), inout (stringa), label (stringa), length (stringa), localizzabile (booleano), name (MNTOKEN), notNull (booleano), pkgStatus (stringa), ref (stringa), required (booleano), sql (booleano), sqlDefault (stringa), sqlname (stringa), sqltable (stringa), target (MNTOKEN), template (stringa), translationDefault (stringa), transledExpr (stringa), type (MNTOKEN), user (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano)

## Padri {#parents}

`<element>`

## Elementi secondari {#children}

`<help>`

## Descrizione {#description}

Gli elementi `<attribute>` consentono di definire un campo nel database.

## Uso e contesto di utilizzo {#use-and-context-of-use}

`<attribute>` elementi devono essere dichiarati in un elemento `<element>`.

La sequenza in cui sono definiti `<attribute>` elementi in un `<srcschema>` non influisce sulla sequenza di creazione dei campi nel database. La sequenza di creazione sarà in ordine alfabetico.

## Descrizione attributo {#attribute-description}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

  Questo attributo viene utilizzato principalmente quando si estendono schemi predefiniti.

  I valori accessibili sono:

   * &quot;Nessuno&quot;: la riconciliazione da sola. Ciò significa che Adobe Campaign recupererà l’elemento senza aggiornarlo o genererà un errore, se non esiste.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che Adobe Campaign aggiornerà l’elemento o lo creerà se non esiste.
   * &quot;insert&quot;: insertion Ciò significa che Adobe Campaign inserirà l’elemento senza verificarne l’esistenza.
   * &quot;update&quot; (aggiorna): aggiornamento. Ciò significa che Adobe Campaign aggiornerà l’elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **avanzato (booleano)**: quando questa opzione è attivata (@advanced=&quot;true&quot;), consente di nascondere l&#39;attributo nell&#39;elenco dei campi disponibili accessibili per la configurazione di un elenco in un modulo.
* **applicabileIf (stringa)**: questo attributo consente di rendere facoltativi i campi. L&#39;elemento `<attribute>` verrà preso in considerazione durante l&#39;aggiornamento del database quando il vincolo verrà rispettato. &quot;applyIf&quot; riceve un’espressione XTK.
* **autoIncrement (booleano)**: se questa opzione è attivata, il campo diventa un contatore. Questo consente di incrementare un valore (per lo più ID). (uso esterno)
* **AppartieneA (stringa)**: prende il nome e lo spazio dei nomi della tabella che condivide il campo e popola lo schema in cui è dichiarato l&#39;attributo. (utilizzato solo in un `<schema>`).
* **criteri dati (stringa)**: consente di specificare vincoli di approvazione per i valori consentiti nel campo SQL o XML. I valori per questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: prime lettere maiuscole
   * &quot;lowerCase&quot;: tutte minuscole
   * &quot;upperCase&quot;: tutte maiuscole
   * &quot;email&quot;: indirizzo e-mail
   * &quot;phone&quot;: numero di telefono
   * &quot;identifier&quot;: nome dell’identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti in `<srcschema>`.
* **defOnDuplicate (booleano)**: se questo attributo è attivato, quando un record viene duplicato il valore predefinito (definito in @default) viene automaticamente riapplicato al record.
* **default (stringa)**: consente di definire il valore del campo predefinito (chiamata a una funzione, valore predefinito). Questo attributo riceve un&#39;espressione XTK.
* **desc (stringa)**: consente di inserire una descrizione dell&#39;attributo. Questa descrizione viene utilizzata per capire cos’è l’elemento e a cosa serve. È possibile visualizzarlo nel modulo.
* **modifica (stringa)**: questo attributo specifica il tipo di input che verrà utilizzato nel modulo collegato allo schema.
* **enum (stringa)**: riceve il nome dell&#39;enumerazione collegata al campo. L’enumerazione può essere inserita nello stesso schema o in uno schema remoto.
* **expr (stringa)**: definisce un&#39;espressione di precalcolo del campo. Questo attributo riceve un&#39;espressione Xpath o XTK.
* **funzione (stringa)**: definisce un campo delle caratteristiche. Questi campi vengono utilizzati per estendere i dati in una tabella esistente, ma con l&#39;archiviazione in una tabella allegata. I valori accettati sono:

   * &quot;shared&quot; (condiviso): il contenuto viene memorizzato in una tabella condivisa per tipo di dati
   * &quot;dedicato&quot;: il contenuto viene memorizzato in una tabella dedicata

  Le tabelle delle caratteristiche SQL vengono create automaticamente in base al tipo di caratteristica:

   * dedicato: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * condiviso: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Esistono due tipi di campi delle caratteristiche: campi oà<sup>1</sup> semplici in cui è autorizzato un singolo valore per la caratteristica e campi a scelta multipla oà<sup>1</sup> in cui la caratteristica è collegata a un elemento di raccolta che può contenere diversi valori.

  Quando una caratteristica è definita in uno schema, questo schema deve avere una chiave principale basata su un singolo campo (le chiavi composite non sono autorizzate).

* **featureDate (booleano)**: attributo collegato al campo delle caratteristiche &quot;@feature&quot;. Se il suo valore è &quot;true&quot;, ti consente di scoprire quando è stato aggiornato l’ultima volta il valore.
* **img (stringa)**: consente di definire un percorso per un&#39;immagine collegata a un campo (spazio dei nomi + nome immagine) (esempio: img=&quot;cus:mypicture.jpg&quot;). A livello fisico, l&#39;immagine deve essere importata nel server applicazioni.
* **etichetta (stringa)**: etichetta collegata al campo, per lo più destinata all&#39;utente nell&#39;interfaccia. Consente di evitare vincoli di denominazione.
* **lunghezza (stringa)**: max. numero di caratteri per un valore del campo SQL di tipo &quot;stringa&quot;. Se l’attributo &quot;@length&quot; non è specificato, Adobe Campaign crea automaticamente un campo di 255 caratteri.
* **localizzabile (booleano)**: se attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **nome (MNTOKEN)**: nome dell&#39;attributo che corrisponderà al nome del campo nella tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e deve essere conforme ai vincoli di denominazione XML.

  Quando lo schema viene scritto nel database, Adobe Campaign aggiunge automaticamente i prefissi al nome del campo:

   * &quot;i&quot;: prefisso per il tipo &#39;integer&#39;.
   * &quot;d&quot;: prefisso per il tipo &quot;double&quot;.
   * &quot;s&quot;: prefisso per il tipo di stringa di caratteri.
   * &quot;ts&quot;: prefisso per il tipo &quot;date&quot;.

  Per definire completamente il nome del campo nella tabella, utilizzare l&#39;opzione &quot;@sqlname&quot; durante la definizione di un attributo.

* **notNull (booleano)**: consente di ridefinire il comportamento di Adobe Campaign relativo alla gestione dei record NULL nel database. Per impostazione predefinita, i campi numerici non sono nulli e i campi di tipo stringa e data possono essere nulli.
* **pkgStatus (stringa)**: durante le esportazioni del pacchetto, i valori vengono presi in considerazione a seconda del valore del &quot;@pkgStatus&quot;:

   * &quot;always&quot;: sempre presente
   * &quot;mai&quot;: mai presente
   * &quot;default (or Nothing)&quot;: il valore viene esportato tranne se si tratta del valore predefinito o se non è un campo interno che non sarebbe compatibile con altre istanze.

* **ref (stringa)**: questo attributo definisce un riferimento a un elemento `<attribute>` condiviso da più schemi (factoring delle definizioni). La definizione non viene copiata nello schema corrente.
* **obbligatorio (booleano)**: se questo attributo è attivato (@required=&quot;true&quot;), il campo viene evidenziato nell&#39;interfaccia. L’etichetta del campo sarà rossa nei moduli.
* **sql (booleano)**: se questo attributo è attivato (@sql=&quot;true&quot;), forza l&#39;archiviazione dell&#39;attributo SQL, anche quando l&#39;elemento che contiene l&#39;attributo ha la proprietà xml=&quot;true&quot;.
* **sqlDefault (stringa)**: questo attributo consente di definire il valore predefinito preso in considerazione per l&#39;aggiornamento del database se l&#39;attributo @notNull è attivato. Se questo attributo viene aggiunto dopo la creazione dell’attributo, il comportamento dello schema non cambia nemmeno per i nuovi record. Per modificare lo schema e aggiornare il valore per i nuovi record, è necessario eliminare e creare nuovamente l’attributo.
* **sqlname (stringa)**: del campo durante la creazione della tabella. Se non @sqlname specificato, per impostazione predefinita viene utilizzato il valore dell&#39;attributo &quot;@name&quot;. Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente a seconda del tipo di campo.
* **modello (stringa)**: questo attributo definisce un riferimento a un elemento `<attribute>` condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, &quot;@translatedDefault&quot; ti consentirà di ridefinire un&#39;espressione in modo che corrisponda a quella definita in @default, che deve essere raccolta dallo strumento di traduzione (uso interno).
* **TranslatedExpr (stringa)**: se è presente un attributo &quot;@expr&quot;, l&#39;attributo &quot;@translatedExpr&quot; consente di ridefinire un&#39;espressione che corrisponda a quella definita in @expr, che deve essere raccolta dallo strumento di traduzione (uso interno).
* **tipo (MNTOKEN)**: tipo di campo.

  I tipi di campo sono generici. A seconda del tipo di database installato, Adobe Campaign modifica il tipo definito in un valore specifico per il database installato durante l’aggiornamento della struttura.

  Elenco dei tipi disponibili:

   * QUALSIASI
   * raccoglitore
   * blob
   * booleano
   * byte
   * CDATA
   * Data e ora
   * datetimetz
   * datetimenotz
   * data
   * doppio
   * enum
   * mobile
   * html
   * int64
   * link
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * chiave primaria
   * corto
   * stringa
   * ora
   * intervallo di tempo
   * uuid

  Se l’attributo &quot;@type&quot; viene lasciato vuoto, Adobe Campaign collega al campo per impostazione predefinita una stringa di caratteri (STRING) di lunghezza pari a 100.

  Se il campo è di tipo STRING e il nome del campo non è specificato dalla presenza dell’attributo &quot;@sqlname&quot;, il nome del campo nel database sarà automaticamente preceduto da una &quot;s&quot;. Questa modalità operativa sarà simile ai campi di tipo INTEGER (i), DOUBLE (d) e DATE (ts).

* **userEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;open&quot;. I valori dell’enumerazione possono essere definiti dall’utente nell’interfaccia.
* **visibleIf (stringa)**: definisce una condizione sotto forma di espressione XTK per mostrare o nascondere l&#39;attributo.

  >[!IMPORTANT]
  >
  >L’attributo è nascosto, ma è comunque possibile accedere ai relativi dati.

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

Esempio con un &quot;@applicableIf&quot;: l’attributo &quot;contiene&quot; viene creato solo se il numero di paesi è maggiore di 20.

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
