---
product: campaign
title: Introduzione al tracciamento dei collegamenti personalizzati
description: Scopri come scrivere nelle e-mail collegamenti che possono essere personalizzati e supportare il tracciamento in Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 7%

---

# Introduzione al tracciamento dei collegamenti personalizzati {#tracking-personalized-links}

I collegamenti nel contenuto delle e-mail che contengono la personalizzazione devono essere tracciati con una sintassi specifica.

L’utilizzo di JavaScript nel contenuto delle e-mail (HTML o Testo) consente di generare e inviare contenuto dinamico ai destinatari, con due limitazioni:

* Lo script non può accedere direttamente al database (funzioni SQL e API non disponibili),
* Adobe Campaign deve essere in grado di rilevare gli URL in modo da poter tenere traccia dei collegamenti. [Ulteriori informazioni](detecting-tracking-urls.md)

Puoi aggiungere istruzioni di pre-elaborazione specifiche per scrivere lo script dell’URL e tracciarlo. [Ulteriori informazioni](pre-processing-instructions.md)

Per il rilevamento del tracciamento, Adobe Campaign incorpora [Tidy](https://www.html-tidy.org/) per analizzare l&#39;origine HTML e rilevare il modello. Elenca tutti gli URL del contenuto in modo che possano essere tracciati singolarmente. Adobe Campaign utilizza nuovamente Tidy per sostituire l&#39;URL (`http://myurl.com`) con un URL che punta al server di reindirizzamento di Adobe Campaign.

Ad esempio, nel contenuto iniziale: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` è sostituito per un destinatario particolare con: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Dove:

* &quot;h&quot; significa contenuto HTML (o &quot;t&quot; per contenuto di testo).
* 617791 è l’ID del messaggio/broadLog ID (esadecimale).
* 71ffa3 è l’ID NmsDelivery (esadecimale).
* 71ffa8 è l’ID NmsTrackingUrl (esadecimale).
* p1, p2 e così via sono tutti i parametri da sostituire nell&#39;URL.
