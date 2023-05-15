---
product: campaign
title: Nota tecnica - Aggiornamento del certificato del server del servizio di notifica push Apple
description: Aggiornamento del certificato del server del servizio di notifica push Apple
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Aggiornamento del certificato del server del servizio di notifica push Apple {#apns-certificate-update}



Il 29 marzo 2021, un aggiornamento dell’infrastruttura del servizio di notifica push (APN) di Apple ha interessato il canale iOS di Adobe Campaign Classic. Una modifica alla configurazione del sistema operativo è **obbligatorio** per evitare l’interruzione del canale push iOS.

Ulteriori informazioni sulle modifiche APN [in questa pagina](https://developer.apple.com/news/?id=7gx0a2lp).

Come cliente in hosting, non è necessaria alcuna azione: Adobe ha già incorporato il nuovo certificato radice nell&#39;ambiente.

In qualità di cliente on-premise/ibrido, devi aggiornare la configurazione per garantire una transizione senza soluzione di continuità **prima del 29 marzo 2021**.

Per incorporare il nuovo certificato, effettua le seguenti operazioni:

1. Scarica la **AAACertificateServices 5/12/2020** certificato principale [da questa pagina](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Controlla che il certificato AAA sia presente sia nel tuo sistema operativo che nei trust JAVA. In caso contrario, aggiungilo.

1. Riavvia il servizio Web Adobe Campaign:

   ```
   nlserver restart web
   ```
