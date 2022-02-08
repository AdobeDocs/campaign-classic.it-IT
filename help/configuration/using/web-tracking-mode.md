---
product: campaign
title: Modalità di tracciamento web
description: Scopri come selezionare la modalità di web tracking
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# Modalità di tracciamento web{#web-tracking-mode}

![](../../assets/v7-only.svg)

Adobe Campaign consente di selezionare una modalità di web tracking che definisce il modo in cui i log di tracking vengono elaborati nell’applicazione.

Sono disponibili tre modalità di web tracking: **&quot;Tracciamento sessione&quot;**,**&quot;Tracciamento permanente&quot;** e **&quot;Tracking anonimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Ogni modalità ha caratteristiche specifiche. La modalità di web tracking &quot;permanente&quot; include le caratteristiche della modalità di web tracking &quot;sessione&quot;, mentre la modalità &quot;anonima&quot; include le caratteristiche delle modalità &quot;permanente&quot; e &quot;sessione&quot;.

>[!IMPORTANT]
>
>La modalità di web tracking &quot;anonymous&quot; è abilitata per impostazione predefinita se il pacchetto &quot;Lead&quot; è abilitato. In tutti gli altri casi, la modalità di web tracking &quot;sessione&quot; è attivata per impostazione predefinita.
>
>In qualsiasi momento, la modalità predefinita può essere modificata nella procedura guidata di distribuzione delle istanze.

Se utilizzi **web permanente** o **anonimo** modalità di tracciamento, devi aggiungere un indice alla colonna &quot;sourceID&quot; (uuid230) nelle tabelle di tracciamento (trackingLogXXX):

1. Identificare le tabelle di tracciamento interessate dal tracciamento permanente.
1. Estendi gli schemi che corrispondono a queste tabelle aggiungendo le righe seguenti:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Permanente** e **Anonimo** Le modalità di web tracking includono due opzioni: **Consegna forzata** e **Ultima consegna**.

La **Consegna forzata** consente di specificare l’identificatore della consegna (@jobid) durante il tracciamento.

La **Ultima consegna** consente di collegare il registro di tracciamento corrente all’ultima consegna tracciata.

**Caratteristiche del tracciamento Web della sessione:**

Questa modalità crea un registro di tracciamento per le persone con un cookie di sessione. Si tratta di persone che hanno fatto clic su un URL in un’e-mail inviata da Adobe Campaign, per consentirci di tenere traccia delle seguenti informazioni:

* ID consegna
* ID contatto
* registro di consegna
* cookie permanente (uuid230)
* URL di tracciamento
* data del registro di tracciamento

Con questa modalità di web tracking, se parte delle informazioni è mancante, nell&#39;applicazione non verrà creato alcun registro di tracking.

Questa modalità è economica in termini di volume (numero limitato di record nella tabella trackingLog) e calcolo (nessuna riconciliazione).

**Caratteristiche della modalità di web tracking permanente:**

Questa modalità di web tracking consente di creare un registro di tracking in base alla presenza del cookie uuid230 permanente. Se un visitatore chiude la sessione, Adobe Campaign utilizza il cookie permanente per recuperare le informazioni su di esso dai registri di tracciamento precedenti. Adobe Campaign reinserisce un registro di tracciamento se l’uuid230 della sessione corrente ha lo stesso valore di un uuid230 già memorizzato nella tabella di tracciamento.

Questo significa che il visitatore deve essere stato identificato in precedenza in Adobe Campaign (tramite una consegna) per abilitare la riconciliazione sui valori uuid230.

Per impostazione predefinita, le ricerche nei registri di tracciamento precedenti vengono eseguite nella tabella &quot;trackingLog&quot;. Se il pacchetto Lead è abilitato, prima di cercare nella tabella &quot;trackingLog&quot;, Adobe Campaign cerca nella tabella &quot;in arrivoLead&quot; i record di log di tracciamento precedenti.

Questa modalità è costosa in termini di calcolo durante la riconciliazione dei log.

**Caratteristiche della modalità di web tracking anonimo:**

Questa modalità di web tracking consente di recuperare un registro di tracciamento collegato alla navigazione anonima in Adobe Campaign. Viene creato automaticamente un registro di tracciamento per ogni clic su un URL tracciato. Questo registro ha solo il valore di uuid230. Durante una campagna di marketing, viene creato automaticamente un registro di tracciamento con tutte le informazioni di identificazione (consulta tracciamento delle sessioni). Adobe Campaign cerca automaticamente nei registri precedenti un valore &quot;uuid230&quot; uguale al valore del registro di tracciamento per questa campagna di marketing. Se vengono trovati valori identici, tutti i registri di tracciamento precedenti vengono inseriti con tutte le informazioni del registro di tracciamento della campagna di marketing.

Questa modalità è la più costosa in termini di calcolo e volume.

>[!NOTE]
>
>Se la **[!UICONTROL Leads]** il pacchetto è installato, è necessario fare lo stesso per la tabella attività (**crm:entrinLead**)

Lo schema seguente riassume le funzionalità di tutte e tre le modalità di web tracking:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Esempio di web tracking permanente basato sull’ultima consegna:**

Firenze riceve una consegna, apre l&#39;e-mail, clicca sul link, naviga sul sito al dettaglio ma non fa acquisti. Il giorno successivo, Firenze ritorna al sito di vendita al dettaglio, naviga e fa un acquisto. Poiché è abilitato il web tracking permanente (ultima consegna), tutti i registri della seconda visita verranno collegati alla consegna inviata il giorno precedente.
