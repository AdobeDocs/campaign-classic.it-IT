---
solution: Campaign Classic
product: campaign
title: Monitoraggio dell’esecuzione dei processi
description: Scoprite come monitorare l’esecuzione dei processi di importazione ed esportazione.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Esecuzione dei processi di monitoraggio {#monitoring-job-execution}

Potete tenere traccia dell’esecuzione dei processi di importazione ed esportazione direttamente dall’elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* La scheda **[!UICONTROL Journal]** consente di esaminare i messaggi di registro relativi all&#39;esecuzione.
* La scheda **[!UICONTROL Rejects]** contiene i record rifiutati. Vedere [Comportamento in caso di errore](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

Nella scheda **[!UICONTROL General]**, il campo **[!UICONTROL Status]** indica lo stato corrente di un processo.

Ogni stato è rappresentato da un’icona e un’etichetta speciali. Gli stati e le relative icone sono elencati di seguito:

![](assets/s_ncs_user_export_status.png)

* **Modifica in corso**

   Creazione del processo in corso.

* **Esecuzione in corso**

   Il processo è in esecuzione.

* **Annulla**

   Fare clic sul pulsante **[!UICONTROL Cancel]**: il processo in corso viene annullato.

* **Annullamento in corso**

   Il comando di annullamento è stato preso in considerazione e il processo viene annullato.

* **Pausa in corso**

   Fare clic su **[!UICONTROL Pause]**: il lavoro è sospeso.

* **In pausa**

   Fare clic su **[!UICONTROL Pause]**: il lavoro è sospeso. È possibile riavviarlo facendo clic su **[!UICONTROL Start]**.

* **Completato**

   Esecuzione del processo completata.

* **Completato con errore**

   Il processo non è stato eseguito a causa di un errore tecnico.

* **Arresto del server in corso**

   Il processo in corso viene interrotto perché il server Adobe Campaign  è stato arrestato.
