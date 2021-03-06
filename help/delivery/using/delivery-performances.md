---
product: campaign
title: Best practice per la consegna
description: Ulteriori informazioni sulle prestazioni di consegna e sulle best practice.
feature: Deliverability
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 6%

---

# Best practice per la consegna {#delivery-performances}

![](../../assets/common.svg)

Per garantire le corrette prestazioni delle consegne, oltre ai controlli da eseguire in caso di problemi di consegna, si consiglia di seguire le linee guida riportate di seguito.

**Argomenti correlati:**

* [Dashboard delle consegne](delivery-dashboard.md)
* [Risoluzione dei problemi nelle consegne](delivery-troubleshooting.md)
* [Informazioni sul recapito messaggi](about-deliverability.md)

## Best practice per le prestazioni {#best-practices-performance}

* Non mantenere le consegne nello stato non riuscito sull’istanza, in quanto questo mantiene tabelle temporanee e influisce sulle prestazioni.

* Rimuovi le consegne non più necessarie.

* Destinatari inattivi negli ultimi 12 mesi da rimuovere dal database per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. C&#39;è un intervallo di 5-10 minuti per distribuire uniformemente il carico sul sistema. Coordinare la pianificazione delle consegne con gli altri membri del team per garantire le migliori prestazioni. Quando il server di marketing gestisce contemporaneamente diverse attività, può rallentare le prestazioni.

* Mantieni la dimensione delle e-mail il più bassa possibile. La dimensione massima consigliata di un’e-mail è di circa 35 KB. La dimensione di una consegna e-mail genera una certa quantità di volume nei server di invio.

* Le consegne di grandi dimensioni, ad esempio le consegne a più di un milione di destinatari, necessitano di spazio nelle code di invio. Questo da solo non è un problema per il server, ma se combinato con dozzine di altre consegne di grandi dimensioni che si verificano contemporaneamente, può introdurre un ritardo di invio.

* La personalizzazione nelle e-mail estrae i dati dal database per ciascun destinatario. Se sono presenti molti elementi di personalizzazione, ciò aumenta la quantità di dati necessari per preparare la consegna.

* Indirizzi indice. Per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione, è possibile dichiarare un indice dall&#39;elemento principale dello schema dati.

>[!NOTE]
>
>Gli ISP disattiverebbero gli indirizzi dopo un periodo di inattività. I messaggi non recapitati vengono inviati ai mittenti per informarli di questo nuovo stato.

## Elenco di controllo dei problemi di prestazioni {#performance-issues}

Se le prestazioni di consegna sono sbagliate, puoi controllare:

* **Dimensione della consegna**: Il completamento delle consegne di grandi dimensioni può richiedere più tempo. Gli elementi figlio MTA sono configurati per gestire una dimensione batch predefinita, che funziona per la maggior parte delle istanze, ma devono essere controllati quando le consegne sono costantemente lente.
* **Obiettivo della consegna**: Il divieto di prestazioni di consegna è influenzato da errori di mancato recapito, che vengono gestiti in base alla configurazione dei tentativi. Maggiore è il numero di errori, più sono necessari tentativi.
* **Il carico complessivo della piattaforma**: Quando vengono inviate diverse consegne di grandi dimensioni, la piattaforma globale può essere interessata. Puoi anche verificare la reputazione dell’IP e i problemi di recapito messaggi. Per ulteriori informazioni, consulta [questa sezione](about-deliverability.md) e [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

La manutenzione della piattaforma e del database può anche influire sulle prestazioni di invio della consegna. Per ulteriori informazioni, consulta [questa pagina](../../production/using/database-performances.md).
