---
product: campaign
title: Query della tabella dei destinatari
description: Scopri come eseguire una query sulla tabella dei destinatari
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# Query della tabella dei destinatari {#querying-recipient-table}

![](../../assets/common.svg)

In questo esempio, vogliamo recuperare i nomi e le e-mail dei destinatari il cui dominio e-mail è &quot;orange.co.uk&quot; e che non vivono a Londra.

* Quale tabella selezionare?

   Tabella dei destinatari (nms:recipient)

* Campi da selezionare come colonne di output

   Email, Nome, Città e numero di conto

* Quali sono le condizioni di filtro dei destinatari?

   dominio città ed e-mail

* È configurato un ordinamento?

   Sì, in base a **[!UICONTROL Account number]** e **[!UICONTROL Last name]**

Per creare questo esempio, esegui i seguenti passaggi:

1. Fai clic su **[!UICONTROL Tools > Generic query editor...]** e scegli la **Destinatari** (**nms:recipient**). Quindi fai clic su **[!UICONTROL Next]**.
1. Scegli: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** e **[!UICONTROL Account number]**. Questi campi vengono aggiunti a **[!UICONTROL Output columns]**. Quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Ordina le colonne in modo da visualizzarle nell’ordine corretto. Qui vogliamo ordinare i numeri dei conti in ordine decrescente e i nomi in ordine alfabetico. Quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. In **[!UICONTROL Data filtering]** finestra, affina la ricerca: scegli **[!UICONTROL Filtering conditions]** e fai clic su **[!UICONTROL Next]**.
1. La **[!UICONTROL Target element]** consente di immettere le impostazioni del filtro.

   Definisci la seguente condizione di filtro: destinatari con un dominio e-mail uguale a &quot;orange.co.uk&quot;. Per eseguire questa operazione, scegli **Dominio e-mail (@email)** in **[!UICONTROL Expression]** colonna, scegli **uguale a** in **[!UICONTROL Operator]** e inserisci &quot;orange.co.uk&quot; nella colonna **[!UICONTROL Value]** colonna.

   ![](assets/query_editor_05.png)

1. Se necessario, fai clic sul pulsante **[!UICONTROL Distribution of values]** per visualizzare una distribuzione basata sul dominio e-mail dei potenziali clienti. È disponibile una percentuale per ogni dominio e-mail nel database. I domini diversi da &quot;orange.co.uk&quot; vengono visualizzati finché non viene applicato il filtro.

   Nella parte inferiore della finestra viene visualizzato un riepilogo della query: **Dominio e-mail uguale a &quot;orange.co.uk&quot;**.

1. Fai clic sul pulsante **[!UICONTROL Preview]** per ottenere un&#39;idea del risultato della query: vengono visualizzati solo i domini e-mail &quot;orange.co.uk&quot;.

   ![](assets/query_editor_nveau_17.png)

1. Ora cambieremo la query per trovare i contatti che non vivono a Londra.

   Seleziona **[!UICONTROL City (location/@city)]** in **[!UICONTROL Expression]** colonna, **[!UICONTROL different from]** come operatore e immetti **[!UICONTROL London]** in **[!UICONTROL Value]** colonna.

   ![](assets/query_editor_08.png)

1. Questo ti porterà al **[!UICONTROL Data formatting]** finestra. Controlla l’ordine delle colonne. Sposta la colonna &quot;Città&quot; in alto sotto la colonna &quot;Numero conto&quot;.

   Deseleziona la colonna &quot;Nome&quot; per rimuoverlo dall’elenco.

   ![](assets/query_editor_nveau_15.png)

1. In **[!UICONTROL Data preview]** finestra, fai clic su **[!UICONTROL Start the preview of the data]**. Questa funzione calcola il risultato della query.

   La **[!UICONTROL Column results]** la scheda mostra il risultato della query in colonne.

   Il risultato mostra tutti i destinatari con un dominio e-mail &quot;orange.co.uk&quot; che non vivono a Londra. La colonna &quot;Nome&quot; non viene visualizzata perché è stata deselezionata durante lo stadio precedente. I numeri di conto sono ordinati in ordine decrescente.

   ![](assets/query_editor_nveau_12.png)

   La **[!UICONTROL XML result]** La scheda mostra il risultato in formato XML.

   ![](assets/query_editor_nveau_13.png)

   La **[!UICONTROL Generated QSL queries]** la scheda mostra il risultato della query in formato SQL.

   ![](assets/query_editor_nveau_14.png)
