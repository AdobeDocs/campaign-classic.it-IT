---
product: campaign
title: API orientate alle aziende
description: API orientate alle aziende
feature: API
role: Data Engineer, Developer
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---

# API orientate alle aziende{#business-oriented-apis}

Le API aziendali sono specifiche per ciascun tipo di oggetto. Hanno un effetto su:

* Consegne:

   * Creazione di un&#39;azione di consegna, fare riferimento a [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * invio di una campagna (avvio, pausa, arresto, invio di una bozza),
   * recupero dei registri di consegna.

* Flussi di lavoro

   * avvio di un flusso di lavoro,
   * verifica dei processi, ecc.

     Consulta [Metodi SOAP in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestione dei contenuti
* Gestione degli abbonamenti, fare riferimento a [Abbonamento (nms:subscription)](#subscribe--nms-subscription-) e [Annullamento dell&#39;abbonamento (nms:subscription)](#unsubscribe--nms-subscription-).
* Processi dati: importazioni, esportazioni.

Questa sezione descrive l’utilizzo dei servizi &quot;Subscribe&quot;, &quot;Unsubscribe&quot; e &quot;SubmitDelivery&quot;.

>[!IMPORTANT]
>
>[La documentazione JSAPI per Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=it) contiene informazioni aggiuntive sulle chiamate SOAP e sull&#39;utilizzo di JavaScript in Adobe Campaign, nonché un riferimento completo a tutti i metodi e le funzioni utilizzati nell&#39;applicazione.

## Sottoscrivi (nms:subscription) {#subscribe--nms-subscription-}

Questo servizio ti consente di abbonare un destinatario a un servizio di informazioni e di aggiornare il profilo del destinatario.

Per chiamare il servizio sono necessari i seguenti parametri:

* un’autenticazione,
* nome interno del servizio di abbonamento,
* un documento XML contenente le informazioni sul destinatario (secondo lo schema &quot;nms:recipient&quot;),
* un valore booleano per la creazione del destinatario, se non esiste già.

Descrizione del metodo &quot;subscribe&quot; nello schema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

La definizione della chiave di riconciliazione deve essere immessa tramite l&#39;attributo _**key** nell&#39;elemento `<recipient>` del documento XML. Il contenuto di questo attributo è un elenco XPath separato da virgole.

Questa chiamata non restituisce alcun dato, ad eccezione degli errori.

### Esempi {#examples}

Iscrizione con chiave di riconciliazione del destinatario sull’indirizzo e-mail: il documento XML di input deve fare riferimento all’indirizzo e-mail e alla definizione della chiave in questo campo.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Aggiornamento del destinatario e dell’abbonamento.

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

## Annulla iscrizione (nms:subscription) {#unsubscribe--nms-subscription-}

Questo servizio ti consente di annullare l’abbonamento di un destinatario a un servizio di informazioni e di aggiornare il profilo del destinatario.

Per chiamare il servizio sono necessari i seguenti parametri:

* un’autenticazione,
* Nome interno del servizio dal quale annullare l’abbonamento,
* un documento XML contenente le informazioni sul destinatario (secondo lo schema &quot;nms:recipient&quot;),

Descrizione del metodo &quot;Unsubscribe&quot; nello schema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La definizione della chiave di riconciliazione deve essere immessa tramite l&#39;attributo _key sull&#39;elemento `<recipient>` del documento XML. Il contenuto di questo attributo è un elenco XPath separato da virgole.

Se il destinatario non è presente nella banca dati o non è abbonato al servizio di informazione in questione, il servizio non esegue alcuna azione e non genera un errore.

>[!NOTE]
>
>Se il nome del servizio non viene specificato come parametro, il destinatario viene automaticamente in fase di inserisco nell&#39;elenco Bloccati del servizio (@blackList=&quot;1&quot;).

Questa chiamata non restituisce alcun dato, ad eccezione degli errori.

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

* un’autenticazione,
* nome interno del modello di consegna,
* un documento XML facoltativo contenente dati di consegna aggiuntivi.

Questa API non deve essere chiamata in volume in quanto si potrebbero riscontrare problemi di prestazioni.

Descrizione del metodo nel relativo schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

È necessario creare un modello di consegna dalla console client di Adobe Campaign. Contiene i parametri comuni a tutte le consegne (indirizzo del mittente o durata di validità del messaggio).

Il documento XML di input è un frammento di modello di consegna che rispetta la struttura dello schema &quot;nms:delivery&quot;. Conterrà tutti i dati aggiuntivi che non possono essere definiti in modo statico nel modello di consegna (ad esempio, l’elenco dei destinatari di destinazione).

Questa chiamata non restituisce alcun dato, ad eccezione degli errori.

### Esempio di documento XML {#xml-document-example}

Questo esempio si basa su un modello di consegna personalizzato proveniente da un’origine dati esterna (in questo caso un file ). La configurazione è completamente descritta nel modello di consegna, quindi tutto ciò che rimane da inviare quando si verifica la chiamata è il contenuto del file dall&#39;elemento `<externalsource>`.

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
