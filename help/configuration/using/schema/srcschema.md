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
source-wordcount: '453'
ht-degree: 1%

---


# `<srcschema>` element  {#srcschema--element}

## Modello di contenuto {#content-model-14}

srcSchema:==(attribute | createdBy | dati | element | enumerazione | help | interfaccia | Metodi | modifiedBy)

## Attributi {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), ExtendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (booleano), mappingType (string), modifiedBy-id (long), name (string), namespace useRecycleBin (booleano), view (booleano), xtkschema (stringa)

## Genitori {#parents-14}

None

## Bambini {#children-14}

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

`<srcschema>` è l&#39;elemento principale di uno schema. È il punto di input per la definizione dello schema.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-9}

La presentazione dello schema è disponibile in [Informazioni sul riferimento allo schema](../../configuration/using/about-schema-reference.md) e [Struttura dello schema](../../configuration/using/schema-structure.md).

## Descrizione attributo {#attribute-description-14}

* **created (datetime)**: questo attributo fornisce informazioni sulla data e l&#39;ora della creazione dello schema. Presenta un modulo &quot;Data e ora&quot;. I valori visualizzati vengono prelevati dal server. L&#39;ora viene visualizzata in formato UTC.
* **createBy-id (long)**: è l&#39;identificatore dell&#39;operatore che ha creato lo schema.
* **desc (stringa)**: descrizione schema
* **entitySchema (stringa)**: schema di base su cui si basano la sintassi e l&#39;approvazione (per impostazione predefinita per  Adobe Campaign: xtk:srcSchema). Quando si salva lo schema corrente,  Adobe Campaign ne approverà la grammatica con lo schema dichiarato nell&#39;attributo @xtkschema.
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

## Esempi {#examples-11}

`<srcschema>` dell&#39;elemento &quot;nms:delivery&quot; fuori dallo schema box

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
