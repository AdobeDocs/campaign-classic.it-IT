---
product: campaign
title: Chiamate per servizi web
description: Chiamate per servizi web
audience: configuration
content-type: reference
topic-tags: api
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Chiamate per servizi web{#web-service-calls}

![](../../assets/v7-only.svg)

## Informazioni generali {#general-information}

Tutti i metodi API sono presentati sotto forma di servizi Web. Questo consente di gestire tutte le funzioni di Adobe Campaign tramite chiamate SOAP, che rappresentano il punto di ingresso nativo dell’application server di Adobe Campaign. La console di Adobe Campaign utilizza solo chiamate SOAP.

I servizi Web consentono di creare più applicazioni da un sistema di terze parti:

* Avvisi sincroni, notifiche ed esecuzione di modelli di consegna in tempo reale da un back office o da un sistema di transazione,
* Sviluppo di interfacce speciali con funzionalità semplificate (interfacce web, ecc.),
* L&#39;alimentazione e la ricerca dei dati nella banca dati, osservando le regole commerciali e rimanendo isolati dal modello fisico sottostante.

## Definizione dei servizi web {#definition-of-web-services}

La definizione dei servizi Web implementati sul server applicazioni Adobe Campaign è disponibile dagli schemi di dati.

Un servizio Web è descritto nella grammatica degli schemi di dati ed è disponibile nella sezione **`<methods>`** elemento.

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

Ecco un esempio della definizione del metodo chiamato **GeneraModulo**.

La descrizione del servizio inizia con `<method>` elemento. L&#39;elenco dei parametri del metodo è completato dal  `<parameters>` elemento. Ogni parametro è specificato da un nome, un tipo (booleano, stringa, DOMElement, ecc.) e una descrizione. L’attributo &quot;inout&quot; con il valore &quot;out&quot; ti consente di specificare che il parametro &quot;result&quot; si trova nell’output di chiamata SOAP.

La presenza dell&#39;attributo &quot;static&quot; (con il valore &quot;true&quot;) descrive questo metodo come statico, il che significa che tutti i parametri del metodo devono essere dichiarati.

Un metodo &quot;const&quot; ha implicitamente un documento XML nel formato del relativo schema associato come input.

Una descrizione completa del `<method>` l’elemento di uno schema Adobe Campaign è disponibile nel capitolo &quot;Riferimenti allo schema&quot; in [Metodo](../../configuration/using/schema/method.md)

Esempio del metodo &quot;ExecuteQuery&quot; di tipo &quot;const&quot; dallo schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

Il parametro di input di questo metodo è un documento XML nel formato dello schema &quot;xtk:queryDef&quot;.

## Descrizione del servizio Web: WSDL {#web-service-description--wsdl}

Per ogni servizio è disponibile un file WSDL (Web Service Description Library). Questo file XML utilizza una metalanguage per descrivere il servizio e specificare i metodi, i parametri e il server disponibili da contattare per l&#39;esecuzione del servizio.

### Generazione di file WSDL {#wsdl-file-generation}

Per generare un file WSDL, è necessario immettere l’URL seguente da un browser Web:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Con:

* **`<server>`**: server applicazioni Adobe Campaign (web nlserver)
* **`<schema>`**: chiave di identificazione dello schema (namespace:nome_schema)

### Esempio sul metodo &#39;ExecuteQuery&#39; dello schema &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Il file WSDL viene generato dall’URL:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

Una descrizione WSDL inizia definendo i tipi utilizzati per la creazione dei messaggi, associati nelle &quot;porte&quot;, collegati a un protocollo mediante i &quot;binding&quot; che formano i servizi Web.

#### Tipi {#types}

Le definizioni dei tipi si basano su schemi XML. Nel nostro esempio, il metodo &quot;ExecuteQuery&quot; utilizza una stringa &quot;s:string&quot; e un documento XML (`<s:complextype>`) come parametri. Il valore restituito del metodo (&quot;ExecuteQueryResponse&quot;) è un documento XML (  `<s:complextype>`).

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

#### Messaggi {#messages}

La `<message>` descrive i nomi e i tipi di un insieme di campi da inviare. Il metodo utilizza due messaggi da trasmettere come parametro (&quot;ExecuteQueryIn&quot;) e come valore restituito (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### TipoPorta {#porttype}

La `<porttype>` associa i messaggi sull&#39;operazione &quot;ExecuteQuery&quot; attivata dalla query (&quot;input&quot;) che genera una risposta (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Binding {#binding}

La `<binding>` part specifica il protocollo di comunicazione SOAP ( `<soap:binding>` ), il trasporto dei dati in HTTP (valore dell&#39;attributo &quot;transport&quot;) e il formato dei dati per l&#39;operazione &quot;ExecuteQuery&quot;. Il corpo dell’inviluppo SOAP contiene i segmenti di messaggio direttamente senza trasformazione.

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

La `<service>` in questa sezione viene descritto il servizio &quot;XtkQueryDef&quot; con il relativo URI sull&#39;URL del server dell&#39;applicazione Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Connettività {#connectivity}

Adobe Campaign ha aumentato la sicurezza dei meccanismi di autenticazione introducendo [zone di sicurezza](../../installation/using/security-zones.md) e le impostazioni di gestione delle sessioni.

Sono disponibili due modalità di autenticazione:

* **tramite una chiamata al metodo di accesso()**. Questa modalità genera un token di sessione e un token di sicurezza. È la modalità più sicura e quindi la più consigliata.

o

* **tramite l’accesso Adobe Campaign + password** che crea un token di sessione. Il token di sessione scade automaticamente dopo un periodo impostato. Questa modalità non è consigliata e richiede la riduzione delle impostazioni di sicurezza dell&#39;applicazione per alcune impostazioni di zona (allowUserPassword=&quot;true&quot; e sessionTokenOnly=&quot;true&quot;).

### Caratteristiche del token di sessione {#session-token-characteristics}

Il token di sessione ha le seguenti caratteristiche:

* un ciclo di vita di X ore (il ciclo di vita è configurabile nel file &#39;serverConf.xml&#39;, il periodo predefinito è 24 ore)
* una costruzione casuale (non contiene più il login utente e la password)
* quando si accede tramite il Web:

   * il token di sessione diventa un token permanente e non viene distrutto dopo la chiusura del browser
   * viene posizionato in un cookie HTTP-ONLY (i cookie devono essere attivati per gli operatori)

### Caratteristiche del token di sicurezza {#security-token-characteristics}

Il token di sicurezza ha le seguenti caratteristiche:

* viene generato dal token di sessione
* ha un ciclo di vita di 24 ore (configurabile nel file &#39;serverConf.xml&#39;, il periodo predefinito è 24 ore)
* viene memorizzato nella console Adobe Campaign
* quando si accede tramite il Web:

   * viene memorizzato in un documento.__securityToken, proprietà
   * gli URL della pagina vengono aggiornati per aggiornare il token di sicurezza
   * i moduli vengono inoltre aggiornati tramite un campo nascosto contenente il token

#### Movimento token di sicurezza {#security-token-movement}

Se accessibile tramite la console, è:

* trasmesso nella risposta di accesso (nell&#39;intestazione HTTP)
* utilizzato in ogni query (nell’intestazione HTTP)

Da un POST e GET HTTP:

* il server completa i collegamenti con il token
* il server aggiunge un campo nascosto ai moduli

Da una chiamata SOAP:

* viene aggiunto alle intestazioni di chiamata

### Esempi di chiamata {#call-examples}

* Utilizzo **HttpSoapConnection/SoapService**:

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

* Utilizzo **HttpServletRequest**:

>[!NOTE]
>
>URL utilizzati nei seguenti **HttpServletRequest** le chiamate devono essere su elenco Consentiti nella sezione delle autorizzazioni url del **serverConf.xml** file. Questo vale anche per l’URL del server stesso.

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
