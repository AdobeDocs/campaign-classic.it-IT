---
solution: Campaign Classic
product: campaign
title: Best practice per la distribuzione
description: Ulteriori informazioni sulle prestazioni di distribuzione e sulle best practice.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 5b43412286762977c416665d296908a9bfc9b20a
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 2%

---


# Best practice per la distribuzione {#delivery-performances}

Si consiglia di seguire le linee guida riportate di seguito per garantire il corretto svolgimento delle consegne, nonché i controlli eseguiti in caso di problemi di consegna.

**Argomenti correlati:**

* [Pannello consegna](../../delivery/using/delivery-dashboard.md)
* [Risoluzione dei problemi di consegna](../../delivery/using/delivery-troubleshooting.md)
* [Informazioni sul recapito messaggi](../../delivery/using/about-deliverability.md)

## Procedure ottimali per le prestazioni {#best-practices-performance}

* Non mantenere le consegne in stato di errore nell&#39;istanza, in quanto questo mantiene le tabelle temporanee e influisce sulle prestazioni.

* Rimuovere le consegne che non sono più necessarie.

* Destinatari inattivi negli ultimi 12 mesi da rimuovere dal database per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. C&#39;è uno spazio di 5-10 minuti per distribuire uniformemente il carico sul sistema. Coordinate la pianificazione delle consegne con gli altri membri del team per garantire le migliori prestazioni. Quando il server di marketing gestisce contemporaneamente diverse attività, può rallentare le prestazioni.

* Mantenete le dimensioni dei vostri messaggi e-mail il più possibile ridotte. La dimensione massima consigliata per un messaggio e-mail è di circa 35 KB. La dimensione di una distribuzione di e-mail genera una certa quantità di volume nei server di invio.

* Le consegne di grandi dimensioni, come le consegne a più di un milione di destinatari, richiedono spazio nelle code di invio. Questo non è un problema per il server, ma se combinato con dozzine di altre consegne di grandi dimensioni che vanno tutte fuori allo stesso tempo, può introdurre un ritardo di invio.

* La personalizzazione nelle e-mail estrae i dati dal database per ciascun destinatario. Se sono presenti molti elementi di personalizzazione, questo aumenta la quantità di dati necessari per preparare la consegna.

* Indirizzi indice. Per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione, è possibile dichiarare un indice dall&#39;elemento principale dello schema di dati.

>[!NOTE]
>
>Gli ISP disattiverebbero gli indirizzi dopo un periodo di inattività. I messaggi di rifiuto vengono inviati ai mittenti per informarli di questo nuovo stato.

## Elenco di controllo dei problemi di prestazioni {#performance-issues}

Se le prestazioni di consegna sono sbagliate, è possibile controllare:

* **Dimensioni della consegna**: Il completamento delle consegne di grandi dimensioni può richiedere più tempo. Gli elementi figlio MTA sono configurati per gestire una dimensione batch predefinita, che funziona per la maggior parte delle istanze, ma devono essere controllati quando le consegne sono costantemente lente.
* **Destinazione della consegna**: Il divieto di prestazioni di consegna è influenzato da errori di rimbalzo soft, che vengono gestiti in base alla configurazione del nuovo tentativo. Maggiore è il numero di errori, maggiori saranno i tentativi necessari.
* **Il carico** complessivo della piattaforma: Quando vengono inviate diverse consegne di grandi dimensioni, la piattaforma globale può risentirne. È inoltre possibile controllare la reputazione dell&#39;IP e i problemi di recapito. Per ulteriori informazioni, consultare  Guida alle best practice di recapito di Adobe Campaign [e ](../../delivery/using/deliverability-key-points.md) e [questa pagina](../../delivery/using/about-deliverability.md).

La manutenzione di piattaforme e database può anche influire sulle prestazioni di invio delle consegne. Per ulteriori informazioni, consulta [questa pagina](../../production/using/database-performances.md).
