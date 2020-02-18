---
title: Database Blacklist
seo-title: Database Blacklist
description: Database Blacklist
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ac3a0ca00591943d79563e9fd4d85d71fa0ba81a

---


# Database Blacklist{#blacklisting-databases}

Diverse organizzazioni gestiscono database di indirizzi IP e domini ritenuti utilizzati dagli spammers. La consultazione di questi siti può essere utile per capire perché alcuni messaggi sono stati rifiutati come spam. È generalmente possibile richiedere la rimozione di un indirizzo inserito erroneamente in tali elenchi.

Questi database sono denominati RBL (Real-time Blackhole Lists) e vengono consultati tramite un meccanismo DNS. Esistono tre tipi di RBL:

* Per indirizzo IP: elenca gli indirizzi IP che inviano spam o che probabilmente trasmettono spam.
* Per dominio mittente: elenca i domini del mittente (dominio completo dell&#39;indirizzo e-mail di rimbalzo) che inviano spam o che non sono configurati correttamente.
* Per dominio Web: elenca i domini (domini di alto livello registrati con i registrar) che si trovano negli URL dei collegamenti e delle immagini contenuti nel contenuto spam. In Adobe Campaign, il dominio da prendere in considerazione è generalmente l&#39;indirizzo utilizzato per il tracciamento.

Di seguito è riportato un elenco degli URL più utilizzati. Per un elenco più completo, fare riferimento al modulo [https://www.dnsstuff.com/](https://tools.dnsstuff.com/) (&quot;Ricerca nella lista nera degli spam&quot;).

* **Spamhaus**

   Fare riferimento a [https://www.spamhaus.org/](https://www.spamhaus.org/)

   Il database è più importante. Essere classificato in questo elenco è generalmente una situazione grave. In tal caso, devi agire immediatamente e avvisare i servizi commerciali, la recapito e il supporto Adobe Campaign.

* **SpamCop**

   Fare riferimento a [https://www.spamcop.net/](https://www.spamcop.net/)

   È uno dei database più rinomati. Se uno dei tuoi indirizzi IP è inserito in questo elenco, in genere significa che gli utenti SpamCop hanno dichiarato i tuoi messaggi come Spam o che hai inviato messaggi a un honeypot SpamCop.

* **URIBL**

   Fare riferimento a [https://www.uribl.com/](https://www.uribl.com/)

   Questo elenco identifica i domini che vengono visualizzati regolarmente nei messaggi dichiarati come spam. Se il dominio viene visualizzato in questo elenco, può influenzare in modo significativo la sua recapito. Devi informare immediatamente i servizi di recapito e il supporto Adobe Campaign.

* **SURBL**

   Fare riferimento a [https://www.surbl.org/](https://www.surbl.org/)

   SURBL identifica i siti web che appaiono regolarmente nello spam. Se il dominio viene visualizzato in questo elenco, può influenzare in modo significativo la sua recapito. Devi informare immediatamente i servizi di recapito e il supporto Adobe Campaign.

* **Manitu iX**

   Questo è un elenco di IP ed è ampiamente utilizzato in Germania. Fare riferimento a [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->