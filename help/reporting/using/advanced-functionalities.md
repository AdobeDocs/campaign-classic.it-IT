---
product: campaign
title: Funzionalità avanzate
description: Ulteriori informazioni sulle funzionalità avanzate quando si lavora con i rapporti
feature: Reporting, Monitoring
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 4%

---

# Funzionalità avanzate{#advanced-functionalities}



In qualità di utente tecnico, oltre a [proprietà generali](../../reporting/using/properties-of-the-report.md), puoi sfruttare funzionalità avanzate per configurare i rapporti, ad esempio:

* Creare query complesse per elaborare dati in un&#39;attività **Script**. [Ulteriori informazioni](#script-activity)

* Aggiungi uno script esterno da eseguire sul lato server o client. [Ulteriori informazioni](#external-script)

* Chiama un report con un&#39;attività **Jump**. [Ulteriori informazioni](#calling-up-another-report)

* Aggiungi un parametro URL a un report per renderlo più accessibile. [Ulteriori informazioni](#calling-up-another-report)

* Aggiungi le variabili da utilizzare nel contesto del rapporto. [Ulteriori informazioni](#adding-variables)

## Utilizzo degli script {#adding-a-script}

### Riferimento a script esterni {#external-script}

Puoi fare riferimento ai codici JavaScript che verranno eseguiti sul lato client e/o server quando viene richiamata la pagina del rapporto.

Per eseguire questa operazione:

1. Modifica le [proprietà report](../../reporting/using/properties-of-the-report.md) e fai clic su **[!UICONTROL Scripts]**.
1. Fare clic su **[!UICONTROL Add]** e selezionare lo script a cui fare riferimento.
1. Quindi seleziona la modalità di esecuzione.

   Se aggiungi più script, utilizza le frecce della barra degli strumenti per definirne la sequenza di esecuzione.

   ![](assets/reporting_custom_js.png)

Per la normale esecuzione sul lato client, gli script di riferimento devono essere scritti in JavaScript ed essere compatibili con i browser più diffusi. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/web-forms-answers.md).

### Aggiunta di un’attività Script {#script-activity}

Durante la [progettazione del report](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), utilizzare l&#39;attività **[!UICONTROL Script]** per elaborare i dati e creare facilmente query complesse che non abilitano il linguaggio SQL. È possibile inserire direttamente la query nella finestra dello script.

La scheda **[!UICONTROL Texts]** consente di definire stringhe di testo. Possono quindi essere utilizzati con la seguente sintassi: **$(Identifier)**. Per ulteriori informazioni sull&#39;utilizzo dei testi, vedere [Aggiunta di un&#39;intestazione e di un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Per la creazione di aggregati, si sconsiglia di utilizzare il codice JavaScript.

Per creare una cronologia del rapporto, aggiungi la seguente riga alla query JavaScript per salvare i dati archiviati:

```
if( ctx.@_historyId.toString().length == 0 )
```

In caso contrario, verranno visualizzati solo i dati correnti.

## Aggiunta di un parametro URL {#defining-additional-settings}

La scheda **[!UICONTROL Parameters]** delle [proprietà report](../../reporting/using/properties-of-the-report.md) ti consente di definire impostazioni aggiuntive per il report: queste impostazioni verranno passate nell&#39;URL durante la chiamata.

>[!CAUTION]
>
>Per motivi di sicurezza, questi parametri devono essere utilizzati con cautela.

Per creare una nuova impostazione:

1. Fare clic sul pulsante **[!UICONTROL Add]** e immettere il nome dell&#39;impostazione.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessario, specificare se l&#39;impostazione sarà obbligatoria o meno.

1. Selezionare il tipo di impostazione da creare: **[!UICONTROL Filter]** o **[!UICONTROL Variable]**.

   L&#39;opzione **[!UICONTROL Filter entities]** consente di utilizzare un campo del database come parametro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   I dati vengono recuperati direttamente a livello di entità: **ctx/recipient/@account**.

   L&#39;opzione **[!UICONTROL Variable]** consente di creare o selezionare una variabile che verrà passata come parametro dell&#39;URL e potrà essere utilizzata nei filtri.

**[!UICONTROL Response HTTP headers]** consente di impedire il clickjacking quando si include la pagina del report in una pagina HTML utilizzando iframe. Per evitare il clickjacking, puoi scegliere il comportamento **[!UICONTROL X-Frame-options header]**:

* **[!UICONTROL None]**: il report non avrà **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: impostato per impostazione predefinita per i nuovi report e i report ripubblicati. Il nome host sarà lo stesso dell’URL del rapporto.
* **[!UICONTROL Deny]**: impossibile includere il report in una pagina HTML utilizzando iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Aggiungere variabili {#adding-variables}

La scheda **[!UICONTROL Variables]** contiene l&#39;elenco delle variabili configurate nel report. Queste variabili sono esposte nel contesto del rapporto e possono essere utilizzate nei calcoli.

Fare clic sul pulsante **[!UICONTROL Add]** per creare una nuova variabile.

Per visualizzare la definizione di una variabile, selezionarla e fare clic sul pulsante **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Caso d’uso: utilizzare variabili e parametri in un rapporto

Nell’esempio video seguente, scoprirai come aggiungere un parametro &quot;_type&quot; per creare visualizzazioni diverse di un rapporto, in base al valore di questo attributo.

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## Richiamo di un altro report {#calling-up-another-report}

Un&#39;attività **Jump** è simile a una transizione senza freccia: consente di passare da un&#39;attività all&#39;altra o di accedere a un altro report.
