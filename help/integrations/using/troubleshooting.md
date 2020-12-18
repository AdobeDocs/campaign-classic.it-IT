---
solution: Campaign Classic
product: campaign
title: Risoluzione dei problemi
description: Risoluzione dei problemi
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# Risoluzione dei problemi{#troubleshooting}

In caso di errore, accertatevi che i seguenti elementi siano configurati correttamente:

* **Account esterni**

   In **[!UICONTROL Administration > Platform > External accounts]**, accertatevi che i seguenti account SFTP esterni siano configurati correttamente. I server SFTP indicati dovrebbero essere stati configurati in Adobe Experience Cloud dal consulente.

   * **[!UICONTROL importSharedAudience]** : Account SFTP dedicato all&#39;importazione di audience.
   * **[!UICONTROL exportSharedAudience]** : Account SFTP dedicato all&#39;esportazione dei tipi di pubblico.

* **Origine dati AMC**

   In **[!UICONTROL Administration > Platform > AMC Data sources]**, verificare che l&#39;origine dati AMC sia impostata correttamente.

Può accadere che alcuni dati manchino durante la condivisione di un&#39;audience tramite il servizio di base Persone o durante l&#39;importazione di un&#39;audience. Vengono trasferiti solo i record per i quali l&#39;ID (&#39;ID visitatore&#39; o &#39;ID dichiarato&#39;) è stato riconciliato con la dimensione del profilo. Gli ID dai segmenti del servizio di base Persone che non sono riconosciuti da  Adobe Campaign non vengono importati.
