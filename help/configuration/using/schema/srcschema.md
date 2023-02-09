---
product: campaign
title: Elementi e attributi - elemento srcschema
description: Elementi e attributi
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# elemento srcschema {#srcschema--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-14}

srcSchema:==(attribute) | createdBy | dati | elemento | enumerazione | aiuto | interfaccia | Metodi | modifiedBy)

## Attributi {#attributes-14}

creato (datetime), createdBy-id (long), desc (string), entitySchema (string), ExtendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (booleano), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (booleano), view (booleano), xtkschema (stringa)

## Genitori {#parents-14}

Nessuna

## Elementi figli {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Descrizione {#description-14}

La `<srcschema>` è l’elemento principale di uno schema. È il punto di input per la definizione dello schema.

## Uso e contesto di utilizzo {#use-and-context-of-use-9}

La presentazione dello schema è disponibile in [Informazioni sul riferimento di schema](../../../configuration/using/about-schema-reference.md) e [Struttura dello schema](../../../configuration/using/schema-structure.md).

## Descrizione attributo {#attribute-description-14}

* **create (datetime)**: questo attributo fornisce informazioni sulla data e l’ora della creazione dello schema. Ha un modulo &quot;Data e ora&quot;. I valori visualizzati vengono estratti dal server. L’ora viene visualizzata in formato UTC.
* **createdBy-id (long)**: è l&#39;identificatore dell&#39;operatore che ha creato lo schema.
* **desc (stringa)**: descrizione schema
* **entitySchema (stringa)**: schema di base su cui si basano la sintassi e l’approvazione (per impostazione predefinita per Adobe Campaign: xtk:srcSchema). Quando salvi lo schema corrente, Adobe Campaign ne approverà la grammatica con lo schema dichiarato nell&#39;attributo @xtkschema.
* **ExtendedSchema (stringa)**: riceve il nome dello schema predefinito su cui si basa l’estensione dello schema corrente. Il modulo è &quot;namespace:name&quot;.
* **img (stringa)**: icona collegata allo schema (può essere definita nella procedura guidata di creazione dello schema).
* **label (stringa)**: etichetta dello schema.
* **labelSingular (stringa)**: etichetta (singolare) da visualizzare nell’interfaccia.
* **lastModified (datetime)**: questo attributo fornisce informazioni sulla data e l’ora dell’ultima modifica. Ha un modulo &quot;Data e ora&quot;. I valori visualizzati vengono estratti dal server. L’ora viene visualizzata in formato UTC.
* **libreria (booleana)**: utilizzo dello schema come libreria e non come entità. Questo schema può quindi essere referenziato da altri schemi grazie agli attributi &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (stringa)**:

   * &quot;sql&quot;: mappatura del database
   * &quot;textFile&quot;: mappatura file di testo
   * &quot;xmlFile&quot;: Mappatura file di testo in formato XML
   * &quot;binaryFile&quot;: mappatura file binari

* **modifiedBy-id (long)**: corrisponde all’identificatore dell’operatore che ha modificato lo schema.
* **name (stringa)**: nome dello schema univoco.
* **namespace (stringa)**: spazio dei nomi dello schema (predefinito: nms, xtk, nl). Quando crei un nuovo schema per un progetto, ti consigliamo di utilizzare uno spazio dei nomi dedicato.
* **useRecycleBin (booleano)**: attiva la funzione di eliminazione nell&#39;applicazione. I record eliminati verranno inseriti nel cestino prima dell&#39;eliminazione finale. Questa funzione è disponibile solo in modalità &quot;Consegna&quot;.
* **view (booleano)**: se è attivato (@view=&quot;true&quot;), lo schema verrà utilizzato come visualizzazione. La procedura guidata di aggiornamento della struttura del database non terrà conto dello schema. Questa opzione viene utilizzata principalmente per fare riferimento a tabelle esterne.
* **xtkschema (stringa)**: nome dello schema che definisce la grammatica dello schema (xtk:srcSchema per impostazione predefinita).

## Esempi {#examples-11}

`<srcschema>` elemento dello schema predefinito &quot;nms:delivery&quot;

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
