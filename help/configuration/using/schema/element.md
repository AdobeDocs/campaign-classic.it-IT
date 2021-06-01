---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# elemento {#element--element}

## Modello dei contenuti {#content-model-4}

element:===(attribute | stringa di calcolo | dbindex | default | elemento | aiuto | join | chiave | sysFilter | tradottoPredefinito)

## Attributi {#attributes-4}

_operation (stringa), advanced (booleano), aggregate (stringa), applyIf (stringa), autopk (booleano), ownedTo (stringa), convDate (stringa), dataPolicy (stringa), dataSource (stringa), dbEnum (stringa), defOnDuplicate (booleano), default (stringa), desc (stringa), displayAsField (booleano), does NotSupportDiff (booleano), edit (stringa), emptyKeyValue (stringa), enum (stringa), enumImage (stringa), expandSchemaTarget (stringa), expr (stringa), externalJoin (booleano), feature (stringa), featureDate (booleano), filterPath (stringa), folderLink (stringa), folderModel (stringa), folderProcess) string), fullLoad (booleano), gerarchico (booleano), gerarchicoPath (stringa), img (stringa), inout (stringa), integrità (stringa), etichetta (stringa), etichettaSingolare (stringa), lunghezza (stringa), localizzabile (booleano), nome (MNTOKEN), noDbIndex (booleano), noKey (booleano) Boolean), overflowtable (booleano), pkSequence (stringa), pkgStatus (stringa), ref (stringa), required (booleano), revAdvanced (booleano), revCardinality (stringa), revDesc (stringa), revExternalJoin (booleano), revIntegrity (stringa), revLabel (stringa), revLink (stringa), revTarget ), revVisibleIf (stringa), sql (booleano), sqlname (stringa), sqltable (stringa), tableSpace (stringa), tableSpaceIndex (stringa), target (MNTOKEN), template (stringa), temporaryTable (booleano), translateDefault (stringa), translateExpr (stringa), type (MNTOKEN), unbound) booleano), utente (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano), xmlChildren (booleano)

## Genitori {#parents-4}

`<srcschema>`

`<element>`

## Figli {#children-4}

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

## Descrizione {#description-4}

In Adobe Campaign sono disponibili quattro tipi di elementi `<element>`:

* Radice `<element>` : definisce il nome della tabella SQL corrispondente allo schema.
* Struttura `<element>` : definisce un gruppo di `<element>`   o   `<attribute>`    elementi.
* Collegamento `<element>` : definisce un collegamento. Questi elementi devono includere l’attributo &quot;@type=link&quot;.
* XML `<element>` : definisce un campo di tipo Testo &quot;mData&quot;. Questo elemento deve includere l&#39;attributo &quot;@type=xml&quot;.

## Descrizione dell&#39;attributo {#attribute-description-4}

