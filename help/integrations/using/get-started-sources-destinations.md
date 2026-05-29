---
product: campaign
title: Guida introduttiva a origini e destinazioni
description: Ulteriori informazioni su origini e destinazioni di Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
TQID: https://experienceleague.adobe.com/xPpBR6NrQ315FIw1beLnw4c0gyLzEoYWzIXDljDg9H4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 15%

---

# Utilizzare origini e destinazioni {#rtcdp}



## Informazioni su origini e destinazioni

Con Adobe Experience Platform puoi condividere i dati tra Campaign Classic e Adobe Real-time Customer Data Platform (RTCDP). Questo consente di indirizzare l’attività ai tipi di pubblico di Adobe Experience Platform nei flussi di lavoro di Campaign e quindi di inviare ad Adobe Real-time Customer Data Platform i dati relativi a tali tipi di pubblico, ad esempio invii, aperture e clic.

* Con **Destinazioni**, acquisisci il pubblico da Adobe Experience Platform in Campaign Classic. Questo ti consente di attivare i dati noti e sconosciuti per le campagne di marketing.
* Con **Origini**, esporta i dati di Campaign Classic (ad esempio invii, aperture, clic) in Adobe Experience Platform. Questo consente di centralizzare i dati raccolti da origini diverse in un’unica posizione e di utilizzare le informazioni acquisite per fare di più.

>[!IMPORTANT]
>
>Tieni presenti i limiti di archiviazione SFTP, i limiti di archiviazione del database e i limiti del profilo attivo in base al tuo contratto Adobe Campaign durante l’esecuzione di questa integrazione.

Per una panoramica più dettagliata di Adobe Real-time Customer Data Platform, Destinations and Sources, consulta queste pagine:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=it)
* [Documentazione sulle destinazioni](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=it)
* [Documentazione sulle origini](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=it)

## Collegare Campaign Classic a Adobe Experience Platform

Per condividere i dati tra Adobe Experience Platform e Campaign Classic, devi innanzitutto connettere Adobe Campaign come **Destinazione** e il percorso di archiviazione BLOB AWS S3 o Azure come **Source** in Adobe Experience Platform.

Una volta configurati i connettori, puoi impostare un’importazione o un’esportazione di dati in Campaign Classic utilizzando i flussi di lavoro.

![](assets/rtcdp-schema.png)

Per ulteriori informazioni su come impostare questi processi di importazione ed esportazione, consulta le sezioni seguenti:

* [Inserire segmenti Adobe Experience Platform in Campaign](../../integrations/using/ingest-aep-data.md)
* [Esportare dati da Campaign ad Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
