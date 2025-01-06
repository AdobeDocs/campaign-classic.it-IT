---
product: campaign
title: Descrizione di un evento
description: Scopri come gli eventi di messaggistica transazionale vengono gestiti in Adobe Campaign Classic utilizzando i metodi SOAP
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: 9f7f4b6c-2ee8-4091-847d-f616d6abeb6b
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 0%

---

# Descrizione di un evento {#event-description}



## Modello dati di messaggistica transazionale {#about-transactional-messaging-datamodel}

La messaggistica transazionale si basa sul modello dati di Adobe Campaign e utilizza due tabelle separate aggiuntive. Queste [tabelle](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** e **NmsBatchEvent** contengono gli stessi campi e consentono di gestire eventi in tempo reale da un lato e eventi batch dall&#39;altro.

## Metodi SOAP {#soap-methods}

Questa sezione descrive i metodi SOAP associati agli schemi del modulo dei messaggi transazionali.

Due metodi SOAP **PushEvent** o **PushEvents** sono collegati ai due dataschemi **nms:rtEvent** e **nms:BatchEvent**. È il sistema informativo che determina se un evento è di tipo &quot;batch&quot; o &quot;tempo reale&quot;.

* **PushEvent** consente di inserire un singolo evento nel messaggio,
* **PushEvents** consente di inserire una serie di eventi nel messaggio.

Il percorso WSDL per l&#39;accesso a entrambi i metodi è:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** per accedere allo schema dei tipi in tempo reale.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** per accedere allo schema del tipo di batch.

Per ulteriori informazioni sulla generazione di un file WSDL, vedere [questa sezione](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

Entrambi i metodi contengono un elemento **`<urn:sessiontoken>`** per l&#39;accesso al modulo di messaggistica transazionale. È consigliabile utilizzare un metodo di identificazione tramite indirizzi IP attendibili. Per recuperare il token di sessione, esegui una chiamata SOAP di accesso, quindi un token GET seguito da una disconnessione. Utilizza lo stesso token per diverse chiamate RT. Gli esempi inclusi in questa sezione utilizzano il metodo del token di sessione consigliato.

Se utilizzi un server con bilanciamento del carico, puoi utilizzare l’autenticazione Utente/Password (a livello del messaggio RT). Esempio:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

Il metodo **PushEvent** è costituito da un parametro **`<urn:domevent>`** che contiene l&#39;evento.

Il metodo **PushEvents** è costituito da un parametro **`<urn:domeventcollection>`** contenente eventi.

Esempio di utilizzo di PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>In caso di chiamata al metodo **PushEvents**, è necessario aggiungere un elemento XML padre per garantire la conformità con l&#39;XML standard. Questo elemento XML inquadrerà i vari elementi **`<rtevent>`** contenuti nell&#39;evento.

Esempio di utilizzo di PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

Gli elementi **`<rtevent>`** e **`<batchevent>`** hanno un set di attributi e un elemento figlio obbligatorio: **`<ctx>`** per l&#39;integrazione dei dati del messaggio.

>[!NOTE]
>
>L&#39;elemento **`<batchevent>`** consente di aggiungere l&#39;evento alla coda &quot;batch&quot;. **`<rtevent>`** aggiunge l&#39;evento alla coda in tempo reale.

Gli attributi obbligatori degli elementi **`<rtevent>`** e **`<batchevent>`** sono @type e @email. Il valore di @type deve essere uguale al valore dell’elenco dettagliato definito durante la configurazione dell’istanza di esecuzione. Questo valore ti consente di definire il modello da collegare al contenuto dell’evento durante la consegna.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

In questo esempio, vengono forniti due canali: l’indirizzo e-mail e il numero di telefono cellulare. **wwishChannel** consente di selezionare il canale da utilizzare per trasformare l&#39;evento in un messaggio. Il valore &quot;0&quot; corrisponde al canale e-mail, il valore &quot;1&quot; al canale mobile e così via.

Se desideri posticipare la consegna di un evento, aggiungi il campo **[!UICONTROL scheduled]** seguito dalla data preferita. L’evento verrà trasformato in un messaggio in questa data.

È consigliabile compilare gli attributi @wishedChannel e @emailFormat con valori numerici. La tabella delle funzioni che collega i valori numerici e le etichette si trova nella descrizione dello schema di dati.

>[!NOTE]
>
>Una descrizione dettagliata di tutti gli attributi autorizzati e dei relativi valori è disponibile nella descrizione dello schema dati **nms:rtEvent** e **nms:BatchEvent**.

L&#39;elemento **`<ctx>`** contiene i dati del messaggio. Il contenuto XML è aperto, il che significa che può essere configurato a seconda del contenuto da distribuire.

>[!NOTE]
>
>È importante ottimizzare il numero e le dimensioni dei nodi XML contenuti nel messaggio per evitare di sovraccaricare i server durante la consegna.

Esempio di dati:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
```

## Informazioni restituite dalla chiamata SOAP {#information-returned-by-the-soap-call}

Quando riceve un evento, Adobe Campaign genera un ID restituito univoco. Questo è l’ID della versione archiviata dell’evento.

>[!IMPORTANT]
>
>Quando ricevi chiamate SOAP, Adobe Campaign verifica il formato dell’indirizzo e-mail. Se un indirizzo e-mail non è formattato correttamente, viene restituito un errore.

* Esempio di un identificatore restituito dal metodo quando l’elaborazione dell’evento ha esito positivo:

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">72057594037935966</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

Se il valore dell’identificatore restituito è rigorosamente maggiore di zero, significa che l’evento è stato archiviato correttamente in Adobe Campaign.

Tuttavia, se l&#39;evento non viene elaborato, il metodo restituisce un messaggio di errore o un valore uguale a zero.

* Esempio di elaborazione di un evento non riuscito quando la query non contiene un account di accesso o l’operatore specificato non dispone dei diritti necessari:

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
           <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Esempio di un evento non riuscito a causa di un errore nella query (la classificazione XML non è rispettata):

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <SOAP-ENV:Fault>
           <faultcode>SOAP-ENV:Client</faultcode>
           <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
           <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
  Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
     <soapenv:Header/>
     <soapenv:Body>
        <urn:PushEvent>
           <urn:sessiontoken>mc/</urn:sessiontoken>
           <urn:domEvent>
  <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
        externalId="1596" language="english" country="EN" emailFormat="2"
        mobilePhone="+447700123123">
    <ctx>
     <website name="eCommerce" url="http://www.eCo']]></detail>
        </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Esempio di un evento non riuscito e che ha restituito un identificatore zero (nome di metodo errato):

  ```
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
     <SOAP-ENV:Body>
        <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
           <plId xsi:type="xsd:long">0</plId>
        </urn:PushEventResponse>
     </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
