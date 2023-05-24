---
product: campaign
title: Risoluzione dei problemi
description: Risoluzione dei problemi
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---

# Risoluzione dei problemi{#troubleshooting}



In caso di errore, assicurati che i seguenti elementi siano configurati correttamente:

* **Account esterni**

   In entrata **[!UICONTROL Administration > Platform > External accounts]**, assicurati che i seguenti account SFTP esterni siano configurati correttamente. I server SFTP menzionati avrebbero dovuto essere configurati in Adobe Experience Cloud dal tuo consulente.

   * **[!UICONTROL importSharedAudience]** : account SFTP dedicato all’importazione di tipi di pubblico.
   * **[!UICONTROL exportSharedAudience]** : account SFTP dedicato all’esportazione dei tipi di pubblico.

* **Origine dati AMC**

   In entrata **[!UICONTROL Administration > Platform > AMC Data sources]**, verificare che l&#39;origine dati AMC sia impostata correttamente.

Alcuni dati possono mancare quando si condivide un pubblico tramite il servizio core People o quando si importa un pubblico. Vengono trasferiti solo i record per i quali l’ID (&quot;ID visitatore&quot; o &quot;ID dichiarato&quot;) è stato riconciliato con la dimensione del profilo. Gli ID dei segmenti del servizio core People che non sono riconosciuti da Adobe Campaign non vengono importati.
