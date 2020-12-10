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
source-wordcount: '337'
ht-degree: 2%

---


# `<dbindex>` element  {#dbindex--element}

## Modello di contenuto {#content-model-3}

dbindex:==keyfield

## Attributi {#attributes-3}

* @_operation (stringa)
* @applyIf (stringa)
* @label (stringa)
* @name (MNTOKEN)
* @univoche (booleano)

## Genitori {#parents-3}

`<element>`

## Bambini {#children-3}

`<keyfield>`

## Descrizione {#description-3}

Questo elemento consente di definire un indice collegato a una tabella.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-3}

È possibile definire diversi indici. Un indice può fare riferimento a uno o più campi della tabella. La dichiarazione dell&#39;indice in genere segue la definizione dell&#39;elemento dello schema principale.

L&#39;ordine degli elementi `<keyfield>` definiti in un `<dbindex>` è molto importante. Il primo `<keyfield>` deve essere il criterio di indicizzazione su cui si basano principalmente le query.

Il nome dell&#39;indice nel database viene calcolato concatenando il nome della tabella e il nome dell&#39;indice. Ad esempio: Nome tabella &quot;Sample&quot;, spazio dei nomi &quot;Cus&quot;, nome indice &quot;MyIndex&quot;-> nome del campo indice durante la creazione dell&#39;indice durante la query: &quot;CusSample_myIndex&quot;.

## Descrizione attributo {#attribute-description-3}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

   Questo attributo è utilizzato principalmente per estendere gli schemi out-of-the-box.

   I valori accessibili sono:

   * &quot;none&quot;: solo riconciliazione. Ciò significa che  Adobe Campaign recupererà l&#39;elemento senza aggiornarlo o generando un errore in caso contrario.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che  Adobe Campaign aggiornerà l&#39;elemento o lo creerà se non esiste.
   * &quot;insert&quot;: inserimento. Ciò significa che  Adobe Campaign inserirà l&#39;elemento senza verificarne l&#39;esistenza.
   * &quot;update&quot;: update. Ciò significa che  Adobe Campaign aggiornerà l&#39;elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che  Adobe Campaign recupererà ed eliminerà gli elementi.

* **applyIf (stringa)**: condizione per tenere conto dell&#39;indice - riceve un&#39;espressione XTK.
* **label (stringa)**: index label.
* **name (MNTOKEN)**: nome di indice univoco.
* **univoco (booleano)**: se questa opzione è attivata (@univoche=&quot;true&quot;), l&#39;attributo garantisce l&#39;univocità dell&#39;indice in tutti i campi.

## Esempi {#examples-3}

Creazione di un indice nel campo &quot;id&quot;. (l&#39;attributo &quot;@Unique&quot; sull&#39;elemento `<dbindex>` attiva l&#39;aggiunta della parola chiave SQL &quot;UNIQUE&quot; quando l&#39;indice viene creato nel database (query)).

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
