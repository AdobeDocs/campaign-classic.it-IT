---
product: campaign
title: Nota tecnica - Aggiornamento del certificato del server del servizio Apple Push Notification
description: Aggiornamento del certificato del server del servizio di notifica push di Apple
feature: Technote, Push
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 4%

---

# Aggiornamento del certificato del server del servizio di notifica push di Apple {#apns-certificate-update}



Il 29 marzo 2021, un aggiornamento dell’infrastruttura del servizio di notifica push di Apple (APNs) ha interessato il canale Adobe Campaign Classic iOS. Una modifica alla configurazione del sistema operativo è **obbligatorio** per evitare interruzioni del canale push di iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=7gx0a2lp).

In qualità di cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nel tuo ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione fluida **prima del 29 marzo 2021**.

Per incorporare il nuovo certificato, effettua le seguenti operazioni:

1. Scarica il file **AAACertificateServices 5/12/2020** certificato radice [da questa pagina](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Verifica che il certificato AAA sia presente sia nel sistema operativo che nei trustores JAVA. In caso contrario, aggiungilo.

1. Riavvia servizio Web Adobe Campaign:

   ```
   nlserver restart web
   ```
