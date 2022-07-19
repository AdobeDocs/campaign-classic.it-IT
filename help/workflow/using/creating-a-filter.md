---
product: campaign
title: Creare un filtro
description: Scopri come creare un filtro durante l’esecuzione delle query
feature: Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# Creare un filtro {#creating-a-filter}

![](../../assets/v7-only.svg)

I filtri disponibili in Adobe Campaign sono definiti tramite condizioni di filtro create utilizzando la stessa modalità operativa delle query.

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione dei filtri, consulta [questa sezione](../../platform/using/filtering-options.md).

La **[!UICONTROL Administration > Configuration > Predefined filters]** contiene tutti i filtri utilizzati negli elenchi e nelle panoramiche.

Ad esempio, l’elenco degli operatori può essere filtrato tramite **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Il filtro corrispondente contiene la query sul **[!UICONTROL Account disabled]** del valore **[!UICONTROL Operators]** schema:

![](assets/query_editor_filter_sample_2.png)

Per lo stesso elenco, il **[!UICONTROL By login or label]** filter ti consente di filtrare i dati dell’elenco in base al valore inserito nel campo filter:

![](assets/query_editor_filter_sample_3.png)

Viene costruito come segue:

![](assets/query_editor_filter_sample_4.png)

Per soddisfare le condizioni di filtro, l’account dell’operatore deve controllare una delle seguenti condizioni:

* La sua etichetta contiene i caratteri immessi nel campo di immissione,
* Il nome dell’operatore contiene i caratteri immessi nel campo di immissione,
* Il contenuto dell’area di descrizione contiene i caratteri immessi nel campo di input.

>[!NOTE]
>
>La **[!UICONTROL Upper]** consente di disattivare la funzione sensibile a maiuscole e minuscole.

La **[!UICONTROL Taken into account if]** La colonna ti consente di definire i criteri dell’applicazione per queste condizioni di filtro. Qui, il **$(/tmp/@text)** i caratteri rappresentano il contenuto del campo di input collegato al filtro:

![](assets/query_editor_filter_sample_5.png)

Qui, **$(/tmp/@text)=&#39;agenzia&#39;**

La **$(/tmp/@text)!=&#39;&#39;** espressione applica ogni condizione quando il campo di input non è vuoto.
