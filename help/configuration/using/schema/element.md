---
product: campaign
title: 'Elementi e attributi dello schema: elemento'
description: elemento
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---

# elemento {#element--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-4}

element:==(attribute) | stringa di calcolo | dbindex | predefinito | elemento | aiuto | unire | chiave | sysFilter | translationDefault)

## Attributi {#attributes-4}

_operation (stringa), advanced (booleano), aggregate (stringa), applyIf (stringa), autopk (booleano), membersTo (stringa), convDate (stringa), dataPolicy (stringa), dataSource (stringa), dbEnum (stringa), defOnDuplicate (booleano), default (stringa), desc (stringa), displayAsField (booleano), doesNotSupportDiff (booleano), edit (stringa), emptyKeyValue (stringa), enum (stringa), enumImage (stringa), expandTargetSchema string), expr (string), externalJoin (booleano), feature (string), featureDate (booleano), filterPath (string), folderLink (string), folderModel (string), folderProcess (string), fullLoad (booleano), hierarchical (booleano), hierarchicalPath (string), img (string), inout (string), integrity (string), label (string), labelSingular (string), length (string), localizable (booleano), name (MNTOKEN), noDbIndex (booleano), no (booleano), ordered (booleano), overflowtable (booleano), pkSequence (stringa), pkgStatus (stringa), ref (stringa), required (booleano), revAdvanced (booleano), revCardinality (stringa), revDesc (stringa), revExternalJoin (booleano), revIntegrity (stringa), revLabel (stringa), revLink (stringa), revTarget (stringa), revVisibleIf (stringa), sql (booleano), sqlname (stringa) (stringa), tableSpace (stringa), tableSpaceIndex (stringa), target (MNTOKEN), template (stringa), temporaryTable (booleano), translDefault (stringa), translExpr (stringa), type (MNTOKEN), unbound (booleano), user (booleano), userEnum (stringa), visibleIf (stringa), xml (booleano), xmlChildren (booleano)

## Padri {#parents-4}

`<srcschema>`

`<element>`

## Elementi figli {#children-4}

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

Esistono quattro tipi di `<element>`  elementi in Adobe Campaign:

* Directory principale `<element>`  : definisce il nome della tabella SQL che corrisponde allo schema.
* Struttura `<element>`  : definisce un gruppo di  `<element>`   o   `<attribute>`    elementi.
* Collegamento `<element>`  : definisce un collegamento. Questi elementi devono includere l’attributo &quot;@type=link&quot;.
* XML `<element>`  : definisce un campo &quot;mData&quot; di tipo Testo. Questo elemento deve includere l’attributo &quot;@type=xml&quot;.

## Descrizione attributo {#attribute-description-4}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

  Questo attributo viene utilizzato principalmente quando si estendono schemi predefiniti.

  I valori accessibili sono:

   * &quot;Nessuno&quot;: la riconciliazione da sola. Ciò significa che Adobe Campaign recupererà l’elemento senza aggiornarlo o genererà un errore, se non esiste.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che Adobe Campaign aggiornerà l’elemento o lo creerà se non esiste.
   * &quot;insert&quot;: insertion Ciò significa che Adobe Campaign inserirà l’elemento senza verificarne l’esistenza.
   * &quot;update&quot; (aggiorna): aggiornamento. Ciò significa che Adobe Campaign aggiornerà l’elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **avanzato (booleano)**: quando questa opzione è attivata (@advanced=&quot;true&quot;), consente di nascondere l’attributo nell’elenco dei campi disponibili accessibili per la configurazione di un elenco in un modulo.
* **aggregato (stringa)**: consente di copiare la definizione di un’ `<element>`  tramite un altro schema. Questo attributo riceve una dichiarazione dello schema sotto forma di &quot;namespace:name&quot;.
* **applyIf (stringa)**: condizione per applicare l’indice. Questo attributo riceve un&#39;espressione XTK.
* **autopk (booleano)**: se questa opzione è attivata (autopk=&quot;true&quot;), viene automaticamente definita una chiave univoca. Questa opzione può essere utilizzata solo sull’elemento principale dello schema. Attenzione: Adobe Campaign garantisce solo che la chiave generata sia univoca. Non è garantito che i valori chiave siano consecutivi e incrementali.
* **dataPolicy (stringa)**: consente di specificare i vincoli di approvazione per i valori consentiti nel campo SQL. I valori per questo attributo sono:

   * &quot;none&quot;: nessun valore
   * &quot;smartCase&quot;: prime lettere maiuscole
   * &quot;lowerCase&quot;: tutte minuscole
   * &quot;upperCase&quot;: tutte maiuscole
   * &quot;email&quot;: indirizzo e-mail
   * &quot;phone&quot;: numero di telefono
   * &quot;identifier&quot;: nome dell’identificatore
   * &quot;resIdentifier&quot;: nome file

