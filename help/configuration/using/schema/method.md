---
product: campaign
title: 'Elementi e attributi dello schema: elemento del metodo'
description: elemento method
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# elemento method {#method--element}

![](../../../assets/v7-only.svg)

## Modello di contenuto {#content-model-10}

metodo:==( guida | )

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

`<methods>` , `<interface />`

## Elementi figli {#children-10}

* `<help>`
* `<parameters>`

## Descrizione {#description-10}

Questo elemento ti consente di definire un metodo SOAP.

## Uso e contesto di utilizzo {#use-and-context-of-use-7}

I metodi SOAP consentono l&#39;esecuzione di processi applicativi.

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
