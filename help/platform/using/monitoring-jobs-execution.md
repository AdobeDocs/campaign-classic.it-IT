---
product: campaign
title: Monitoraggio dell’esecuzione dei processi
description: Scopri come monitorare l’esecuzione di processi di importazione ed esportazione.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 4%

---

# Monitorare l’esecuzione dei processi {#monitoring-job-execution}

![](../../assets/common.svg)

Puoi tenere traccia dell’esecuzione dei processi di importazione ed esportazione direttamente dall’elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* La **[!UICONTROL Journal]** La scheda ti consente di esaminare i messaggi di log relativi all’esecuzione.
* La **[!UICONTROL Rejects]** contiene i record rifiutati. Vedi [questa sezione](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

In **[!UICONTROL General]** scheda **[!UICONTROL Status]** campo indica lo stato corrente di un processo.

Ogni stato è rappresentato da un’icona e un’etichetta speciali. Gli stati e le relative icone sono elencati di seguito:

![](assets/s_ncs_user_export_status.png)

* **Modifica in corso**

   Creazione del processo in corso.

* **Esecuzione in corso**

   Esecuzione del processo in corso.

* **Annulla**

   Fai clic sul pulsante **[!UICONTROL Cancel]** pulsante: il processo in corso viene annullato.

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
