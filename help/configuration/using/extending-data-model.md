---
title: Utilizzo della tabella Destinatari classici di Adobe Campaign
description: Scopri come utilizzare la tabella dei destinatari out-of-the-box in Adobe Campaign Classic durante la progettazione del modello dati.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Estensione del modello dati{#extending-data-model}

Quando inizi con Adobe Campaign, devi valutare il modello dati predefinito per verificare quale tabella è la più adatta per memorizzare i dati di marketing.

Se pertinente, puoi utilizzare la tabella dei destinatari predefinita con i campi out-of-the-box, come descritto in questa [sezione](../../configuration/using/default-recipient-table.md).

Se necessario, potete estenderlo con due meccanismi:

* Estende una tabella esistente con nuovi campi. Ad esempio, puoi aggiungere un nuovo campo &quot;Fedeltà&quot; alla tabella Destinatario.
* Create una nuova tabella, ad esempio una tabella &quot;Acquista&quot; in cui sono elencati tutti gli acquisti effettuati da ciascun profilo del database e collegatela alla tabella Destinatario.

Per ulteriori informazioni sulla configurazione degli schemi di estensione per estendere il modello dati concettuale, vedere [Informazioni sull&#39;edizione](../../configuration/using/about-schema-edition.md)dello schema.

>[!IMPORTANT]
>
>L&#39;estensione del modello dati è riservata agli utenti avanzati.
