---
solution: Campaign Classic
product: campaign
title: Introduzione al tracciamento dei collegamenti personalizzati
description: Scopri come scrivere collegamenti nelle e-mail che possono essere personalizzati e supportare il tracciamento in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 6%

---


# Introduzione al tracciamento dei collegamenti personalizzati {#tracking-personalized-links}

I collegamenti nel contenuto delle e-mail che contengono personalizzazioni devono essere tracciati con una sintassi specifica.

L’utilizzo di JavaScript nel contenuto delle e-mail (HTML o testo) consente di generare e inviare contenuto dinamico ai destinatari, con due limitazioni:

* Lo script non può accedere direttamente al database (funzioni SQL e funzioni API non disponibili),
* Adobe Campaign deve essere in grado di rilevare gli URL in modo che i collegamenti possano essere tracciati. [Ulteriori informazioni](detecting-tracking-urls.md)

Puoi aggiungere [istruzioni specifiche di pre-elaborazione](pre-processing-instructions.md) in questi URL

istruzioni di pre-elaborazione.

Per il rilevamento del tracciamento, Adobe Campaign incorpora [Tidy](http://www.html-tidy.org/) per analizzare l&#39;origine HTML e rilevare il pattern. Elenca tutti gli URL del contenuto in modo che possano essere tracciati singolarmente. Adobe Campaign utilizza di nuovo Tidy per sostituire l&#39;URL (`http://myurl.com`) con un URL che punta al server di reindirizzamento di Adobe Campaign.

Ad esempio, nel contenuto iniziale: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` è sostituito per un particolare destinatario con: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Dove:

* &quot;h&quot; significa il contenuto HTML (o &quot;t&quot; per il contenuto di testo).
* 617791 è l&#39;ID del messaggio / wideLog ID (esadecimale).
* 71ffa3 è l&#39;ID NmsDelivery (esadecimale).
* 71ffa8 è l&#39;ID NmsTrackingUrl (esadecimale).
* p1, p2 e così via sono tutti i parametri da sostituire nell’URL.
