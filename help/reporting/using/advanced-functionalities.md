---
product: campaign
title: Funzionalità avanzate
description: Funzionalità avanzate
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 5%

---

# Funzionalità avanzate{#advanced-functionalities}

![](../../assets/common.svg)

In qualità di utente tecnico, oltre a [proprietà generali](../../reporting/using/properties-of-the-report.md), puoi sfruttare le funzionalità avanzate per configurare i rapporti, ad esempio:

* Crea query complesse per elaborare i dati in un&#39;attività **Script**. [Ulteriori informazioni](#script-activity)

* Aggiungi uno script esterno da eseguire sul lato server o client. [Ulteriori informazioni](#external-script)

* Chiama un report con un&#39;attività **Jump** . [Ulteriori informazioni](#calling-up-another-report)

* Aggiungi un parametro URL a un rapporto per renderlo più accessibile. [Ulteriori informazioni](#calling-up-another-report)

* Aggiungi le variabili da utilizzare nel contesto del rapporto. [Ulteriori informazioni](#adding-variables)

## Utilizzo degli script {#adding-a-script}

### Riferimento a script esterni {#external-script}

È possibile fare riferimento ai codici JavaScript che verranno eseguiti sul lato client e/o server quando viene richiamata la pagina del rapporto.

Per eseguire questa operazione:

1. Modifica le proprietà del [report](../../reporting/using/properties-of-the-report.md) e fai clic su **[!UICONTROL Scripts]**.
1. Fare clic su **[!UICONTROL Add]** e selezionare lo script a cui fare riferimento.
1. Quindi seleziona la modalità di esecuzione.

   Se si aggiungono diversi script, utilizzare le frecce della barra degli strumenti per definirne la sequenza di esecuzione.

   ![](assets/reporting_custom_js.png)

Per una normale esecuzione sul lato client, gli script a cui si fa riferimento devono essere scritti in JavaScript e devono essere compatibili con i browser più comuni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/web-forms-answers.md).

### Aggiunta di un’attività Script {#script-activity}

Durante la [progettazione del report](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), utilizza l&#39;attività **[!UICONTROL Script]** per elaborare i dati e creare facilmente query complesse che non abilitano SQL Language. È possibile immettere direttamente la query nella finestra dello script.

La scheda **[!UICONTROL Texts]** consente di definire stringhe di testo. Possono quindi essere utilizzati con la seguente sintassi: **$(Identifier)**. Per ulteriori informazioni sull&#39;utilizzo dei testi, vedere [Aggiunta di un&#39;intestazione e di un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>NON è consigliabile utilizzare il codice JavaScript per creare aggregati.

Per creare una cronologia del rapporto, aggiungi la seguente riga alla query JavaScript per salvare i dati archiviati:

```
if( ctx.@_historyId.toString().length == 0 )
```

In caso contrario, verranno visualizzati solo i dati correnti.

## Aggiunta di un parametro URL {#defining-additional-settings}

La scheda **[!UICONTROL Parameters]** delle [proprietà del report](../../reporting/using/properties-of-the-report.md) consente di definire impostazioni aggiuntive per il report: queste impostazioni verranno passate nell’URL durante la chiamata .

>[!CAUTION]
>
>Per motivi di sicurezza, questi parametri devono essere utilizzati con grande cautela.

Per creare una nuova impostazione:

1. Fai clic sul pulsante **[!UICONTROL Add]** e immetti il nome dell’impostazione.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessario, specifica se l’impostazione sarà obbligatoria o meno.

1. Seleziona il tipo di impostazione da creare: **[!UICONTROL Filter]** o **[!UICONTROL Variable]**.

   L’opzione **[!UICONTROL Filter entities]** ti consente di utilizzare un campo del database come parametro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   I dati vengono recuperati direttamente a livello di entità: **ctx/recipient/@account**.

   L’opzione **[!UICONTROL Variable]** ti consente di creare o selezionare una variabile che verrà passata come parametro dell’URL e può essere utilizzata nei filtri.

Il **[!UICONTROL Response HTTP headers]** consente di evitare il clickjacking quando si include la pagina del rapporto in una pagina HTML utilizzando iframe. Per evitare il clickjacking, puoi scegliere il comportamento **[!UICONTROL X-Frame-options header]**:

* **[!UICONTROL None]**: Il rapporto non avrà  **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Impostato per impostazione predefinita per nuovi rapporti e rapporti ripubblicati. Il nome host sarà lo stesso dell’URL del rapporto.
* **[!UICONTROL Deny]**: Il rapporto non può essere incluso in una pagina HTML utilizzando iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Aggiunta di variabili {#adding-variables}

La scheda **[!UICONTROL Variables]** contiene l’elenco delle variabili configurate nel rapporto. Queste variabili sono esposte nel contesto del rapporto e possono essere utilizzate nei calcoli.

Fai clic sul pulsante **[!UICONTROL Add]** per creare una nuova variabile.

Per visualizzare la definizione di una variabile, selezionala e fai clic sul pulsante **[!UICONTROL Detail...]** .

![](assets/s_ncs_advuser_report_properties_10.png)

## Caso d’uso: utilizzare variabili e parametri in un rapporto

Nell’esempio video seguente, imparerai come aggiungere un parametro &quot;_type&quot; per creare visualizzazioni diverse di un rapporto, in base al valore di questo attributo.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Chiamata di un altro rapporto {#calling-up-another-report}

Un&#39;attività **Jump** è simile a una transizione senza una freccia: ti consente di passare da un’attività all’altra o di accedere a un altro rapporto.
