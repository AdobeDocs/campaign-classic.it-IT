---
product: campaign
title: Elementi e attributi - elemento dbindex
description: elemento dbindex
feature: Schema Extension
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# elemento dbindex {#dbindex--element}


## Modello di contenuto {#content-model-3}

dbindex:==keyfield

## Attributi {#attributes-3}

* @_operation (stringa)
* @applicableIf (stringa)
* @label (stringa)
* @name (MNTOKEN)
* @unique (boolean)

## Padri {#parents-3}

`<element>`

## Elementi secondari {#children-3}

`<keyfield>`

## Descrizione {#description-3}

Questo elemento ti consente di definire un indice collegato a una tabella.

## Uso e contesto di utilizzo {#use-and-context-of-use-3}

È possibile definire diversi indici. Un indice può fare riferimento a uno o più campi della tabella. La dichiarazione dell’indice segue in genere la definizione dell’elemento dello schema principale.

L&#39;ordine degli elementi `<keyfield>` definiti in un `<dbindex>` è molto importante. Il primo `<keyfield>` deve essere il criterio di indicizzazione su cui si basano principalmente le query.

Il nome dell&#39;indice nel database viene calcolato concatenando il nome della tabella e il nome dell&#39;indice. Ad esempio: nome della tabella &quot;Sample&quot;, spazio dei nomi &quot;Cus&quot;, nome dell’indice &quot;MyIndex&quot;-> nome del campo dell’indice durante la creazione dell’indice query: &quot;CusSample_myIndex&quot;.

## Descrizione attributo {#attribute-description-3}

* **_operation (stringa)**: definisce il tipo di scrittura nel database.

  Questo attributo viene utilizzato principalmente quando si estendono schemi predefiniti.

  I valori accessibili sono:

   * &quot;Nessuno&quot;: la riconciliazione da sola. Ciò significa che Adobe Campaign recupererà l’elemento senza aggiornarlo o genererà un errore, se non esiste.
   * &quot;insertOrUpdate&quot;: aggiornamento con inserimento. Ciò significa che Adobe Campaign aggiornerà l’elemento o lo creerà se non esiste.
   * &quot;insert&quot;: insertion Ciò significa che Adobe Campaign inserirà l’elemento senza verificarne l’esistenza.
   * &quot;update&quot; (aggiorna): aggiornamento. Ciò significa che Adobe Campaign aggiornerà l’elemento o genererà un errore se non esiste.
   * &quot;delete&quot;: eliminazione. Ciò significa che Adobe Campaign recupererà ed eliminerà gli elementi.

* **applyIf (stringa)**: condizione per prendere in considerazione l&#39;indice - riceve un&#39;espressione XTK.
* **etichetta (stringa)**: etichetta indice.
* **nome (MNTOKEN)**: nome di indice univoco.
* **univoco (booleano)**: se questa opzione è attivata (@unique=&quot;true&quot;), l&#39;attributo garantisce l&#39;univocità dell&#39;indice in tutti i relativi campi.

## Esempi {#examples-3}

Creazione di un indice sul campo &quot;id&quot;. L&#39;attributo &quot;@unique&quot; dell&#39;elemento `<dbindex>` attiva l&#39;aggiunta della parola chiave SQL &quot;UNIQUE&quot; quando l&#39;indice viene creato nel database (query).

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

Creazione di un indice composito sui campi &quot;@mail&quot; e &quot;@phoneNumber&quot;:

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
