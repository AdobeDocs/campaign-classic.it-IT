---
solution: Campaign Classic
product: campaign
title: Introduzione al tracciamento dei collegamenti personalizzati
description: Scopri come scrivere collegamenti in e-mail personalizzabili e supportare il tracciamento in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Introduzione al tracciamento dei collegamenti personalizzati {#tracking-personalized-links}

I collegamenti nel contenuto dell&#39;e-mail che contengono la personalizzazione richiedono il tracciamento di una sintassi specifica.

L&#39;utilizzo di JavaScript nel contenuto delle e-mail (HTML o Testo) consente di generare e inviare contenuto dinamico ai destinatari, con due limitazioni:

* Lo script non può accedere direttamente al database (la funzione SQL e le funzioni API non sono disponibili),
*  Adobe Campaign deve essere in grado di rilevare gli URL in modo che i collegamenti possano essere tracciati (scopo di questo documento).

Per il rilevamento del tracciamento,  Adobe Campaign incorpora [Tidy](http://www.html-tidy.org/) per analizzare l&#39;origine HTML e rilevare il pattern. Elenca tutti gli URL del contenuto in modo che possano essere tracciati singolarmente.  Adobe Campaign utilizza nuovamente Tidy per sostituire l&#39;URL (`http://myurl.com`) con un URL che punta al server di reindirizzamento  Adobe Campaign.

Ad esempio, nel contenuto iniziale: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` è sostituito per un particolare destinatario con: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Dove:

* &quot;h&quot; indica il contenuto HTML (o &quot;t&quot; per il contenuto di testo).
* 617791 è l&#39;ID del messaggio / wideLog ID (esadecimale).
* 71ffa3 è l’ID NmsDelivery (esadecimale).
* 71ffa8 è l’ID NmsTrackingUrl (esadecimale).
* p1, p2 e così via, sono tutti i parametri da sostituire nell’URL.
