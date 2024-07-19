---
product: campaign
title: Configurare le autorizzazioni URL
description: Scopri come configurare le autorizzazioni URL
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 24%

---

# Configurare le autorizzazioni URL (on-premise){#url-permissions}



L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) dalle istanze Campaign Classic è limitato. Si tratta di URL che consentono il corretto funzionamento delle istanze.

Per impostazione predefinita, le istanze non possono connettersi a URL esterni. Tuttavia, è possibile aggiungere URL esterni all’elenco degli URL autorizzati in modo che l’istanza possa connettersi ad essi. Questo consente di connettere le istanze Campaign a sistemi esterni, ad esempio server SFTP o siti Web, per abilitare il trasferimento di file e/o dati.

>[!NOTE]
>
>Questa procedura è limitata a **distribuzioni locali**.
>
>In qualità di cliente **hosted**, se puoi accedere a [Pannello di controllo Campaign Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it), puoi utilizzare l&#39;interfaccia self-service delle autorizzazioni URL. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=it)
>
>Altri clienti **ibridi/ospitati** devono contattare il team di supporto Adobe per aggiungere l&#39;IP al inserisco nell&#39;elenco Consentiti di.
>

Per le distribuzioni **Hybrid** e **On-Premise**, l&#39;amministratore deve fare riferimento a un nuovo **urlPermission** nel file **serverConf.xml**.


Sono disponibili tre modalità di protezione della connessione:

* **Blocco**: tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di sono bloccati, con un messaggio di errore. Questa è la modalità predefinita dopo un post-aggiornamento.
* **Permissivo**: sono consentiti tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di.
* **Avviso**: sono consentiti tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di, ma l&#39;interprete JS genera un avviso che consente all&#39;amministratore di raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Per impostazione predefinita, le nuove implementazioni utilizzano la modalità **Blocco**.
>
>In qualità di cliente esistente proveniente da una migrazione, puoi utilizzare temporaneamente la modalità **Avviso**. Analizza il traffico in uscita prima di consentire gli URL. Una volta definito l&#39;elenco degli URL consentiti, puoi aggiungerli al inserisco nell&#39;elenco Consentiti di e attivare la modalità **Blocco**.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Documentazione del Pannello di controllo](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it)
* [Modelli di hosting](hosting-models.md)
* [Configurazione del server Campaign](configuring-campaign-server.md)
* [Parametri del file di configurazione del server Campaign](the-server-configuration-file.md)
* [Lista di controllo per sicurezza e privacy](get-started-security-privacy.md)
