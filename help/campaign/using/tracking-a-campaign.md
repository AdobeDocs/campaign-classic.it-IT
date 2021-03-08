---
solution: Campaign Classic
product: campaign
title: Tracking di una campagna
description: Tracking di una campagna
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 2%

---


# Tracking di una campagna{#tracking-a-campaign}

Gli operatori di entità centrale possono tenere traccia degli ordini delle campagne nell’elenco dei pacchetti delle campagne.

Questo consente di:

* [Colli](#filter-packages) filtranti,
* [Modifica pacchetti](#edit-packages),
* [Annulla un pacchetto](#cancel-a-package),
* [Reinizializzazione di un pacchetto](#reinitializing-a-package).

## Pacchetti filtro {#filter-packages}

Dalla scheda **[!UICONTROL Campaigns]** è possibile visualizzare l’elenco di **[!UICONTROL Campaign packages]** che raggruppa tutte le campagne Distributed Marketing esistenti. Puoi filtrare questo elenco in modo che visualizzi solo le campagne pubblicate, in ritardo, in attesa di approvazione, ecc. A questo scopo, fai clic sui collegamenti nella sezione superiore di questa visualizzazione oppure utilizza il collegamento **[!UICONTROL Filter list]** e seleziona lo stato del pacchetto della campagna da visualizzare.

![](assets/mkg_dist_catalog_filter.png)

## Modifica pacchetti {#edit-packages}

La pagina **[!UICONTROL Campaign packages]** ti consente di visualizzare il riepilogo di ciascun pacchetto.

Questo riepilogo mostra le seguenti informazioni: etichetta, tipo di campagna, nome della campagna da cui è stata creata e la cartella.

Fai clic sul nome del pacchetto per modificarlo. È inoltre possibile visualizzare gli ordini in base alle rispettive entità locali e al loro stato.

Queste informazioni sono disponibili anche nella visualizzazione **[!UICONTROL Campaign orders]** in cui sono elencati tutti gli ordini.

![](assets/mkg_dist_catalog_op_command_details.png)

L’operatore centrale può modificare l’ordine. Ci sono due modi per farlo:

1. L’operatore può fare clic sul nome dell’ordine per modificarlo: vengono visualizzati i dettagli dell’ordine.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   La scheda **[!UICONTROL Edit > General]** ti consente di visualizzare le informazioni immesse dall’entità locale al momento dell’ordine della campagna.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. L’operatore può fare clic sull’etichetta del pacchetto della campagna per modificarlo e modificare alcune impostazioni.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Annulla un pacchetto {#cancel-a-package}

L’entità centrale può annullare un pacchetto della campagna in qualsiasi momento.

Fai clic su **[!UICONTROL Cancel]** nel pacchetto della campagna **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

Il campo **[!UICONTROL Comment]** consente di giustificare l’annullamento.

Per **campagne locali**, l&#39;annullamento di un pacchetto lo rimuove dall&#39;elenco delle campagne di marketing disponibili.

Per **campagne collaborative**, l&#39;annullamento di un pacchetto attiva numerose azioni:

1. Tutti gli ordini relativi a questo pacchetto vengono annullati,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. La campagna di riferimento viene annullata e tutti i processi attivi (flussi di lavoro, consegne) vengono interrotti,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Viene inviata una notifica a tutti gli enti locali interessati.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

I pacchetti annullati possono ancora essere accessibili e reinizializzati dall&#39;entità centrale (vedi sotto), se necessario. Essi saranno offerti agli enti locali solo una volta approvati e avviati. Il processo di reinizializzazione del pacchetto è mostrato di seguito.

## Reinizializzazione di un pacchetto {#reinitializing-a-package}

I pacchetti di campagna già pubblicati possono essere reinizializzati, modificati e resi disponibili alle entità locali.

1. Selezionare il pacchetto in questione.
1. Fai clic sul collegamento **[!UICONTROL Reinitialize the package to reuse it]** e fai clic su **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Fai clic sul pulsante **[!UICONTROL Save]** per approvare la reinizializzazione del pacchetto.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. Lo stato del pacchetto cambia in **[!UICONTROL Being edited]**. Modifica, approva e pubblica di nuovo per ripristinarlo nell’elenco del pacchetto della campagna.

>[!NOTE]
>
>È inoltre possibile reinizializzare i pacchetti campagna annullati.

