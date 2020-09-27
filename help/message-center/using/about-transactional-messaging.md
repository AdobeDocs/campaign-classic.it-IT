---
title: Informazioni sulla messaggistica transazionale
description: 'Invia messaggi di attivazione in base agli eventi generati dai sistemi di informazione. '
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# Informazioni sulla messaggistica transazionale{#about-transactional-messaging}

Messaggi transazionali (Centro messaggi) è un modulo Campaign progettato per gestire i messaggi di attivazione. Questi messaggi sono generati da eventi attivati dai sistemi informativi e possono essere: fattura, conferma dell&#39;ordine, conferma della spedizione, modifica della password, notifica dell&#39;indisponibilità del prodotto, dichiarazione dell&#39;account o creazione dell&#39;account del sito Web, ad esempio.

>[!IMPORTANT]
>
>I messaggi transazionali richiedono una licenza specifica. Controllare il contratto di licenza.

 modulo Adobe Campaign Message Center è integrato in un sistema informativo che restituisce gli eventi da modificare in messaggi transazionali personalizzati. Questi messaggi possono essere inviati individualmente o in batch tramite e-mail, SMS o notifiche push.

In questa architettura specifica, la cella di esecuzione è separata dall&#39;istanza di controllo, che garantisce una maggiore disponibilità e una migliore gestione del carico.

>[!NOTE]
>
>Per creare nuovi utenti per le istanze di esecuzione del Centro messaggi ospitate  Adobe Cloud, è necessario contattare  Assistenza clienti del Adobe. Gli utenti del Centro messaggi sono operatori specifici che richiedono autorizzazioni dedicate per accedere alle cartelle &#39;Eventi in tempo reale&#39; (nmsRtEvent).
