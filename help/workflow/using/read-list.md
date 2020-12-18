---
solution: Campaign Classic
product: campaign
title: Leggi elenco
description: Ulteriori informazioni sull'attività del flusso di lavoro Leggi elenco
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# Leggi elenco{#read-list}

I dati elaborati in un flusso di lavoro possono provenire da elenchi in cui i dati sono stati preparati o strutturati in anticipo (dopo una precedente segmentazione o caricamento di file).

L&#39;attività **[!UICONTROL Read list]** consente di copiare i dati da un elenco nella tabella di lavoro del flusso di lavoro, come i dati di una query. che può essere accessibile in tutto il flusso di lavoro.

L&#39;elenco da elaborare può essere specificato esplicitamente, calcolato da uno script o localizzato dinamicamente, in base alle opzioni selezionate e ai parametri definiti in un&#39;attività **[!UICONTROL Read list]**.

![](assets/list_edit_select_option_01.png)

Se l&#39;elenco non è specificato in modo esplicito, è necessario fornire un elenco da utilizzare come modello per individuarne la struttura.

![](assets/s_advuser_list_template_select.png)

Una volta configurata la selezione dell&#39;elenco, potete aggiungere un filtro utilizzando l&#39;opzione **[!UICONTROL Edit query]** per mantenere una parte della popolazione per il flusso di lavoro successivo.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Per poter creare un filtro in un&#39;attività dell&#39;elenco di lettura, l&#39;elenco pertinente deve essere di tipo &quot;file&quot;.

Gli elenchi possono essere creati direttamente in  Adobe Campaign tramite il collegamento **[!UICONTROL Profiles and Targets > Lists]** della home page. Possono anche essere creati in un flusso di lavoro utilizzando l&#39;attività **[!UICONTROL List update]**.

**Esempio: Escludere un elenco di indirizzi di invio**

L’esempio seguente consente di utilizzare un elenco di indirizzi e-mail da escludere dalla destinazione di consegna delle e-mail.

![](assets/s_advuser_list_read_sample_1.png)

I profili contenuti nella cartella **Nuovi contatti** devono essere mirati da un&#39;azione di consegna. Gli indirizzi e-mail da escludere dalla destinazione sono memorizzati in un elenco esterno. Nel nostro esempio, solo le informazioni sugli indirizzi e-mail sono necessarie per l&#39;esclusione.

1. La query di selezione della cartella **New Contatti** deve consentire di caricare gli indirizzi e-mail dei profili selezionati, al fine di abilitare l&#39;allineamento con le informazioni nell&#39;elenco.

   ![](assets/s_advuser_list_read_sample_0.png)

1. In questo caso, l&#39;elenco viene memorizzato nella cartella **Lists** e la relativa etichetta viene calcolata.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Per escludere gli indirizzi e-mail dell&#39;elenco esterno dalla destinazione principale, è necessario configurare l&#39;attività di esclusione e specificare che la cartella **Nuovi contatti** contiene i dati da conservare. I dati comuni tra questo set e qualsiasi altro set in entrata dall&#39;attività di esclusione verranno eliminati dalla destinazione.

   ![](assets/s_advuser_list_read_sample_3.png)

   Le regole di esclusione sono configurate nella sezione centrale dello strumento di modifica. Fare clic sul pulsante **[!UICONTROL Add]** per definire il tipo di esclusione da applicare.

   Potete definire diverse esclusioni in base al numero di transizioni in entrata dell&#39;attività.

1. Nel campo **[!UICONTROL Exclusion set]**, selezionare l&#39;attività **[!UICONTROL Read list]**: i dati contenuti in questa attività devono essere esclusi dalla serie principale.

   Nel nostro esempio, esiste un&#39;esclusione per le unioni: i dati contenuti nell&#39;elenco verranno riconciliati con i dati del set principale tramite il campo contenente l&#39;indirizzo e-mail. Per configurare il join, selezionare **[!UICONTROL Joins]** nel campo **[!UICONTROL Change dimension]**.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Selezionate quindi il campo corrispondente all’indirizzo e-mail nei due set (Origine e Destinazione). Le colonne verranno quindi collegate e i destinatari il cui indirizzo e-mail è nell&#39;elenco degli indirizzi importati verranno esclusi dalla destinazione.

