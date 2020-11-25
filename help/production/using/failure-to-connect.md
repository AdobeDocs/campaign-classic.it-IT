---
solution: Campaign Classic
product: campaign
title: Errore di connessione
description: Errore di connessione
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 57063c1ed0100b171bda93e273c399c40d8e980a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# Errore di connessione{#failure-to-connect}

I motivi di un problema di connessione possono essere molteplici e dipendono da diversi contesti.

È possibile provare i seguenti test e se il problema di connessione persiste, contattare il supporto **Adobe Campaign**.



<table> 
 <thead> 
  <tr> 
   <th>Verifiche<br /> </th> 
   <th>Risoluzione<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td>Avete accesso a Internet dal vostro computer?</td> 
   <td>Verificate che sia possibile connettersi ai siti Web in Internet (ad esempio). Se non riuscite a connettervi, il problema è sul computer. Contattate l’amministratore di sistema.</td>
  </tr>
  <tr> 
   <td>È possibile connettersi al server che ospita  Adobe Campaign tramite un altro servizio?</td> 
   <td>Connettersi al server tramite SSH o altri mezzi. Se questo non è possibile, la società ospitante ha un problema. Contattare l'amministratore di sistema.</td>
  </tr>
  <tr> 
   <td>Il server Web risponde?</td> 
   <td>Collegarsi all'URL di accesso  server Adobe Campaign utilizzando un browser Web: <b>http(s):// &lt;urlserver&gt;</b>. Se non risponde, il server Web viene arrestato sul computer. Per riavviare il servizio, contattare l'amministratore di sistema della società host.</td>
  </tr>
  <tr> 
   <td> Adobe Campaign è stato integrato correttamente?</td> 
   <td>Accedi a: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Il server deve restituire il seguente tipo di messaggio:

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;AAAA/MM/GG HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
Se non si ottiene questo risultato, verificare nella configurazione del server Web che l&#39;integrazione viene presa in considerazione.</td>
</tr>
  <tr> 
   <td>È stato avviato il modulo Web  Adobe Campaign?</td> 
   <td>Connettiti al seguente URL: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Se viene visualizzato un errore Java Tomcat:

L&#39;integrazione JAVA viene eseguita correttamente?  Adobe Campaign richiede un JDK SOLE.

È integrato nel [percorso file dell&#39;applicazione]/nl6/customer.sh

* Se ottenete una pagina vuota:
È stato avviato il modulo Web  Adobe Campaign? È necessario ottenere:

<pre>
nlserver pdumpHH:MM:SS &gt; Application server per Adobe Campaign Classic (build 7.X AA.R XXX@SHA1) di DD/MM/YYYYY[...]web@default (27515) - 55.2 Mb[...]
</pre>
* In caso contrario, riavviarlo utilizzando il comando seguente:

<pre>        
web di avvio del server
</pre>
</td>
</tr>
  <tr>
  	<td>Controllare la configurazione generale delle zone di protezione.</td>
  	<td>Per ulteriori informazioni sulla configurazione delle aree di protezione, consultate [questa sezione](../../installation/using/configuring-campaign-server.md#Defining-security-zone)</td>
  </tr>
 </tbody> 
</table>
