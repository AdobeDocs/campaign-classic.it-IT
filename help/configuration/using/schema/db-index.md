---
product: campaign
title: Elementi e attributi
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---

# elemento dbindex {#dbindex--element}

## Modello dei contenuti {#content-model-3}

dbindex:==keyfield

## Attributi {#attributes-3}

* @_operation (stringa)
* @applyIf (stringa)
* @label (stringa)
* @name (MNTOKEN)
* @unique (booleano)

## Genitori {#parents-3}

`<element>`

## Figli {#children-3}

`<keyfield>`

## Descrizione {#description-3}

Questo elemento ti consente di definire un indice collegato a una tabella.

## Uso e contesto di utilizzo {#use-and-context-of-use-3}

È possibile definire diversi indici. Un indice può fare riferimento a uno o più campi della tabella. La dichiarazione dell&#39;indice di solito segue la definizione dell&#39;elemento dello schema principale.

L&#39;ordine degli elementi `<keyfield>` definiti in un `<dbindex>` è molto importante. Il primo `<keyfield>` deve essere il criterio di indicizzazione su cui si basano principalmente le query.

Il nome dell’indice nel database viene calcolato concatenando il nome della tabella e il nome dell’indice. Ad esempio: Nome della tabella &quot;Sample&quot;, spazio dei nomi &quot;Cus&quot;, nome dell&#39;indice &quot;MyIndex&quot;-> nome del campo dell&#39;indice durante la creazione dell&#39;indice che richiede: &quot;CusSample_myIndex&quot;.

## Descrizione dell&#39;attributo {#attribute-description-3}

* **_operazione (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo viene utilizzato principalmente per l’estensione degli schemi predefiniti.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che Adobe Campaign recupererà l’elemento senza aggiornarlo o genererà un errore se non esiste.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che Adobe Campaign aggiornerà l’elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che Adobe Campaign inserirà l’elemento senza verificare se esiste.
   * &quot;update&quot;: aggiornamento. Ciò significa che Adobe Campaign aggiornerà l’elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Questo significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **applyIf (string)**: condizione per tenere conto dell&#39;indice - riceve un&#39;espressione XTK.
* **etichetta (stringa)**: etichetta dell&#39;indice.
* **nome (MNTOKEN)**: nome di indice univoco.
* **univoco (booleano)**: se questa opzione è attivata (@unique=&quot;true&quot;), l’attributo garantisce l’univocità dell’indice in tutti i campi.

## Esempi {#examples-3}

Creazione di un indice sul campo &quot;id&quot;. (l&#39;attributo &quot;@unique&quot; sull&#39;elemento `<dbindex>` attiva l&#39;aggiunta della parola chiave SQL &quot;UNIQUE&quot; quando l&#39;indice viene creato nel database (query)).

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
