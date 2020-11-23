---
solution: Campaign Classic
product: campaign
title: Implementazione dei metodi SOAP
description: Implementazione dei metodi SOAP
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---


# Implementazione dei metodi SOAP{#implementing-soap-methods}

## Introduzione {#introduction}

È possibile creare metodi SOAP in JavaScript. Questa funzione consente semplicemente i processi applicativi, può evitare lo sviluppo di JSP e la loro chiamata nei moduli.

Questi metodi SOAP si comportano nello stesso modo di quelli definiti in modo nativo nell&#39;applicazione. Sono supportati gli stessi attributi: static, key only and const.

## Definizione di una libreria di metodi {#defining-a-method-library}

La creazione di una libreria di metodi prevede due fasi:

* La dichiarazione del metodo SOAP,
* Definizione (o implementazione) in JavaScript.

### Dichiarazione {#declaration}

Cominciate dichiarando i metodi negli schemi (per ulteriori informazioni sulla creazione e la modifica degli schemi, consultate [questa sezione](../../configuration/using/about-schema-edition.md)).

La loro dichiarazione è simile a quella dei metodi nativi, con la differenza che è necessario aggiungere l&#39;attributo &#39;library&#39; specificando il nome della libreria dei metodi in cui si trova la definizione.

Questo nome coincide con il nome (con lo spazio dei nomi) dell&#39;entità di tipo &#39;codice JavaScript&#39;.

Esempio:

Il metodo testLog(msg) è dichiarato in un&#39;estensione nms:Recipient

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
>Una libreria di metodi può raggruppare funzioni per vari schemi o viceversa; le funzioni di uno schema possono essere definite in librerie separate.

Lo script può contenere codice da eseguire durante il caricamento iniziale della libreria.

**1. Nome**

Il nome della funzione deve essere conforme al seguente formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Esempio:

La seguente funzione JavaScript è l&#39;implementazione del metodo descritto in precedenza. Deve essere definito nell&#39;entità di tipo &quot;codice JavaScript&quot; utilizzando il nome &#39;cus:test&#39;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Firma**

La firma della funzione deve includere un argomento per ogni parametro &#39;in&#39; o &#39;inout&#39; della dichiarazione.

Casi specifici:

* **metodi** non statici: la funzione deve includere prima un argomento aggiuntivo, che coincide con l&#39;entità XML passata sotto forma di oggetto di tipo &#39;xml&#39; (E4X).
* **Metodi** di tipo &quot;solo chiave&quot;: la funzione deve includere prima un argomento aggiuntivo, che coincide con la chiave passata sotto forma di stringhe di caratteri.

**3. Valori restituiti**

La funzione deve restituire un valore per ogni parametro di tipo &#39;out&#39; o &#39;inout&#39;. Caso specifico: Se il metodo è dichiarato senza gli attributi &#39;static&#39;, &#39;key only&#39; o &#39;const&#39;, il primo valore restituito deve coincidere con l&#39;entità modificata. È possibile restituire un nuovo oggetto o restituire il primo parametro modificato.

Ad esempio:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Per restituire più valori, questi devono essere visualizzati in una tabella.

Esempio:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

