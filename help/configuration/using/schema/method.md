---
product: campaign
title: 'Elementi e attributi dello schema: elemento del metodo'
description: elemento method
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
TQID: 'https://experienceleague.adobe.com/GaT6bmWzojcbk8-XjCoqrMv2-02aoxv1cIXM0E0Y0UU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 2%
---
# elemento method {#method--element}


## Modello di contenuto {#content-model-10}

metodo:==( guida | parametri)

## Attributi {#attributes-10}

* @_operation (stringa)
* @access (stringa)
* @const (boolean)
* @hidden (boolean)
* @label (stringa)
* @library (stringa)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## Padri {#parents-10}

`<methods>`  ,  `<interface />`

## Elementi secondari {#children-10}

* `<help>`
* `<parameters>`

## Descrizione {#description-10}

Questo elemento consente di definire un metodo SOAP.

## Uso e contesto di utilizzo {#use-and-context-of-use-7}

I metodi di SOAP consentono di eseguire i processi dell&#39;applicazione.

Il &quot;@library&quot; è necessario per dichiarare un nuovo metodo (non nativo): lo spazio dei nomi e il nome utilizzato per la libreria sono indipendenti dallo spazio dei nomi e dal nome dello schema in cui si trova la dichiarazione.

## Descrizione attributo {#attribute-description-10}

* **accesso (stringa)**: questo attributo definisce il controllo di accesso per l&#39;utilizzo del metodo. Se questo attributo è mancante, l&#39;identificazione è obbligatoria. I valori disponibili sono: &quot;anonymous&quot;, &quot;admin&quot; e &quot;sql&quot;.
* **const (booleano)**: se attivato, significa che il metodo dichiarato modificherà l&#39;entità
* **etichetta (stringa)**: etichetta del metodo.
* **libreria (stringa)**: metodo non nativo per l&#39;applicazione. Questo attributo accetta il valore della libreria di metodi in cui viene trovata la definizione del metodo (nms:mylibrary.js).
* **name (MNTOKEN)**: nome di metodo univoco.
* **statico (booleano)**: se questo attributo è attivato, il metodo è considerato autonomo, tutti i parametri devono essere specificati per il metodo quando viene richiamato.

## Esempi {#examples-7}

Definizione del metodo predefinito &quot;Subscribe&quot;:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
