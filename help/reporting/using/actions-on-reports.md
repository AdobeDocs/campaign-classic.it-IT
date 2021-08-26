---
product: campaign
title: Azioni sui rapporti
description: Azioni sui rapporti
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# Azioni sui rapporti{#actions-on-reports}

![](../../assets/common.svg)

Quando visualizzi un rapporto, la barra degli strumenti ti consente di eseguire un certo numero di azioni. Questi sono descritti di seguito.

![](assets/s_ncs_advuser_report_wizard_2.png)

La barra degli strumenti consente, ad esempio, di esportare, stampare, archiviare o visualizzare il rapporto in un browser Web.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Esportazione di un report {#exporting-a-report}

Seleziona il formato in cui esportare il rapporto dall’elenco a discesa. (.xls, .pdf o .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Quando un rapporto contiene più pagine, è necessario ripetere l’operazione per ogni pagina.

È possibile configurare il rapporto in modo da esportarlo in formato PDF, Excel o OpenOffice. Apri Adobe Campaign Explorer e seleziona il rapporto interessato.

Le opzioni di esportazione sono accessibili tramite le attività **[!UICONTROL Page]** del rapporto, nella scheda **[!UICONTROL Advanced]** .

Modifica le impostazioni di **[!UICONTROL Paper]** e **[!UICONTROL Margins]** in base alle tue esigenze. È inoltre possibile autorizzare l’esportazione di una pagina solo in formato PDF. A questo scopo, deseleziona l’opzione **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** .

![](assets/s_ncs_advuser_report_wizard_021.png)

### Esportazione in Microsoft Excel {#exporting-into-microsoft-excel}

Per i report di tipo **[!UICONTROL List with group]** destinati all&#39;esportazione in Excel, si applicano le seguenti raccomandazioni e limitazioni:

* Questi rapporti non devono contenere righe vuote.

   ![](assets/export_limitations_remove_empty_line.png)

* La legenda dell&#39;elenco deve essere nascosta.

   ![](assets/export_limitations_hide_label.png)

* I rapporti non devono utilizzare una formattazione specifica definita a livello di cella. È preferibile utilizzare **[!UICONTROL Form rendering]** per definire il formato delle celle nella tabella. È possibile accedere a **[!UICONTROL Form rendering]** tramite **[!UICONTROL Administration > Configuration > Form rendering]**.
* Non è consigliabile inserire contenuto HTML.
* Se un report contiene diverse tabelle, grafici e così via. gli elementi di tipo , saranno esportati uno sotto l’altro.
* È possibile forzare il ritorno a capo nelle celle: questa configurazione verrà mantenuta in Excel. Per ulteriori informazioni, consulta questo documento [Definizione del formato della cella](../../reporting/using/creating-a-table.md#defining-cell-format).

### Posticipare l&#39;esportazione {#postpone-the-export}

Puoi posticipare l’esportazione di un rapporto, ad esempio per attendere le chiamate asincrone. A questo scopo, immetti il seguente parametro nello script di inizializzazione della pagina:

```
document.nl_waitBeforeRender = true;
```

Per attivare l’esportazione e iniziare la conversione in un PDF, utilizza la funzione **document.nl_renderToPdf()** senza alcun parametro.

### Allocazione della memoria {#memory-allocation}

Quando si esportano alcuni report di grandi dimensioni, possono verificarsi errori di allocazione della memoria.

In alcune istanze, il valore predefinito **maxMB** (**SKMS** per le istanze in hosting) del JavaScript indicato nel file di configurazione **serverConf.xml** è impostato su 64 MB. Se durante l&#39;esportazione di un report si verificano errori di memoria insufficienti, è consigliabile aumentare questa cifra a 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Per applicare le modifiche apportate alla configurazione, è necessario riavviare il servizio **nlserver**.

Per ulteriori informazioni sul file **serverConf.xml**, consulta [questa sezione](../../production/using/configuration-principle.md).

Per ulteriori informazioni sul servizio **nlserver**, consulta [questa sezione](../../production/using/administration.md).

## Stampa di un report {#printing-a-report}

È possibile stampare il rapporto: a questo scopo, fai clic sull’icona della stampante: viene visualizzata la finestra di dialogo.

Per ottenere un risultato migliore, modificare le opzioni di stampa di Internet Explorer e selezionare **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Creazione di archivi dei rapporti {#creating-report-archives}

L’archiviazione di un rapporto consente di creare una visualizzazione del rapporto in diversi periodi, ad esempio per mostrare le statistiche per un determinato periodo di tempo.

Per creare un archivio, apri il rapporto interessato e fai clic sull’icona appropriata.

![](assets/s_ncs_advuser_report_wizard_07.png)

Per visualizzare o nascondere gli archivi esistenti, fai clic sull’icona mostra/nascondi .

![](assets/s_ncs_advuser_report_history_06.png)

Le date dell’archivio vengono visualizzate sotto l’icona mostra/nascondi . Fai clic sull’archivio per visualizzarlo.

![](assets/s_ncs_advuser_report_history_04.png)

È possibile eliminare un archivio dei rapporti. A questo scopo, vai al nodo Adobe Campaign in cui sono memorizzati i tuoi rapporti. Fai clic sulla scheda **[!UICONTROL Archives]** , seleziona quella da eliminare e fai clic su **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
