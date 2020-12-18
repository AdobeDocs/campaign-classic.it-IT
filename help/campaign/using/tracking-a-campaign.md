---
solution: Campaign Classic
product: campaign
title: Tracking di una campagna
description: Tracking di una campagna
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---


# Tracking di una campagna{#tracking-a-campaign}

Gli operatori di entità centrale possono tenere traccia degli ordini delle campagne nell&#39;elenco dei pacchetti delle campagne.

Questo consente di:

* [Filtra pacchetti](#filter-packages),
* [Modificare i pacchetti](#edit-packages),
* [Annullare un pacchetto](#cancel-a-package),
* [Reinizializzazione di un pacchetto](#reinitializing-a-package).

## Pacchetti filtro {#filter-packages}

Da **[!UICONTROL Campaigns universe]** è possibile visualizzare l&#39;elenco di **[!UICONTROL Campaign packages]** che raggruppa tutte le campagne Distributed Marketing esistenti. Potete filtrare questo elenco in modo che visualizzi solo le campagne pubblicate, in ritardo, in attesa di approvazione, ecc. A questo scopo, fate clic sui collegamenti nella sezione superiore della vista oppure utilizzate il collegamento **[!UICONTROL Filter list]** e selezionate lo stato del pacchetto della campagna da visualizzare.

![](assets/mkg_dist_catalog_filter.png)

## Modifica pacchetti {#edit-packages}

La pagina **[!UICONTROL Campaign packages]** consente di visualizzare il riepilogo di ciascun pacchetto.

Questo riepilogo mostra le seguenti informazioni: etichetta, tipo di campagna, nome della campagna da cui è stata creata e la cartella.

Fate clic sul nome del pacchetto per modificarlo. Potete inoltre visualizzare gli ordini in base alle entità locali e al relativo stato.

Queste informazioni sono disponibili anche nella **[!UICONTROL Campaign orders]** vista in cui sono elencati tutti gli ordini.

![](assets/mkg_dist_catalog_op_command_details.png)

L&#39;operatore centrale può modificare l&#39;ordine. Esistono due modi per farlo:

1. L&#39;operatore può fare clic sul nome dell&#39;ordine per modificarlo: vengono visualizzati i dettagli dell&#39;ordine.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   La scheda **[!UICONTROL Edit > General]** consente di visualizzare le informazioni immesse dall&#39;entità locale al momento dell&#39;ordine della campagna.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. L&#39;operatore può fare clic sull&#39;etichetta del pacchetto della campagna per modificarlo e modificare determinate impostazioni.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Annullare un pacchetto {#cancel-a-package}

L&#39;entità centrale può annullare un pacchetto di campagna in qualsiasi momento.

Fate clic su **[!UICONTROL Cancel]** nel pacchetto della campagna **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

Il campo **[!UICONTROL Comment]** consente di giustificare la cancellazione.

Per **campagne locali**, l&#39;annullamento di un pacchetto lo rimuove dall&#39;elenco delle campagne di marketing disponibili.

Per **campagne collaborative**, l&#39;annullamento di un pacchetto attiva numerose azioni:

1. Tutti gli ordini relativi a questo pacchetto vengono annullati,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. La campagna di riferimento viene annullata e tutti i processi attivi (flussi di lavoro, consegne) vengono interrotti,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Una notifica viene inviata a tutti gli enti locali interessati.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

I pacchetti annullati possono essere ancora accessibili e reinizializzati dall&#39;entità centrale (vedere di seguito), se necessario. Essi saranno offerti agli enti locali solo dopo che saranno stati approvati e avviati. Il processo di reinizializzazione del pacchetto è illustrato di seguito.

## Reinizializzazione di un pacchetto {#reinitializing-a-package}

I pacchetti campagna che sono già stati pubblicati possono essere reinizializzati, modificati e resi disponibili alle entità locali.

1. Selezionare il pacchetto interessato.
1. Fare clic sul collegamento **[!UICONTROL Reinitialize the package to reuse it]** e fare clic su **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Fate clic sul pulsante **[!UICONTROL Save]** per approvare la reinizializzazione del pacchetto.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. Lo stato del pacchetto cambia in **[!UICONTROL Being edited]**. Modificatelo, approvatelo e pubblicatelo di nuovo per ripristinarlo nell&#39;elenco del pacchetto della campagna.

>[!NOTE]
>
>Potete anche reinizializzare i pacchetti campagna annullati.

