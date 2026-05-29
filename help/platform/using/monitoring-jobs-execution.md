---
product: campaign
title: Monitoraggio dell’esecuzione dei processi
description: Scopri come monitorare l’esecuzione dei processi di importazione ed esportazione
feature: Monitoring
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
TQID: https://experienceleague.adobe.com/g25R2WVJ2ULkITvhyNbvq87lxMdUNaHDJdm9rZNg-PA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 193
ht-degree: 3%

---

# Monitorare l’esecuzione dei processi {#monitoring-job-execution}



È possibile tenere traccia dell&#39;esecuzione dei processi di importazione ed esportazione direttamente dall&#39;elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* La scheda **[!UICONTROL Journal]** consente di esaminare i messaggi di registro relativi all&#39;esecuzione.
* La scheda **[!UICONTROL Rejects]** contiene i record rifiutati. Consulta [questa sezione](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

Nella scheda **[!UICONTROL General]**, il campo **[!UICONTROL Status]** indica lo stato corrente di un processo.

Ogni stato è rappresentato da un’icona e un’etichetta speciali. Gli stati e le relative icone sono elencati di seguito:

![](assets/s_ncs_user_export_status.png)

* **Modifica in corso**

  Il processo è in fase di creazione.

* **Esecuzione in corso**

  Il processo è in esecuzione.

* **Annulla**

  Fare clic sul pulsante **[!UICONTROL Cancel]**: il processo in corso viene annullato.

* **Annullamento in corso**

  Il comando di annullamento è stato preso in considerazione e il processo è stato annullato.

* **Pausa in corso**

  Fare clic su **[!UICONTROL Pause]**: processo sospeso.

* **In pausa**

  Fare clic su **[!UICONTROL Pause]**: il processo è sospeso. È possibile riavviarlo facendo clic su **[!UICONTROL Start]**.

* **Completato**

  Esecuzione del processo completata.

* **Completato con errore**

  Il processo non è stato eseguito a causa di un errore tecnico.

* **Arresto del server in corso**

  Il processo in corso è stato interrotto perché il server Adobe Campaign è stato arrestato.
