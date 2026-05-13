---
product: campaign
title: Elementi e attributi - Elemento srcschema
description: Elementi e attributi
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
TQID: https://experienceleague.adobe.com/nUdM-iVzh7yI2Z3ZnFh5JK8FDZpmHAR1crzEb9S5xYg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 459
ht-degree: 1%

---

# elemento srcschema {#srcschema--element}


## Modello di contenuto {#content-model-14}

srcSchema:==(attribute | creatoDa | dati | elemento | enumerazione | guida | interfaccia | metodi | ModificatoDa)

## Attributi {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (booleano), mappingType (string), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (booleano), view (booleano), xtkschema (string)

## Padri {#parents-14}

Nessuno

## Elementi secondari {#children-14}

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

## Uso e contesto di utilizzo {#use-and-context-of-use-9}

La presentazione dello schema è disponibile in [Informazioni sul riferimento dello schema](../../../configuration/using/about-schema-reference.md) e [Struttura dello schema](../../../configuration/using/schema-structure.md).

## Descrizione attributo {#attribute-description-14}

* **creato (datetime)**: questo attributo fornisce informazioni sulla data e l&#39;ora di creazione dello schema. Ha un modulo &quot;Date Time&quot; (Data e ora). I valori visualizzati vengono ricavati dal server. L’ora viene visualizzata in formato UTC.
* **createdBy-id (long)**: è l&#39;identificatore dell&#39;operatore che ha creato lo schema.
* **desc (stringa)**: descrizione schema
* **entitySchema (stringa)**: schema di base su cui si basano sintassi e approvazione (per impostazione predefinita per Adobe Campaign: xtk:srcSchema). Quando salvi lo schema corrente, Adobe Campaign ne approverà la grammatica con lo schema dichiarato nell’attributo @xtkschema.
* **extendedSchema (stringa)**: riceve il nome dello schema predefinito su cui si basa l&#39;estensione dello schema corrente. Il modulo è &quot;namespace:name&quot;.
* **img (stringa)**: icona collegata allo schema (può essere definita nell&#39;assistente alla creazione dello schema).
* **etichetta (stringa)**: etichetta dello schema.
* **labelSingular (stringa)**: label (singular) per la visualizzazione nell&#39;interfaccia.
* **lastModified (datetime)**: questo attributo fornisce informazioni sulla data e l&#39;ora dell&#39;ultima modifica. Ha un modulo &quot;Date Time&quot; (Data e ora). I valori visualizzati vengono ricavati dal server. L’ora viene visualizzata in formato UTC.
* **libreria (booleana)**: utilizzo dello schema come libreria e non come entità. Altri schemi possono quindi fare riferimento a questo schema tramite gli attributi &quot;@ref&quot; e &quot;@template&quot;.
* **mappingType (stringa)**:

   * &quot;sql&quot;: mapping del database
   * &quot;textFile&quot;: mappatura file di testo
   * &quot;xmlFile&quot;: mapping di file di testo in formato XML
   * &quot;binaryFile&quot;: mappatura file binario

* **modifiedBy-id (long)**: corrisponde all&#39;identificatore dell&#39;operatore che ha modificato lo schema.
* **nome (stringa)**: nome di schema univoco.
* **spazio dei nomi (stringa)**: spazio dei nomi dello schema (impostazione predefinita: nms, xtk, nl). Quando crei un nuovo schema per un progetto, ti consigliamo di utilizzare uno spazio dei nomi dedicato.
* **useRecycleBin (booleano)**: attiva la funzionalità di eliminazione nell&#39;applicazione. I record eliminati verranno inseriti nel cestino prima dell&#39;eliminazione finale. Questa funzione è disponibile solo in modalità &quot;Delivery&quot;.
* **visualizzazione (booleana)**: se attivata (@view=&quot;true&quot;), lo schema verrà utilizzato come visualizzazione. L&#39;Assistente all&#39;aggiornamento della struttura del database non terrà conto dello schema. Questa opzione viene utilizzata principalmente per fare riferimento a tabelle esterne.
* **xtkschema (stringa)**: nome dello schema che definisce la grammatica dello schema (xtk:srcSchema per impostazione predefinita).

## Esempi {#examples-11}

`<srcschema>` elemento dello schema &quot;nms:delivery&quot; preconfigurato

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
