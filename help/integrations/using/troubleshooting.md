---
title: Risoluzione dei problemi
seo-title: Risoluzione dei problemi
description: Risoluzione dei problemi
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Risoluzione dei problemi{#troubleshooting}

In caso di errore, accertatevi che i seguenti elementi siano configurati correttamente:

* **Account esterni**

   In **[!UICONTROL Administration > Platform > External accounts]**, accertatevi che i seguenti account SFTP esterni siano configurati correttamente. I server SFTP indicati dovrebbero essere stati configurati in Adobe Experience Cloud dal tuo consulente.

   * **[!UICONTROL importSharedAudience]** : Account SFTP dedicato all&#39;importazione di audience.
   * **[!UICONTROL exportSharedAudience]** : Account SFTP dedicato all&#39;esportazione di audience.

* **Origine dati AMC**

   In **[!UICONTROL Administration > Platform > AMC Data sources]**, verificate che l&#39;origine dati AMC sia impostata correttamente.

Può accadere che alcuni dati manchino durante la condivisione di un&#39;audience tramite il servizio di base Persone o durante l&#39;importazione di un&#39;audience. Vengono trasferiti solo i record per i quali l&#39;ID (&#39;ID visitatore&#39; o &#39;ID dichiarato&#39;) è stato riconciliato con la dimensione del profilo. Gli ID dai segmenti del servizio di base Persone non riconosciuti da Adobe Campaign non vengono importati.
