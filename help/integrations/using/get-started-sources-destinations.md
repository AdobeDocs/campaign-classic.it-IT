---
product: campaign
title: Guida introduttiva a origini e destinazioni
description: Ulteriori informazioni su Origini e Destinazioni Adobe Experience Platform.
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 89a18ae9ec57376d6ebec6c416c7562f960eb882
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 15%

---

# Utilizzare origini e destinazioni {#rtcdp}

![](../../assets/v7-only.svg)

## Informazioni su origini e destinazioni

Con Adobe Experience Platform è possibile condividere dati tra Campaign Classic e Adobe Real-time Customer Data Platform (RTCDP). Questo ti consente di eseguire il targeting dei tipi di pubblico di Adobe Experience Platform nei flussi di lavoro di Campaign, quindi di inviarli nuovamente ai dati di Adobe Real-time Customer Data Platform relativi a questi tipi di pubblico come invii, aperture e clic.

* Con **Destinazioni**, assimila i tipi di pubblico da Adobe Experience Platform a Campaign Classic. Questo consente di attivare i dati noti e sconosciuti per le campagne di marketing.
* Con **Origini**, esporta i dati di Campaign Classic (ad esempio, invia, apre, fai clic) in Adobe Experience Platform. Questo ti consente di centralizzare i dati raccolti da fonti diverse in un unico luogo e di utilizzare le informazioni raccolte per fare di più.

>[!IMPORTANT]
>
>Tieni presente i limiti di archiviazione SFTP, i limiti di archiviazione del database e i limiti dei profili attivi in base al contratto Adobe Campaign durante l’esecuzione di questa integrazione.

Per una panoramica più dettagliata di Adobe Real-time Customer Data Platform, Destinazioni e Origini, consulta queste pagine:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=it)
* [Documentazione sulle origini](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=it)

## Connetti Campaign Classic con Adobe Experience Platform

Per poter condividere dati tra Adobe Experience Platform e Campaign Classic, è innanzitutto necessario collegare Adobe Campaign as a **Destinazione** e collega il percorso di archiviazione BLOB di AWS S3 o Azure come **Origine** in Adobe experience Platform.

Una volta configurati i connettori, puoi impostare un’importazione o un’esportazione di dati in Campaign Classic tramite flussi di lavoro.

![](assets/rtcdp-schema.png)

Per ulteriori informazioni su come impostare questi processi di importazione ed esportazione, consulta le sezioni seguenti:

* [Inserire segmenti Adobe Experience Platform in Campaign](../../integrations/using/ingest-aep-data.md)
* [Esportare dati da Campaign ad Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
