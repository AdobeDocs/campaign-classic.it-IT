---
product: campaign
title: Cambiare dimensione
description: Cambiare dimensione
feature: Workflows, Targeting Activity
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# Cambiare dimensione{#change-dimension}



L’attività di modifica della dimensione consente di modificare la dimensione di targeting durante il ciclo di costruzione del target. Lo spostamento degli assi dipende dal modello di dati e dalla dimensione di input. Questo consente di passare dalla dimensione &quot;contratti&quot; alla dimensione &quot;clienti&quot;, ad esempio.

Puoi anche utilizzare questa attività per definire le colonne aggiuntive della nuova destinazione.

È possibile definire i criteri di deduplicazione dei dati.

## Modalità di configurazione {#configuration-mode}

Per configurare l’attività di modifica della dimensione, effettua le seguenti operazioni:

1. Seleziona la nuova dimensione di targeting tramite **[!UICONTROL Change dimension]** campo.

   ![](assets/s_user_change_dimension_param1.png)

1. Durante la modifica della quota, potete mantenere tutti gli elementi o selezionarli da mantenere nell&#39;output. Nell&#39;esempio seguente, il valore massimo. numero di duplicati impostato su 2.

   ![](assets/s_user_change_dimension_limit.png)

   Quando si sceglie di mantenere un solo record, nello schema di lavoro viene visualizzata una raccolta: questa raccolta rappresenta tutti i record che non verranno inclusi nel risultato finale (poiché viene mantenuto un solo record). Come tutte le altre raccolte, questo consente di calcolare aggregati o recuperare informazioni nelle colonne.

   Ad esempio, se modifichi il **[!UICONTROL Customers]** dimensione al **[!UICONTROL Recipients]** sarà possibile rivolgersi ai clienti di un negozio specifico, aggiungendo il numero di acquisti effettuati.

1. Se scegli di non conservare tutte queste informazioni, puoi configurare la modalità di gestione dei duplicati.

   ![](assets/s_user_change_dimension_param2.png)

   Le frecce blu ti consentono di definire la priorità di elaborazione dei duplicati.

   Nell’esempio precedente, i destinatari verranno deduplicati prima sul loro indirizzo e-mail e, se necessario, poi sul loro numero di account.

1. Il **[!UICONTROL Result]** consente di aggiungere ulteriori informazioni.

   Ad esempio, puoi recuperare la provincia in base al codice postale utilizzando una **Sottostringa** funzione di testo. Per eseguire questa operazione:

   * Fai clic su **[!UICONTROL Add data...]** collega e seleziona **[!UICONTROL Data linked to the filtering dimension]**.

     ![](assets/wf_change-dimension_sample_01.png)

     >[!NOTE]
     >
     >Per informazioni sulla creazione e la gestione di colonne aggiuntive, fare riferimento a [Aggiunta di dati](query.md#adding-data).

   * Selezionare la dimensione di targeting precedente (prima del cambio asse) e selezionare **[!UICONTROL Zip Code]** nel campo del destinatario **[!UICONTROL Location]** sottostruttura, quindi fai clic su **[!UICONTROL Edit expression]**.

     ![](assets/wf_change-dimension_sample_02.png)

   * Clic **[!UICONTROL Advanced selection]** e scegli **[!UICONTROL Edit the formula using an expression]**.

     ![](assets/wf_change-dimension_sample_03.png)

   * Utilizzare le funzioni offerte nell&#39;elenco e specificare il calcolo da eseguire.

     ![](assets/wf_change-dimension_sample_04.png)

   * Infine, immetti l’etichetta della colonna appena creata.

     ![](assets/wf_change-dimension_sample_05.png)

1. Esegui il flusso di lavoro per visualizzare il risultato di questa configurazione. Confronta i dati nelle tabelle prima e dopo l’attività di modifica della dimensione e confronta la struttura delle tabelle del flusso di lavoro, come illustrato negli esempi seguenti:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
