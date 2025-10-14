---
product: campaign
title: Esportare dati da Campaign ad Adobe Experience Platform
description: Scopri come esportare dati da Campaign Classic a Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8d1404c5-030b-47fe-a4c3-e72f15f09bbb
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 3%

---

# Esportare dati da Campaign ad Adobe Experience Platform {#sources}



Per esportare i dati di Campaign Classic in Adobe Real-time Customer Data Platform (RTCDP), devi innanzitutto creare un flusso di lavoro in Campaign Classic per esportare nel percorso di archiviazione BLOB S3 o Azure i dati da condividere.

Dopo aver configurato il flusso di lavoro e aver inviato i dati al percorso di archiviazione, è necessario connettere il percorso di archiviazione BLOB S3 o Azure come **Source** in Adobe Experience Platform.

>[!NOTE]
>
>Si consiglia di esportare solo i dati generati da Campaign (ad esempio invii, aperture, clic ecc.) in Adobe Experience Platform. I dati acquisiti da un’origine di terze parti (come il CRM) devono essere importati direttamente in Adobe Experience Platform.

## Creare un flusso di lavoro di esportazione in Campaign Classic

Per esportare i dati da Campaign Classic nel percorso di archiviazione S3 o BLOB di Azure, devi creare un flusso di lavoro per eseguire il targeting dei dati da esportare e inviarli al percorso di archiviazione.

A questo scopo, aggiungi e configura:

* Attività **[!UICONTROL Data extraction (file)]** per estrarre i dati di destinazione in un file CSV. Per ulteriori informazioni su come configurare questa attività, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html){target="_blank"}.

  ![](assets/rtcdp-extract-file.png)

* Un&#39;attività **[!UICONTROL File transfer]** per trasferire il file CSV nel percorso di archiviazione. Per ulteriori informazioni su come configurare questa attività, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html){target="_blank"}.

  ![](assets/rtcdp-file-transfer.png)

Ad esempio, il flusso di lavoro seguente estrae i registri regolarmente in un file CSV, quindi trasferisce il file in un percorso di archiviazione.

![](assets/aep-export.png)

## Collegare la posizione di archiviazione come Source

Di seguito sono elencati i passaggi principali per connettere il percorso di archiviazione BLOB di S3 o Azure come **Source** in Adobe Experience Platform. Informazioni dettagliate su ciascuno di questi passaggi sono disponibili nella [documentazione dei connettori Source](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=it).

1. Nel menu di Adobe Experience Platform **[!UICONTROL Sources]**, crea una connessione al percorso di archiviazione:

   * [Creare una connessione di origine Amazon S3](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Connettore BLOB di Azure](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >Il percorso di archiviazione può essere Amazon S3, SFTP con password, SFTP con chiave SSH o connessioni BLOB di Azure. Il metodo preferito per inviare dati ad Adobe Campaign è tramite Amazon S3 o Azure Blob:

   ![](assets/rtcdp-connector.png)

1. Configurare un flusso di dati per una connessione batch di archiviazione cloud. Un flusso di dati è un’attività pianificata che recupera e acquisisce i dati dal percorso di archiviazione a un set di dati Adobe Experience Platform. Questi passaggi ti consentono di configurare l’acquisizione dei dati dalla posizione di archiviazione, inclusa la selezione dei dati e la mappatura dei campi CSV su uno schema XDM.

   Informazioni dettagliate sono disponibili in [questa pagina](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. Dopo aver configurato Source, Adobe Experience Platform importa il file dal percorso di archiviazione fornito.

   Questa operazione può essere pianificata in base alle tue esigenze. È consigliabile eseguire l’esportazione fino a 6 volte al giorno, a seconda del carico già presente nell’istanza.
