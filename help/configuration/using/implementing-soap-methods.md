---
product: campaign
title: Implementazione dei metodi SOAP
description: Implementazione dei metodi SOAP
audience: configuration
content-type: reference
topic-tags: api
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# Implementazione dei metodi SOAP{#implementing-soap-methods}

![](../../assets/v7-only.svg)

## Introduzione {#introduction}

È possibile creare metodi SOAP in JavaScript. Questa funzione consente semplicemente i processi applicativi, può evitare lo sviluppo di JSP e la loro chiamata nei moduli.

Questi metodi SOAP si comportano come quelli definiti in modo nativo nell’applicazione. Sono supportati gli stessi attributi: statica, solo chiave e const.

## Definizione di una libreria di metodi {#defining-a-method-library}

La creazione di una libreria di metodi prevede due fasi:

* la dichiarazione del metodo SOAP,
* Definizione (o implementazione) in JavaScript.

### Dichiarazione {#declaration}

Inizia dichiarando i metodi negli schemi (per ulteriori informazioni su come creare e modificare gli schemi, consulta [questa sezione](../../configuration/using/about-schema-edition.md)).

La loro dichiarazione è simile a quella dei metodi nativi, tranne per il fatto che è necessario aggiungere l&#39;attributo &quot;library&quot; specificando il nome della libreria dei metodi in cui si trova la definizione.

Questo nome coincide con il nome (con lo spazio dei nomi) dell’entità di tipo &quot;Codice JavaScript&quot;.

Esempio:

Il metodo testLog(msg) è dichiarato in un&#39;estensione nms:recipient

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>Lo spazio dei nomi e il nome utilizzati per la libreria sono indipendenti dallo spazio dei nomi e dal nome dello schema in cui viene trovata la dichiarazione.

### Definizione {#definition}

I metodi SOAP sono implementati sotto forma di funzione JavaScript raggruppata in uno script che rappresenta una libreria.

>[!NOTE]
>
>Una libreria di metodi può raggruppare funzioni per vari schemi o viceversa, le funzioni di uno schema possono essere definite in librerie separate.

Lo script può contenere codice da eseguire durante il caricamento della libreria iniziale.

**1. Nome**

Il nome della funzione deve essere conforme al seguente formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Esempio:

La seguente funzione JavaScript è l&#39;implementazione del metodo descritto sopra. Deve essere definito nell’entità di tipo &quot;codice JavaScript&quot; utilizzando il nome &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Firma**

La firma della funzione deve includere un argomento per ogni parametro &#39;in&#39; o &#39;inout&#39; della dichiarazione.

Casi specifici:

* **metodi non statici**: la funzione deve includere prima un argomento aggiuntivo, che coincide con l&#39;entità XML passata sotto forma di un oggetto di tipo &quot;xml&quot; (E4X).
* **Metodi di tipo &quot;solo chiave&quot;**: la funzione deve prima includere un argomento aggiuntivo, che coincide con la chiave passata sotto forma di stringhe di caratteri.

**3. Valori restituiti**

La funzione deve restituire un valore per ogni parametro di tipo &#39;out&#39; o &#39;inout&#39;. Caso specifico: Se il metodo è dichiarato senza gli attributi &quot;static&quot;, &quot;key only&quot; o &quot;const&quot;, il primo valore restituito deve coincidere con l’entità modificata. È possibile restituire un nuovo oggetto o il primo parametro modificato.

Ad esempio:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Quando devono essere restituiti più valori, questi devono essere visualizzati in una tabella.

Esempio:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
