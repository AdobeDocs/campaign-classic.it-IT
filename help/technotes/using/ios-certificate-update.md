---
product: campaign
title: Nota tecnica - Aggiornamento del certificato del server del servizio di notifica push Apple
description: Aggiornamento del certificato del server del servizio di notifica push Apple
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Aggiornamento del certificato del server del servizio di notifica push Apple {#apns-certificate-update}

![](../../assets/v7-only.svg)

Il 29 marzo 2021, un aggiornamento dell’infrastruttura APN (Apple Push Notification Service) ha interessato il canale iOS Adobe Campaign Classic. Una modifica alla configurazione del sistema operativo è **obbligatoria** per evitare l&#39;interruzione del canale push iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=7gx0a2lp).

Come cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nell&#39;ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione senza soluzione di continuità **prima del 29 marzo 2021**.

Per incorporare il nuovo certificato, effettua le seguenti operazioni:

1. Scarica il certificato **AAACertificateServices 5/12/2020** radice [da questa pagina](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Controlla che il certificato AAA sia presente sia nel tuo sistema operativo che nei trust JAVA. In caso contrario, aggiungilo.

1. Riavvia il servizio Web Adobe Campaign:

   ```
   nlserver restart web
   ```
