---
product: campaign
title: API orientate alle aziende
description: API orientate alle aziende
audience: configuration
content-type: reference
topic-tags: api
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 2%

---

# API orientate alle aziende{#business-oriented-apis}

![](../../assets/v7-only.svg)

Le API aziendali sono specifiche per ciascun tipo di oggetto. Hanno un effetto su:

* Consegne:

   * Creazione di un’azione di consegna, fai riferimento a [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * invio di una campagna (avvio, pausa, arresto, invio di prove),
   * recupero dei log di consegna.

* Flussi di lavoro:

   * avvio di un flusso di lavoro,
   * verifica dei processi, ecc.

      Fai riferimento a [Metodi SOAP in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestione dei contenuti
* Gestione sottoscrizione, fare riferimento a [Iscrizione (nms:abbonamento)](#subscribe--nms-subscription-) e [Annulla sottoscrizione (nms:abbonamento)](#unsubscribe--nms-subscription-).
* Processi dati: importazioni, esportazioni.

Questa sezione descrive l’utilizzo dei servizi &quot;Subscribe&quot;, &quot;Unsubscribe&quot; e &quot;SubmitDelivery&quot;.

>[!IMPORTANT]
>
>[Documentazione JSAPI per Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html) contiene informazioni aggiuntive sulle chiamate SOAP e sull’utilizzo di Javascript in Adobe Campaign, nonché un riferimento completo a tutti i metodi e le funzioni utilizzati nell’applicazione.

## Iscrizione (nms:abbonamento) {#subscribe--nms-subscription-}

Questo servizio ti consente di abbonare un destinatario a un servizio di informazioni e di aggiornare il profilo del destinatario.

Per chiamare il servizio sono necessari i seguenti parametri:

* un&#39;autenticazione,
* nome interno del servizio di abbonamento,
* un documento XML contenente le informazioni sui destinatari (dallo schema &quot;nms:recipient&quot;),
* un valore booleano per la creazione del destinatario, se non è già presente.

Descrizione del metodo &quot;subscription&quot; nello schema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

La definizione della chiave di riconciliazione deve essere inserita tramite il valore _**key** dell&#39;attributo `<recipient>` elemento del documento XML. Il contenuto di questo attributo è un elenco XPath separato da virgole.

Questa chiamata non restituisce alcun dato, tranne gli errori.

### Esempi {#examples}

Iscrizione con chiave di riconciliazione dei destinatari sull&#39;indirizzo e-mail: il documento XML di input deve fare riferimento all&#39;indirizzo e-mail e alla definizione della chiave in questo campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Aggiornamento del destinatario e della sottoscrizione.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Esempio di messaggi SOAP {#example-of-soap-messages}

* Query:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Risposta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Annulla sottoscrizione (nms:abbonamento) {#unsubscribe--nms-subscription-}

Questo servizio ti consente di annullare l’iscrizione di un destinatario a un servizio di informazioni e di aggiornare il profilo del destinatario.

Per chiamare il servizio sono necessari i seguenti parametri:

* un&#39;autenticazione,
* Nome interno del servizio da cui annullare l’iscrizione,
* un documento XML contenente le informazioni sui destinatari (dallo schema &quot;nms:recipient&quot;),

Descrizione del metodo &quot;Annulla sottoscrizione&quot; nello schema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La definizione della chiave di riconciliazione deve essere immessa tramite l’attributo _key nella sezione `<recipient>` elemento del documento XML. Il contenuto di questo attributo è un elenco XPath separato da virgole.

Se il destinatario non è presente nel database o non è iscritto al servizio informazioni interessato, il servizio non esegue alcuna azione e non genera un errore.

>[!NOTE]
>
>Se il nome del servizio non è specificato come parametro, il destinatario viene automaticamente al elenco Bloccati(@blackList=&quot;1&quot;).

Questa chiamata non restituisce alcun dato, tranne gli errori.

### Esempio di messaggi SOAP {#example-of-soap-messages-1}

Query:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Risposta:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

Questo servizio ti consente di creare e inviare un’azione di consegna.

Per chiamare il servizio sono necessari i seguenti parametri:

* un&#39;autenticazione,
* nome interno del modello di consegna,
* un documento XML facoltativo contenente dati di consegna aggiuntivi.

Questa API non deve essere chiamata in volume in quanto potrebbero verificarsi problemi di prestazioni.

Descrizione del metodo nel relativo schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Un modello di consegna deve essere creato dalla console client di Adobe Campaign. Contiene i parametri comuni a tutte le consegne (indirizzo del mittente o durata di validità del messaggio).

Il documento XML di input è un frammento di modello di consegna che rispetta la struttura dello schema &quot;nms:delivery&quot;. Conterrà tutti i dati aggiuntivi che non è stato possibile definire in modo statico nel modello di consegna (ad esempio, l’elenco dei destinatari da indirizzare).

Questa chiamata non restituisce alcun dato, tranne gli errori.

### Esempio di documento XML {#xml-document-example}

Questo esempio è basato su un modello di consegna personalizzato proveniente da un’origine dati esterna (in questo caso un file ). La configurazione è descritta completamente nel modello di consegna, quindi tutto ciò che rimane da inviare quando si verifica la chiamata è il contenuto del file dal `<externalsource>` elemento.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Se non disponi di un modello di consegna, puoi utilizzare il seguente esempio:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```
