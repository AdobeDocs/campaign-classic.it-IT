---
product: campaign
title: Implementazione dei metodi SOAP
description: Implementazione dei metodi SOAP
feature: Configuration
role: Data Engineer, Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 3%

---

# Implementare metodi SOAP{#implementing-soap-methods}



## Introduzione {#introduction}

È possibile creare metodi SOAP in JavaScript. Questa funzione abilita semplicemente i processi applicativi, evitando di sviluppare JSP e le relative chiamate nei moduli.

Questi metodi SOAP si comportano nello stesso modo di quelli definiti in modo nativo nella domanda. Sono supportati gli stessi attributi: static, key only e const.

## Definire una libreria di metodi {#defining-a-method-library}

La creazione di una libreria di metodi prevede due fasi:

* la dichiarazione relativa al metodo SOAP,
* Definizione (o implementazione) in JavaScript.

### Dichiarazione {#declaration}

Inizia dichiarando i metodi negli schemi (per ulteriori informazioni su come creare e modificare gli schemi, consulta [questa sezione](../../configuration/using/about-schema-edition.md)).

La loro dichiarazione è simile a quella dei metodi nativi, con la differenza che è necessario aggiungere l&#39;attributo &quot;library&quot; che specifica il nome della libreria dei metodi in cui si trova la definizione.

Questo nome coincide con il nome (con lo spazio dei nomi) dell&#39;entità di tipo &quot;Codice JavaScript&quot;.

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
>Lo spazio dei nomi e il nome utilizzati per la libreria sono indipendenti dallo spazio dei nomi e dal nome dello schema in cui si trova la dichiarazione.

### Definizione {#definition}

I metodi SOAP sono implementati sotto forma di funzione JavaScript raggruppata in uno script che rappresenta una libreria.

>[!NOTE]
>
>Una libreria di metodi può raggruppare le funzioni per vari schemi o viceversa, le funzioni di uno schema possono essere definite in librerie separate.

Lo script può contenere il codice da eseguire durante il caricamento iniziale della libreria.

**1. Nome**

Il nome della funzione deve rispettare il seguente formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Esempio:

La seguente funzione di JavaScript è l’implementazione del metodo descritto sopra. È definita nell&#39;entità di tipo &quot;codice JavaScript&quot; utilizzando il nome &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Firma**

La firma della funzione deve includere un argomento per ogni parametro &#39;in&#39; o &#39;inout&#39; della dichiarazione.

Casi specifici:

* **metodi non statici**: la funzione deve includere prima un argomento aggiuntivo che coincida con l&#39;entità XML passata sotto forma di oggetto di tipo &#39;xml&#39; (E4X).
* **metodi di tipo &quot;solo chiave&quot;**: la funzione deve includere prima un argomento aggiuntivo che coincida con la chiave passata sotto forma di stringhe di caratteri.

**3. Valori restituiti**

La funzione deve restituire un valore per ogni parametro di tipo &quot;out&quot; o &quot;inout&quot;. Caso specifico: se il metodo viene dichiarato senza gli attributi &quot;static&quot;, &quot;key only&quot; o &quot;const&quot;, il primo valore restituito deve coincidere con l’entità modificata. È possibile restituire un nuovo oggetto o il primo parametro modificato.

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
