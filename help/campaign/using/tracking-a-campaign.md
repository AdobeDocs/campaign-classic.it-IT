---
title: Tracking di una campagna
seo-title: Tracking di una campagna
description: Tracking di una campagna
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 2%

---


# Tracking di una campagna{#tracking-a-campaign}

Gli operatori di entità centrale possono tenere traccia degli ordini delle campagne nell&#39;elenco dei pacchetti delle campagne.

Questo consente di:

* [Filtra pacchetti](#filter-packages),
* [Modificare i pacchetti](#edit-packages),
* [Annullare un pacchetto](#cancel-a-package),
* [Reinizializzazione di un pacchetto](#reinitializing-a-package).

## Filtrare i pacchetti {#filter-packages}

Da **[!UICONTROL Campaigns universe]**, potete visualizzare l&#39;elenco dei **[!UICONTROL Campaign packages]** raggruppamenti di tutte le campagne Distributed Marketing esistenti. Potete filtrare questo elenco in modo che visualizzi solo le campagne pubblicate, in ritardo, in attesa di approvazione, ecc. A questo scopo, fate clic sui collegamenti nella sezione superiore della vista oppure utilizzate il **[!UICONTROL Filter list]** collegamento e selezionate lo stato del pacchetto della campagna da visualizzare.

![](assets/mkg_dist_catalog_filter.png)

## Modificare i pacchetti {#edit-packages}

La **[!UICONTROL Campaign packages]** pagina consente di visualizzare il riepilogo di ciascun pacchetto.

Questo riepilogo mostra le seguenti informazioni: etichetta, tipo di campagna, nome della campagna da cui è stata creata e la cartella.

Fate clic sul nome del pacchetto per modificarlo. Potete inoltre visualizzare gli ordini in base alle entità locali e al relativo stato.

Queste informazioni sono disponibili anche nella **[!UICONTROL Campaign orders]** visualizzazione in cui sono elencati tutti gli ordini.

![](assets/mkg_dist_catalog_op_command_details.png)

L&#39;operatore centrale può modificare l&#39;ordine. Esistono due modi per farlo:

1. L&#39;operatore può fare clic sul nome dell&#39;ordine per modificarlo: vengono visualizzati i dettagli dell&#39;ordine.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   La **[!UICONTROL Edit > General]** scheda consente di visualizzare le informazioni immesse dall&#39;entità locale al momento dell&#39;ordine della campagna.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. L&#39;operatore può fare clic sull&#39;etichetta del pacchetto della campagna per modificarlo e modificare determinate impostazioni.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Annullamento di un pacchetto {#cancel-a-package}

L&#39;entità centrale può annullare un pacchetto di campagna in qualsiasi momento.

Fate clic **[!UICONTROL Cancel]** nel pacchetto della campagna **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

Il **[!UICONTROL Comment]** campo consente di giustificare l’annullamento.

Per le campagne **** locali, l&#39;annullamento di un pacchetto lo rimuove dall&#39;elenco delle campagne di marketing disponibili.

Per le campagne **** collaborative, l&#39;annullamento di un pacchetto attiva numerose azioni:

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
1. Fate clic sul **[!UICONTROL Reinitialize the package to reuse it]** collegamento e fate clic su **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Fate clic sul **[!UICONTROL Save]** pulsante per approvare la reinizializzazione del pacchetto.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. Lo stato del pacchetto cambia in **[!UICONTROL Being edited]**. Modificatelo, approvatelo e pubblicatelo di nuovo per ripristinarlo nell&#39;elenco del pacchetto della campagna.

>[!NOTE]
>
>Potete anche reinizializzare i pacchetti campagna annullati.

