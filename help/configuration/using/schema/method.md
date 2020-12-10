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
source-wordcount: '204'
ht-degree: 3%

---


# `<method>` element  {#method--element}

## Modello di contenuto {#content-model-10}

metodo:==( help | parametri)

## Attributi {#attributes-10}

* @_operation (stringa)
* @access (stringa)
* @const (booleano)
* @hidden (booleano)
* @label (stringa)
* @library (stringa)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (booleano)

## Genitori {#parents-10}

`<methods>`  ,  `<interface />`

## Bambini {#children-10}

* `<help>`
* `<parameters>`

## Descrizione {#description-10}

Questo elemento consente di definire un metodo SOAP.

## Utilizzo e contesto di utilizzo {#use-and-context-of-use-7}

I metodi SOAP consentono i processi dell&#39;applicazione.

Il simbolo &quot;@library&quot; è necessario per dichiarare un nuovo metodo (non nativo): lo spazio dei nomi e il nome utilizzati per la libreria sono indipendenti dallo spazio dei nomi e dal nome dello schema in cui si trova la dichiarazione.

## Descrizione attributo {#attribute-description-10}

* **access (stringa)**: questo attributo definisce il controllo di accesso per l&#39;utilizzo del metodo. Se questo attributo non è presente, l&#39;identificazione è obbligatoria. I valori disponibili sono: &#39;anonimo&#39;, &#39;admin&#39; e &#39;sql&#39;.
* **const (booleano)**: se è attivato, questo attributo significa che il metodo dichiarato modificherà l&#39;entità
* **label (stringa)**: etichetta del metodo.
* **libreria (stringa)**: questo metodo non è nativo dell&#39;applicazione. Questo attributo prende il valore della libreria dei metodi in cui viene trovata la definizione del metodo (nms:mylibrary.js).
* **name (MNTOKEN)**: nome univoco del metodo.
* **static (boolean)**: se questo attributo è attivato, il metodo è considerato autonomo, tutti i parametri devono essere specificati al metodo quando viene chiamato.

## Esempi {#examples-7}

Definizione del metodo &quot;Subscribe&quot; out of the box:

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
