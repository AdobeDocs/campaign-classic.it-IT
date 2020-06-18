---
title: API orientate al business
seo-title: API orientate al business
description: API orientate al business
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c51a51f175e9f3fe5a55f2b5f57872057f70909d
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---


# API orientate al business{#business-oriented-apis}

Le API business sono specifiche per ciascun tipo di oggetto. Hanno un effetto su:

* Consegne:

   * Creazione di un&#39;azione di consegna, fare riferimento a [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * inviare una campagna (avviare, mettere in pausa, interrompere, inviare una prova),
   * recupero dei log di consegna.

* Flussi di lavoro:

   * avvio di un flusso di lavoro,
   * verifica dei processi, ecc.

      Fare riferimento ai metodi [SOAP in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Gestione dei contenuti
* Gestione delle iscrizioni, consultate [Iscrizione (nms:subscription)](#subscribe--nms-subscription-) e [Annulla sottoscrizione (nms:subscription)](#unsubscribe--nms-subscription-).
* Processi di dati: importazioni, esportazioni.

In questa sezione viene illustrato l&#39;utilizzo dei servizi &quot;Subscribe&quot;, &quot;Unsubscription&quot; e &quot;SubmitDelivery&quot;.

>[!IMPORTANT]
>
>[La documentazione](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) JSAPI della campagna contiene informazioni aggiuntive sulle chiamate SOAP e sull&#39;utilizzo di Javascript nel  Adobe Campaign, nonché un riferimento completo a tutti i metodi e le funzioni utilizzati nell&#39;applicazione.

## Iscrizione (nms:iscrizione) {#subscribe--nms-subscription-}

Questo servizio consente di iscrivere un destinatario a un servizio di informazione e aggiornare il profilo del destinatario.

Per chiamare il servizio sono necessari i seguenti parametri:

* un&#39;autenticazione,
* nome interno del servizio di iscrizione,
* un documento XML contenente le informazioni sui destinatari (dallo schema &quot;nms:destinatario&quot;),
* un valore booleano per la creazione del destinatario, se non ne esiste già uno.

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

La definizione della chiave di riconciliazione deve essere immessa tramite l&#39;attributo _**key** sull&#39; `<recipient>` elemento del documento XML. Il contenuto di questo attributo è un elenco XPath separato da virgole.

Questa chiamata non restituisce alcun dato, tranne eventuali errori.

### Esempi {#examples}

Iscrizione con chiave di riconciliazione del destinatario sull&#39;indirizzo e-mail: il documento XML di input deve fare riferimento all&#39;indirizzo e-mail e alla definizione della chiave in questo campo.

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

## Annulla sottoscrizione (nms:iscrizione) {#unsubscribe--nms-subscription-}

Questo servizio consente di annullare l’iscrizione di un destinatario da un servizio di informazione e di aggiornare il profilo del destinatario.

Per chiamare il servizio sono necessari i seguenti parametri:

* un&#39;autenticazione,
* Nome interno del servizio da cui annullare l’iscrizione,
* un documento XML contenente le informazioni sui destinatari (dallo schema &quot;nms:destinatario&quot;),

Descrizione del metodo &quot;Annulla sottoscrizione&quot; nello schema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

La definizione della chiave di riconciliazione deve essere immessa tramite l&#39;attributo _key sull&#39; `<recipient>` elemento del documento XML. Il contenuto di questo attributo è un elenco XPath separato da virgole.

Se il destinatario non è presente nel database o non è iscritto al servizio informazioni interessato, il servizio non esegue alcuna azione e non genera un errore.

>[!NOTE]
>
>Se il nome del servizio non è specificato come parametro, il destinatario viene inserito automaticamente nell&#39;elenco dei blocchi (@blockList=&quot;1&quot;).

Questa chiamata non restituisce alcun dato, tranne eventuali errori.

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

Questo servizio consente di creare e inviare un&#39;azione di consegna.

Per chiamare il servizio sono necessari i seguenti parametri:

* un&#39;autenticazione,
* nome interno del modello di consegna,
* un documento XML facoltativo contenente dati di consegna aggiuntivi.

Questa API non deve essere richiamata in volume perché potrebbero verificarsi problemi di prestazioni.

Descrizione del metodo nello schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

È necessario creare un modello di consegna dalla console client  Adobe Campaign. Contiene i parametri comuni a tutte le consegne (indirizzo del mittente o durata di validità del messaggio).

Il documento XML di input è un frammento di modello di consegna che segue la struttura dello schema &quot;nms:delivery&quot;. Conterrà tutti i dati aggiuntivi che non è stato possibile definire in modo statico nel modello di consegna (ad esempio, l&#39;elenco dei destinatari da destinare).

Questa chiamata non restituisce alcun dato, tranne eventuali errori.

### Esempio di documento XML {#xml-document-example}

Questo esempio è basato su un modello di consegna personalizzato da un&#39;origine dati esterna (in questo caso un file). La configurazione è descritta completamente nel modello di consegna, quindi tutto ciò che rimane da inviare quando si verifica la chiamata è il contenuto del file dall&#39; `<externalsource>` elemento .

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

Se non disponete di un modello di consegna, potete utilizzare il seguente esempio:

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

