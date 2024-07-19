---
product: campaign
title: Azioni sui rapporti
description: Azioni sui rapporti
feature: Reporting, Monitoring
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 3%

---

# Azioni sui rapporti{#actions-on-reports}



Quando visualizzi un rapporto, la barra degli strumenti ti consente di eseguire un certo numero di azioni. Tali informazioni sono descritte di seguito.

![](assets/s_ncs_advuser_report_wizard_2.png)

La barra degli strumenti consente di esportare, stampare, archiviare o visualizzare il rapporto, ad esempio in un browser Web.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Esportare un rapporto {#exporting-a-report}

Seleziona il formato in cui desideri esportare il rapporto dall’elenco a discesa. (.xls, .pdf o .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Quando un report contiene più pagine, è necessario ripetere l’operazione per ogni pagina.

Puoi configurare il report per esportarlo in formato PDF, Excel o OpenOffice. Apri Adobe Campaign Explorer e seleziona il rapporto interessato.

Le opzioni di esportazione sono accessibili tramite le attività **[!UICONTROL Page]** del report, nella scheda **[!UICONTROL Advanced]**.

Modifica le impostazioni di **[!UICONTROL Paper]** e **[!UICONTROL Margins]** in base alle tue esigenze. Puoi anche autorizzare l’esportazione di una pagina solo in formato PDF. Per eseguire questa operazione, deselezionare l&#39;opzione **[!UICONTROL Activate OpenOffice/Microsoft Excel export]**.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Esporta in Microsoft Excel {#exporting-into-microsoft-excel}

Per i report di tipo **[!UICONTROL List with group]** destinati all&#39;esportazione in Excel, si applicano le seguenti raccomandazioni e limitazioni:

* Questi rapporti non devono contenere righe vuote.

  ![](assets/export_limitations_remove_empty_line.png)

* La legenda dell&#39;elenco deve essere nascosta.

  ![](assets/export_limitations_hide_label.png)

* I rapporti non devono utilizzare una formattazione specifica definita a livello di cella. È preferibile utilizzare **[!UICONTROL Form rendering]** per definire il formato delle celle nella tabella. **[!UICONTROL Form rendering]** è accessibile tramite **[!UICONTROL Administration > Configuration > Form rendering]**.
* Si sconsiglia di inserire contenuto HTML.
* Se un rapporto contiene più tabelle, grafici, ecc. elementi di tipo, verranno esportati uno sotto l&#39;altro.
* Puoi forzare il ritorno a capo nelle celle: questa configurazione verrà mantenuta in Excel. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/creating-a-table.md#defining-cell-format).

### Posticipa l&#39;esportazione {#postpone-the-export}

Puoi posticipare l’esportazione di un rapporto, ad esempio per attendere chiamate asincrone. A questo scopo, immetti il seguente parametro nello script di inizializzazione della pagina:

```
document.nl_waitBeforeRender = true;
```

Per attivare l&#39;esportazione e iniziare la conversione in un PDF, utilizzare la funzione **document.nl_renderToPdf()** senza alcun parametro.

### Allocazione di memoria {#memory-allocation}

Durante l’esportazione di alcuni rapporti di grandi dimensioni, possono verificarsi errori di allocazione della memoria.

In alcune istanze, il valore predefinito **maxMB** (**SKMS** per le istanze ospitate) del JavaScript indicato nel file di configurazione **serverConf.xml** è impostato su 64 MB. In caso di errori di memoria insufficiente durante l’esportazione di un rapporto, si consiglia di aumentare questo valore a 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Per applicare le modifiche apportate alla configurazione, è necessario riavviare il servizio **nlserver**.

Per ulteriori informazioni sul file **serverConf.xml**, vedere [questa sezione](../../production/using/configuration-principle.md).

Per ulteriori informazioni sul servizio **nlserver**, vedere [questa sezione](../../production/using/administration.md).

## Stampare un rapporto {#printing-a-report}

Puoi stampare il rapporto: a questo scopo, fai clic sull’icona della stampante: viene visualizzata la finestra di dialogo.

Per ottenere risultati migliori, modificare le opzioni di stampa di Explorer e selezionare **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Creare archivi di rapporti {#creating-report-archives}

L’archiviazione di un rapporto consente di creare una visualizzazione del rapporto in vari periodi, ad esempio per visualizzare le statistiche per un determinato periodo di tempo.

Per creare un archivio, apri il rapporto in questione e fai clic sull’icona appropriata.

![](assets/s_ncs_advuser_report_wizard_07.png)

Per visualizzare o nascondere gli archivi esistenti, fare clic sull&#39;icona Mostra/Nascondi.

![](assets/s_ncs_advuser_report_history_06.png)

Le date dell&#39;archivio vengono visualizzate sotto l&#39;icona mostra/nascondi. Fai clic sull’archivio per visualizzarlo.

![](assets/s_ncs_advuser_report_history_04.png)

È possibile eliminare un archivio di rapporti. A questo scopo, vai al nodo Adobe Campaign in cui sono memorizzati i rapporti. Fare clic sulla scheda **[!UICONTROL Archives]**, selezionare quella che si desidera eliminare e fare clic su **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
