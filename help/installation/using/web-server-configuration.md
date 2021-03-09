---
solution: Campaign Classic
product: campaign
title: Configurazione server web
description: Ulteriori informazioni sulle best practice principali per la configurazione del server web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Configurazione server web {#web-server-configuration}

Di seguito sono riportate alcune delle best practice principali relative alla configurazione del server web (Apache/IIS).

* Modificare le pagine di errore predefinite.

* Disattiva la versione e i codici SSL precedenti:

   **Su Apache**, modifica /etc/apache2/mods-available/ssl.conf. Ecco un esempio:

   * SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **In IIS**  (consulta la  [documentazione](https://support.microsoft.com/en-us/kb/245030)), esegui la seguente configurazione:

   * Aggiungi la sottochiave del Registro di sistema in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Per consentire al sistema di utilizzare i protocolli che non saranno negoziati per impostazione predefinita (ad esempio TLS 1.2), cambia i dati del valore DWORD del valore DisabledByDefault in 0x0 nelle seguenti chiavi del Registro di sistema sotto la chiave **Protocols**:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Disattiva SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client DisabledByDefault: Valore DWORD (32 bit) a 1

   SCHANNEL\Protocols\SSL 3.0\Server Abilitato: Valore DWORD (32 bit) a 0

* Rimuovi il metodo **TRACE** :

   **Su Apache**, modifica in /etc/apache2/conf.d/security: TraceEnable  **Off**

   **In IIS**  (consulta la  [documentazione](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), esegui la seguente configurazione:

   * Assicurati che sia installato il servizio o la funzione **Richiedi filtro** .
   * Nel riquadro **Filtro richieste**, fare clic sulla scheda Verbi HTTP e quindi fare clic su Nega verbo. Nel riquadro Azioni, immettere TRACE nella finestra di dialogo aperta.

* Rimuovi il banner:

   **Su Apache**, modifica /etc/apache2/conf.d/security:

   * Firma server **Off**
   * Token server **Prod**

   **In IIS**  (consulta la  [documentazione](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), esegui la seguente configurazione:

   * Installa **URLScan**.
   * Modifica il file **Urlscan.ini** per avere **RemoveServerHeader=1**


* Limita le dimensioni della query per impedire il caricamento di file importanti:

   **Su Apache**  (consulta la  [documentazione](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody)), aggiungi la direttiva  **** LimitRequestBodyDirective (dimensione in byte) nella directory / .

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **In IIS**  (consulta la  [documentazione](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), imposta  **maxAllowedContentLength**  (lunghezza massima consentita per il contenuto) nelle opzioni di filtro del contenuto.

Argomenti correlati:

* [Panoramica sulla conformità Adobe Marketing Cloud](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  (PDF)
* [Panoramica sulla sicurezza di Adobe Campaign](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  (PDF)
