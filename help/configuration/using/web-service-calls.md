---
product: campaign
title: Chiamate per servizi web
description: Chiamate per servizi web
feature: API
role: Developer
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 1%

---

# Chiamate per servizi web{#web-service-calls}

## Informazioni generali {#general-information}

Tutti i metodi API sono presentati sotto forma di servizi web. Questo consente di gestire tutte le funzioni di Adobe Campaign tramite chiamate SOAP, che rappresentano il punto di ingresso nativo del server applicazioni Adobe Campaign. La console Adobe Campaign utilizza solo chiamate SOAP.

I servizi Web consentono di creare molte applicazioni da un sistema di terze parti:

* Avvisi sincroni, notifiche ed esecuzione di modelli di consegna in tempo reale da un back office o da un sistema di transazioni.
* sviluppo di interfacce speciali con funzionalità semplificate (interfacce web, ecc.),
* Invio e ricerca di dati nel database, nel rispetto delle regole commerciali, e isolamento dal modello fisico sottostante.

## Definizione di servizi web {#definition-of-web-services}

La definizione dei servizi Web implementati nel server applicazioni Adobe Campaign è disponibile negli schemi di dati.

Un servizio Web è descritto nella grammatica degli schemi di dati ed è disponibile dall&#39;elemento **`<methods>`**.

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

Ecco un esempio della definizione del metodo denominato **GenerateForm**.

La descrizione del servizio inizia con l&#39;elemento `<method>`. L&#39;elenco dei parametri del metodo è completato dall&#39;elemento `<parameters>`. Ogni parametro è specificato da un nome, un tipo (booleano, stringa, DOMElement, ecc.) e una descrizione. L’attributo &quot;inout&quot; con il valore &quot;out&quot; consente di specificare che il parametro &quot;result&quot; si trova nell’output della chiamata SOAP.

La presenza dell’attributo &quot;static&quot; (con il valore &quot;true&quot;) descrive questo metodo come static, il che significa che tutti i parametri del metodo devono essere dichiarati.

Un metodo &quot;const&quot; ha implicitamente un documento XML nel formato dello schema associato come input.

Una descrizione completa dell&#39;elemento `<method>` di uno schema Adobe Campaign è disponibile nel capitolo &quot;Riferimenti schema&quot; in [Metodo](../../configuration/using/schema/method.md)

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

## Descrizione servizio Web: WSDL {#web-service-description--wsdl}

Per ogni servizio è disponibile un file WSDL (Web Service Description Library). Questo file XML utilizza un metalinguaggio per descrivere il servizio e specificare i metodi, i parametri e il server disponibili da contattare per l&#39;esecuzione del servizio.

### Generazione di file WSDL {#wsdl-file-generation}

Per generare un file WSDL, è necessario immettere l&#39;URL seguente da un browser Web:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Con:

* **`<server>`**: server applicazioni Adobe Campaign (nlserver web)
* **`<schema>`**: chiave di identificazione dello schema (spazio dei nomi:schema_name)

### Esempio sul metodo &#39;ExecuteQuery&#39; dello schema &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Il file WSDL viene generato dall&#39;URL:

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

Una descrizione WSDL inizia definendo i tipi utilizzati per la creazione dei messaggi, associati in &quot;porte&quot;, connessi a un protocollo mediante &quot;binding&quot; che formano i servizi Web.

#### Tipi {#types}

Le definizioni dei tipi si basano su schemi XML. Nel nostro esempio, il metodo &quot;ExecuteQuery&quot; accetta una stringa &quot;s:string&quot; e un documento XML (`<s:complextype>`) come parametri. Il valore restituito dal metodo (&quot;ExecuteQueryResponse&quot;) è un documento XML ( `<s:complextype>`).

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

`<message>` descrive i nomi e i tipi di un set di campi da inviare. Il metodo utilizza due messaggi da passare come parametro (&quot;ExecuteQueryIn&quot;) e il valore restituito (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

`<porttype>` associa i messaggi sull&#39;operazione &quot;ExecuteQuery&quot; attivata dalla query (&quot;input&quot;) che genera una risposta (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Binding {#binding}

La parte `<binding>` specifica il protocollo di comunicazione SOAP ( `<soap:binding>` ), il trasporto dei dati in HTTP (valore dell&#39;attributo &quot;transport&quot;) e il formato dei dati per l&#39;operazione &quot;ExecuteQuery&quot;. Il corpo della busta SOAP contiene i segmenti del messaggio direttamente senza trasformazione.

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

La parte `<service>` descrive il servizio &quot;XtkQueryDef&quot; con il relativo URI nell&#39;URL del server applicazioni Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Connettività {#connectivity}

Adobe Campaign ha aumentato la sicurezza per i meccanismi di autenticazione introducendo [aree di sicurezza](../../installation/using/security-zones.md) e impostazioni di gestione delle sessioni.

Sono disponibili due modalità di autenticazione:

* **tramite chiamata al metodo di accesso()**. Questa modalità genera un token di sessione e un token di sicurezza. È la modalità più sicura e quindi la più consigliata.

o

* **tramite l&#39;accesso Adobe Campaign + password** che crea un token di sessione. Il token di sessione scade automaticamente dopo un periodo impostato. Questa modalità non è consigliata e richiede la riduzione delle impostazioni di protezione dell&#39;applicazione per alcune impostazioni di zona (allowUserPassword=&quot;true&quot; e sessionTokenOnly=&quot;true&quot;).

### Caratteristiche del token di sessione {#session-token-characteristics}

Il token di sessione presenta le seguenti caratteristiche:

* un ciclo di vita di X ore (il ciclo di vita è configurabile nel file &quot;serverConf.xml&quot;; il periodo predefinito è di 24 ore)
* una costruzione casuale (non contiene più il login utente e la password)
* quando si accede tramite il Web:

   * il token di sessione diventa un token permanente e non viene eliminato una volta chiuso il browser
   * viene inserito in un cookie solo HTTP (i cookie devono essere attivati per gli operatori)

### Caratteristiche del token di sicurezza {#security-token-characteristics}

Il token di sicurezza presenta le seguenti caratteristiche:

* viene generato dal token di sessione
* ha un ciclo di vita di 24 ore (configurabile nel file &quot;serverConf.xml&quot;, il periodo predefinito è di 24 ore)
* viene memorizzato nella console Adobe Campaign
* quando si accede tramite il Web:

   * viene memorizzato in un documento.__securityToken, proprietà
   * gli URL della pagina vengono aggiornati per aggiornare il token di sicurezza
   * i moduli vengono aggiornati anche tramite un campo nascosto contenente il token

#### Spostamento dei token di sicurezza {#security-token-movement}

Se vi si accede tramite la console, si ottiene:

* trasmesse nella risposta di accesso (nell’intestazione HTTP)
* utilizzato in ogni query (nell’intestazione HTTP)

Da un HTTP POST e GET:

* il server completa i collegamenti con il token
* il server aggiunge un campo nascosto ai moduli

Da una chiamata SOAP:

* viene aggiunto alle intestazioni di chiamata

### Esempi di chiamata {#call-examples}

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
>Gli URL utilizzati nelle seguenti **chiamate HttpServletRequest** devono essere elenchi Consentiti nella sezione delle autorizzazioni URL del file **serverConf.xml**. Questo vale anche per l’URL del server stesso.

Esecuzione accesso:

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

Esecuzione query:

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
