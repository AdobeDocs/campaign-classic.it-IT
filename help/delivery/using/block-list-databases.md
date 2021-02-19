---
solution: Campaign Classic
product: campaign
title: Database Elenco Bloccati
description: Database Elenco Bloccati
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# Elenco Bloccati database{#denylist-databases}

Diverse organizzazioni gestiscono database di indirizzi IP e domini ritenuti utilizzati dagli spammers. La consultazione di questi siti può essere utile per capire perché alcuni messaggi sono stati rifiutati come spam. In genere è possibile richiedere la rimozione di un indirizzo inserito erroneamente in tali elenchi.

Questi database sono denominati RBL (Real-time Blackhole Lists) e vengono consultati tramite un meccanismo DNS. Esistono tre tipi di RBL:

* Per indirizzo IP: elenca gli indirizzi IP che inviano spam o che probabilmente trasmettono spam.
* Per dominio mittente: elenca i domini del mittente (dominio completo dell&#39;indirizzo e-mail di rimbalzo) che inviano spam o che non sono configurati correttamente.
* Per dominio Web: elenca i domini (domini di alto livello registrati con i registrar) che si trovano negli URL dei collegamenti e delle immagini contenuti nel contenuto spam. In  Adobe Campaign, il dominio da prendere in considerazione è generalmente l&#39;indirizzo utilizzato per il tracciamento.

Di seguito è riportato un elenco degli URL più utilizzati. Per un elenco più completo, fare riferimento a [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

   Fare riferimento a [https://www.spamhaus.org/](https://www.spamhaus.org/)

   Il database è più importante. Essere classificato in questo elenco è generalmente una situazione grave. In tal caso, devi agire immediatamente e avvisare i servizi commerciali, la recapito e l&#39;assistenza clienti [ Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

   Fare riferimento a [https://www.spamcop.net/](https://www.spamcop.net/)

   È uno dei database più rinomati. Se uno dei tuoi indirizzi IP è inserito in questo elenco, in genere significa che gli utenti SpamCop hanno dichiarato i tuoi messaggi come Spam o che hai inviato messaggi a un honeypot SpamCop.

* **URIBL**

   Fare riferimento a [https://www.uribl.com/](https://www.uribl.com/)

   Questo elenco identifica i domini che vengono visualizzati regolarmente nei messaggi dichiarati come spam. Se il dominio viene visualizzato in questo elenco, può influenzare in modo significativo la sua recapito. È necessario informare immediatamente i servizi di recapito e [ assistenza clienti di Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SURBL**

   Fare riferimento a [http://www.surbl.org/](http://www.surbl.org/)

   SURBL identifica i siti web che appaiono regolarmente nello spam. Se il dominio viene visualizzato in questo elenco, può influenzare in modo significativo la sua recapito. È necessario informare immediatamente i servizi di recapito e [ assistenza clienti di Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **Manitu iX**

   Questo è un elenco di IP ed è ampiamente utilizzato in Germania. Fare riferimento a [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->