---
product: campaign
title: Come utilizzare i dati dei flussi di lavoro
description: Scopri come utilizzare i dati del flusso di lavoro
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# Come utilizzare i dati dei flussi di lavoro{#how-to-use-workflow-data}



## Aggiornamento del database {#updating-the-database}

Tutti i dati raccolti possono essere utilizzati per aggiornare il database o nelle consegne. Ad esempio, puoi arricchire le possibilità di personalizzazione del contenuto dei messaggi (include il numero di contratti nel messaggio, specifica il carrello medio nell’ultimo anno, ecc.) o il targeting dettagliato della popolazione (inviare un messaggio ai titolari di contratto, indirizzare i 1.000 migliori abbonati ai servizi online, ecc.). Questi dati possono anche essere esportati o archiviati in un elenco.

### Elenchi e aggiornamenti diretti {#lists-and-direct-updates}

I dati del database Adobe Campaign e degli elenchi esistenti possono essere aggiornati utilizzando due attività dedicate:

* La **[!UICONTROL List update]** attività ti consente di memorizzare tabelle di lavoro in un datalist.

   È possibile selezionare un elenco esistente o crearlo. In questo caso, vengono calcolati il nome e probabilmente la cartella di record.

   ![](assets/s_user_create_list.png)

   Fai riferimento a [Aggiornamento elenco](list-update.md).

* La **[!UICONTROL Update data]** l’attività esegue un aggiornamento di massa dei campi nel database.

   Per ulteriori informazioni, consulta [Update data](update-data.md).

### Gestione dell’abbonamento/annullamento dell’abbonamento {#subscription-unsubscription-management}

Per informazioni sull’abbonamento e l’annullamento dell’abbonamento dei destinatari a un servizio di informazione tramite un flusso di lavoro, consulta [Servizi sottoscrizione](subscription-services.md).

## Invio tramite un flusso di lavoro {#sending-via-a-workflow}

### Attività di consegna {#delivery-activity}

L’attività di consegna è descritta in [Consegna](delivery.md).

### Arricchimento e targeting delle consegne {#enriching-and-targeting-deliveries}

Le consegne possono elaborare i dati dai flussi di lavoro per personalizzare i contenuti o nel quadro della selezione della popolazione target.

Ad esempio, nel framework di una consegna direct mailing, puoi includere nel file di estrazione i dati aggiuntivi, tratti dalla manipolazione dei dati eseguita nel flusso di lavoro:

![](assets/s_advuser_add_data_postal_mail.png)

Oltre ai campi di personalizzazione consueti, puoi aggiungere campi di personalizzazione dalle fasi del flusso di lavoro al contenuto della consegna. I dati aggiuntivi definiti nelle attività del flusso di lavoro possono essere mantenuti e resi accessibili nella procedura guidata di consegna, come mostrato nell’esempio seguente, per definire il nome del file di output nel framework della consegna della direct mailing:

![](assets/s_advuser_using_additional_data.png)

I dati contenuti nella tabella del flusso di lavoro sono identificati dal relativo nome: è sempre costituito da **targetData** link. Per ulteriori informazioni, consulta [Dati di Target](data-life-cycle.md#target-data).

Nel framework della consegna e-mail, i campi di personalizzazione possono utilizzare anche i dati provenienti dall’estensione target eseguita nelle fasi del flusso di lavoro di targeting, come mostrato nell’esempio seguente:

![](assets/s_advuser_add_data_email.png)

Se un codice di segmento viene specificato in un’attività di targeting, viene aggiunto a una colonna specifica della tabella del flusso di lavoro e viene offerto insieme ai campi di personalizzazione. Per visualizzare tutti i campi di personalizzazione, fai clic sul pulsante **[!UICONTROL Target extension > Other...]** collegamento accessibile tramite il pulsante di personalizzazione .

![](assets/s_advuser_segment_code_select.png)
