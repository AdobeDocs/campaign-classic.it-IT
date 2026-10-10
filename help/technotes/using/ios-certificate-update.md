---
product: campaign
title: Nota tecnica - Aggiornamento del certificato del server del servizio Apple Push Notification
description: Aggiornamento del certificato del server del servizio di notifica push di Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
TQID: 'https://experienceleague.adobe.com/3tQ4npyE0-ZfCgVPYy3kiRv1q0HPcq-DI4rpAXTCXb0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: ab81f6c3-9317-564f-af92-6670a8784294
    internal-label: Technote
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%
---
# Aggiornamento del certificato del server del servizio di notifica push di Apple {#apns-certificate-update}



Il 17 ottobre 2024, un aggiornamento dell’infrastruttura del servizio Apple Push Notification (APNs) ha interessato il canale Adobe Campaign Classic iOS. Una modifica alla configurazione del sistema operativo è **obbligatoria** per evitare l&#39;interruzione del canale push di iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=09za8wzy).

In qualità di cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nel tuo ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione fluida **prima del 24 febbraio 2025**.

Per incorporare il nuovo certificato, effettua le seguenti operazioni:

1. Scarica il certificato radice **SHA-2: USERTrust RSA Certification Authority** [da questa pagina](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Verifica che il certificato AAA sia presente sia nel sistema operativo che nei trustores JAVA. In caso contrario, aggiungilo.

1. Riavvia servizio Web Adobe Campaign:

   ```
   nlserver restart web
   ```
