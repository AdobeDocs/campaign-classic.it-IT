---
solution: Campaign Classic
product: campaign
title: Tracciare e monitorare i messaggi
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 53e239c04f9c4239a5c32e4f25549cbc5f6ece50
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 3%

---


# Tracciare e monitorare {#track-and-monitor}

Hai fatto clic sul pulsante **Invia**? Vediamo cosa succede. Una volta inviata la consegna, Adobe Campaign ti consente di tenere traccia dei messaggi inviati e scoprire come reagiscono i destinatari alla consegna. In questo modo potrai migliorare l’invio futuro e ottimizzare le campagne successive.

## Monitoraggio delle consegne {#monitoring-deliveries}

Per controllare le campagne, assicurati che il messaggio sia stato effettivamente consegnato ai destinatari.

Dal dashboard di consegna Campaign, puoi controllare i messaggi elaborati e i registri di controllo della consegna.
Puoi anche controllare lo stato dei messaggi nei registri di consegna. [Ulteriori informazioni](../../delivery/using/about-delivery-monitoring.md).

Cosa succede se le consegne non vengono inviate e il loro stato rimane **In sospeso**?

* Il processo di esecuzione è in attesa della disponibilità di alcune risorse. L&#39;MTA potrebbe non essere stato avviato.
Verifica che i moduli mta@instance siano lanciati sui server MTA e avvia il modulo MTA se necessario. [Ulteriori informazioni](../../production/using/administration.md).

* La consegna può utilizzare un’affinità non configurata sull’istanza di invio.
Suggerimento: Controlla la configurazione della gestione del traffico (affinità IP). Per ulteriori informazioni, consulta Controllo del traffico SMTP in uscita.

>[!NOTE]
>
>Questi passaggi possono essere eseguiti solo da un utente esperto.

## Tracking {#tracking-deliveries}

Per conoscere meglio il comportamento dei destinatari, puoi tenere traccia della loro reazione a una consegna: ricezione, apertura, clic su collegamenti, annullamenti di abbonamenti, ecc. In Campaign Classic, queste informazioni vengono visualizzate nella scheda Tracking dei destinatari target interessati dalla consegna e nella scheda Tracking della consegna. In Campaign Standard, viene visualizzato nella scheda Registri di tracciamento della consegna.

**Suggerimento**: Il tracciamento dei messaggi è abilitato per impostazione predefinita. Per configurare gli URL, seleziona l’opzione Visualizza URL nella sezione inferiore della procedura guidata di consegna. Per ogni URL del messaggio, puoi scegliere se attivare il tracciamento.

Per ulteriori informazioni, consulta la sezione [Configurazione del tracciamento](../../delivery/using/how-to-configure-tracked-links.md) e la descrizione [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators) .

## Prestazioni di consegna {#delivery-performances}

Per misurare la velocità di consegna dei messaggi, puoi controllare la velocità di consegna. I criteri corrispondono al numero di messaggi inviati all’ora e alle dimensioni dei messaggi (in bit al secondo). Per ulteriori informazioni, consulta [Velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput).

**Suggerimenti**:

* Non mantenere le consegne nello stato non riuscito sull’istanza, in quanto questo mantiene tabelle temporanee e influisce sulle prestazioni.

* Rimuovi dal database le consegne non più necessarie e inattive per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. Si prega di notare che possono essere necessari da 5 a 10 minuti per distribuire uniformemente il carico sul sistema.

## Risoluzione dei problemi relativi alle consegne {#delivery-troubleshooting}

È possibile eseguire azioni specifiche quando si verificano problemi con le consegne:

* [Problemi di recapito messaggi](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)

* [Problemi di prestazioni di consegna](../../delivery/using/delivery-performances.md)

* [Problemi relativi ai file temporanei](../../production/using/temporary-files.md) : solo per i clienti  *on-premise*
