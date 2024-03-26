---
product: campaign
title: Lettura di un elenco
description: Ulteriori informazioni sull’attività del flusso di lavoro Read list (Leggi elenco)
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Lettura di un elenco{#read-list}



I dati elaborati in un flusso di lavoro possono provenire da elenchi in cui i dati sono stati preparati o strutturati in precedenza (dopo una precedente segmentazione o caricamento di file).

Il **[!UICONTROL Read list]** attività consente di copiare i dati da un elenco nella tabella di lavoro del flusso di lavoro, come i dati di una query. È quindi accessibile in tutto il flusso di lavoro.

L’elenco da elaborare può essere specificato esplicitamente, calcolato da uno script o localizzato dinamicamente, in base alle opzioni selezionate e ai parametri definiti in un **[!UICONTROL Read list]** attività.

![](assets/list_edit_select_option_01.png)

Se l’elenco non è specificato in modo esplicito, devi fornire un elenco da utilizzare come modello per scoprirne la struttura.

![](assets/s_advuser_list_template_select.png)

Una volta configurata la selezione dell’elenco, puoi aggiungere un filtro utilizzando **[!UICONTROL Edit query]** per mantenere una parte della popolazione per il flusso di lavoro successivo.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Per poter creare un filtro in un’attività di lettura elenco, l’elenco pertinente deve essere di tipo &quot;file&quot;.

Gli elenchi possono essere creati direttamente in Adobe Campaign tramite **[!UICONTROL Profiles and Targets > Lists]** collegamento della home page. Possono essere create anche in un flusso di lavoro utilizzando **[!UICONTROL List update]** attività.

**Esempio: escludere un elenco di indirizzi di invio**

L’esempio seguente ti consente di utilizzare un elenco di indirizzi e-mail da escludere dal target della consegna e-mail.

![](assets/s_advuser_list_read_sample_1.png)

I profili contenuti nel **Nuovi contatti** La cartella deve essere interessata da un’azione di consegna. Gli indirizzi e-mail da escludere dal target vengono memorizzati in un elenco esterno. Nel nostro esempio, per l’esclusione sono necessarie solo le informazioni sugli indirizzi e-mail.

1. Il **Nuovi contatti** la query di selezione della cartella deve consentire di caricare gli indirizzi e-mail dei profili selezionati, al fine di abilitare l’allineamento con le informazioni nell’elenco.

   ![](assets/s_advuser_list_read_sample_0.png)

1. In questo caso, l’elenco viene memorizzato in **Elenchi** e la relativa etichetta.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Per escludere gli indirizzi e-mail dell’elenco esterno dal target principale, devi configurare l’attività di esclusione e specificare che il **Nuovi contatti** contiene i dati da conservare. I dati congiunti tra questo set e qualsiasi altro set in entrata dall’attività di esclusione verranno eliminati dal target.

   ![](assets/s_advuser_list_read_sample_3.png)

   Le regole di esclusione sono configurate nella sezione centrale dello strumento di modifica. Fai clic su **[!UICONTROL Add]** per definire il tipo di esclusione da applicare

   Puoi definire diverse esclusioni a seconda del numero di transizioni in entrata dell’attività.

1. In **[!UICONTROL Exclusion set]** , selezionare il campo **[!UICONTROL Read list]** attività: i dati di questa attività devono essere esclusi dal set principale.

   Nel nostro esempio, abbiamo un’esclusione sui join: i dati contenuti nell’elenco verranno riconciliati con i dati del set principale tramite il campo contenente l’indirizzo e-mail. Per configurare l’unione, seleziona **[!UICONTROL Joins]** nel **[!UICONTROL Change dimension]** campo.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Quindi seleziona il campo corrispondente all’indirizzo e-mail nei due set (Origine e Destinazione). Le colonne verranno quindi collegate e i destinatari il cui indirizzo e-mail si trova nell’elenco degli indirizzi importati verranno esclusi dal target.
