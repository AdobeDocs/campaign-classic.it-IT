---
solution: Campaign Classic
product: campaign
title: Monitoraggio dell’esecuzione dei processi
description: Scopri come monitorare l’esecuzione di processi di importazione ed esportazione.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 3%

---


# Monitorare l&#39;esecuzione di processi {#monitoring-job-execution}

Puoi tenere traccia dell’esecuzione dei processi di importazione ed esportazione direttamente dall’elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* La scheda **[!UICONTROL Journal]** ti consente di esaminare i messaggi di log relativi all’esecuzione.
* La scheda **[!UICONTROL Rejects]** contiene i record rifiutati. Vedi [questa sezione](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

Nella scheda **[!UICONTROL General]** , il campo **[!UICONTROL Status]** indica lo stato corrente di un processo.

Ogni stato è rappresentato da un’icona e un’etichetta speciali. Gli stati e le relative icone sono elencati di seguito:

![](assets/s_ncs_user_export_status.png)

* **Modifica in corso**

   Creazione del processo in corso.

* **Esecuzione in corso**

   Esecuzione del processo in corso.

* **Annulla**

   Fai clic sul pulsante **[!UICONTROL Cancel]** : il processo in corso viene annullato.

* **Annullamento in corso**

   Il comando di annullamento è stato preso in considerazione e il processo viene annullato.

* **Pausa in corso**

   Fai clic su **[!UICONTROL Pause]**: il lavoro viene sospeso.

* **In pausa**

   Fai clic su **[!UICONTROL Pause]**: il lavoro è sospeso. È possibile riavviarlo facendo clic su **[!UICONTROL Start]**.

* **Completato**

   Esecuzione del processo completata.

* **Completato con errore**

   Il processo non è stato eseguito a causa di un errore tecnico.

* **Arresto del server in corso**

   Il processo in corso viene interrotto perché il server Adobe Campaign è stato arrestato.
