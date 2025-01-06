---
product: campaign
title: Nota tecnica - Aggiornamento del certificato del server del servizio Apple Push Notification
description: Aggiornamento del certificato del server del servizio di notifica push di Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
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
