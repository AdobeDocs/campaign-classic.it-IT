---
product: campaign
title: Tracciare una campagna
description: Scopri come tracciare una campagna con Campaign Distributed Marketing
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Distributed Marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# Tracciare una campagna{#tracking-a-campaign}



Gli operatori di entità centrale possono tenere traccia degli ordini delle campagne nell’elenco dei pacchetti delle campagne.

Questo consente di:

* [Pacchetti filtro](#filter-packages),
* [Modifica pacchetti](#edit-packages),
* [Annullare un pacchetto](#cancel-a-package),
* [Reinizializzare un pacchetto](#reinitializing-a-package).

## Pacchetti filtro {#filter-packages}

Da **[!UICONTROL Campaigns]** è possibile visualizzare l’elenco dei **[!UICONTROL Campaign packages]** raggruppa tutte le campagne Distributed Marketing esistenti. Puoi filtrare questo elenco in modo che visualizzi solo le campagne pubblicate, in ritardo, in attesa di approvazione, ecc. A questo scopo, fai clic sui collegamenti nella sezione superiore di questa visualizzazione oppure utilizza il **[!UICONTROL Filter list]** e seleziona lo stato del pacchetto della campagna da visualizzare.

![](assets/mkg_dist_catalog_filter.png)

## Modifica pacchetti {#edit-packages}

La **[!UICONTROL Campaign packages]** consente di visualizzare il riepilogo di ciascun pacchetto.

Questo riepilogo mostra le seguenti informazioni: etichetta, tipo di campagna, nome della campagna da cui è stata creata e la cartella.

Fai clic sul nome del pacchetto per modificarlo. È inoltre possibile visualizzare gli ordini in base alle rispettive entità locali e al loro stato.

Queste informazioni sono disponibili anche nel **[!UICONTROL Campaign orders]** visualizza l&#39;elenco di tutti gli ordini.

![](assets/mkg_dist_catalog_op_command_details.png)

L’operatore centrale può modificare l’ordine. Ci sono due modi per farlo:

1. L’operatore può fare clic sul nome dell’ordine per modificarlo: vengono visualizzati i dettagli dell’ordine.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   La **[!UICONTROL Edit > General]** consente di visualizzare le informazioni immesse dall’entità locale quando ha ordinato la campagna.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. L’operatore può fare clic sull’etichetta del pacchetto della campagna per modificarlo e modificare alcune impostazioni.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Annullare un pacchetto {#cancel-a-package}

L’entità centrale può annullare un pacchetto della campagna in qualsiasi momento.

Fai clic su **[!UICONTROL Cancel]** nel pacchetto della campagna **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

La **[!UICONTROL Comment]** consente di giustificare l’annullamento.

Per **campagne locali**, l’annullamento di un pacchetto lo rimuove dall’elenco delle campagne di marketing disponibili.

Per **campagne collaborative**, l’annullamento di un pacchetto attiva numerose azioni:

1. Tutti gli ordini relativi a questo pacchetto vengono annullati,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. La campagna di riferimento viene annullata e tutti i processi attivi (flussi di lavoro, consegne) vengono interrotti,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Viene inviata una notifica a tutti gli enti locali interessati.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

I pacchetti annullati possono ancora essere accessibili e reinizializzati dall&#39;entità centrale (vedi sotto), se necessario. Essi saranno offerti agli enti locali solo una volta approvati e avviati. Il processo di reinizializzazione del pacchetto è mostrato di seguito.

## Reinizializzare un pacchetto {#reinitializing-a-package}

I pacchetti di campagna già pubblicati possono essere reinizializzati, modificati e resi disponibili alle entità locali.

1. Selezionare il pacchetto in questione.
1. Fai clic sul pulsante **[!UICONTROL Reinitialize the package to reuse it]** collegamento e clic **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Fai clic sul pulsante **[!UICONTROL Save]** per approvare la reinizializzazione del pacchetto.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. Lo stato del pacchetto cambia in **[!UICONTROL Being edited]**. Modifica, approva e pubblica di nuovo per ripristinarlo nell’elenco del pacchetto della campagna.

>[!NOTE]
>
>È inoltre possibile reinizializzare i pacchetti campagna annullati.
