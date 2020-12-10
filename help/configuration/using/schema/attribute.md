---
solution: Campaign Classic
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 0%

---


# `<attribute>` element  {#attribute--element}

## Modello di contenuto {#content-model}

attribute:==help

## Attributi {#attributes}

_operation (stringa), advanced (booleano), applyIf (stringa), autoIncrement (booleano), membersTo (stringa), dataPolicy (stringa), dbEnum (stringa), defOnDuplicate (booleano), default (stringa), desc (stringa), enum (stringa), expr (stringa), feature (stringa), feature (stringa), featureDate (booleano) img (stringa), inout (stringa), label (stringa), length (stringa), localizable (booleano), name (MNTOKEN), notNull (booleano), pkgStatus (stringa), ref (stringa), Required (booleano), sqlDefault (stringa), sqlname (stringa), sqltable (stringa), target (mltable) NTOKEN), template (stringa), translateDefault (stringa), translateExpr (stringa), type (MNTOKEN), user (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano)

## Genitori {#parents}

`<element>`

## Bambini {#children}

`<help>`

## Descrizione {#description}

`<attribute>` consentono di definire un campo nel database.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use}

`<attribute>` gli elementi devono essere dichiarati in un  `<element>` elemento.

La sequenza in cui gli elementi `<attribute>` sono definiti in un `<srcschema>` non influenza la sequenza di creazione del campo nel database. La sequenza di creazione sarà in ordine alfabetico.

## Descrizione attributo {#attribute-description}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo è utilizzato principalmente per estendere gli schemi out-of-the-box.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che  Adobe Campaign recupererà l&#39;elemento senza aggiornarlo o generando un errore in caso contrario.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che  Adobe Campaign aggiornerà l&#39;elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che  Adobe Campaign inserirà l&#39;elemento senza verificarne l&#39;esistenza.
   * &quot;update&quot;: update. Ciò significa che  Adobe Campaign aggiornerà l&#39;elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che  Adobe Campaign recupererà ed eliminerà gli elementi.

* **advanced (booleano)**: quando questa opzione è attivata (@advanced=&quot;true&quot;), consente di nascondere l&#39;attributo nell&#39;elenco dei campi disponibili, accessibili per configurare un elenco in un modulo.
* **applyIf (stringa)**: questo attributo consente di rendere facoltativi i campi. L&#39;elemento `<attribute>` verrà preso in considerazione durante l&#39;aggiornamento del database quando il vincolo viene rispettato. &quot;applyIf&quot; riceve un&#39;espressione XTK.
* **autoIncrement (booleano)**: se questa opzione è attivata, il campo diventa un contatore. Questo consente di incrementare un valore (per la maggior parte ID). (uso esterno)
* **membersTo (stringa)**: prende il nome e lo spazio dei nomi della tabella che condivide il campo e compila lo schema in cui è dichiarato l&#39;attributo. (utilizzato solo in un `<schema>`).
* **dataPolicy (stringa)**: consente di specificare i vincoli di approvazione per i valori consentiti nel campo SQL o XML. I valori per questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: lettere maiuscole
   * &quot;lowerCase&quot;: Tutte le maiuscole
   * &quot;UpCase&quot;: maiuscolo
   * &quot;email&quot;: indirizzo e-mail
   * &quot;phone&quot;: numero di telefono
   * &quot;identifier&quot;: nome identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti in `<srcschema>`.
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
* **length (stringa)**: max numero di caratteri per un valore del campo SQL di tipo &quot;stringa&quot;. Se l&#39;attributo &quot;@length&quot; non è specificato,  Adobe Campaign crea automaticamente un campo per 255 caratteri.
* **localizzabile (booleano)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **name (MNTOKEN)**: nome dell&#39;attributo che corrisponderà al nome del campo nella tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e conforme ai vincoli di denominazione XML.

   Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente al nome del campo da  Adobe Campaign:

   * &quot;i&quot;: prefisso per il tipo &#39;integer&#39;.
   * &quot;d&quot;: per il tipo &#39;double&#39;.
   * &quot;s&quot;: per il tipo di stringa del carattere.
   * &quot;t&quot;: per il tipo &#39;date&#39;.

   Per definire completamente il nome del campo nella tabella, utilizzate l&#39;opzione &quot;@sqlname&quot; quando definite un attributo.

