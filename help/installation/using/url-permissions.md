---
solution: Campaign Classic
product: campaign
title: Configurare le autorizzazioni URL
description: Scopri come configurare le autorizzazioni URL
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 23%

---


# Configurare le autorizzazioni URL (on-premise){#url-permissions}

L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) dalle istanze Campaign Classic è limitato. Si tratta di URL che consentono il corretto funzionamento delle istanze.

Per impostazione predefinita, le istanze non possono connettersi a URL esterni. Tuttavia, è possibile aggiungere alcuni URL esterni all’elenco degli URL autorizzati, in modo che l’istanza possa connettersi ad essi. Questo consente di connettere le istanze Campaign a sistemi esterni, ad esempio server SFTP o siti Web, per abilitare il trasferimento di file e/o dati.

>[!NOTE]
>
>Questa procedura è limitata alle distribuzioni **on-premise**.
>
>In qualità di cliente **in hosting**, se puoi accedere a [Pannello di controllo Campaign di campagne](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html), puoi utilizzare l’interfaccia self-service delle autorizzazioni URL. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html)
>
>Altri clienti **ibridi/in hosting** devono contattare il team di supporto Adobe per aggiungere IP all’elenco consentiti.


Per le distribuzioni **Hybrid** e **On-Premise**, l&#39;amministratore deve fare riferimento a un nuovo **urlPermission** nel file **serverConf.xml**.


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
>Per impostazione predefinita, le nuove implementazioni utilizzano la modalità **Blocco** .
>
>Come cliente esistente proveniente da una migrazione, puoi utilizzare temporaneamente la modalità **Avviso** . Analizza il traffico in uscita prima di consentire gli URL. Una volta definito l’elenco degli URL consentiti, puoi aggiungere gli URL all’inserire nell&#39;elenco Consentiti e attivare la modalità **Blocking** .

Per ulteriori informazioni, consulta queste sezioni:

* [Documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Modelli di hosting](hosting-models.md)
* [Configurazione del server Campaign](configuring-campaign-server.md)
* [Parametri del file di configurazione del server Campaign](the-server-configuration-file.md)
* [Lista di controllo protezione e privacy](get-started-security-privacy.md)