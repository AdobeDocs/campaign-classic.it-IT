---
product: campaign
title: Informazioni sui servizi web
description: Informazioni sui servizi web
feature: API
role: Data Engineer, Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 3%

---

# Informazioni sui servizi web{#about-web-services}

## Definizione delle API di Adobe Campaign {#definition-of-adobe-campaign-apis}

Il server applicazioni Adobe Campaign è stato progettato per offrire apertura e facilità di integrazione con sistemi informativi aziendali sempre più complessi e diversificati.

Le API di Adobe Campaign vengono utilizzate in JavaScript all’interno dell’applicazione e nell’SOAP al di fuori di essa. Costituiscono una libreria di funzioni generiche che possono essere arricchite. Per ulteriori informazioni, vedere [Implementazione dei metodi SOAP](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Il numero di chiamate al motore autorizzate al giorno varia in base al contratto di licenza. Per ulteriori informazioni, consulta [questa pagina](https://helpx.adobe.com/it/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>Un elenco di tutte le API, inclusa la loro descrizione completa, è disponibile in [questa documentazione dedicata](https://experienceleague.adobe.com/developer/campaign-api/api/index.html.

## Prerequisiti {#prerequisites}

Prima di utilizzare le API di Adobe Campaign, è necessario avere familiarità con i seguenti argomenti:

* JavaScript
* Protocollo SOAP
* Modello dati di Adobe Campaign

## Utilizzo delle API di Adobe Campaign {#using-adobe-campaign-apis}

Adobe Campaign utilizza due tipi di API:

* API di accesso ai dati generiche per l’esecuzione di query sui dati del modello di dati. Consulta [API orientate ai dati](../../configuration/using/data-oriented-apis.md).
* API specifiche per l’azienda che consentono di agire su ciascun oggetto: consegne, flussi di lavoro, abbonamenti, ecc. Consulta [API orientate alle aziende](../../configuration/using/business-oriented-apis.md).

Per sviluppare API e interagire con Adobe Campaign, devi acquisire familiarità con il modello dati. Adobe Campaign consente di generare una descrizione completa della base. Fare riferimento a [Descrizione del modello](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## Chiamate SOAP {#soap-calls}

Il protocollo SOAP consente di richiamare i metodi API tramite il rich client, le applicazioni di terze parti tramite i servizi web o JSP utilizzando tali metodi in modo nativo.

![](assets/s_ncs_configuration_architecture.png)

La struttura del messaggio SOAP è la seguente:

* una busta che definisce la struttura del messaggio,
* un’intestazione facoltativa,
* un corpo contenente le informazioni sulla chiamata e la risposta,
* gestione degli errori che definisce la condizione di errore.

## Risorse e scambi {#resources-and-exchanges}

Lo schema seguente mostra le varie risorse coinvolte nell’utilizzo delle API di Adobe Campaign:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Esempio di messaggio SOAP sul metodo &#39;ExecuteQuery&#39; {#example-of-a-soap-message-on-the--executequery--method--}

In questo esempio, una query SOAP richiama il metodo &quot;ExecuteQuery&quot;, che accetta una stringa di caratteri come parametro per l&#39;autenticazione (token di sessione) e un contenuto XML per la descrizione della query da eseguire.

Per ulteriori informazioni, consultare [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>La descrizione WSDL del servizio è stata completata nell&#39;esempio seguente: [Descrizione servizio Web: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### Query SOAP {#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

L&#39;elemento `<soap-env:envelope>` è il primo elemento del messaggio che rappresenta la busta SOAP.

L&#39;elemento `<soap-env:body>` è il primo elemento figlio della busta. Contiene la descrizione del messaggio, ovvero il contenuto della query o della risposta.

Il metodo da richiamare viene immesso nell&#39;elemento `<executequery>` dal corpo del messaggio SOAP.

Nell&#39;SOAP i parametri sono riconosciuti in ordine di apparizione. Il primo parametro, `<__sessiontoken>`, accetta la catena di autenticazione, il secondo parametro è la descrizione XML della query dall&#39;elemento `<querydef>`.

### Risposta SOAP {#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Il risultato della query viene immesso dall&#39;elemento `<pdomoutput>`.

## Gestione degli errori {#error-management}

Esempio di risposta di errore SOAP:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

L&#39;elemento `<soap-env:fault>` nel corpo del messaggio SOAP viene utilizzato per trasmettere i segnali di errore generati durante l&#39;elaborazione del servizio Web. È composto dai seguenti sottoelementi:

* `<faultcode>` : indica il tipo di errore. I tipi di errore sono:

   * &quot;VersionMismatch&quot; in caso di incompatibilità con la versione SOAP utilizzata,
   * &quot;MustUnderstand&quot; in caso di problema nell’intestazione del messaggio,
   * &quot;Client&quot; nel caso in cui al client manchino alcune informazioni,
   * &quot;Server&quot; nel caso in cui il server abbia un problema durante l’esecuzione dell’elaborazione.

* `<faultstring>`: messaggio che descrive l&#39;errore
* `<detail>`: messaggio di errore lungo

L&#39;esito positivo o negativo della chiamata al servizio viene identificato quando viene verificato l&#39;elemento `<faultcode>`.

>[!IMPORTANT]
>
>Tutti i servizi Web Adobe Campaign gestiscono gli errori. Si consiglia pertanto vivamente di testare ogni chiamata per gestire gli errori restituiti.

Esempio di gestione degli errori in C#:

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## URL del server del servizio Web (o EndPoint) {#url-of-web-service-server--or-endpoint-}

Per inviare il servizio Web, è necessario contattare il server Adobe Campaign che implementa il metodo di servizio corrispondente.

L’URL del server è il seguente:

https://serverName/nl/jsp/soaprouter.jsp

Con **`<server>`** il server applicazioni Adobe Campaign (**nlserver web**).
