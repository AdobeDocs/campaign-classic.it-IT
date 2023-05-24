---
product: campaign
title: Monitoraggio dell’esecuzione dei processi
description: Scopri come monitorare l’esecuzione dei processi di importazione ed esportazione
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 11%

---

# Monitorare l’esecuzione dei processi {#monitoring-job-execution}



È possibile tenere traccia dell&#39;esecuzione dei processi di importazione ed esportazione direttamente dall&#39;elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* Il **[!UICONTROL Journal]** Questa scheda ti consente di esaminare i messaggi di registro relativi all’esecuzione.
* Il **[!UICONTROL Rejects]** contiene i record rifiutati. Vedi [questa sezione](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

In **[!UICONTROL General]** , la scheda **[!UICONTROL Status]** indica lo stato corrente di un processo.

Ogni stato è rappresentato da un’icona e un’etichetta speciali. Gli stati e le relative icone sono elencati di seguito:

![](assets/s_ncs_user_export_status.png)

* **Modifica in corso**

   Il processo è in fase di creazione.

* **Esecuzione in corso**

   Il processo è in esecuzione.

* **Annulla**

   Fai clic su **[!UICONTROL Cancel]** pulsante: processo in corso annullato.

* **Annullamento in corso**

   Il comando di annullamento è stato preso in considerazione e il processo è stato annullato.

* **Pausa in corso**

   Clic **[!UICONTROL Pause]**: processo in fase di sospensione.

* **In pausa**

   Clic **[!UICONTROL Pause]**: processo sospeso. Per riavviarlo, fai clic su **[!UICONTROL Start]**.

* **Finito**

   Esecuzione del processo completata.

* **Completato con errore**

   Il processo non è stato eseguito a causa di un errore tecnico.

* **Arresto del server in corso**

   Il processo in corso è stato interrotto perché il server Adobe Campaign è stato arrestato.
