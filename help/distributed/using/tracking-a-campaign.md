---
product: campaign
title: Tracciare una campagna
description: Scopri come tracciare una campagna con Campaign Distributed Marketing
feature: Distributed Marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# Tracciare una campagna{#tracking-a-campaign}



Gli operatori di entità centrali possono tenere traccia degli ordini delle campagne nell’elenco dei pacchetti di campagne.

Ciò consente loro di:

* [Filtra pacchetti](#filter-packages),
* [Modifica pacchetti](#edit-packages),
* [Annulla pacchetto](#cancel-a-package),
* [Reinizializzare un pacchetto](#reinitializing-a-package).

## Filtrare i pacchetti {#filter-packages}

Dalla scheda **[!UICONTROL Campaigns]**, puoi visualizzare l&#39;elenco di **[!UICONTROL Campaign packages]** che raggruppa tutte le campagne Distributed Marketing esistenti. Puoi filtrare questo elenco in modo da visualizzare solo le campagne pubblicate, in ritardo, in attesa di approvazione, ecc. A questo scopo, fai clic sui collegamenti nella sezione superiore di questa visualizzazione, oppure utilizza il collegamento **[!UICONTROL Filter list]** e seleziona lo stato del pacchetto della campagna da visualizzare.

![](assets/mkg_dist_catalog_filter.png)

## Modifica pacchetti {#edit-packages}

La pagina **[!UICONTROL Campaign packages]** consente di visualizzare il riepilogo di ciascun pacchetto.

Questo riepilogo mostra le seguenti informazioni: etichetta, tipo di campagna, nonché il nome della campagna da cui è stata creata e la cartella.

Fai clic sul nome del pacchetto per modificarlo. È inoltre possibile visualizzare gli ordini in base alle entità locali e allo stato.

Queste informazioni sono disponibili anche nella visualizzazione **[!UICONTROL Campaign orders]** che elenca tutti gli ordini.

![](assets/mkg_dist_catalog_op_command_details.png)

L’operatore centrale può modificare l’ordine. Esistono due modi per farlo:

1. L’operatore può fare clic sul nome dell’ordine per modificarlo: vengono visualizzati i dettagli dell’ordine.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   La scheda **[!UICONTROL Edit > General]** consente di visualizzare le informazioni immesse dall&#39;entità locale quando ha ordinato la campagna.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. L’operatore può fare clic sull’etichetta del pacchetto della campagna per modificarla e modificare alcune impostazioni.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Annullare un pacchetto {#cancel-a-package}

L’entità centrale può annullare un pacchetto della campagna in qualsiasi momento.

Fare clic su **[!UICONTROL Cancel]** nel pacchetto della campagna **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

Il campo **[!UICONTROL Comment]** consente di giustificare l&#39;annullamento.

Per **campagne locali**, l&#39;annullamento di un pacchetto ne comporta la rimozione dall&#39;elenco delle campagne di marketing disponibili.

Per **campagne collaborative**, l&#39;annullamento di un pacchetto attiva numerose azioni:

1. Tutti gli ordini relativi a questo pacchetto vengono annullati,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. La campagna di riferimento viene annullata e tutti i processi attivi (flussi di lavoro, consegne) vengono interrotti,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Viene inviata una notifica a tutti gli enti locali interessati.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

Se necessario, i pacchetti annullati possono essere comunque accessibili e reinizializzati dall’entità centrale (vedi sotto). Saranno offerti di nuovo agli enti locali solo dopo che saranno stati approvati e avviati. Il processo di reinizializzazione del pacchetto è illustrato di seguito.

## Reinizializzare un pacchetto {#reinitializing-a-package}

I pacchetti di campagne già pubblicati possono essere reinizializzati, modificati e resi disponibili alle entità locali.

1. Seleziona il pacchetto interessato.
1. Fare clic sul collegamento **[!UICONTROL Reinitialize the package to reuse it]** e quindi su **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Fare clic sul pulsante **[!UICONTROL Save]** per approvare la reinizializzazione del pacchetto.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. Lo stato del pacchetto cambia in **[!UICONTROL Being edited]**. Modificalo, approvalo e pubblicalo nuovamente per ripristinarlo nell’elenco del pacchetto della campagna.

>[!NOTE]
>
>Puoi anche reinizializzare i pacchetti di campagne annullati.
