---
product: campaign
title: Configurazione server web
description: Ulteriori informazioni sulle best practice principali per la configurazione del server web
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Configurazione server web {#web-server-configuration}



Di seguito sono riportate alcune delle best practice principali relative alla configurazione del server web (Apache/IIS).

* Modificare le pagine di errore predefinite.

* Disattiva la versione SSL e le crittografie precedenti:

  **In Apache**, modifica /etc/apache2/mods-available/ssl.conf. Ecco un esempio:

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **In IIS** (vedi la [documentazione](https://support.microsoft.com/en-us/kb/245030)), esegui la seguente configurazione:

   * Aggiungi sottochiave del Registro di sistema in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Per consentire al sistema di utilizzare i protocolli che non verranno negoziati per impostazione predefinita (ad esempio TLS 1.2), modificare i dati del valore DWORD del valore DisabledByDefault su 0x0 nelle seguenti chiavi del Registro di sistema nella chiave **Protocols**:

     SCHANNEL\Protocolli\TLS 1.2\Client

     SCHANNEL\Protocolli\TLS 1.2\Server

  **Disabilita SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: valore DWORD (32 bit) su 1

  SCHANNEL\Protocolli\SSL 3.0\Server: abilitato: valore DWORD (32 bit) su 0

* Rimuovi il metodo **TRACE**:

  **Su Apache**, modifica in /etc/apache2/conf.d/security: TraceEnable **Off**

  **In IIS** (vedi la [documentazione](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), esegui la seguente configurazione:

   * Verificare che la funzionalità o il servizio ruolo **Filtro richieste** sia installato.
   * Nel riquadro **Filtro richieste** fare clic sulla scheda Verbi HTTP e quindi su Nega verbo. Nel riquadro Azioni, immettere TRACE nella finestra di dialogo aperta.

* Rimuovi il banner:

  **In Apache**, modificare /etc/apache2/conf.d/security:

   * Firma server **disattivata**
   * ServerTokens **Prod**

  **In IIS**, eseguire la configurazione seguente:

   * Installa **URLScan**.
   * Modifica il file **Urlscan.ini** in modo che abbia **RemoveServerHeader=1**

* Limita le dimensioni delle query per impedire il caricamento di file importanti:

  **Su Apache**, aggiungi la direttiva **LimitRequestBody** (dimensione in byte) nella directory /.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **In IIS** (vedi la [documentazione](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), imposta **maxAllowedContentLength** (lunghezza massima consentita per il contenuto) nelle opzioni di filtro del contenuto.

Argomenti correlati:

* [Panoramica sulla conformità di Adobe Marketing Cloud](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Panoramica sulla sicurezza di Adobe Campaign](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)
