---
product: campaign
title: Introduzione al tracciamento dei collegamenti personalizzati
description: Scopri come scrivere collegamenti nelle e-mail che possono essere personalizzati e supportare il tracciamento in Campaign Classic.
feature: Personalization
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# Introduzione al tracciamento dei collegamenti personalizzati {#tracking-personalized-links}

![](../../assets/common.svg)

I collegamenti nel contenuto delle e-mail che contengono personalizzazioni devono essere tracciati con una sintassi specifica.

L’utilizzo di JavaScript nel contenuto delle e-mail (HTML o Testo) consente di generare e inviare contenuto dinamico ai destinatari, con due limitazioni:

* Lo script non può accedere direttamente al database (funzioni SQL e funzioni API non disponibili),
* Adobe Campaign deve essere in grado di rilevare gli URL in modo che i collegamenti possano essere tracciati. [Ulteriori informazioni](detecting-tracking-urls.md)

Puoi aggiungere istruzioni specifiche di pre-elaborazione per creare uno script dell’URL e tenerne traccia. [Ulteriori informazioni](pre-processing-instructions.md)

Per il rilevamento del tracciamento, incorporamenti Adobe Campaign [Riordinato](https://www.html-tidy.org/) per analizzare la sorgente di HTML e rilevare il pattern. Elenca tutti gli URL del contenuto in modo che possano essere tracciati singolarmente. Adobe Campaign utilizza di nuovo Tidy per sostituire l’URL (`http://myurl.com`) con un URL che punta al server di reindirizzamento di Adobe Campaign.

Ad esempio, nel contenuto iniziale: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` è sostituito per un particolare destinatario con: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Dove:

* &quot;h&quot; indica il contenuto di HTML (o &quot;t&quot; per il contenuto di testo).
* 617791 è l&#39;ID del messaggio / wideLog ID (esadecimale).
* 71ffa3 è l&#39;ID NmsDelivery (esadecimale).
* 71ffa8 è l&#39;ID NmsTrackingUrl (esadecimale).
* p1, p2 e così via sono tutti i parametri da sostituire nell’URL.
