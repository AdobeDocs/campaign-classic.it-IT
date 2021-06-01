---
product: campaign
title: Creazione di un filtro
description: Scopri come creare un filtro durante l’esecuzione delle query
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# Creazione di un filtro {#creating-a-filter}

I filtri disponibili in Adobe Campaign sono definiti tramite condizioni di filtro create utilizzando la stessa modalità operativa delle query.

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione dei filtri, consulta [questa sezione](../../platform/using/filtering-options.md).

Il nodo **[!UICONTROL Administration > Configuration > Predefined filters]** contiene tutti i filtri utilizzati negli elenchi e nelle panoramiche.

Ad esempio, l’elenco degli operatori può essere filtrato da **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Il filtro corrispondente contiene la query sul valore **[!UICONTROL Account disabled]** dello schema **[!UICONTROL Operators]**:

![](assets/query_editor_filter_sample_2.png)

Per lo stesso elenco, il filtro **[!UICONTROL By login or label]** ti consente di filtrare i dati dell’elenco in base al valore inserito nel campo del filtro:

![](assets/query_editor_filter_sample_3.png)

Viene costruito come segue:

![](assets/query_editor_filter_sample_4.png)

Per soddisfare le condizioni di filtro, l’account dell’operatore deve controllare una delle seguenti condizioni:

* La sua etichetta contiene i caratteri immessi nel campo di immissione,
* Il nome dell’operatore contiene i caratteri immessi nel campo di immissione,
* Il contenuto dell’area di descrizione contiene i caratteri immessi nel campo di input.

>[!NOTE]
>
>La funzione **[!UICONTROL Upper]** consente di disattivare la funzione sensibile a maiuscole e minuscole.

La colonna **[!UICONTROL Taken into account if]** ti consente di definire i criteri dell’applicazione per queste condizioni di filtro. In questo caso, i caratteri **$(/tmp/@text)** rappresentano il contenuto del campo di input collegato al filtro:

![](assets/query_editor_filter_sample_5.png)

Qui, **$(/tmp/@text)=&#39;agenzia&#39;**

Il **$(/tmp/@text)!=&#39;&#39;** applica ogni condizione quando il campo di input non è vuoto.
