---
product: campaign
title: Come utilizzare i dati del flusso di lavoro
description: Scopri come utilizzare i dati dei flussi di lavoro
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Come utilizzare i dati del flusso di lavoro{#how-to-use-workflow-data}



## Aggiornamento del database {#updating-the-database}

Tutti i dati raccolti possono essere utilizzati per aggiornare il database o nelle consegne. Ad esempio, puoi arricchire le possibilità di personalizzazione del contenuto dei messaggi (includere il numero di contratti nel messaggio, specificare il carrello acquisti medio nell’ultimo anno, ecc.) o specificare il targeting dettagliato della popolazione (inviare un messaggio ai titolari di contratti, indirizzare i 1.000 migliori abbonati ai servizi online, ecc.). Questi dati possono anche essere esportati o archiviati in un elenco.

### Elenchi e aggiornamenti diretti {#lists-and-direct-updates}

I dati del database di Adobe Campaign e gli elenchi esistenti possono essere aggiornati utilizzando due attività dedicate:

* L&#39;attività **[!UICONTROL List update]** consente di archiviare le tabelle di lavoro in un datalist.

  È possibile selezionare un elenco esistente o crearlo. In questo caso, vengono calcolati il nome e, se possibile, la cartella dei record.

  ![](assets/s_user_create_list.png)

  Consulta [Aggiornamento elenco](list-update.md).

* L&#39;attività **[!UICONTROL Update data]** esegue un aggiornamento di massa dei campi nel database.

  Per ulteriori informazioni, consulta [Aggiorna dati](update-data.md).

### Gestione abbonamento/annullamento abbonamento {#subscription-unsubscription-management}

Per informazioni sull&#39;abbonamento e l&#39;annullamento dell&#39;abbonamento dei destinatari a un servizio di informazioni tramite un flusso di lavoro, fare riferimento a [Servizi di abbonamento](subscription-services.md).

## Invio tramite un flusso di lavoro {#sending-via-a-workflow}

### Attività di consegna {#delivery-activity}

L&#39;attività di consegna è descritta in [Consegna](delivery.md).

### Arricchimento e targeting delle consegne {#enriching-and-targeting-deliveries}

Le consegne possono elaborare i dati dei flussi di lavoro per personalizzare il contenuto o nel quadro della selezione della popolazione target.

Ad esempio, nel quadro di una consegna direct mailing, puoi includere nel file di estrazione i dati aggiuntivi, derivati dalla manipolazione dei dati eseguita nel flusso di lavoro:

![](assets/s_advuser_add_data_postal_mail.png)

Oltre ai consueti campi di personalizzazione, puoi aggiungere campi di personalizzazione dalle fasi del flusso di lavoro al contenuto della consegna. I dati aggiuntivi definiti nelle attività del flusso di lavoro possono essere conservati e resi accessibili nell’assistente alla consegna, come mostrato nell’esempio seguente, per definire il nome del file di output nel quadro della consegna di direct mailing:

![](assets/s_advuser_using_additional_data.png)

I dati contenuti nella tabella del flusso di lavoro sono identificati dal nome: sono sempre costituiti dal collegamento **targetData**. Per ulteriori informazioni, consulta [Dati di destinazione](data-life-cycle.md#target-data).

Nel framework della consegna e-mail, i campi di personalizzazione possono anche utilizzare dati dell’estensione target eseguita nelle fasi del flusso di lavoro di targeting, come mostrato nell’esempio di seguito:

![](assets/s_advuser_add_data_email.png)

Se un codice di segmento è specificato in un’attività di targeting, viene aggiunto a una colonna specifica della tabella del flusso di lavoro e viene offerto insieme ai campi di personalizzazione. Per visualizzare tutti i campi di personalizzazione, fare clic sul collegamento **[!UICONTROL Target extension > Other...]** accessibile tramite il pulsante di personalizzazione.

![](assets/s_advuser_segment_code_select.png)
