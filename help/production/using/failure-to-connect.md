---
product: campaign
title: Errore di connessione
description: Errore di connessione
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 4%

---

# Errore di connessione{#failure-to-connect}



I motivi di un problema di connessione possono essere molteplici e dipendere da vari contesti.

Puoi provare i seguenti test e se l&#39;errore di connessione persiste, contatta il [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>Controlli<br /> </th> 
<th>Risoluzione<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Hai accesso a Internet dal tuo computer?</td> 
<td>Verificare che sia possibile connettersi ai siti web su Internet (ad esempio). Se non è possibile connettersi, il problema è sul computer. Contattare l'amministratore di sistema.</td>
</tr>
<tr> 
<td>Puoi connetterti al server che ospita Adobe Campaign tramite un altro servizio?</td> 
<td>Connettersi al server tramite SSH o qualsiasi altro mezzo. Se questo non è possibile, la società host ha un problema. Contattare l'amministratore di sistema.</td>
</tr>
<tr> 
<td>Il server web risponde?</td> 
<td>Connettiti all’URL di accesso al server Adobe Campaign utilizzando un browser Web: <b>http(s):// &lt;urlserver&gt;</b>. Se non risponde, il server Web viene arrestato sul computer. Per riavviare il servizio, contatta l'amministratore di sistema della società host.</td>
</tr>
<tr> 
<td>Adobe Campaign è stato integrato correttamente?</td> 
<td>Accedi a: <b>http(s)://&lt;urlserver&gt;/r/test</b> URL. Il server deve restituire il seguente tipo di messaggio: &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
Se non si ottiene questo risultato, verificare nella configurazione del server Web che l'integrazione è presa in considerazione.:MM:</td>
</tr>
<tr> 
<td>Collegati al seguente URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Se ottieni un errore Tomcat Java, controlla se l'integrazione JAVA viene eseguita correttamente. È integrato nel file [percorso dell'applicazione]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Collegati al seguente URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>Se si ottiene una pagina vuota, verificare se il modulo Web Adobe Campaign è avviato. Il comando nlserver pdump deve restituire Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) di DD/MM/YYYY. In caso contrario, riavvia il modulo con il comando nlserver start web</td>
</tr>
<tr>
<td>Controllare la configurazione generale delle aree di protezione.</td>
<td>Per ulteriori informazioni sulla configurazione delle aree di protezione, consulta <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>questa sezione.</a></td>
</tr>
<tr>
<td>Il comando nlserver pdump restituisce <b>Nessuna attività</b></td>
<td>È necessario riavviare l'intera applicazione Adobe Campaign. A questo scopo, utilizza il seguente comando: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
