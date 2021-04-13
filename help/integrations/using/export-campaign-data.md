---
solution: Campaign Classic
product: campaign
title: Esportare dati da Campaign a Adobe Experience Platform
description: Scopri come esportare dati da Campaign Classic a Adobe Experience Platform.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 1c07c3b10a6d38ca67c20746a51301d71aec0015
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---


# Esportare dati da Campaign a Adobe Experience Platform {#sources}

Per esportare i dati di Campaign Classic in Adobe Real-time Customer Data Platform (RTCDP), devi innanzitutto creare un flusso di lavoro in Campaign Classic per esportare nella posizione di archiviazione BLOB S3 o Azure i dati che desideri condividere.

Una volta configurato il flusso di lavoro e inviati i dati al percorso di archiviazione, è necessario collegare il percorso di archiviazione BLOB S3 o Azure come **Origine** in Adobe experience Platform.

>[!NOTE]
>
>È consigliabile esportare solo i dati generati da Campaign (ad esempio, invii, aperture, clic, ecc.) a Adobe Experience Platform. I dati acquisiti da un’origine di terze parti (come il CRM) devono essere importati direttamente in Adobe Experience Platform.

## Creare un flusso di lavoro di esportazione in Campaign Classic

Per esportare i dati da Campaign Classic nel percorso di archiviazione S3 o Azure Blob, è necessario creare un flusso di lavoro per eseguire il targeting dei dati da esportare e inviarli al percorso di archiviazione.

A questo scopo, aggiungi e configura:

* Un’attività **[!UICONTROL Data extraction (file)]** per estrarre i dati di destinazione in un file CSV. Per ulteriori informazioni su come configurare questa attività, consulta [questa sezione](../../workflow/using/extraction--file-.md).

   ![](assets/rtcdp-extract-file.png)

* Un’attività **[!UICONTROL File transfer]** per trasferire il file CSV nel percorso di archiviazione. Per ulteriori informazioni su come configurare questa attività, consulta [questa sezione](../../workflow/using/file-transfer.md).

   ![](assets/rtcdp-file-transfer.png)

Ad esempio, il flusso di lavoro seguente estrae regolarmente i registri in un file CSV, quindi li trasferisce in una posizione di archiviazione.

![](assets/aep-export.png)

## Collegare la posizione di archiviazione come origine

Di seguito sono elencati i passaggi principali per collegare il percorso di archiviazione BLOB S3 o Azure come **Origine** in Adobe experience Platform. Informazioni dettagliate su ciascuno di questi passaggi sono disponibili nella documentazione [Connettori sorgente](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html).

1. Nel menu Adobe Experience Platform **[!UICONTROL Sources]** , crea una connessione al percorso di archiviazione:

   * [Creare una connessione sorgente Amazon S3](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Connettore BLOB di Azure](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >Il percorso di archiviazione può essere Amazon S3, SFTP con password, SFTP con chiave SSH o connessioni BLOB di Azure. Il metodo preferito per inviare dati ad Adobe Campaign è tramite Amazon S3 o Azure Blob:

   ![](assets/rtcdp-connector.png)

1. Configurare un flusso di dati per una connessione batch di archiviazione cloud. Un flusso di dati è un’attività pianificata che recupera e trasferisce i dati dal percorso di archiviazione a un set di dati Adobe Experience Platform. Questa procedura consente di configurare l’acquisizione dei dati dalla posizione di archiviazione, inclusa la selezione dei dati e la mappatura dei campi CSV su uno schema XDM.

   Informazioni dettagliate sono disponibili in [questa pagina](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. Dopo la configurazione dell’origine, Adobe Experience Platform importa il file dal percorso di archiviazione fornito.

   Questa operazione può essere pianificata in base alle tue esigenze. Consigliamo di eseguire l’esportazione fino a 6 volte al giorno, a seconda del carico già presente nell’istanza.
