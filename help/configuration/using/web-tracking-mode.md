---
title: Modalità di web tracking
seo-title: Modalità di web tracking
description: Modalità di web tracking
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---


# Modalità di web tracking{#web-tracking-mode}

 Adobe Campaign consente di selezionare una modalità di tracciamento Web che definisce il modo in cui i registri di tracciamento vengono elaborati nell’applicazione.

Sono disponibili tre modalità di tracciamento Web: **&quot;Tracciamento della sessione&quot;**,**&quot;Tracciamento permanente&quot;** e **&quot;Tracciamento anonimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Ogni modalità ha caratteristiche specifiche. La modalità di tracciamento Web &quot;permanente&quot; include le caratteristiche della modalità di tracciamento Web &quot;sessione&quot;, mentre la modalità &quot;anonima&quot; include le caratteristiche delle modalità &quot;permanente&quot; e &quot;sessione&quot;.

>[!IMPORTANT]
>
>La modalità di tracciamento Web &quot;anonima&quot; è abilitata per impostazione predefinita se il pacchetto &quot;Lead&quot; è abilitato. In tutti gli altri casi, la modalità di tracciamento Web &quot;sessione&quot; è abilitata per impostazione predefinita.
>
>In qualsiasi momento, la modalità predefinita può essere modificata nella procedura guidata di distribuzione delle istanze.

Se utilizzi la modalità di tracciamento **permanente Web** o **anonima** , devi aggiungere un indice alla colonna &quot;sourceID&quot; (uuid230) nelle tabelle di tracciamento (trackingLogXXX):

1. Identificare le tabelle di tracciamento interessate dal tracciamento permanente.
1. Estendere gli schemi che corrispondono a queste tabelle aggiungendo le righe seguenti:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Le modalità di tracciamento Web permanente** e **anonima** includono due opzioni: **Consegna** forzata e **Ultima consegna**.

L&#39;opzione **Consegna** forzata consente di specificare l&#39;identificatore della consegna (@jobid) durante il tracciamento.

L’opzione **Ultima consegna** consente di collegare il registro di tracciamento corrente all’ultima consegna tracciata.

**Caratteristiche del tracciamento Web della sessione:**

Questa modalità crea un registro di monitoraggio per le persone con un cookie di sessione. Si tratta di persone che hanno fatto clic su un URL in un messaggio e-mail inviato da  Adobe Campaign, per consentirci di tenere traccia delle seguenti informazioni:

* ID consegna
* ID contatto
* registro di consegna
* cookie permanente (uuid230)
* URL tracciamento
* data del registro di tracciamento

Con questa modalità di tracciamento Web, se parte delle informazioni non è presente, nell’applicazione non verrà creato alcun registro di tracciamento.

Questa modalità è economica in termini di volume (numero limitato di record nella tabella trackingLog) e di calcolo (nessuna riconciliazione).

**Caratteristiche della modalità di tracciamento Web permanente:**

Questa modalità di tracciamento Web consente di creare un registro di tracciamento basato sulla presenza del cookie uuuid230 permanente. Se un visitatore chiude la propria sessione,  Adobe Campaign utilizza il cookie permanente per recuperare le informazioni presenti nei registri di tracciamento precedenti.  Adobe Campaign reinserisce un registro di tracciamento se l&#39;uuid230 della sessione corrente ha lo stesso valore di un uuuid230 già memorizzato nella tabella di tracciamento.

Questo significa che il visitatore deve essere stato identificato in precedenza in  Adobe Campaign (tramite una consegna) per abilitare la riconciliazione sui valori uuuid230.

Per impostazione predefinita, le ricerche nei precedenti registri di tracciamento vengono eseguite nella tabella &quot;trackingLog&quot;. Se il pacchetto Lead è abilitato, prima di cercare nella tabella &quot;trackingLog&quot;,  Adobe Campaign cercherà nella tabella &quot;entrinLead&quot; i record di registro di tracciamento precedenti.

Questa modalità è costosa in termini di calcolo durante la riconciliazione del registro.

**Caratteristiche della modalità di tracciamento Web anonima:**

Questa modalità di tracciamento Web consente di recuperare un registro di tracciamento collegato alla navigazione anonima in  Adobe Campaign. Viene creato automaticamente un registro di tracciamento per ogni clic su un URL tracciato. Questo registro ha solo il valore di uuid230. Durante una campagna di marketing, viene creato automaticamente un registro di tracciamento con tutte le informazioni di identificazione (fare riferimento al tracciamento delle sessioni).  Adobe Campaign cercherà automaticamente nei registri precedenti un valore &quot;uuid230&quot; uguale al valore del registro di tracciamento per questa campagna di marketing. Se vengono trovati valori identici, tutti i precedenti registri di tracciamento vengono inseriti con tutte le informazioni presenti nel registro di tracciamento della campagna di marketing.

Questa modalità è la più costosa in termini di calcolo e volume.

>[!NOTE]
>
>Se il **[!UICONTROL Leads]** pacchetto è installato, è necessario eseguire le stesse operazioni per la tabella delle attività (**crm:entrinLead**)

Lo schema seguente riassume le funzionalità di tutte e tre le modalità di tracciamento Web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Esempio di tracciamento Web permanente in base all&#39;ultima consegna:**

Firenze riceve una consegna, apre l&#39;e-mail, fa clic sul collegamento, naviga sul sito di vendita al dettaglio ma non effettua acquisti. Il giorno successivo, Florence ritorna al sito di vendita al dettaglio, naviga e fa un acquisto. Poiché è abilitato il tracciamento Web permanente (ultima consegna), tutti i registri della seconda visita verranno collegati alla consegna che le è stata inviata il giorno precedente.