* **notNull (booleano)**: consente di ridefinire  comportamento di Adobe Campaign per quanto riguarda la gestione dei record NULL nel database. Per impostazione predefinita, i campi numerici non sono null e i campi stringa e tipo data possono essere null.
* **pkgStatus (stringa)**: durante le esportazioni del pacchetto, i valori vengono presi in considerazione a seconda del valore di &quot;@pkgStatus&quot;:

   * &quot;always&quot;: always present
   * &quot;never&quot;: never
   * &quot;default (or nothing)&quot;: il valore viene esportato tranne se è il valore predefinito o se non è un campo interno che non sarebbe compatibile con altre istanze.

* **ref (stringa)**: questo attributo definisce un riferimento a un  `<attribute>` elemento condiviso da più schemi (factoring di definizione). La definizione non viene copiata nello schema corrente.
* **obbligatorio (booleano)**: se questo attributo è attivato (@requirements=&quot;true&quot;), il campo è evidenziato nell&#39;interfaccia. L&#39;etichetta del campo sarà rossa nei moduli.
* **sql (booleano)**: se questo attributo è attivato (@sql=&quot;true&quot;), forza l&#39;archiviazione dell&#39;attributo SQL, anche quando l&#39;elemento che contiene l&#39;attributo ha la proprietà xml=&quot;true&quot;.
* **sqlDefault (stringa)**: questo attributo consente di definire il valore predefinito preso in considerazione per l&#39;aggiornamento del database se l&#39;attributo @notNull è attivato. Se questo attributo viene aggiunto dopo la creazione dell&#39;attributo, il comportamento dello schema non verrà modificato nemmeno per i nuovi record. Per modificare lo schema e aggiornare il valore dei nuovi record, è necessario eliminare e creare nuovamente l&#39;attributo.
* **sqlname (stringa)**: del campo durante la creazione della tabella. Se @sqlname non è specificato, per impostazione predefinita viene utilizzato il valore dell&#39;attributo &quot;@name&quot;. Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente a seconda del tipo di campo.
* **template (stringa)**: questo attributo definisce un riferimento a un  `<attribute>` elemento condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translateDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, l&#39;attributo &quot;@translateDefault&quot; consentirà di ridefinire un&#39;espressione che corrisponda a quella definita in @default, che verrà raccolta dallo strumento di traduzione (uso interno).
* **translateExpr (stringa)**: se è presente un attributo &quot;@expr&quot;, l&#39;attributo &quot;@translateExpr&quot; consente di ridefinire un&#39;espressione che corrisponda a quella definita in @expr, da raccogliere con lo strumento di traduzione (uso interno).
* **type (MNTOKEN)**: tipo di campo.

   I tipi di campo sono generici. A seconda del tipo di database installato,  Adobe Campaign modifica il tipo definito in un valore specifico per il database installato durante l&#39;aggiornamento della struttura.

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
   * orario
   * periodo
   * uuid

   Se l&#39;attributo &quot;@type&quot; viene lasciato vuoto, per impostazione predefinita  Adobe Campaign collegherà al campo una stringa di caratteri (STRING) con una lunghezza pari a 100.

   Se il campo è di tipo STRING e il nome del campo non è specificato dalla presenza dell&#39;attributo &quot;@sqlname&quot;, il nome del campo nel database sarà automaticamente preceduto da un nome &#39;s&#39;. Questa modalità operativa sarà simile a quella dei campi INTEGER (i), DOUBLE (d) e DATES (ts).

* **userEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;open&quot;. I valori dell&#39;enumerazione possono essere definiti dall&#39;utente nell&#39;interfaccia.
* **visibleIf (stringa)**: definisce una condizione sotto forma di espressione XTK per mostrare o nascondere l&#39;attributo.

   >[!IMPORTANT]
   >
   >L&#39;attributo è nascosto, ma è comunque possibile accedervi.

* **xml (booleano)**: se questa opzione è attivata, i valori del campo non hanno un campo SQL collegato.  Adobe Campaign crea un campo di tipo Testo &quot;mData&quot; per la memorizzazione dei record. Ciò significa che non è possibile filtrare o ordinare i campi.

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