* **dbEnum (stringa)**: riceve il nome interno di un’enumerazione &quot;chiusa&quot;. I valori di enumerazione devono essere definiti nella `<srcschema>`.
* **defOnDuplicate (booleano)**: se questo attributo è attivato, quando un record viene duplicato il valore predefinito (definito in @default) viene riapplicato automaticamente al record.
* **impostazione predefinita (stringa)**: consente di definire il comportamento dell’elemento (chiamata a una funzione, valore predefinito). Questo attributo riceve un&#39;espressione XTK.
* **desc (stringa)**: ti consente di inserire una descrizione dell’elemento. Questa descrizione viene visualizzata nella barra di stato dell’interfaccia.
* **displayAsField (booleano)**: se questo attributo è attivato, è necessario un tipo &quot;link&quot; `<element>`  verrà visualizzato come campo nella struttura degli schemi (scheda &quot;Struttura&quot;). In questo modo, è possibile visualizzare un collegamento come campo locale e modificarne il comportamento durante una query. Quando l’elemento viene trovato nella SELECT di una query, verrà utilizzato il valore della destinazione del collegamento. Quando l’elemento viene trovato nel WHERE di una query, viene utilizzata la chiave sottostante del collegamento.
* **modifica (stringa)**: questo attributo specifica il tipo di input che verrà utilizzato nel modulo collegato allo schema.
* **enum (stringa)**: riceve il nome dell’enumerazione collegata al campo. L’enumerazione può essere inserita nello stesso schema o in uno schema remoto.
* **expr (stringa)**: questo attributo definisce un campo calcolato per il quale non è memorizzata alcuna definizione nella tabella. Riceve un’espressione Xpath o XTK (stringa).
* **externalJoin (booleano)**: join esterno in un elemento di tipo &quot;link&quot;.
* **feature (stringa)**: definisce un campo delle caratteristiche: questi campi vengono utilizzati per estendere i dati in una tabella esistente, ma con la memorizzazione in una tabella allegata. I valori accettati sono:

   * &quot;shared&quot; (condiviso): il contenuto viene memorizzato in una tabella condivisa per tipo di dati
   * &quot;dedicato&quot;: il contenuto viene memorizzato in una tabella dedicata

  Le tabelle delle caratteristiche SQL vengono create automaticamente in base al tipo di caratteristica:

   * dedicato: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * condiviso: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Esistono due tipi di campi delle caratteristiche: campi semplici in cui è autorizzato un singolo valore sulla caratteristica e campi a scelta multipla in cui la caratteristica è collegata a un elemento di raccolta che può contenere più valori.

  Quando una caratteristica è definita in uno schema, questo schema deve avere una chiave principale basata su un singolo campo (le chiavi composite non sono autorizzate).

