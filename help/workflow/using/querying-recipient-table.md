---
product: campaign
title: Eseguire una query sulla tabella dei destinatari
description: Scopri come eseguire query sulla tabella dei destinatari
feature: Query Editor, Workflows
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# Eseguire una query sulla tabella dei destinatari {#querying-recipient-table}



In questo esempio, vogliamo recuperare i nomi e le e-mail dei destinatari il cui dominio e-mail è &quot;orange.co.uk&quot; e che non vivono a Londra.

* Quale tabella selezionare?

  Tabella dei destinatari (nms:recipient)

* Campi da selezionare come colonne di output

  E-mail, nome, città e numero account

* Quali sono le condizioni di filtro dei destinatari?

  città e dominio e-mail

* È configurato un ordinamento?

  Sì, in base a **[!UICONTROL Account number]** e **[!UICONTROL Last name]**

Per creare questo esempio, attieniti alla seguente procedura:

1. Clic **[!UICONTROL Tools > Generic query editor...]** e scegli la **Destinatari** (**nms:destinatario**). Quindi fai clic su **[!UICONTROL Next]**.
1. Scegli: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** e **[!UICONTROL Account number]**. Questi campi vengono aggiunti a **[!UICONTROL Output columns]**. Quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Ordinare le colonne per visualizzarle nell&#39;ordine corretto. In questo caso si desidera ordinare i numeri di conto in ordine decrescente e i nomi in ordine alfabetico. Quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. In **[!UICONTROL Data filtering]** finestra, perfeziona la ricerca: scegli **[!UICONTROL Filtering conditions]** e fai clic su **[!UICONTROL Next]**.
1. Il **[!UICONTROL Target element]** consente di immettere le impostazioni del filtro.

   Definisci la seguente condizione di filtro: destinatari con un dominio e-mail uguale a &quot;orange.co.uk&quot;. A questo scopo, scegli **Dominio e-mail (@email)** nel **[!UICONTROL Expression]** , scegli **uguale a** nel **[!UICONTROL Operator]** e immetti &quot;orange.co.uk&quot; nella **[!UICONTROL Value]** colonna.

   ![](assets/query_editor_05.png)

1. Se necessario, fai clic su **[!UICONTROL Distribution of values]** per visualizzare una distribuzione basata sul dominio e-mail dei potenziali clienti. È disponibile una percentuale per ogni dominio e-mail nel database. I domini diversi da &quot;orange.co.uk&quot; vengono visualizzati finché non viene applicato il filtro.

   Nella parte inferiore della finestra viene visualizzato un riepilogo della query: **Dominio e-mail uguale a &quot;orange.co.uk&quot;**.

1. Fai clic su **[!UICONTROL Preview]** per avere un’idea del risultato della query: vengono visualizzati solo i domini e-mail orange.co.uk.

   ![](assets/query_editor_nveau_17.png)

1. Ora modificheremo la query per trovare i contatti che non vivono a Londra.

   Seleziona **[!UICONTROL City (location/@city)]** nel **[!UICONTROL Expression]** colonna, **[!UICONTROL different from]** come operatore e immetti **[!UICONTROL London]** nel **[!UICONTROL Value]** colonna.

   ![](assets/query_editor_08.png)

1. Verrà visualizzato il **[!UICONTROL Data formatting]** finestra. Controlla l’ordine delle colonne. Sposta la colonna &quot;Città&quot; verso l’alto sotto la colonna &quot;Numero account&quot;.

   Deselezionare la colonna &quot;Nome&quot; per rimuoverla dall&#39;elenco.

   ![](assets/query_editor_nveau_15.png)

1. In **[!UICONTROL Data preview]** finestra, fai clic su **[!UICONTROL Start the preview of the data]**. Questa funzione calcola il risultato della query.

   Il **[!UICONTROL Column results]** mostra il risultato della query in colonne.

   Il risultato mostra tutti i destinatari con un dominio e-mail &quot;orange.co.uk&quot; che non vivono a Londra. La colonna &quot;Nome&quot; non viene visualizzata perché è stata deselezionata durante la fase precedente. I numeri di conto sono ordinati in ordine decrescente.

   ![](assets/query_editor_nveau_12.png)

   Il **[!UICONTROL XML result]** mostra il risultato in formato XML.

   ![](assets/query_editor_nveau_13.png)

   Il **[!UICONTROL Generated QSL queries]** La scheda mostra il risultato della query in formato SQL.

   ![](assets/query_editor_nveau_14.png)
