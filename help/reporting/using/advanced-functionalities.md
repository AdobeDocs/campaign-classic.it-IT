---
product: campaign
title: Funzionalità avanzate
description: Ulteriori informazioni sulle funzionalità avanzate quando si lavora con i rapporti
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 4%

---

# Funzionalità avanzate{#advanced-functionalities}



Come utente tecnico, oltre a [proprietà generali](../../reporting/using/properties-of-the-report.md), puoi sfruttare funzionalità avanzate per configurare i rapporti, ad esempio:

* Creare query complesse per elaborare i dati in una **Script** attività. [Ulteriori informazioni](#script-activity)

* Aggiungi uno script esterno da eseguire sul lato server o client. [Ulteriori informazioni](#external-script)

* Chiama un rapporto con un **Salta** attività. [Ulteriori informazioni](#calling-up-another-report)

* Aggiungi un parametro URL a un report per renderlo più accessibile. [Ulteriori informazioni](#calling-up-another-report)

* Aggiungi le variabili da utilizzare nel contesto del rapporto. [Ulteriori informazioni](#adding-variables)

## Utilizzo degli script {#adding-a-script}

### Riferimento a script esterni {#external-script}

Puoi fare riferimento ai codici JavaScript che verranno eseguiti sul lato client e/o server quando viene richiamata la pagina del rapporto.

Per eseguire questa operazione:

1. Modifica il [proprietà report](../../reporting/using/properties-of-the-report.md) e fai clic su **[!UICONTROL Scripts]**.
1. Clic **[!UICONTROL Add]** e seleziona lo script a cui fare riferimento.
1. Quindi seleziona la modalità di esecuzione.

   Se aggiungi più script, utilizza le frecce della barra degli strumenti per definirne la sequenza di esecuzione.

   ![](assets/reporting_custom_js.png)

Per la normale esecuzione sul lato client, gli script di riferimento devono essere scritti in JavaScript e devono essere compatibili con i browser più diffusi. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/web-forms-answers.md).

### Aggiunta di un’attività Script {#script-activity}

Quando [progettazione del report](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), utilizza **[!UICONTROL Script]** attività per elaborare i dati e creare facilmente query complesse che non abilitano il linguaggio SQL. È possibile inserire direttamente la query nella finestra dello script.

Il **[!UICONTROL Texts]** consente di definire stringhe di testo. Possono quindi essere utilizzati con la seguente sintassi: **$(Identifier)**. Per ulteriori informazioni sull’utilizzo dei testi, consulta [Aggiunta di un’intestazione e un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Si sconsiglia di utilizzare il codice JavaScript per creare aggregati.

Per creare una cronologia del rapporto, aggiungi la seguente riga alla query JavaScript per salvare i dati archiviati:

```
if( ctx.@_historyId.toString().length == 0 )
```

In caso contrario, verranno visualizzati solo i dati correnti.

## Aggiunta di un parametro URL {#defining-additional-settings}

Il **[!UICONTROL Parameters]** scheda di [proprietà report](../../reporting/using/properties-of-the-report.md) consente di definire impostazioni aggiuntive per il rapporto: queste impostazioni verranno trasmesse nell’URL durante la chiamata.

>[!CAUTION]
>
>Per motivi di sicurezza, questi parametri devono essere utilizzati con cautela.

Per creare una nuova impostazione:

1. Fai clic su **[!UICONTROL Add]** e immettere il nome dell&#39;impostazione.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessario, specificare se l&#39;impostazione sarà obbligatoria o meno.

1. Selezionare il tipo di impostazione che si desidera creare: **[!UICONTROL Filter]** o **[!UICONTROL Variable]**.

   Il **[!UICONTROL Filter entities]** consente di utilizzare un campo del database come parametro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   I dati vengono recuperati direttamente a livello di entità: **ctx/recipient/@account**.

   Il **[!UICONTROL Variable]** L’opzione ti consente di creare o selezionare una variabile che verrà passata come parametro dell’URL e che può essere utilizzata nei filtri.

Il **[!UICONTROL Response HTTP headers]** consente di impedire il clickjacking quando si include la pagina del report in una pagina HTML utilizzando iframe. Per evitare il clickjacking, puoi scegliere **[!UICONTROL X-Frame-options header]** comportamento:

* **[!UICONTROL None]**: il rapporto non avrà **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: impostato per impostazione predefinita per i nuovi rapporti e i rapporti ripubblicati. Il nome host sarà lo stesso dell’URL del rapporto.
* **[!UICONTROL Deny]**: il report non può essere incluso in una pagina HTML utilizzando iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Aggiunta di variabili {#adding-variables}

Il **[!UICONTROL Variables]** La scheda contiene l’elenco delle variabili configurate nel rapporto. Queste variabili sono esposte nel contesto del rapporto e possono essere utilizzate nei calcoli.

Fai clic su **[!UICONTROL Add]** per creare una nuova variabile.

Per visualizzare la definizione di una variabile, selezionala e fai clic sul pulsante **[!UICONTROL Detail...]** pulsante.

![](assets/s_ncs_advuser_report_properties_10.png)

## Caso d’uso: utilizzare variabili e parametri in un rapporto

Nell’esempio video seguente, scoprirai come aggiungere un parametro &quot;_type&quot; per creare visualizzazioni diverse di un rapporto, in base al valore di questo attributo.

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## Richiamo di un altro report {#calling-up-another-report}

A **Salta** l’attività è simile a una transizione senza freccia: ti consente di passare da un’attività all’altra o di accedere a un altro rapporto.