* **featureDate (booleano)**: attributo collegato al campo @feature delle caratteristiche. Se il suo valore è &quot;true&quot;, ti consente di scoprire quando è stato aggiornato l’ultima volta il valore.
* **filterPath (stringa)**: questo attributo riceve un Xpath e ti consente di definire un filtro per un campo.
* **folderLink (stringa)**: questo attributo riceve il nome del collegamento che consente di recuperare i file contenenti le entità.
* **folderModel (stringa)**: definisce il tipo di cartella che abilita l’archiviazione delle entità. Questo attributo è definito solo se è presente &quot;@folderLink&quot;.
* **folderProcess (stringa)**: definisce il collegamento in cui vengono memorizzate le istanze del modello di entità. Questo attributo è definito solo se è presente &quot;@folderLink&quot;.
* **fullLoad (booleano)**: questo attributo forza la visualizzazione di tutti i record di una tabella durante la selezione dei campi in un modulo.
* **img (stringa)**: riceve il percorso di un’immagine collegata a un elemento. Il valore di questo attributo è del tipo &quot;namespace:image name&quot;. Ad esempio: img=&quot;cus:myImage.jpg&quot;. A livello fisico, l&#39;immagine deve essere importata nel server applicazioni.
* **integrità (stringa)**: integrità referenziale dell’occorrenza della tabella sorgente verso la tabella di destinazione.

  I valori accessibili sono:

   * &quot;define&quot;: Adobe Campaign non elimina l’entità se vi si fa riferimento tramite il collegamento
   * &quot;normal&quot;: l’eliminazione dell’occorrenza sorgente inizializza le chiavi del collegamento nell’occorrenza target (modalità predefinita). questo tipo di integrità inizializza tutte le chiavi esterne
   * &quot;own&quot;: l’eliminazione dell’occorrenza sorgente attiva l’eliminazione dell’occorrenza target
   * &quot;owncopy&quot;: simile a &quot;own&quot; (in caso di eliminazione) o che duplica le occorrenze (in caso di duplicazione)
   * &quot;neutro&quot;: non esegue alcuna operazione

* **etichetta (stringa)**: etichetta elemento.
* **labelSingular (stringa)**: etichetta (forma singolare) dell’elemento utilizzato in alcune parti dell’interfaccia.
* **length (stringa)**: max numero di caratteri autorizzati per un valore del campo SQL di tipo &quot;stringa&quot;.
* **localizzabile (booleano)**: se è attivato, questo attributo indica allo strumento di raccolta di recuperare il valore dell’attributo &quot;@label&quot; per la traduzione (uso interno).
* **nome (MNTOKEN)**: nome interno dell’elemento che corrisponde al nome della tabella. Il valore dell&#39;attributo &quot;@name&quot; deve essere breve, preferibilmente in inglese, e deve essere conforme ai vincoli di denominazione collegati a XML.

  Quando lo schema viene scritto nel database, Adobe Campaign aggiunge automaticamente i prefissi al nome del campo.

   * &quot;i&quot;: prefisso per il tipo &#39;integer&#39;.
   * &quot;d&quot;: prefisso per il tipo &quot;double&quot;.
   * &quot;s&quot;: prefisso per il tipo di stringa di caratteri.
   * &quot;ts&quot;: prefisso per il tipo &quot;date&quot;.

  Per definire il nome della tabella in modo autonomo, è necessario utilizzare l&#39;attributo &quot;@sqltable&quot; nella definizione dell&#39;elemento dello schema principale.

* **noDbIndex (booleano)**: consente di specificare che l’elemento non sarà indicizzato.
* **ordinato (booleano)**: se l’attributo è attivato (ordered=&quot;true&quot;), Adobe Campaign mantiene la sequenza di dichiarazione dell’elemento in un elemento di raccolta XML.
* **pkSequence (stringa)**: riceve il nome della sequenza da utilizzare per calcolare una chiave incrementale automatica. Questo attributo può essere utilizzato solo se è definita una chiave incrementale automatica sull’elemento principale dello schema.
* **pkgStatus (stringa)**: durante le esportazioni dei pacchetti, i valori vengono presi in considerazione in funzione del valore di questo attributo:

   * &quot;always&quot;: l’elemento sarà sempre presente
   * &quot;mai&quot;: l’elemento non sarà mai presente
   * &quot;default (or Nothing)&quot;: l’elemento viene esportato a meno che non sia l’elemento predefinito o se non è un campo interno e non è compatibile con altre istanze

* **ref (stringa)**: questo attributo definisce un riferimento a un elemento >element> condiviso da più schemi (factoring di definizione). La definizione non viene copiata nello schema corrente.
* **obbligatorio (booleano)**: se questo attributo è attivato (@required=&quot;true&quot;), il campo viene evidenziato nell’interfaccia. L’etichetta del campo sarà rossa nei moduli.
* **revAdvanced (booleano)**: quando è attivato, questo attributo specifica che il collegamento opposto è un collegamento &quot;avanzato&quot;.
* **revCardinality (stringa)**: questo attributo definisce la cardinalità di un collegamento tra due tabelle. Viene utilizzato in un tipo &quot;link&quot; `<element>`.

  I valori possibili sono:

   * &quot;single&quot; : collegamento semplice di tipo 1-1
   * &quot;unbound&quot;: collegamento per raccolta di tipo 1-N

  Per impostazione predefinita, se l’attributo non è specificato durante la creazione del collegamento, la cardinalità sarà 1-N.

