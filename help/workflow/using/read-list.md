---
product: campaign
title: Lettura di un elenco
description: Ulteriori informazioni sull’attività del flusso di lavoro Read list (Leggi elenco)
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Lettura di un elenco{#read-list}



I dati elaborati in un flusso di lavoro possono provenire da elenchi in cui i dati sono stati preparati o strutturati in precedenza (dopo una precedente segmentazione o caricamento di file).

L&#39;attività **[!UICONTROL Read list]** consente di copiare i dati da un elenco nella tabella di lavoro del flusso di lavoro, come i dati di una query. È quindi accessibile in tutto il flusso di lavoro.

L&#39;elenco da elaborare può essere specificato esplicitamente, calcolato da uno script o localizzato in modo dinamico, in base alle opzioni selezionate e ai parametri definiti in un&#39;attività **[!UICONTROL Read list]**.

![](assets/list_edit_select_option_01.png)

Se l’elenco non è specificato in modo esplicito, devi fornire un elenco da utilizzare come modello per scoprirne la struttura.

![](assets/s_advuser_list_template_select.png)

Una volta configurata la selezione dell&#39;elenco, è possibile aggiungere un filtro utilizzando l&#39;opzione **[!UICONTROL Edit query]** per mantenere una parte della popolazione per il flusso di lavoro successivo.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Per poter creare un filtro in un’attività di lettura elenco, l’elenco pertinente deve essere di tipo &quot;file&quot;.

Gli elenchi possono essere creati direttamente in Adobe Campaign tramite il collegamento **[!UICONTROL Profiles and Targets > Lists]** della home page. Possono essere create anche in un flusso di lavoro utilizzando l&#39;attività **[!UICONTROL List update]**.

**Esempio: escludere un elenco di indirizzi di invio**

L’esempio seguente ti consente di utilizzare un elenco di indirizzi e-mail da escludere dal target della consegna e-mail.

![](assets/s_advuser_list_read_sample_1.png)

I profili contenuti nella cartella **Nuovi contatti** devono essere interessati da un&#39;azione di consegna. Gli indirizzi e-mail da escludere dal target vengono memorizzati in un elenco esterno. Nel nostro esempio, per l’esclusione sono necessarie solo le informazioni sugli indirizzi e-mail.

1. La query di selezione della cartella **Nuovi contatti** deve consentire di caricare gli indirizzi e-mail dei profili selezionati, per consentire l&#39;allineamento con le informazioni nell&#39;elenco.

   ![](assets/s_advuser_list_read_sample_0.png)

1. In questo caso, l&#39;elenco viene archiviato nella cartella **Elenchi** e l&#39;etichetta viene calcolata.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Per escludere gli indirizzi di posta elettronica dell&#39;elenco esterno dalla destinazione principale, è necessario configurare l&#39;attività di esclusione e specificare che la cartella **Nuovi contatti** contiene i dati da mantenere. I dati congiunti tra questo set e qualsiasi altro set in entrata dall’attività di esclusione verranno eliminati dal target.

   ![](assets/s_advuser_list_read_sample_3.png)

   Le regole di esclusione sono configurate nella sezione centrale dello strumento di modifica. Fare clic sul pulsante **[!UICONTROL Add]** per definire il tipo di esclusione da applicare.

   Puoi definire diverse esclusioni a seconda del numero di transizioni in entrata dell’attività.

1. Nel campo **[!UICONTROL Exclusion set]**, selezionare l&#39;attività **[!UICONTROL Read list]**: i dati in questa attività devono essere esclusi dal set principale.

   Nel nostro esempio, abbiamo un’esclusione sui join: i dati contenuti nell’elenco verranno riconciliati con i dati del set principale tramite il campo contenente l’indirizzo e-mail. Per configurare il join, selezionare **[!UICONTROL Joins]** nel campo **[!UICONTROL Change dimension]**.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Quindi seleziona il campo corrispondente all’indirizzo e-mail nei due set (Source e Destinazione). Le colonne verranno quindi collegate e i destinatari il cui indirizzo e-mail si trova nell’elenco degli indirizzi importati verranno esclusi dal target.
