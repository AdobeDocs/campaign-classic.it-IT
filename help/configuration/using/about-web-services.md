---
product: campaign
title: Informazioni sui servizi web
description: Informazioni sui servizi web
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: API
role: Data Engineer, Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 5%

---

# Informazioni sui servizi web{#about-web-services}

## Definizione delle API di Adobe Campaign {#definition-of-adobe-campaign-apis}

Il server applicazioni Adobe Campaign è stato progettato per offrire apertura e facilità di integrazione con sistemi informativi aziendali sempre più complessi e diversificati.

Le API di Adobe Campaign vengono utilizzate in JavaScript all’interno dell’applicazione e in SOAP al di fuori di essa. Costituiscono una libreria di funzioni generiche che possono essere arricchite. Per ulteriori informazioni, fare riferimento a [Implementazione dei metodi SOAP](../../configuration/using/implementing-soap-methods.md).

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

* API di accesso ai dati generiche per l’esecuzione di query sui dati del modello dati. Fai riferimento a [API orientate ai dati](../../configuration/using/data-oriented-apis.md).
* API specifiche per l’azienda che consentono di agire su ciascun oggetto: consegne, flussi di lavoro, abbonamenti, ecc. Fai riferimento a [API orientate alle aziende](../../configuration/using/business-oriented-apis.md).

Per sviluppare API e interagire con Adobe Campaign, è necessario avere familiarità con il modello dati. Adobe Campaign consente di generare una descrizione completa della base. Fai riferimento a [Descrizione del modello](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## Chiamate SOAP {#soap-calls}

Il protocollo SOAP consente di richiamare i metodi API tramite il rich client, le applicazioni di terze parti tramite i servizi web o JSP utilizzando tali metodi in modo nativo.

![](assets/s_ncs_configuration_architecture.png)

La struttura di un messaggio SOAP è la seguente:

* una busta che definisce la struttura del messaggio,
* un’intestazione facoltativa,
* un corpo contenente le informazioni sulla chiamata e la risposta,
* gestione degli errori che definisce la condizione di errore.

## Risorse e scambi {#resources-and-exchanges}

Lo schema seguente mostra le varie risorse coinvolte nell’utilizzo delle API di Adobe Campaign:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Esempio di messaggio SOAP sul metodo &#39;ExecuteQuery&#39; {#example-of-a-soap-message-on-the--executequery--method--}

In questo esempio, una query SOAP richiama il metodo &quot;ExecuteQuery&quot;, che accetta una stringa di caratteri come parametro per l&#39;autenticazione (token di sessione) e un contenuto XML per la descrizione della query da eseguire.

Per ulteriori informazioni, fare riferimento a [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>La descrizione WSDL di questo servizio viene completata nell&#39;esempio riportato di seguito: [Descrizione servizio Web: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

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

Il `<soap-env:envelope>` è il primo elemento del messaggio che rappresenta la busta SOAP.

Il `<soap-env:body>` è il primo elemento figlio della busta. Contiene la descrizione del messaggio, ovvero il contenuto della query o della risposta.

Il metodo da richiamare viene immesso nel `<executequery>` dal corpo del messaggio SOAP.

In SOAP, i parametri vengono riconosciuti in base all&#39;ordine di visualizzazione. Il primo parametro, `<__sessiontoken>`, prende la catena di autenticazione, il secondo parametro è la descrizione XML della query dal `<querydef>` elemento.

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

Il risultato della query viene immesso dal `<pdomoutput>` elemento.

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

Il `<soap-env:fault>` nel corpo del messaggio SOAP viene utilizzato per trasmettere i segnali di errore generati durante l&#39;elaborazione del servizio web. È composto dai seguenti sottoelementi:

* `<faultcode>` : indica il tipo di errore. I tipi di errore sono:

   * &quot;VersionMismatch&quot; in caso di incompatibilità con la versione SOAP utilizzata,
   * &quot;MustUnderstand&quot; in caso di problema nell’intestazione del messaggio,
   * &quot;Client&quot; nel caso in cui al client manchino alcune informazioni,
   * &quot;Server&quot; nel caso in cui il server abbia un problema durante l’esecuzione dell’elaborazione.

* `<faultstring>` : messaggio che descrive l’errore
* `<detail>` : messaggio di errore lungo

L&#39;esito positivo o negativo della chiamata del servizio viene identificato quando `<faultcode>` è verificato.

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
