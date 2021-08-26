---
product: campaign
title: Configurazioni specifiche nella versione v6.02
description: Configurazioni specifiche nella versione v6.02
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 7e8f8488-f3ef-4b64-9981-335d67caf372
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---

# Configurazioni specifiche nella versione v6.02{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

La sezione seguente descrive la configurazione aggiuntiva necessaria per la migrazione dalla versione v6.02. È inoltre necessario configurare le impostazioni descritte nella sezione [Configurazioni generali](../../migration/using/general-configurations.md) .

## Applicazioni web {#web-applications}

Se stai eseguendo la migrazione dalla versione v6.02, potrebbero essere visualizzati registri di errore relativi alle applicazioni web di tipo panoramica. Esempi di messaggi di errore:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Queste applicazioni web hanno utilizzato SQLData e non sono compatibili con v7, a causa di una maggiore sicurezza. Questi errori causeranno un errore di migrazione.

Se non hai utilizzato queste applicazioni web, esegui il seguente script di pulizia ed esegui nuovamente il post aggiornamento:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Se hai modificato queste applicazioni web e desideri continuare a utilizzarle in v7, devi attivare l&#39;opzione **allowSQLInjection** nelle diverse aree di sicurezza e riavviare il post aggiornamento. Per ulteriori informazioni, consulta la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) .

## Facilità di utilizzo: Home page e navigazione {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Per continuare a utilizzare le applicazioni web di tipo panoramica v6.02, è necessario attivare l&#39;opzione **allowSQLInjection** nelle diverse aree di sicurezza prima dell&#39;aggiornamento successivo. Fare riferimento a [Applicazioni web](#web-applications).

Dopo una migrazione dalla versione 6.02, la home page di Adobe Campaign v6.02 non viene più visualizzata ma è ancora accessibile e compatibile con Adobe Campaign v7.

Per continuare a utilizzare la home page v6.02, è necessario installare un pacchetto di &quot;compatibilità&quot; dopo la migrazione.

A questo scopo, importa il pacchetto di compatibilità:

Fai clic su **[!UICONTROL Tools > Advanced > Import package]** e scegli il pacchetto **campaignMigration.xml** in **`\nl\datakit\nms\[Your language]\package\optional`**.

Per consentire l&#39;accesso alle interfacce di tipo applicazione Web v6.02, l&#39;opzione di configurazione del server **sessionTokenOnly** deve essere attivata nel file **serverConf.xml** :

```
sessionTokenOnly="true"
```

Questa opzione modifica i livelli di sicurezza per garantire la compatibilità dell’interfaccia.

Una volta installato il pacchetto, la home page di Adobe Campaign v7 viene sostituita dalla vecchia home page v6.02 completa con le configurazioni generali della v7 (banner blu home page).

![](assets/dashboards.png)

Tutti i collegamenti in questa home page collegano alle schermate v7 eccetto gli elenchi (**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]**, ecc.) che collegano alla panoramica v6.02 (applicazioni web).

![](assets/dashboards2.png)

Se desideri aggiungere un’altra panoramica configurata nella versione v6.02, devi aggiungerla alla home page dal dashboard. (**[!UICONTROL Administration > Access management > Dashboard]**).

>[!NOTE]
>
>Ricorda di disconnettersi e ricollegare la console per registrare le modifiche.

## Centro messaggi {#message-center}

Dopo la migrazione di un&#39;istanza di controllo del Centro messaggi, devi ripubblicare i modelli dei messaggi transazionali affinché funzionino.

In v7, i nomi dei modelli di messaggi transazionali nelle istanze di esecuzione sono cambiati. Sono attualmente preceduti dal nome dell’operatore che corrisponde all’istanza di controllo in cui sono stati creati, ad esempio **control1_template1_rt** (dove **control1** è il nome dell’operatore). Se si dispone di un volume significativo di modelli, è consigliabile eliminare i vecchi modelli nelle istanze di controllo.
