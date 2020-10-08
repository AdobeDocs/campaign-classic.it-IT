---
title: Azioni sui report
seo-title: Azioni sui report
description: Azioni sui report
seo-description: null
page-status-flag: never-activated
uuid: 7f9d99ab-ce19-46dd-bbf0-79de348d38fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 3b9c138e-8f7f-4ee1-9baa-328848d01d3a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---


# Azioni sui report{#actions-on-reports}

Quando visualizzate un rapporto, la barra degli strumenti consente di eseguire un certo numero di azioni. Questi sono descritti di seguito.

![](assets/s_ncs_advuser_report_wizard_2.png)

La barra degli strumenti consente, ad esempio, di esportare, stampare, archiviare o visualizzare il rapporto in un browser Web.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Esportazione di un rapporto {#exporting-a-report}

Dall’elenco a discesa, selezionate il formato in cui desiderate esportare il rapporto. (.xls, .pdf o .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Quando un rapporto contiene più pagine, è necessario ripetere l&#39;operazione per ogni pagina.

È possibile configurare il rapporto per esportarlo in formato PDF, Excel o OpenOffice. Aprite  Adobe Campaign Explorer e selezionate il report interessato.

Le opzioni di esportazione sono accessibili tramite le **[!UICONTROL Page]** attività del rapporto, nella **[!UICONTROL Advanced]** scheda.

Modificate le impostazioni di **[!UICONTROL Paper]** e **[!UICONTROL Margins]** in base alle vostre esigenze. È inoltre possibile autorizzare l’esportazione di una pagina solo in formato PDF. Per eseguire questa operazione, deselezionare l&#39; **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** opzione.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Esportazione in Microsoft Excel {#exporting-into-microsoft-excel}

Per i report di **[!UICONTROL List with group]** tipo destinati all&#39;esportazione in Excel, si applicano le seguenti raccomandazioni e limitazioni:

* Tali rapporti non devono contenere righe vuote.

   ![](assets/export_limitations_remove_empty_line.png)

* La legenda dell&#39;elenco deve essere nascosta.

   ![](assets/export_limitations_hide_label.png)

* I rapporti non devono utilizzare una formattazione specifica definita a livello di cella. È preferibile utilizzare **[!UICONTROL Form rendering]** per definire il formato delle celle nella tabella. È **[!UICONTROL Form rendering]** possibile accedervi tramite **[!UICONTROL Administration > Configuration > Form rendering]**.
* Non è consigliabile inserire contenuto HTML.
* Se un rapporto contiene diverse tabelle, grafici e così via. gli elementi di tipo, verranno esportati uno sotto l’altro.
* È possibile forzare il ritorno a capo in celle: questa configurazione verrà mantenuta in Excel. Per ulteriori informazioni, vedere [Definizione del formato](../../reporting/using/creating-a-table.md#defining-cell-format)delle celle.

### Posticipare l&#39;esportazione {#postpone-the-export}

Potete posticipare l’esportazione di un rapporto, ad esempio per attendere le chiamate asincrone. A questo scopo, immettete il seguente parametro nello script di inizializzazione della pagina:

```
document.nl_waitBeforeRender = true;
```

Per attivare l’esportazione e iniziare la conversione in PDF, utilizzare la funzione **document.nl_renderizzazioneToPdf()** senza alcun parametro.

### Allocazione memoria {#memory-allocation}

Quando si esportano alcuni report di grandi dimensioni, possono verificarsi errori di allocazione della memoria.

In alcuni casi, il valore predefinito **maxMB** (**SKMS** per le istanze ospitate) del codice JavaScript indicato nel file di configurazione **serverConf.xml** è impostato su 64 MB. Se durante l&#39;esportazione di un rapporto si verificano errori di memoria insufficienti, è consigliabile aumentare questa cifra a 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Per applicare le modifiche apportate alla configurazione, è necessario riavviare il servizio **nlserver** .

Per ulteriori informazioni sul file **serverConf.xml** , consultare [questa sezione](../../production/using/configuration-principle.md).

Per ulteriori informazioni sul servizio **nlserver** , consultare [questa sezione](../../production/using/administration.md).

## Stampa di un rapporto {#printing-a-report}

È possibile stampare il rapporto: a questo scopo, fare clic sull&#39;icona della stampante: si apre la finestra di dialogo.

Per ottenere un risultato migliore, modificate le opzioni di stampa di Internet Explorer e selezionate **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Creazione di archivi di rapporti {#creating-report-archives}

L&#39;archiviazione di un rapporto consente di creare una visualizzazione del rapporto in diversi periodi, ad esempio per mostrare le statistiche per un determinato periodo di tempo.

Per creare un archivio, aprite il rapporto interessato e fate clic sull&#39;icona appropriata.

![](assets/s_ncs_advuser_report_wizard_07.png)

Per visualizzare o nascondere gli archivi esistenti, fate clic sull’icona Mostra/nascondi .

![](assets/s_ncs_advuser_report_history_06.png)

Le date dell&#39;archivio vengono visualizzate sotto l&#39;icona Mostra/Nascondi. Fare clic sull&#39;archivio per visualizzarlo.

![](assets/s_ncs_advuser_report_history_04.png)

È possibile eliminare un archivio di report. A tal fine, andate al nodo Adobe Campaign  in cui sono memorizzati i rapporti. Fare clic sulla **[!UICONTROL Archives]** scheda, selezionare quella da eliminare e fare clic su **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)

