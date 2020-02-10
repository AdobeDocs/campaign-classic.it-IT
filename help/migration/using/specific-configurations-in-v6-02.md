---
title: Configurazioni specifiche in v6.02
seo-title: Configurazioni specifiche in v6.02
description: Configurazioni specifiche in v6.02
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Configurazioni specifiche in v6.02{#specific-configurations-in-v6-02}

Nella sezione seguente viene descritta la configurazione aggiuntiva richiesta per la migrazione dalla versione 6.02. È inoltre necessario configurare le impostazioni dettagliate nella sezione Configurazioni [](../../migration/using/general-configurations.md) generali.

## Applicazioni Web {#web-applications}

Se state eseguendo la migrazione dalla versione 6.02, potrebbero essere visualizzati registri di errore relativi alle applicazioni Web di tipo panoramica. Esempi di messaggi di errore:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Tali applicazioni Web hanno utilizzato SQLData e non sono compatibili con v7 a causa di un livello di protezione maggiore. Questi errori porteranno a un errore di migrazione.

Se non avete utilizzato queste applicazioni Web, eseguite lo script di pulizia seguente ed eseguite nuovamente il post-aggiornamento:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Se avete modificato queste applicazioni Web e desiderate continuare a utilizzarle in v7, dovete attivare l’opzione **allowSQLInjection** nelle diverse aree di sicurezza e riavviare il postaggiornamento. Per ulteriori informazioni, consulta la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) .

## Facilità di utilizzo: Home page e navigazione {#user-friendliness--home-page-and-navigation}

>[!CAUTION]
>
>Se desiderate continuare a utilizzare le applicazioni Web di tipo v6.02, è necessario attivare l&#39;opzione **allowSQLInjection** nelle diverse aree di protezione prima dell&#39;aggiornamento successivo. Fare riferimento alle applicazioni [](#web-applications)Web.

Dopo una migrazione dalla versione 6.02, la homepage di Adobe Campaign v6.02 non viene più visualizzata ma resta accessibile e compatibile con Adobe Campaign v7.

Per continuare a utilizzare la homepage v6.02, dopo la migrazione dovete installare un pacchetto di &quot;compatibilità&quot;.

A questo scopo, importate il pacchetto di compatibilità:

Fate clic su **[!UICONTROL Tools > Advanced > Import package]** e scegliete il pacchetto **campaignMigration.xml** nella **`\nl\datakit\nms\[Your language]\package\optional`**.

Per consentire l&#39;accesso alle interfacce dei tipi di applicazione Web v6.02, l&#39;opzione di configurazione del server **sessionTokenOnly** deve essere attivata nel file **serverConf.xml** :

```
sessionTokenOnly="true"
```

Questa opzione modifica i livelli di protezione per garantire la compatibilità dell&#39;interfaccia.

Una volta installato il pacchetto, la home page di Adobe Campaign v7 viene sostituita dalla vecchia homepage v6.02 completa delle configurazioni generali della v7 (banner blu della home page).

![](assets/dashboards.png)

Tutti i collegamenti presenti in questa homepage sono collegati alle schermate v7 ad eccezione degli elenchi (**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]** ecc.) collegamento alla panoramica v6.02 (applicazioni Web).

![](assets/dashboards2.png)

Per aggiungere un’altra panoramica configurata in v6.02, è necessario aggiungerla alla pagina principale dal dashboard. (**[!UICONTROL Administration > Access management > Dashboard]**)

>[!NOTE]
>
>Per registrare le modifiche, disconnettetevi e ricollegate la console.

## Centro messaggi {#message-center}

Dopo la migrazione dell&#39;istanza di controllo del Centro messaggi, devi ripubblicare i modelli dei messaggi transazionali affinché funzionino.

In v7, i nomi dei modelli di messaggi transazionali sulle istanze di esecuzione sono cambiati. Sono attualmente contraddistinti dal nome dell&#39;operatore che corrisponde all&#39;istanza di controllo su cui sono creati, ad esempio **control1_template1_rt** (dove **control1** è il nome dell&#39;operatore). Se disponete di un volume significativo di modelli, è consigliabile eliminare vecchi modelli nelle istanze di controllo.
