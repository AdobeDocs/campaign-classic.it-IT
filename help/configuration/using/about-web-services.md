---
title: Informazioni sui servizi web
description: Informazioni sui servizi web
page-status-flag: never-activated
uuid: f0b21cb3-aa75-4f54-a9f5-64e880f93e53
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 65919173-3ce0-4d98-936b-f4581df536ae
translation-type: tm+mt
source-git-commit: 75ab345e3b9360229ecc3ba9529a33e320228fa0
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 4%

---


# Informazioni sui servizi web{#about-web-services}

## Definizione di  API Adobe Campaign {#definition-of-adobe-campaign-apis}

Il server  delle applicazioni Adobe Campaign è stato progettato per garantire l&#39;apertura e la facilità di integrazione con sistemi informativi aziendali sempre più diversificati e complessi.

 le API Adobe Campaign vengono utilizzate in JavaScript all&#39;interno dell&#39;applicazione e in SOAP all&#39;esterno. Costituiscono una libreria di funzioni generiche che possono essere arricchite. Per ulteriori informazioni, vedere [Implementazione dei metodi](../../configuration/using/implementing-soap-methods.md)SOAP.

>[!IMPORTANT]
>
>Il numero di chiamate al motore autorizzate al giorno varia in base al contratto di licenza. Per ulteriori informazioni, consulta [questa pagina](https://helpx.adobe.com/it/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>In [questa documentazione](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)dedicata è disponibile un elenco di tutte le API, inclusa la descrizione completa.

## Prerequisiti {#prerequisites}

Prima di utilizzare le API Adobe Campaign , è necessario avere familiarità con i seguenti argomenti:

* Javascript
* Protocollo SOAP
*  modello dati Adobe Campaign

## Utilizzo  API Adobe Campaign {#using-adobe-campaign-apis}

 Adobe Campaign utilizza due tipi di API:

* API di accesso ai dati generici per la query dei dati del modello dati. Fare riferimento alle API [orientate ai dati](../../configuration/using/data-oriented-apis.md).
* API specifiche per le aziende che consentono di agire su ciascun oggetto: consegne, flussi di lavoro, iscrizioni ecc. Fate riferimento a API [orientate al business](../../configuration/using/business-oriented-apis.md).

Per sviluppare le API e interagire con  Adobe Campaign, è necessario avere familiarità con il modello dati.  Adobe Campaign consente di generare una descrizione completa della base. Fare riferimento a [Descrizione del modello](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## Chiamate SOAP {#soap-calls}

Il protocollo SOAP consente di invocare metodi API tramite il client avanzato, applicazioni di terze parti che utilizzano servizi Web o JSP utilizzando questi metodi in modo nativo.

![](assets/s_ncs_configuration_architecture.png)

La struttura di un messaggio SOAP è la seguente:

* un involucro che definisce la struttura del messaggio,
* un&#39;intestazione opzionale,
* un organismo contenente le informazioni sulla chiamata e la risposta,
* gestione degli errori che definisce la condizione di errore.

## Risorse e scambi {#resources-and-exchanges}

Lo schema seguente mostra le varie risorse coinvolte nell&#39;utilizzo delle API  Adobe Campaign:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Esempio di messaggio SOAP sul metodo &#39;ExecuteQuery&#39; {#example-of-a-soap-message-on-the--executequery--method--}

In questo esempio, una query SOAP richiama il metodo &quot;ExecuteQuery&quot;, che considera una stringa di caratteri come parametro per l&#39;autenticazione (token sessione) e un contenuto XML per la descrizione della query da eseguire.

Per ulteriori informazioni, vedere [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>La descrizione WSDL di questo servizio è completata nell&#39;esempio seguente: [Descrizione servizio Web: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

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

L&#39; `<soap-env:envelope>` elemento è il primo elemento del messaggio che rappresenta l&#39;inviluppo SOAP.

L’ `<soap-env:body>` elemento è il primo elemento secondario dell’inviluppo. Contiene la descrizione del messaggio, ovvero il contenuto della query o la risposta.

Il metodo da invocare viene immesso nell&#39; `<executequery>` elemento dal corpo del messaggio SOAP.

In SOAP, i parametri sono riconosciuti dall&#39;ordine di aspetto. Il primo parametro, `<__sessiontoken>`prende la catena di autenticazione, il secondo parametro è la descrizione XML della query dall&#39; `<querydef>` elemento.

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

Il risultato della query viene immesso dall&#39; `<pdomoutput>` elemento .

## Error management {#error-management}

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

L&#39; `<soap-env:fault>` elemento nel corpo del messaggio SOAP viene utilizzato per trasmettere i segnali di errore generati durante l&#39;elaborazione del servizio Web. È composta dai seguenti sottoelementi:

* `<faultcode>` : indica il tipo di errore. I tipi di errore sono:

   * &quot;VersionMismatch&quot; in caso di incompatibilità con la versione SOAP utilizzata,
   * &quot;mustUnderstand&quot; in caso di problemi nell&#39;intestazione del messaggio,
   * &quot;Client&quot; nel caso in cui al client manchino alcune informazioni,
   * &quot;Server&quot; nel caso in cui il server abbia un problema durante l&#39;esecuzione dell&#39;elaborazione.

* `<faultstring>` : messaggio che descrive l&#39;errore
* `<detail>` : long error message

Il successo o il fallimento della chiamata del servizio viene identificato quando l&#39; `<faultcode>` elemento viene verificato.

>[!IMPORTANT]
>
>Tutti  servizi Web Adobe Campaign gestiscono gli errori. È quindi vivamente consigliato testare ogni chiamata per gestire gli errori restituiti.

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

## URL del server del servizio Web (o di EndPoint) {#url-of-web-service-server--or-endpoint-}

Per inviare il servizio Web, è necessario contattare il server Adobe Campaign  che implementa il metodo di servizio corrispondente.

L&#39;URL del server è il seguente:

https://serverName/nl/jsp/soaprouter.jsp

Con **`<server>`** il server applicazione Adobe Campaign  (**Web** nlserver).
