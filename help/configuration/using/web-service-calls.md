---
title: Chiamate a servizi Web
seo-title: Chiamate a servizi Web
description: Chiamate a servizi Web
seo-description: null
page-status-flag: never-activated
uuid: 7defe0e4-bb4a-4f6a-b6e8-e2ffac73b4c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 6934c165-6d27-4ce5-8607-170f299b4702
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c51a51f175e9f3fe5a55f2b5f57872057f70909d
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Chiamate a servizi Web{#web-service-calls}

## Informazioni generali {#general-information}

Tutti i metodi API sono presentati sotto forma di servizi Web. Questo consente di gestire tutte le funzioni  Adobe Campaign tramite chiamate SOAP, che sono il punto di ingresso nativo del server applicazione del Adobe Campaign . La console del Adobe Campaign  utilizza solo le chiamate SOAP.

I servizi Web consentono di creare molte applicazioni da un sistema di terze parti:

* Avvisi, notifiche ed esecuzione di modelli di consegna in tempo reale da un back office o da un sistema di transazione,
* sviluppo di interfacce speciali con funzionalità semplificate (interfacce Web, ecc.),
* Alimentazione e ricerca di dati nella banca dati, osservando le regole commerciali e restando isolati dal modello fisico sottostante.

## Definizione dei servizi Web {#definition-of-web-services}

La definizione dei servizi Web implementati nel server applicazione del Adobe Campaign  è disponibile dagli schemi di dati.

Un servizio Web è descritto nella grammatica degli schemi di dati ed è disponibile dall&#39; **`<methods>`** elemento .

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Di seguito è riportato un esempio della definizione del metodo **GenerateForm**.

La descrizione del servizio inizia con l&#39; `<method>` elemento . L&#39;elenco dei parametri del metodo viene completato dall&#39; `<parameters>` elemento . Ogni parametro è specificato da un nome, un tipo (booleano, stringa, DOMElement, ecc.) e una descrizione. L&#39;attributo &quot;inout&quot; con il valore &quot;out&quot; consente di specificare che il parametro &quot;result&quot; si trova nell&#39;output di chiamata SOAP.

La presenza dell&#39;attributo &quot;static&quot; (con il valore &quot;true&quot;) descrive questo metodo come statico, il che significa che tutti i parametri del metodo devono essere dichiarati.

Un metodo &quot;const&quot; contiene implicitamente un documento XML nel formato del relativo schema associato come input.

Una descrizione completa dell&#39; `<method>` elemento di uno schema di Adobe Campaign  è disponibile nel capitolo &quot;Riferimenti allo schema&quot; in  <a href="../../configuration/using/elements-and-attributes.md#method--element" target="_blank">  `<method>`    element.

Esempio del metodo &quot;const&quot; di tipo &quot;ExecuteQuery&quot; dallo schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

Il parametro di input di questo metodo è un documento XML nel formato dello schema &quot;xtk:queryDef&quot;.

## Descrizione servizio Web: WSDL {#web-service-description--wsdl}

Per ciascun servizio è disponibile un file WSDL (Web Service Description Library). Questo file XML utilizza una lingua metalinguage per descrivere il servizio e specificare i metodi, i parametri disponibili e il server da contattare per l&#39;esecuzione del servizio.

### Generazione di file WSDL {#wsdl-file-generation}

Per generare un file WSDL, è necessario immettere il seguente URL da un browser Web:

[https://`<server>`?/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Con:

* **`<server>`**: il server applicazione del Adobe Campaign  (web nlserver)
* **`<schema>`**: chiave di identificazione dello schema (namespace:nome_schema)

### Esempio del metodo &#39;ExecuteQuery&#39; dello schema &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Il file WSDL viene generato dall&#39;URL:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

Una descrizione WSDL inizia definendo i tipi utilizzati per creare i messaggi, associati in &quot;porte&quot;, connessi a un protocollo tramite &quot;binding&quot; che costituiscono servizi Web.

#### Tipi {#types}

Le definizioni dei tipi si basano sugli schemi XML. Nel nostro esempio, il metodo &quot;ExecuteQuery&quot; utilizza come parametri una stringa &quot;s:string&quot; e un documento XML (`<s:complextype>`). Il valore restituito dal metodo (&quot;ExecuteQueryResponse&quot;) è un documento XML ( `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Messages {#messages}

La `<message>` descrizione descrive i nomi e i tipi di un insieme di campi da inviare. Il metodo utilizza due messaggi per passare come parametro (&quot;ExecuteQueryIn&quot;) e il valore restituito (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

Associa `<porttype>` i messaggi nell&#39;operazione &quot;ExecuteQuery&quot; attivata dalla query (&quot;input&quot;) che genera una risposta (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Binding {#binding}

La `<binding>` parte specifica il protocollo di comunicazione SOAP ( `<soap:binding>` ), il trasporto dei dati in HTTP (valore dell&#39;attributo &quot;trasporto&quot;) e il formato dei dati per l&#39;operazione &quot;ExecuteQuery&quot;. Il corpo della busta SOAP contiene direttamente i segmenti di messaggio senza trasformazione.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Servizio {#service}

La `<service>` parte descrive il servizio &quot;XtkQueryDef&quot; con il relativo URI sull&#39;URL del server dell&#39;applicazione del Adobe Campaign .

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Connettività {#connectivity}

 Adobe Campaign ha aumentato la sicurezza per i meccanismi di autenticazione introducendo le aree di sicurezza (vedere il capitolo **Definizione delle aree** di sicurezza in [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones)) e le impostazioni di gestione delle sessioni.

Sono disponibili due modalità di autenticazione:

* **tramite una chiamata al metodo di accesso()**. Questa modalità genera un token sessione e un token di protezione. È la modalità più sicura e quindi la più consigliata.

o

* **tramite il login  Adobe Campaign + password** per creare un token sessione. Il token di sessione scade automaticamente dopo un determinato periodo. Questa modalità non è consigliata e richiede di ridurre le impostazioni di protezione dell’applicazione per alcune impostazioni di area (allowUserPassword=&quot;true&quot; e sessionTokenOnly=&quot;true&quot;).

### Caratteristiche del token di sessione {#session-token-characteristics}

Il token sessione ha le seguenti caratteristiche:

* un ciclo di vita di X ora (il ciclo di vita è configurabile nel file &#39;serverConf.xml&#39;, il periodo predefinito è 24 ore)
* costruzione casuale (non contiene più il login utente e la password)
* quando si accede tramite Web:

   * il token di sessione diventa un token permanente, non viene distrutto dopo la chiusura del browser
   * viene inserito in un cookie HTTP-ONLY (i cookie devono essere attivati per gli operatori)

### Caratteristiche token di protezione {#security-token-characteristics}

Il token di protezione ha le seguenti caratteristiche:

* viene generato dal token di sessione
* ha un ciclo di vita di 24 ore (configurabile nel file &#39;serverConf.xml&#39;, il periodo predefinito è 24 ore)
* è memorizzato nella console Adobe Campaign 
* quando si accede tramite Web:

   * viene memorizzato in un documento.__securityToken, proprietà
   * gli URL delle pagine vengono aggiornati per aggiornare il token di protezione
   * i moduli vengono anche aggiornati tramite un campo nascosto contenente il token

#### Movimento token di protezione {#security-token-movement}

Quando si accede tramite la console, è:

* trasmesse nella risposta di accesso (nell’intestazione HTTP)
* utilizzato in ogni query (nell’intestazione HTTP)

Da POST e GET HTTP:

* il server completa i collegamenti con il token
* il server aggiunge ai moduli un campo nascosto

Da una chiamata SOAP:

* viene aggiunto alle intestazioni delle chiamate

### Esempi di chiamate {#call-examples}

* Utilizzo di **HttpSoapConnection/SoapService**:

   ```
     var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
   var session = new SoapService(cnx, 'urn:xtk:session');
   session.addMethod("Logon", "xtk:session#Logon",
                       ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                       ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
   
   var res = session.Logon("", "admin", "pwd", <param/>);
   var sessionToken = res[0];
   var securityToken = res[2];
   
   cnx.addTokens(sessionToken, securityToken);
   var query = new SoapService(cnx, 'urn:xtk:queryDef');
   query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                       ["sessiontoken", "string", "entity", "NLElement"],
                       ["res", "NLElement"]);
   
   var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@email = 'joe.doe@aol.com'"/>
             </where>
           </queryDef>);
   logInfo(queryRes[0].toXMLString())
   ```

* Utilizzo di **HttpServletRequest**:

>[!NOTE]
>
>Gli URL utilizzati nelle seguenti chiamate **HttpServletRequest** devono trovarsi nell’elenco di autorizzazioni nella sezione delle autorizzazioni URL del file **serverConf.xml** . Ciò vale anche per l&#39;URL del server stesso.

Esecuzione di accesso():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
  '<soapenv:Header/>' +
  '<soapenv:Body>' +
      '<urn:Logon>' +
          '<urn:sessiontoken></urn:sessiontoken>' +
          '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
          '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
          '<urn:elemParameters></urn:elemParameters>' +
      '</urn:Logon>' +
  '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
         
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Esecuzione della query:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
           '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
              '<queryDef operation="select" schema="nms:recipient">' +
                '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
              '</queryDef>' +
         '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```

