---
product: campaign
title: Monitoraggio dell’esecuzione dei processi
description: Scopri come monitorare l’esecuzione dei processi di importazione ed esportazione
feature: Monitoring
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 3%

---

# Monitorare l’esecuzione dei processi {#monitoring-job-execution}



È possibile tenere traccia dell&#39;esecuzione dei processi di importazione ed esportazione direttamente dall&#39;elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* Il **[!UICONTROL Journal]** Questa scheda ti consente di esaminare i messaggi di registro relativi all’esecuzione.
* Il **[!UICONTROL Rejects]** contiene i record rifiutati. Consulta [questa sezione](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

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

* **Completato**

  Esecuzione del processo completata.

* **Completato con errore**

  Il processo non è stato eseguito a causa di un errore tecnico.

* **Arresto del server in corso**

  Il processo in corso è stato interrotto perché il server Adobe Campaign è stato arrestato.
