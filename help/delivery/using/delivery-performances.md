---
product: campaign
title: Best practice per le prestazioni di consegna
description: Ulteriori informazioni sulle prestazioni di consegna e sulle best practice
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 5%

---

# Best practice per le prestazioni di consegna {#delivery-performances}

È consigliabile seguire le linee guida riportate di seguito per garantire il corretto funzionamento delle consegne, nonché i controlli da eseguire in caso di problemi con le consegne.

**Argomenti correlati:**

* [Dashboard delle consegne](delivery-dashboard.md)
* [Risoluzione dei problemi nelle consegne](delivery-troubleshooting.md)
* [Informazioni sul recapito messaggi](about-deliverability.md)

## Best practice per le prestazioni {#best-practices-performance}

* Non mantenere le consegne in stato di errore nell’istanza, in quanto questa operazione mantiene le tabelle temporanee e influisce sulle prestazioni.

* Rimuovi le consegne che non sono più necessarie.

* Destinatari inattivi negli ultimi 12 mesi da rimuovere dal database per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. Vi è uno spazio di 5-10 minuti per distribuire uniformemente il carico sul sistema. Coordina la pianificazione delle consegne con gli altri membri del team per garantire le migliori prestazioni. Quando il server di marketing gestisce molte attività diverse allo stesso tempo, può rallentare le prestazioni.

* Mantieni la dimensione delle e-mail il più bassa possibile. La dimensione massima consigliata per un’e-mail è di circa 35 KB. La dimensione di una consegna e-mail genera una certa quantità di volume nei server di invio.

* Le consegne di grandi dimensioni, come le consegne a più di un milione di destinatari, richiedono spazio nelle code di invio. Questo da solo non è un problema per il server, ma se combinato con decine di altre consegne di grandi dimensioni che escono tutte nello stesso momento, può introdurre un ritardo di invio.

* Personalization nelle e-mail estrae i dati dal database per ogni destinatario. Se sono presenti molti elementi di personalizzazione, aumenta la quantità di dati necessari per preparare la consegna.

* Indirizzi di indice. Per ottimizzare le prestazioni delle query SQL utilizzate nell’applicazione, è possibile dichiarare un indice dall’elemento principale dello schema di dati.

>[!NOTE]
>
>Gli ISP disattivano gli indirizzi dopo un periodo di inattività. I messaggi non recapitati vengono inviati ai mittenti per informarli di questo nuovo stato.

## Elenco di controllo dei problemi di prestazioni {#performance-issues}

Se le prestazioni di consegna non sono soddisfacenti, puoi controllare:

* **Dimensione della consegna**: il completamento delle consegne di grandi dimensioni può richiedere più tempo. Gli elementi secondari MTA sono configurati per gestire una dimensione batch predefinita, che funziona per la maggior parte delle istanze, ma devono essere controllati quando le consegne sono costantemente lente.
* **Destinazione della consegna**: le prestazioni della consegna non sono interessate da errori di mancati recapiti non permanenti, che vengono gestiti in base alla configurazione dei nuovi tentativi. Maggiore è il numero di errori, maggiore è il numero di tentativi necessari.
* **Caricamento complessivo della piattaforma**: l&#39;invio di diverse consegne di grandi dimensioni può influire sulla piattaforma complessiva. Puoi anche controllare la reputazione IP e i problemi di consegna. Per ulteriori informazioni, consulta [questa sezione](about-deliverability.md) e la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

La manutenzione della piattaforma e del database può influire anche sulle prestazioni di invio della consegna. Per ulteriori informazioni, consulta [questa pagina](../../production/using/database-performances.md).
