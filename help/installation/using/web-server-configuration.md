---
product: campaign
title: Configurazione server web
description: Ulteriori informazioni sulle best practice principali per la configurazione del server web.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 3709aaf0543a50ff6c2e65a75e7189ab805cd742
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Configurazione server web {#web-server-configuration}

![](../../assets/v7-only.svg)

Di seguito sono riportate alcune delle best practice principali relative alla configurazione del server web (Apache/IIS).

* Modificare le pagine di errore predefinite.

* Disattiva la versione e i codici SSL precedenti:

   **Su Apache**, modifica /etc/apache2/mods-available/ssl.conf. Ecco un esempio:

   * SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **In IIS** (vedi [documentazione](https://support.microsoft.com/en-us/kb/245030)), esegui la seguente configurazione:

   * Aggiungi la sottochiave del Registro di sistema in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Per consentire al sistema di utilizzare i protocolli che non saranno negoziati per impostazione predefinita (ad esempio TLS 1.2), cambia i dati del valore DWORD del valore DisabledByDefault in 0x0 nelle seguenti chiavi del Registro di sistema sotto la **Protocolli** chiave:

      SCHANNEL\Protocolli\TLS 1.2\Client

      SCHANNEL\Protocolli\TLS 1.2\Server
   **Disattiva SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: Valore DWORD (32 bit) a 1

   SCHANNEL\Protocols\SSL 3.0\Server: Abilitato: Valore DWORD (32 bit) a 0

* Rimuovi **TRACE** metodo:

   **Su Apache**, modifica in /etc/apache2/conf.d/security: TraceEnable **Disattivato**

   **In IIS** (vedi [documentazione](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), esegui la seguente configurazione:

   * Assicurati che **Filtro richieste** il servizio ruolo o la funzionalità è installata.
   * In **Filtro richieste** fare clic sulla scheda Verbi HTTP, quindi fare clic su Nega verbo. Nel riquadro Azioni, immettere TRACE nella finestra di dialogo aperta.

* Rimuovi il banner:

   **Su Apache**, modifica /etc/apache2/conf.d/security:

   * FirmaServer **Disattivato**
   * ServerToken **Prod**

   **In IIS**, esegui la seguente configurazione:

   * Installa **URLcan**.
   * Modifica le **Urlscan.ini** file **RemoveServerHeader=1**


* Limita le dimensioni della query per impedire il caricamento di file importanti:

   **Su Apache**, aggiungi **LimitRequestBody** Direttiva (dimensione in byte) nella directory / .

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **In IIS** (vedi [documentazione](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), imposta la **maxAllowedContentLength** (lunghezza massima consentita per il contenuto) nelle opzioni di filtro del contenuto.

Argomenti correlati:

* [Panoramica sulla conformità Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Panoramica sulla sicurezza di Adobe Campaign](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)
