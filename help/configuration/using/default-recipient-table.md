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


# Utilizzo della tabella Destinatario predefinita{#default-recipient-table}

La tabella dei destinatari out-of-the-box in Adobe Campaign rappresenta un buon punto di partenza per la creazione del modello dati. Contiene una serie di campi e collegamenti di tabella predefiniti che possono essere facilmente estesi. Ciò è particolarmente utile quando si esegue il targeting principalmente dei destinatari, perché si adatta a un semplice modello dati incentrato sui destinatari.

L&#39;utilizzo della tabella Destinatario standard comporta i seguenti vantaggi:

* Utilizzo di funzionalità quali abbonamenti, elenchi di sementi, sondaggi, social network e così via.
* Fornire un database di marketing con un modello dati incentrato sui destinatari.
* Implementazione più rapida.
* Facile manutenzione da parte del supporto e dei partner.

Tuttavia, è possibile estendere la tabella Destinatario, ma non ridurre il numero di campi o collegamenti nella tabella.

>[!IMPORTANT]
>
>Si consiglia di non eliminare i campi (anche se inutili) nella tabella dei destinatari, in quanto ciò potrebbe causare errori nei moduli incorporati.

Inoltre, poiché la tabella Destinatario fa parte del prodotto, sia la tabella che il modulo associato si evolvono mano a mano che il prodotto cambia. Pertanto, è necessaria ulteriore manutenzione per verificare che eventuali estensioni siano ancora valide al momento dell&#39;aggiornamento.
