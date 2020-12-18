---
solution: Campaign Classic
product: campaign
title: Descrizione evento del centro messaggi
description: Ulteriori informazioni sull'evento di messaggistica transazionale
audience: message-center
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# Descrizione di un evento{#event-description}

## Informazioni sul modello di dati di messaggistica transazionali {#about-transactional-messaging-datamodel}

I messaggi transazionali si basano sul modello dati Adobe Campaign  e utilizzano due tabelle separate aggiuntive. Queste [tabelle](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** e **NmsBatchEvent** contengono gli stessi campi e consentono di gestire eventi in tempo reale da un lato e gli eventi batch dall&#39;altro.

## Metodi SOAP {#soap-methods}

Questa sezione descrive i metodi SOAP associati agli schemi del modulo dei messaggi transazionali.

Due metodi SOAP **PushEvent** o **PushEvents** sono collegati alle due classi di dati **nms:rtEvent** e **nms:BatchEvent**. È il sistema di informazioni che determina se un evento è di tipo &quot;batch&quot; o &quot;in tempo reale&quot;.

* **** PushEvent consente di inserire un singolo evento nel messaggio,
* **** PushEventslets consente di inserire una serie di eventi nel messaggio.

Il percorso WSDL per l&#39;accesso a entrambi i metodi è:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:** rtEventper accedere allo schema del tipo in tempo reale.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:** batchEventper accedere allo schema del tipo di batch.

Entrambi i metodi contengono un elemento **`<urn:sessiontoken>`** per accedere al modulo di messaggistica transazionale. È consigliabile utilizzare un metodo di identificazione tramite indirizzi IP affidabili. Per recuperare il token di sessione, eseguite una chiamata SOAP di accesso, quindi un token get seguito da un logoff. Utilizzate lo stesso token per diverse chiamate RT. Gli esempi inclusi in questa sezione utilizzano il metodo token sessione consigliato.

Se utilizzate un server con bilanciamento del carico, potete utilizzare l&#39;autenticazione utente/password (a livello del messaggio RT). Esempio:

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

Il metodo **PushEvent** è composto da un parametro **`<urn:domevent>`** che contiene l&#39;evento.

Il metodo **PushEvents** è composto da un parametro **`<urn:domeventcollection>`** che contiene eventi.

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
>In caso di chiamata al metodo **PushEvents**, è necessario aggiungere un elemento XML principale per conformarsi al codice XML standard. Questo elemento XML incornicia i vari elementi **`<rtevent>`** contenuti nell&#39;evento.

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

Gli elementi **`<rtevent>`** e **`<batchevent>`** hanno un insieme di attributi e un elemento figlio obbligatorio: **`<ctx>`** per l&#39;integrazione dei dati dei messaggi.

>[!NOTE]
>
>L&#39;elemento **`<batchevent>`** consente di aggiungere l&#39;evento alla coda &quot;batch&quot;. L&#39; **`<rtevent>`** aggiunge l&#39;evento alla coda &quot;in tempo reale&quot;.

Gli attributi obbligatori degli elementi **`<rtevent>`** e **`<batchevent>`** sono @type e @email. Il valore di @type deve corrispondere al valore elenco dettagliato definito al momento della configurazione dell&#39;istanza di esecuzione. Questo valore consente di definire il modello da collegare al contenuto dell&#39;evento durante la consegna.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

In questo esempio vengono forniti due canali: l’indirizzo e-mail e il numero di telefono cellulare. Il **wishChannel** consente di selezionare il canale da utilizzare per trasformare l&#39;evento in un messaggio. Il valore &quot;0&quot; corrisponde al canale e-mail, il valore &quot;1&quot; al canale mobile, ecc.

Se desiderate posticipare la consegna di un evento, aggiungete il campo **[!UICONTROL scheduled]** seguito dalla data desiderata. L’evento verrà trasformato in un messaggio a tale data.

È consigliabile compilare gli attributi @wishChannel e @emailFormat con valori numerici. La tabella della funzione che collega valori numerici ed etichette si trova nella descrizione dello schema dati.

>[!NOTE]
>
>Una descrizione dettagliata di tutti gli attributi autorizzati e dei relativi valori è disponibile nella descrizione dello schema di dati **nms:rtEvent** e **nms:BatchEvent**.

L&#39;elemento **`<ctx>`** contiene i dati del messaggio. Il contenuto XML è aperto, il che significa che può essere configurato in base al contenuto da distribuire.

>[!NOTE]
>
>È importante ottimizzare il numero e la dimensione dei nodi XML contenuti nel messaggio per evitare di sovraccaricare i server durante la distribuzione.

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

Quando riceve un evento,  Adobe Campaign genera un ID restituito univoco. Questo è l&#39;ID della versione archiviata dell&#39;evento.

>[!IMPORTANT]
>
>Quando ricevete chiamate SOAP,  Adobe Campaign verifica il formato dell&#39;indirizzo e-mail. Se un indirizzo e-mail non è formattato correttamente, viene restituito un errore.

* Esempio di identificatore restituito dal metodo quando l&#39;elaborazione dell&#39;evento ha esito positivo:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

Se il valore dell&#39;identificatore restituito è rigorosamente maggiore di zero, significa che l&#39;evento è stato archiviato correttamente in  Adobe Campaign.

Tuttavia, se l&#39;evento non viene elaborato, il metodo restituisce un messaggio di errore o un valore uguale a zero.

* Esempio di elaborazione di un evento che non è riuscito quando la query non contiene un login o l&#39;operatore specificato non dispone dei diritti richiesti:

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

* Esempio di un evento che non è riuscito a causa di un errore nella query (la classificazione XML non è rispettata):

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

* Esempio di evento che ha avuto esito negativo e ha restituito un identificatore zero (nome metodo errato):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

