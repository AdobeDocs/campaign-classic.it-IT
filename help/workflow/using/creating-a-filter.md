---
solution: Campaign Classic
product: campaign
title: Creazione di un filtro
description: Scopri come creare un filtro durante le query
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---


# Creazione di un filtro {#creating-a-filter}

I filtri disponibili in  Adobe Campaign sono definiti tramite condizioni di filtraggio create utilizzando la stessa modalità operativa delle query.

>[!NOTE]
>
>For more on creating filters, refer to [this section](../../platform/using/filtering-options.md).

Il **[!UICONTROL Administration > Configuration > Predefined filters]** nodo contiene tutti i filtri utilizzati negli elenchi e nelle panoramiche.

Ad esempio, l&#39;elenco di operatori può essere filtrato per **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Il filtro corrispondente contiene la query sul **[!UICONTROL Account disabled]** valore dello **[!UICONTROL Operators]** schema:

![](assets/query_editor_filter_sample_2.png)

Per lo stesso elenco, il **[!UICONTROL By login or label]** filtro consente di filtrare i dati presenti nell&#39;elenco in base al valore immesso nel campo del filtro:

![](assets/query_editor_filter_sample_3.png)

È costruito come segue:

![](assets/query_editor_filter_sample_4.png)

Per soddisfare le condizioni di filtraggio, l&#39;account dell&#39;operatore deve verificare una delle seguenti condizioni:

* La sua etichetta contiene i caratteri immessi nel campo di immissione,
* Il nome dell&#39;operatore contiene i caratteri immessi nel campo di immissione,
* Il contenuto dell&#39;area di descrizione contiene i caratteri immessi nel campo di input.

>[!NOTE]
>
>La **[!UICONTROL Upper]** funzione consente di disattivare la funzione sensibile alle maiuscole/minuscole.

La **[!UICONTROL Taken into account if]** colonna consente di definire i criteri di applicazione per queste condizioni di filtro. In questo caso, i caratteri **$(/tmp/@text)** rappresentano il contenuto del campo di input collegato al filtro:

![](assets/query_editor_filter_sample_5.png)

Qui, **$(/tmp/@text)=&#39;agenzia&#39;**

Il **$(/tmp/@text)!=&#39;&#39;** espressione applica ogni condizione quando il campo di input non è vuoto.
