---
solution: Campaign Classic
product: campaign
title: Errore di connessione
description: Errore di connessione
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: fc5a44fe7bf4c88eca4634a67eaae48c722d8e5e
workflow-type: tm+mt
source-wordcount: '337'
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
<td>Accedi a: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Il server deve restituire il seguente tipo di messaggio: &lt;redir status='OK' date='AAAA/MM/GG HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;Se non si ottiene questo risultato, verificare nella configurazione del server Web che l'integrazione è presa in considerazione.</td>
</tr>
<tr> 
<td>Connettiti al seguente URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se viene visualizzato un errore Tomcat Java, verificate che l'integrazione JAVA sia stata eseguita correttamente. È integrato nel file [percorso dell'applicazione]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Connettiti al seguente URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Se si ottiene una pagina vuota, verificare se il modulo Web  Adobe Campaign è avviato. Il comando nlserver pdump deve restituire Application Server per Adobe Campaign Classic (build 7.X AA.R XXX@SHA1) di DD/MM/YYYY. In caso contrario, riavviare il modulo con il comando nlserver avviare il Web</td>
</tr>
<tr>
<td>Controllare la configurazione generale delle zone di protezione.</td>
<td>Per ulteriori informazioni sulla configurazione delle aree di protezione, consultate [questa sezione](../../installation/using/configuring-campaign-server.md#Defining-security-zone)</td>
</tr>
</tbody> 
</table>
