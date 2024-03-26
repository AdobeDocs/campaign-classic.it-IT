---
product: campaign
title: Errore di connessione
description: Errore di connessione
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 4%

---

# Errore di connessione{#failure-to-connect}



I motivi di un problema di connessione possono essere molteplici e dipendere da vari contesti.

Puoi provare i seguenti test e, se l’errore di connessione persiste, contatta il [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Verifiche<br /> </th> 
<th>Risoluzione<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Hai accesso a Internet dal tuo computer?</td> 
<td>Verificare che sia possibile connettersi a siti Web su Internet (ad esempio). Se non riesci a connetterti, il problema è sul computer. Contattare l'amministratore di sistema.</td>
</tr>
<tr> 
<td>È possibile connettersi al server che ospita Adobe Campaign tramite un altro servizio?</td> 
<td>Connettersi al server tramite SSH o in qualsiasi altro modo. Se ciò non è possibile, si è verificato un problema nell'azienda ospitante. Contatta l’amministratore di sistema.</td>
</tr>
<tr> 
<td>Il server Web risponde?</td> 
<td>Connettersi all’URL di accesso al server Adobe Campaign utilizzando un browser Web: <b>http(s):// &lt;urlserver&gt;</b>. Se non risponde, il server Web viene arrestato sul computer. Contattare l'amministratore di sistema della società host per riavviare il servizio.</td>
</tr>
<tr> 
<td>Adobe Campaign è stato integrato correttamente?</td> 
<td>Accedi a: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Il server deve restituire il seguente tipo di messaggio: &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
Se non ottieni questo risultato, verifica nella configurazione del server web che l’integrazione sia presa in considerazione.:MM:</td>
</tr>
<tr> 
<td>Connetti al seguente URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Se ricevi un errore Java Tomcat, verifica che l’integrazione JAVA sia eseguita correttamente. È integrato nel file [percorso dell’applicazione]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Connetti al seguente URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Se ottieni una pagina vuota, controlla se il modulo Web Adobe Campaign è stato avviato. Il comando nlserver pdump deve restituire Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) di GG/MM/AAAA. In caso contrario, riavviare il modulo con il comando nlserver start web</td>
</tr>
<tr>
<td>Controllare la configurazione generale delle aree di protezione.</td>
<td>Per ulteriori informazioni sulla configurazione delle aree di protezione, consulta <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>questa sezione.</a></td>
</tr>
<tr>
<td>Il comando nlserver pdump restituisce <b>Nessuna attività</b></td>
<td>È necessario riavviare l'intera applicazione Adobe Campaign. A questo scopo, utilizza il seguente comando: <b>watchdog nlserver -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