* **_operazione (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo viene utilizzato principalmente per l’estensione degli schemi predefiniti.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che Adobe Campaign recupererà l’elemento senza aggiornarlo o genererà un errore se non esiste.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che Adobe Campaign aggiornerà l’elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che Adobe Campaign inserirà l’elemento senza verificare se esiste.
   * &quot;update&quot;: aggiornamento. Ciò significa che Adobe Campaign aggiornerà l’elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Questo significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **avanzato (booleano)**: quando questa opzione viene attivata (@advanced=&quot;true&quot;), consente di nascondere l&#39;attributo nell&#39;elenco dei campi disponibili, accessibili per configurare un elenco in un modulo.
* **aggregato (stringa)**: consente di copiare la definizione di un  `<element>`  tramite un altro schema. Questo attributo riceve una dichiarazione di schema sotto forma di &quot;namespace:name&quot;.
* **applyIf (string)**: condizione per l&#39;applicazione dell&#39;indice. Questo attributo riceve un&#39;espressione XTK.
* **autopk (booleano)**: se questa opzione è attivata (autopk=&quot;true&quot;), viene automaticamente definita una chiave univoca. Questa opzione può essere utilizzata solo sull&#39;elemento principale dello schema. Attenzione, Adobe Campaign garantisce solo che la chiave generata sia univoca. Non è garantito che i valori chiave siano consecutivi e incrementali.
* **dataPolicy (stringa)**: consente di specificare i vincoli di approvazione per i valori consentiti nel campo SQL. I valori di questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: maiuscolo
   * &quot;lowerCase&quot;: tutte le lettere minuscole
   * &quot;UpperCase&quot;: maiuscolo
   * &quot;email&quot;: indirizzo e-mail
   * &quot;telefono&quot;: numero di telefono
   * &quot;identifier&quot;: nome identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti in `<srcschema>`.
* **defOnDuplicate (booleano)**: se questo attributo viene attivato, quando un record viene duplicato, il valore predefinito (definito in @default) viene automaticamente riapplicato al record.
* **predefinito (stringa)**: consente di definire il comportamento degli elementi (chiamata a una funzione, valore predefinito). Questo attributo riceve un&#39;espressione XTK.
* **desc (stringa)**: consente di inserire una descrizione dell’elemento. Questa descrizione viene visualizzata nella barra di stato dell’interfaccia.
* **displayAsField (booleano)**: se questo attributo è attivato, un tipo di &quot;collegamento&quot;  `<element>`  verrà visualizzato come campo nella vista ad albero degli schemi (&quot;Struttura&quot; scheda). In questo modo, è possibile visualizzare un collegamento come campo locale e modificarlo durante una query. Quando l’elemento viene trovato nella SELEZIONE di una query, viene utilizzato il valore della destinazione del collegamento. Quando l’elemento si trova nel punto in cui si trova una query, verrà utilizzata la chiave sottostante del collegamento.
* **modifica (stringa)**: questo attributo specifica il tipo di input che verrà utilizzato nel modulo collegato allo schema.
* **enum (stringa)**: riceve il nome dell&#39;enumerazione collegata al campo. L&#39;enumerazione può essere inserita nello stesso schema o in uno schema remoto.
* **expr (stringa)**: questo attributo definisce un campo calcolato per il quale non è memorizzata alcuna definizione nella tabella. Riceve un’espressione Xpath o XTK (string).
* **externalJoin (booleano)**: join esterno in un elemento di tipo &quot;link&quot;.
* **feature (stringa)**: definisce un campo delle caratteristiche: Questi campi vengono utilizzati per estendere i dati in una tabella esistente, ma con memorizzazione in una tabella allegata. I valori accettati sono:

   * &quot;shared&quot;: il contenuto viene memorizzato in una tabella condivisa per tipo di dati
   * &quot;dedicato&quot;: il contenuto viene memorizzato in una tabella dedicata

   Le tabelle delle caratteristiche SQL vengono create automaticamente in base al tipo di caratteristica:

   * dedicato: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * condiviso: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Esistono due tipi di campi con caratteristiche: campi semplici in cui è autorizzato un singolo valore sui campi caratteristici e a scelta multipla, in cui la caratteristica è collegata a un elemento di raccolta che può contenere più valori.

   Quando una caratteristica è definita in uno schema, questo schema deve avere una chiave principale basata su un singolo campo (le chiavi composite non sono autorizzate).

* **featureDate (booleano)**: attributo collegato al campo delle caratteristiche &quot;@feature&quot;. Se il suo valore è &quot;true&quot;, ti consente di sapere quando è stato aggiornato l’ultimo valore.
* **filterPath (stringa)**: questo attributo riceve un percorso Xpath e consente di definire un filtro su un campo.
* **folderLink (stringa)**: questo attributo riceve il nome del collegamento che consente di recuperare i file contenenti entità.
* **folderModel (stringa)**: definisce il tipo di cartella che consente l’archiviazione delle entità. Questo attributo è definito solo se è presente &quot;@folderLink&quot;.
* **folderProcess (stringa)**: definisce il collegamento in cui vengono memorizzate le istanze del modello di entità. Questo attributo è definito solo se è presente &quot;@folderLink&quot;.
* **fullLoad (booleano)**: questo attributo forza la visualizzazione di tutti i record di una tabella durante la selezione dei campi in un modulo.
* **img (stringa)**: riceve il percorso di un’immagine collegata a un elemento. Il valore di questo attributo è di tipo &quot;namespace:image name&quot;. Ad esempio: img=&quot;cus:myImage.jpg&quot;. Fisicamente, l&#39;immagine deve essere importata nel server dell&#39;applicazione.
* **integrità (stringa)**: integrità referenziale dell&#39;occorrenza della tabella sorgente verso la tabella di destinazione.

   I valori accessibili sono:

   * &quot;define&quot;: Adobe Campaign non elimina l’entità se viene fatto riferimento tramite il collegamento
   * &quot;normale&quot;: l&#39;eliminazione dell&#39;occorrenza di origine inizializza le chiavi del collegamento sull&#39;occorrenza di destinazione (modalità predefinita), questo tipo di integrità inizializza tutte le chiavi esterne
   * &quot;own&quot;: l&#39;eliminazione dell&#39;occorrenza di origine attiva l&#39;eliminazione dell&#39;occorrenza di destinazione
   * &quot;owncopy&quot;: simile a &quot;own&quot; (in caso di eliminazione) o duplica gli eventi (in caso di duplicazione)
   * &quot;neutro&quot;: non fa nulla

* **etichetta (stringa)**: etichetta elemento.
* **labelSingular (stringa)**: etichetta (forma singolare) dell’elemento utilizzato in alcune parti dell’interfaccia.
* **lunghezza (stringa)**: max numero di caratteri autorizzati per un valore del campo SQL di tipo &quot;stringa&quot;.
* **localizzabile (booleano)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell&#39;attributo &quot;@label&quot; per la traduzione (uso interno).
* **nome (MNTOKEN)**: nome interno dell’elemento che corrisponde al nome della tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e deve essere conforme ai vincoli di denominazione collegati a XML.

   Quando lo schema viene scritto nel database, i prefissi vengono aggiunti automaticamente al nome del campo da Adobe Campaign.

   * &quot;i&quot;: prefisso del tipo &quot;integer&quot;.
   * &quot;d&quot;: prefisso del tipo &quot;doppio&quot;.
   * &quot;s&quot;: Prefisso per il tipo di stringa di caratteri.
   * &quot;ts&quot;: prefisso del tipo &quot;date&quot;.

   Per definire il nome della tabella in modo autonomo, devi utilizzare l’attributo &quot;@sqltable&quot; nella definizione dell’elemento dello schema principale.

* **noDbIndex (booleano)**: consente di specificare che l’elemento non verrà indicizzato.
* **ordered (booleano)**: se l’attributo è attivato (ordered=&quot;true&quot;), Adobe Campaign mantiene la sequenza di dichiarazione dell’elemento in un elemento di raccolta XML.
* **pkSequence (stringa)**: riceve il nome della sequenza da utilizzare per il calcolo di una chiave incrementale automatica. Questo attributo può essere utilizzato solo se è definita una chiave automatica incrementale sull&#39;elemento principale dello schema.
* **pkgStatus (stringa)**: durante le esportazioni dei pacchetti, i valori saranno presi in considerazione in funzione del valore di questo attributo:

   * &quot;always&quot;: l’elemento sarà sempre presente
   * &quot;never&quot;: l’elemento non sarà mai presente
   * &quot;predefinito (o nullo)&quot;: l’elemento viene esportato a meno che non sia l’elemento predefinito o se non è un campo interno e non sia compatibile con altre istanze

* **ref (stringa)**: questo attributo definisce un riferimento a un elemento >element> condiviso da diversi schemi (factoring di definizione). La definizione non viene copiata nello schema corrente.
* **obbligatorio (booleano)**: se questo attributo viene attivato (@required=&quot;true&quot;), il campo viene evidenziato nell’interfaccia di . Nei moduli l’etichetta del campo sarà rossa.
* **revAdvanced (booleano)**: quando attivato, questo attributo specifica che il collegamento opposto è un collegamento &quot;avanzato&quot;.
* **revCardinality (stringa)**: questo attributo definisce la cardinalità di un collegamento tra due tabelle. Viene utilizzato in un tipo &quot;link&quot; `<element>`.

   I valori possibili sono:

   * &quot;single&quot; : Collegamento semplice da 1 a 1 tipo
   * &quot;unbound&quot;: Collegamento raccolta tipi 1-N

   Per impostazione predefinita, se l’attributo non è specificato durante la creazione del collegamento, la cardinalità sarà 1-N.

* **revDesc (stringa)**: questo attributo riceve una descrizione collegata al collegamento opposto.
* **revExternalJoin (booleano)**: quando attivato, questo attributo consente di forzare l’unione esterna sul collegamento opposto.
* **revIntegrity (stringa)**: questo attributo definisce l’integrità dello schema di destinazione. Gli stessi valori dell&#39;attributo &quot;@Integrity&quot; sono autorizzati. Per impostazione predefinita, Adobe Campaign assegna il valore &quot;normale&quot; a questo attributo.
* **revLabel (stringa)**: etichetta del link opposto.
* **revLink (stringa)**: nome del link opposto. Se il valore è &quot;_NONE_&quot;, non verrà creato alcun collegamento opposto nello schema di destinazione.
* **revTarget (stringa)**: destinazione del link opposto.
* **sql (booleano)**: se questo attributo è attivato (@sql=&quot;true&quot;), forza l&#39;archiviazione dell&#39;elemento SQL, anche se l&#39;elemento ha la proprietà xml=&quot;true&quot;.
* **sqlname (stringa)**: nome del campo durante la creazione della tabella. Se &quot;@sqlname&quot; non è specificato, il valore dell&#39;attributo &quot;@name&quot; viene utilizzato per impostazione predefinita. Quando si scrive lo schema nella tabella, i prefissi vengono aggiunti automaticamente a seconda del tipo di campo.
* **sqltable (stringa)**: per l&#39;elemento principale dello schema, questo attributo sovrascrive il nome della tabella SQL generata per impostazione predefinita. Se &quot;@sqltable&quot; non è specificato, il nome predefinito sarà strutturato in questo modo: namespace (maiuscolo lettera) seguito dal valore dello SrcSchema &quot;@name&quot;.
* **tableSpace (stringa)**: questo attributo consente di specificare una nuova tablespace di archiviazione dati per una tabella (valida nella directory principale  `<element>`).
* **tableSpaceIndex (stringa)**: questo attributo consente di specificare una nuova tablespace di memorizzazione dell&#39;indice per una tabella (valida nella radice  `<element>`).
* **target (MNTOKEN)**: riceve il nome dello schema di destinazione durante la creazione di un collegamento tra tabelle. Questo attributo è attivo solo per gli elementi di tipo &quot;link&quot;.
* **template (stringa)**: questo attributo definisce un riferimento a un  `<element>` elemento condiviso da diversi schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translateDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, il &quot;@translateDefault&quot; ti permetterà di ridefinire un&#39;espressione che corrisponda a quella definita in @default, da raccogliere dallo strumento di traduzione (uso interno).
* **translateExpr (stringa)**: se viene trovato un attributo &quot;@expr&quot;, l’attributo &quot;@translateExpr&quot; ti consente di ridefinire un’espressione corrispondente a quella definita in &quot;@expr&quot; e che verrà raccolta dallo strumento di traduzione (uso interno).
* **tipo (MNTOKEN)**: definisce il tipo di dati memorizzati nell’elemento.

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
   * collegamento
   * long
   * promemoria
   * MNTOKEN
   * percentuale
   * primarykey
   * short
   * string
   * orario
   * timespan
   * uuid

* **non associato (booleano)**: se l’attributo è attivato (unbound=&quot;true&quot;), il collegamento viene dichiarato come elemento di raccolta per una cardinalità 1-N.
* **userEnum (stringa)**: riceve il nome interno di un&#39;enumerazione &quot;open&quot;. I valori di enumerazione possono essere definiti dall’utente nell’interfaccia di .
* **xml (booleano)**: se questa opzione è attivata, tutti i valori definiti nell&#39;elemento sono memorizzati in XML in un campo di tipo TESTO &quot;mData&quot;. Ciò significa che non vi saranno filtri o ordinamento su questi campi.
* **xmlChildren (booleano)**: forza l&#39;archiviazione per ogni bambino (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
