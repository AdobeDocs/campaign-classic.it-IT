---
product: campaign
title: Configurare le autorizzazioni URL
description: Scopri come configurare le autorizzazioni URL
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# Configurare le autorizzazioni URL (on-premise){#url-permissions}



L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) dalle istanze Campaign Classic è limitato. Si tratta di URL che consentono il corretto funzionamento delle istanze.

Per impostazione predefinita, le istanze non possono connettersi a URL esterni. Tuttavia, è possibile aggiungere alcuni URL esterni all’elenco degli URL autorizzati, in modo che l’istanza possa connettersi ad essi. Questo consente di connettere le istanze Campaign a sistemi esterni, ad esempio server SFTP o siti Web, per abilitare il trasferimento di file e/o dati.

>[!NOTE]
>
>Questa procedura è limitata a **on-premise** distribuzioni.
>
>Come **ospitato** cliente, se è possibile accedere [Pannello di controllo Campaign campagna](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it), puoi utilizzare l’interfaccia self-service delle autorizzazioni URL . [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=it)
>
>Altro **ibrido/ospitato** i clienti devono contattare il team di supporto Adobe per aggiungere IP all’inserire nell&#39;elenco Consentiti.

Per **Ibrido** e **On-Premise** implementazioni, l’amministratore deve fare riferimento a una nuova **urlPermission** in **serverConf.xml** file.


Sono disponibili tre modalità di protezione della connessione:

* **Blocco**: tutti gli URL che non appartengono all&#39;inserire nell&#39;elenco Consentiti vengono bloccati, con un messaggio di errore. Questa è la modalità predefinita dopo un aggiornamento successivo.
* **Permissivo**: tutti gli URL che non appartengono all’inserire nell&#39;elenco Consentiti sono consentiti.
* **Avviso**: tutti gli URL che non appartengono all’inserire nell&#39;elenco Consentiti sono consentiti, ma l’interprete JS emette un avviso in modo che l’amministratore possa raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Per impostazione predefinita, le nuove implementazioni utilizzano le **Blocco** modalità.
>
>Come cliente esistente proveniente da una migrazione, puoi utilizzare temporaneamente la funzione **Avviso** modalità. Analizza il traffico in uscita prima di consentire gli URL. Una volta definito l’elenco degli URL consentiti, puoi aggiungere gli URL all’inserire nell&#39;elenco Consentiti e attivare il **Blocco** modalità.

Per ulteriori informazioni, consulta queste sezioni:

* [Documentazione del Pannello di controllo](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it)
* [Modelli di hosting](hosting-models.md)
* [Configurazione del server Campaign](configuring-campaign-server.md)
* [Parametri del file di configurazione del server Campaign](the-server-configuration-file.md)
* [Lista di controllo protezione e privacy](get-started-security-privacy.md)
