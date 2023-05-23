---
product: campaign
title: Configurare le autorizzazioni URL
description: Scopri come configurare le autorizzazioni URL
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# Configurare le autorizzazioni URL (on-premise){#url-permissions}



L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) dalle istanze Campaign Classic è limitato. Si tratta di URL che consentono il corretto funzionamento delle istanze.

Per impostazione predefinita, le istanze non possono connettersi a URL esterni. Tuttavia, è possibile aggiungere URL esterni all’elenco degli URL autorizzati in modo che l’istanza possa connettersi ad essi. Questo consente di connettere le istanze Campaign a sistemi esterni, ad esempio server SFTP o siti Web, per abilitare il trasferimento di file e/o dati.

>[!NOTE]
>
>Questa procedura è limitata a **on-premise** distribuzioni.
>
>As a **in hosting** cliente, se è possibile accedere [Pannello di controllo Campaign della campagna](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it), puoi utilizzare l’interfaccia self-service per le autorizzazioni URL. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=it)
>
>Altro **ibrido/in hosting** i clienti devono contattare il team di supporto Adobe per aggiungere l’IP al inserisco nell&#39;elenco Consentiti di.

Per **Ibrido** e **On-premise** implementazioni, l’amministratore deve fare riferimento a una nuova **urlPermission** nel **serverConf.xml** file.


Sono disponibili tre modalità di protezione della connessione:

* **Blocco**: tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di vengono bloccati e viene visualizzato un messaggio di errore. Questa è la modalità predefinita dopo un post-aggiornamento.
* **Permissivo**: sono consentiti tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di.
* **Avvertenza**: sono consentiti tutti gli URL che non appartengono al inserisco nell&#39;elenco Consentiti di, ma l’interprete JS genera un avviso che consente all’amministratore di raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Per impostazione predefinita, le nuove implementazioni utilizzano **Blocco** modalità.
>
>In qualità di cliente esistente proveniente da una migrazione, puoi utilizzare temporaneamente la **Avvertenza** modalità. Analizza il traffico in uscita prima di consentire gli URL. Una volta definito l’elenco degli URL consentiti, puoi aggiungerli al elenco Consentiti di e attivare **Blocco** modalità.

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Documentazione del Pannello di controllo](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it)
* [Modelli di hosting](hosting-models.md)
* [Configurazione del server Campaign](configuring-campaign-server.md)
* [Parametri del file di configurazione del server Campaign](the-server-configuration-file.md)
* [Lista di controllo per sicurezza e privacy](get-started-security-privacy.md)
