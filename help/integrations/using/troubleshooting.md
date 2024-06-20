---
product: campaign
title: Risoluzione dei problemi
description: Risoluzione dei problemi
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
hidefromtoc: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '136'
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

Alcuni dati possono mancare quando si condivide un pubblico tramite Experience Cloud Audience o quando si importa un pubblico. Vengono trasferiti solo i record per i quali l’ID (&quot;ID visitatore&quot; o &quot;ID dichiarato&quot;) è stato riconciliato con la dimensione del profilo. Gli ID dai segmenti non riconosciuti da Adobe Campaign non vengono importati.