* **revDesc (stringa)**: questo attributo riceve una descrizione collegata al collegamento opposto.
* **revExternalJoin (booleano)**: quando è attivato, questo attributo ti consente di forzare il join esterno sul collegamento opposto.
* **revIntegrity (stringa)**: questo attributo definisce l’integrità dello schema di destinazione. Sono autorizzati gli stessi valori dell’attributo &quot;@integrity&quot;. Per impostazione predefinita, Adobe Campaign assegna il valore &quot;normale&quot; a questo attributo.
* **revLabel (stringa)**: etichetta del collegamento opposto.
* **revLink (stringa)**: nome del collegamento opposto. Se il valore è &quot;_NESSUNO_&quot;, non verrà creato alcun collegamento opposto nello schema di destinazione.
* **revTarget (stringa)**: destinazione del collegamento opposto.
* **sql (booleano)**: se questo attributo è attivato (@sql=&quot;true&quot;), forza l’archiviazione dell’elemento SQL, anche se l’elemento ha la proprietà xml=&quot;true&quot;.
* **sqlname (stringa)**: nome del campo durante la creazione della tabella. Se &quot;@sqlname&quot; non è specificato, il valore dell&#39;attributo &quot;@name&quot; viene utilizzato per impostazione predefinita. Quando si scrive lo schema nella tabella, i prefissi vengono aggiunti automaticamente a seconda del tipo di campo.
* **sqltable (stringa)**: per l’elemento principale dello schema, questo attributo sovrascrive il nome della tabella SQL generata per impostazione predefinita. Se &quot;@sqltable&quot; non è specificato, il nome predefinito sarà strutturato in questo modo: namespace (prima lettera maiuscola) seguito dal valore di SrcSchema &quot;@name&quot;.
* **tableSpace (stringa)**: questo attributo consente di specificare una nuova tablespace di archiviazione dati per una tabella (valida nella directory principale) `<element>`).
* **tableSpaceIndex (stringa)**: questo attributo consente di specificare una nuova tablespace di archiviazione dell’indice per una tabella (valida nella directory principale) `<element>`).
* **target (MNTOKEN)**: riceve il nome dello schema di destinazione durante la creazione di un collegamento tra tabelle. Questo attributo è attivo solo per gli elementi di tipo &quot;link&quot;.
* **modello (stringa)**: questo attributo definisce un riferimento a un `<element>` condiviso da più schemi. La definizione viene copiata automaticamente nello schema corrente.
* **translDefault (stringa)**: se viene trovato un attributo &quot;@default&quot;, il &quot;@translatedDefault&quot; ti consente di ridefinire un’espressione che corrisponda a quella definita in @default, e che deve essere raccolta dallo strumento di traduzione (uso interno).
* **translExpr (stringa)**: se viene trovato un attributo &quot;@expr&quot;, l’attributo &quot;@translatedExpr&quot; ti consente di ridefinire un’espressione corrispondente a quella definita in &quot;@expr&quot; e che verrà raccolta dallo strumento di traduzione (uso interno).
* **tipo (MNTOKEN)**: definisce il tipo di dati memorizzati nell’elemento.

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

* **non associato (booleano)**: se l’attributo è attivato (unbound=&quot;true&quot;), il collegamento viene dichiarato come elemento di raccolta per una cardinalità 1-N.
* **userEnum (stringa)**: riceve il nome interno di un’enumerazione &quot;open&quot;. I valori di enumerazione possono essere definiti dall’utente nell’interfaccia.
* **xml (booleano)**: se questa opzione è attivata, tutti i valori definiti nell’elemento vengono memorizzati in XML in un campo di tipo TEXT &quot;mData&quot;. Ciò significa che non ci saranno filtri o ordinamenti su questi campi.
* **xmlChildren (booleano)**: forza la memorizzazione per ogni elemento figlio ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
