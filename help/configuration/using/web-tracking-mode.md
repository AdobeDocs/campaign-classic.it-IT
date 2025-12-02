---
product: campaign
title: Modalità di tracciamento web
description: Scopri come selezionare la modalità di tracciamento web
feature: Instance Settings
role: Developer
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 1%

---

# Modalità di tracciamento web{#web-tracking-mode}



Adobe Campaign consente di selezionare una modalità di tracciamento web che definisce il modo in cui i registri di tracciamento vengono elaborati nell’applicazione.

Sono disponibili tre modalità di tracciamento Web: **&quot;Tracciamento sessione&quot;**,**&quot;Tracciamento permanente&quot;** e **&quot;Tracciamento anonimo&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Ogni modalità ha caratteristiche specifiche. La modalità di tracciamento web &quot;permanente&quot; include le caratteristiche della modalità di tracciamento web &quot;sessione&quot;, mentre la modalità &quot;anonimo&quot; include le caratteristiche delle modalità &quot;permanente&quot; e &quot;sessione&quot;.

>[!IMPORTANT]
>
>La modalità di tracciamento web &quot;anonimo&quot; è attivata per impostazione predefinita se il pacchetto &quot;Lead&quot; è abilitato. In tutti gli altri casi, la modalità di tracciamento web &quot;sessione&quot; è attivata per impostazione predefinita.
>
>La modalità predefinita può essere modificata in qualsiasi momento nella procedura guidata di distribuzione dell’istanza.

Se utilizzi la modalità di tracciamento **web permanente** o **anonimo**, devi aggiungere un indice alla colonna &quot;sourceID&quot; (uuid230) nelle tabelle di tracciamento (trackingLogXXX):

1. Identifica le tabelle di tracciamento interessate dal tracciamento permanente.
1. Estendi gli schemi che corrispondono a queste tabelle aggiungendo le righe seguenti:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

Le modalità di tracciamento Web **Permanente** e **Anonimo** includono due opzioni: **Consegna forzata** e **Ultima consegna**.

L&#39;opzione **Consegna forzata** consente di specificare l&#39;identificatore della consegna (@jobid) durante il tracciamento.

L&#39;opzione **Ultima consegna** consente di collegare il registro di tracciamento corrente all&#39;ultima consegna tracciata.

**Caratteristiche del tracciamento Web della sessione:**

Questa modalità crea un registro di tracciamento per le persone con un cookie di sessione. Si tratta di persone che hanno fatto clic su un URL in un’e-mail inviata da Adobe Campaign, consentendoci così di tenere traccia delle seguenti informazioni:

* ID consegna
* ID contatto
* registro di consegna
* cookie permanente (uuid230)
* URL di tracciamento
* data del registro di tracciamento

Con questa modalità di tracciamento web, se parte delle informazioni non è presente, nell’applicazione non verrà creato alcun registro di tracciamento.

Questa modalità è economica in termini di volume (numero limitato di record nella tabella trackingLog) e di calcolo (nessuna riconciliazione).

**Caratteristiche della modalità di tracciamento Web permanente:**

Questa modalità di tracciamento web consente di creare un registro di tracciamento basato sulla presenza del cookie uuid230 permanente. Se un visitatore chiude la sessione, Adobe Campaign utilizza il cookie permanente per recuperare informazioni su di esso dai registri di tracciamento precedenti. Adobe Campaign inserisce nuovamente un registro di tracciamento se l’uuid230 della sessione corrente ha lo stesso valore di un uuid230 già memorizzato nella tabella di tracciamento.

Questo significa che il visitatore deve essere stato precedentemente identificato in Adobe Campaign (tramite una consegna) per abilitare la riconciliazione sui valori uuid230.

Per impostazione predefinita, le ricerche nei registri di tracciamento precedenti vengono eseguite nella tabella &quot;trackingLog&quot;. Se il pacchetto Lead è abilitato, prima di eseguire una ricerca nella tabella &quot;trackingLog&quot;, Adobe Campaign cercherà nella tabella &quot;incomingLead&quot; i record dei registri di tracciamento precedenti.

Questa modalità è costosa in termini di calcolo durante la riconciliazione del registro.

**Caratteristiche della modalità di tracciamento Web anonimo:**

Questa modalità di tracciamento web consente di recuperare un registro di tracciamento collegato alla navigazione anonima in Adobe Campaign. Un registro di tracciamento viene creato automaticamente per ogni clic su un URL tracciato. Questo registro contiene solo il valore di uuid230. Durante una campagna di marketing, viene creato automaticamente un registro di tracciamento con tutte le informazioni di identificazione (fai riferimento al tracciamento delle sessioni). Adobe Campaign cercherà automaticamente nei registri precedenti un valore &quot;uuid230&quot; uguale al valore presente nel registro di tracciamento per questa campagna di marketing. Se vengono trovati valori identici, tutti i registri di tracciamento precedenti vengono immessi con tutte le informazioni provenienti dal registro di tracciamento della campagna di marketing.

Questa modalità è la più costosa in termini di calcolo e volume.

>[!NOTE]
>
>Se il pacchetto **[!UICONTROL Leads]** è installato, è necessario eseguire la stessa operazione per la tabella attività (**crm:incomingLead**)

Lo schema seguente riassume le funzionalità di tutte e tre le modalità di tracciamento web:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Esempio di tracciamento web permanente basato sull&#39;ultima consegna:**

Florence riceve una consegna, apre l’e-mail, fa clic sul collegamento, naviga nel sito di vendita al dettaglio ma non effettua acquisti. Il giorno successivo, Florence ritorna al sito di vendita al dettaglio, naviga ed effettua un acquisto. Poiché è abilitato il tracciamento web permanente (ultima consegna), tutti i registri della seconda visita saranno collegati alla consegna che le è stata inviata il giorno precedente.
