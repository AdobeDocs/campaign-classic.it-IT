---
solution: Campaign Classic
product: campaign
title: Funzionalità avanzate
description: Funzionalità avanzate
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 4%

---


# Funzionalità avanzate{#advanced-functionalities}

In qualità di utente tecnico, oltre alle proprietà [](../../reporting/using/properties-of-the-report.md)generali, potete utilizzare funzionalità avanzate per configurare i rapporti, ad esempio:

* Creare query complesse per elaborare i dati in un&#39;attività **Script** . [Ulteriori informazioni](#script-activity)

* Aggiungere uno script esterno da eseguire sul lato server o client. [Ulteriori informazioni](#external-script)

* Chiama un rapporto con un&#39;attività **Jump** . [Ulteriori informazioni](#calling-up-another-report)

* Aggiungete un parametro URL a un report per renderlo più accessibile. [Ulteriori informazioni](#calling-up-another-report)

* Aggiungere le variabili da utilizzare nel contesto del rapporto. [Ulteriori informazioni](#adding-variables)

## Uso degli script {#adding-a-script}

### Riferimento a script esterni {#external-script}

Potete fare riferimento ai codici JavaScript che verranno eseguiti sul lato client e/o server quando viene richiamata la pagina del rapporto.

Per eseguire questa operazione:

1. Modificate le proprietà [del](../../reporting/using/properties-of-the-report.md) rapporto e fate clic sul **[!UICONTROL Scripts]**.
1. Fare clic **[!UICONTROL Add]** e selezionare lo script a cui fare riferimento.
1. Selezionate quindi la modalità di esecuzione.

   Se si aggiungono diversi script, utilizzare le frecce della barra degli strumenti per definire la sequenza di esecuzione.

   ![](assets/reporting_custom_js.png)

Per una normale esecuzione sul lato client, gli script di riferimento devono essere scritti in JavaScript e devono essere compatibili con i browser più comuni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/web-forms-answers.md).

### Aggiunta di un&#39;attività di script {#script-activity}

Durante la [progettazione del rapporto](../../reporting/using/creating-a-new-report.md#modelizing-the-chart), utilizzate l&#39; **[!UICONTROL Script]** attività per elaborare i dati e creare facilmente query complesse che non abilitano SQL Language. È possibile immettere direttamente la query nella finestra dello script.

La **[!UICONTROL Texts]** scheda consente di definire le stringhe di testo. Possono quindi essere utilizzati con la sintassi seguente: **$(Identifier)**. Per ulteriori informazioni sull&#39;uso dei testi, vedere [Aggiunta di un&#39;intestazione e di un piè di pagina](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>NON è consigliabile utilizzare il codice JavaScript per creare aggregati.

Per creare una cronologia del rapporto, aggiungere la riga seguente alla query JavaScript per salvare i dati archiviati:

```
if( ctx.@_historyId.toString().length == 0 )
```

In caso contrario verranno visualizzati solo i dati correnti.

## Aggiunta di un parametro URL {#defining-additional-settings}

La **[!UICONTROL Parameters]** scheda delle proprietà [del](../../reporting/using/properties-of-the-report.md) rapporto consente di definire impostazioni aggiuntive per il rapporto: queste impostazioni verranno trasmesse all’URL durante la chiamata.

>[!CAUTION]
>
>Per motivi di sicurezza, questi parametri devono essere utilizzati con grande cautela.

Per creare una nuova impostazione:

1. Fate clic sul **[!UICONTROL Add]** pulsante e immettete il nome dell’impostazione.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Se necessario, specificate se l&#39;impostazione sarà obbligatoria o meno.

1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   L&#39; **[!UICONTROL Filter entities]** opzione consente di utilizzare un campo del database come parametro.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   I dati vengono recuperati direttamente a livello di entità: **ctx/receive/@account**.

   L&#39; **[!UICONTROL Variable]** opzione consente di creare o selezionare una variabile che verrà passata come parametro dell&#39;URL e che può essere utilizzata nei filtri.

Questo **[!UICONTROL Response HTTP headers]** consente di evitare il clic quando si inserisce la pagina del rapporto in una pagina HTML utilizzando iframe. Per evitare il clickjacking, potete scegliere il **[!UICONTROL X-Frame-options header]** comportamento:

* **[!UICONTROL None]**: Il rapporto non avrà alcun risultato **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Impostato per impostazione predefinita per i nuovi rapporti e i rapporti ripubblicati. Il nome host sarà uguale all&#39;URL del report.
* **[!UICONTROL Deny]**: Il rapporto non può essere incluso in una pagina HTML utilizzando iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Aggiunta di variabili {#adding-variables}

La **[!UICONTROL Variables]** scheda contiene l&#39;elenco delle variabili configurate nel rapporto. Queste variabili sono esposte nel contesto del rapporto e possono essere utilizzate nei calcoli.

Fate clic sul **[!UICONTROL Add]** pulsante per creare una nuova variabile.

Per visualizzare la definizione di una variabile, selezionatela e fate clic sul **[!UICONTROL Detail...]** pulsante.

![](assets/s_ncs_advuser_report_properties_10.png)

## Caso di utilizzo: utilizzare variabili e parametri in un rapporto

Nell’esempio seguente, scoprirete come aggiungere un parametro &quot;_type&quot; per creare diverse viste di un rapporto, in base al valore di questo attributo.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Chiamata di un altro rapporto {#calling-up-another-report}

Un&#39;attività **Jump** è come una transizione senza una freccia: consente di passare da un&#39;attività all&#39;altra o di accedere a un altro rapporto.
