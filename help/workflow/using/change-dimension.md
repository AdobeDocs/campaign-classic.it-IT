---
product: campaign
title: Cambiare dimensione
description: Cambiare dimensione
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# Cambiare dimensione{#change-dimension}

![](../../assets/common.svg)

L’attività modifica dimensione ti consente di modificare la dimensione di targeting durante il ciclo di costruzione di destinazione. Lo spostamento dell’asse dipende dal modello di dati e dalla dimensione di input. Questo consente ad esempio di passare dalla dimensione &quot;contratti&quot; alla dimensione &quot;clienti&quot;.

Puoi inoltre utilizzare questa attività per definire le colonne aggiuntive della nuova destinazione.

È possibile definire criteri di deduplicazione dei dati.

## Modalità di configurazione {#configuration-mode}

Per configurare l’attività di modifica della dimensione, esegui i seguenti passaggi:

1. Seleziona la nuova dimensione di targeting tramite il campo **[!UICONTROL Change dimension]** .

   ![](assets/s_user_change_dimension_param1.png)

1. Durante la modifica della dimensione, puoi mantenere tutti gli elementi o selezionare quelli da mantenere nell’output. Nell’esempio seguente, il valore massimo è il numero di duplicati è impostato su 2.

   ![](assets/s_user_change_dimension_limit.png)

   Quando si sceglie di conservare un solo record, nello schema di lavoro viene visualizzata una raccolta: Questa raccolta rappresenta tutti i record che non verranno inclusi nel risultato finale (poiché viene conservato un solo record). Come tutte le altre raccolte, questa ti permette di calcolare gli aggregati o recuperare le informazioni in colonne.

   Ad esempio, se modifichi la dimensione **[!UICONTROL Customers]** alla dimensione **[!UICONTROL Recipients]** , sarà possibile eseguire il targeting dei clienti di un archivio specifico, aggiungendo al contempo il numero di acquisti effettuati.

1. Se scegli di non conservare tutte queste informazioni, puoi configurare la modalità di gestione duplicata.

   ![](assets/s_user_change_dimension_param2.png)

   Le frecce blu consentono di definire la priorità di elaborazione duplicata.

   Nell’esempio precedente, i destinatari verranno deduplicati prima sul loro indirizzo e-mail, quindi sul loro numero di account, se necessario.

1. La scheda **[!UICONTROL Result]** ti consente di aggiungere ulteriori informazioni.

   Ad esempio, è possibile recuperare la contea in base al codice postale utilizzando una funzione di tipo **Substring**. Per eseguire questa operazione:

   * Fai clic sul collegamento **[!UICONTROL Add data...]** e seleziona **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Per informazioni sulla creazione e la gestione di colonne aggiuntive, consulta [Aggiunta di dati](query.md#adding-data).

   * Seleziona la dimensione di targeting precedente (prima dell’interruttore dell’asse) e seleziona il sottoalbero **[!UICONTROL Zip Code]** del destinatario, quindi fai clic su **[!UICONTROL Edit expression]**.**[!UICONTROL Location]**

      ![](assets/wf_change-dimension_sample_02.png)

   * Fai clic su **[!UICONTROL Advanced selection]** e scegli **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Utilizzare le funzioni offerte nell&#39;elenco e specificare il calcolo da eseguire.

      ![](assets/wf_change-dimension_sample_04.png)

   * Infine, immetti l’etichetta della colonna appena creata.

      ![](assets/wf_change-dimension_sample_05.png)

1. Esegui il flusso di lavoro per visualizzare il risultato di questa configurazione. Confronta i dati nelle tabelle prima e dopo l’attività di modifica della dimensione e confronta la struttura delle tabelle del flusso di lavoro, come illustrato negli esempi seguenti:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
