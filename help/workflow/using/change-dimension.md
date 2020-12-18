---
solution: Campaign Classic
product: campaign
title: Cambiare dimensione
description: Cambiare dimensione
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# Cambiare dimensione{#change-dimension}

L&#39;attività di modifica della dimensione consente di modificare la dimensione di targeting durante il ciclo di costruzione di destinazione. Lo spostamento dell&#39;asse dipende dal modello di dati e dalla dimensione di input. Questo consente di passare dalla dimensione &quot;contratti&quot; alla dimensione &quot;clienti&quot;, ad esempio.

Potete inoltre utilizzare questa attività per definire le colonne aggiuntive della nuova destinazione.

È possibile definire criteri di deduplicazione dei dati.

## Modalità di configurazione {#configuration-mode}

Per configurare l’attività di modifica della dimensione, effettua i seguenti passaggi:

1. Selezionate la nuova dimensione di targeting tramite il campo **[!UICONTROL Change dimension]**.

   ![](assets/s_user_change_dimension_param1.png)

1. Durante la modifica della dimensione, potete mantenere tutti gli elementi o selezionarli per mantenerli in uscita. Nell&#39;esempio seguente, il valore massimo è numero di duplicati impostato su 2.

   ![](assets/s_user_change_dimension_limit.png)

   Quando si sceglie di mantenere un solo record, una raccolta viene visualizzata nello schema di lavoro: Questa raccolta rappresenta tutti i record che non verranno inseriti nel targeting nel risultato finale (poiché viene mantenuto un solo record). Come tutte le altre raccolte, questa consente di calcolare gli aggregati o recuperare le informazioni nelle colonne.

   Ad esempio, se modificate la dimensione **[!UICONTROL Customers]** nella dimensione **[!UICONTROL Recipients]**, sarà possibile eseguire il targeting dei clienti di uno specifico store, aggiungendo al contempo il numero di acquisti effettuati.

1. Se scegliete di non conservare tutte queste informazioni, potete configurare la modalità di gestione duplicata.

   ![](assets/s_user_change_dimension_param2.png)

   Le frecce blu consentono di definire la priorità di elaborazione duplicata.

   Nell&#39;esempio precedente, i destinatari verranno deduplicati prima sul proprio indirizzo e-mail, quindi sul loro numero di account, se necessario.

1. La scheda **[!UICONTROL Result]** consente di aggiungere ulteriori informazioni.

   Ad esempio, è possibile recuperare la contea in base al codice postale utilizzando una funzione di tipo **Sottostringa**. Per eseguire questa operazione:

   * Fare clic sul collegamento **[!UICONTROL Add data...]** e selezionare **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Per informazioni sulla creazione e la gestione di colonne aggiuntive, fare riferimento a [Aggiunta di dati](../../workflow/using/query.md#adding-data).

   * Selezionate la dimensione di targeting precedente (prima dello switch dell&#39;asse) e selezionate la **[!UICONTROL Zip Code]** nella sottostruttura **[!UICONTROL Location]** del destinatario, quindi fate clic su **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Fare clic su **[!UICONTROL Advanced selection]** e scegliere **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Utilizzare le funzioni offerte nell&#39;elenco e specificare il calcolo da eseguire.

      ![](assets/wf_change-dimension_sample_04.png)

   * Infine, immettete l’etichetta della colonna appena creata.

      ![](assets/wf_change-dimension_sample_05.png)

1. Esegui il flusso di lavoro per visualizzare il risultato di questa configurazione. Confrontare i dati nelle tabelle prima e dopo l&#39;attività della dimensione di modifica e confrontare la struttura delle tabelle del flusso di lavoro, come illustrato negli esempi seguenti:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

