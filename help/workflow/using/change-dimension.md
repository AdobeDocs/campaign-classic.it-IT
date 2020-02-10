---
title: Cambia dimensione
seo-title: Cambia dimensione
description: Cambia dimensione
seo-description: null
page-status-flag: never-activated
uuid: 6cb309c0-4096-47ce-b1d4-37a3ddafaaa1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 61583062-2349-4ab3-a3bf-310d21894f34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Cambia dimensione{#change-dimension}

L&#39;attività di modifica della dimensione consente di modificare la dimensione di targeting durante il ciclo di costruzione di destinazione. Lo spostamento dell&#39;asse dipende dal modello dati e dalla dimensione di input. Questo consente di passare dalla dimensione &quot;contratti&quot; alla dimensione &quot;clienti&quot;, ad esempio.

Potete inoltre utilizzare questa attività per definire le colonne aggiuntive della nuova destinazione.

È possibile definire criteri di deduplicazione dei dati.

## Modalità di configurazione {#configuration-mode}

Per configurare l’attività di modifica della dimensione, effettua i seguenti passaggi:

1. Selezionate la nuova dimensione di targeting tramite il **[!UICONTROL Change dimension]** campo.

   ![](assets/s_user_change_dimension_param1.png)

1. Durante la modifica della dimensione, potete mantenere tutti gli elementi o selezionarli per mantenerli in uscita. Nell&#39;esempio seguente, il valore massimo è numero di duplicati impostato su 2.

   ![](assets/s_user_change_dimension_limit.png)

   Quando scegliete di mantenere un solo record, una raccolta viene visualizzata nello schema di lavoro: Questa raccolta rappresenta tutti i record che non verranno inseriti nel targeting nel risultato finale (poiché viene mantenuto un solo record). Come tutte le altre raccolte, questa consente di calcolare gli aggregati o recuperare le informazioni nelle colonne.

   Ad esempio, se modificate la **[!UICONTROL Customers]** **[!UICONTROL Recipients]** dimensione, sarà possibile eseguire il targeting dei clienti di uno specifico store, aggiungendo al contempo il numero di acquisti effettuati.

1. Se scegliete di non conservare tutte queste informazioni, potete configurare la modalità di gestione duplicata.

   ![](assets/s_user_change_dimension_param2.png)

   Le frecce blu consentono di definire la priorità di elaborazione duplicata.

   Nell&#39;esempio precedente, i destinatari verranno deduplicati prima sul proprio indirizzo e-mail, quindi sul loro numero di account, se necessario.

1. La **[!UICONTROL Result]** scheda consente di aggiungere ulteriori informazioni.

   Ad esempio, è possibile recuperare la contea in base al codice postale utilizzando una funzione di tipo **Sottostringa** . Per eseguire questa operazione:

   * Fate clic sul **[!UICONTROL Add data...]** collegamento e selezionate **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Per informazioni sulla creazione e la gestione di ulteriori colonne, vedere [Aggiunta di dati](../../workflow/using/query.md#adding-data).

   * Seleziona la dimensione di targeting precedente (prima dello switch dell&#39;asse), seleziona la dimensione **[!UICONTROL Zip Code]** nella sottostruttura del destinatario, quindi fai clic su **[!UICONTROL Location]** **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Fate clic **[!UICONTROL Advanced selection]** e scegliete **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Utilizzare le funzioni offerte nell&#39;elenco e specificare il calcolo da eseguire.

      ![](assets/wf_change-dimension_sample_04.png)

   * Infine, immettete l’etichetta della colonna appena creata.

      ![](assets/wf_change-dimension_sample_05.png)

1. Esegui il flusso di lavoro per visualizzare il risultato di questa configurazione. Confrontare i dati nelle tabelle prima e dopo l&#39;attività della dimensione di modifica e confrontare la struttura delle tabelle del flusso di lavoro, come illustrato negli esempi seguenti:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

