---
solution: Campaign Classic
product: campaign
title: Tracciare e monitorare i messaggi
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 2%

---


# Tracciare e monitorare {#track-and-monitor}

Hai fatto clic sul pulsante Invia? Vediamo cosa succede. Una volta inviata la consegna,  Adobe Campaign consente di tenere traccia dei messaggi inviati e di scoprire in che modo i destinatari reagiscono alla consegna. In questo modo potrai migliorare l’invio futuro e ottimizzare le campagne successive.

## Monitoraggio delle consegne {#monitoring-deliveries}

Per controllare le campagne, devi accertarti che il messaggio sia stato effettivamente recapitato ai destinatari.

Dal dashboard di distribuzione della campagna, puoi controllare i messaggi elaborati e i registri di controllo della distribuzione.
Puoi anche controllare lo stato dei messaggi nei registri di consegna. [Ulteriori informazioni](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Cosa succede se le consegne non vengono inviate e il loro stato rimane **In sospeso**?

* Il processo di esecuzione è in attesa della disponibilità di alcune risorse. L&#39;MTA potrebbe non essere stato avviato.
Verificate che i moduli mta@instance siano avviati sui server MTA e avviate il modulo MTA, se necessario. [Ulteriori informazioni](../../production/using/administration.md).

* La consegna potrebbe utilizzare un&#39;affinità non configurata nell&#39;istanza di invio.
Suggerimento: Controllare la configurazione della gestione del traffico (affinità IP). Per ulteriori informazioni, vedere Controllo del traffico SMTP in uscita.

>[!NOTE]
>
>Questi passaggi possono essere eseguiti solo da un utente esperto.

## Tracking {#tracking-deliveries}

Per conoscere meglio il comportamento dei destinatari, puoi tenere traccia delle loro reazioni: ricezione, apertura, clic su collegamenti, annullamento sottoscrizioni, ecc. In Campaign Classic, queste informazioni vengono visualizzate nella scheda Tracciamento dei destinatari destinatari della consegna e nella scheda Tracciamento della consegna. In Campaign Standard , viene visualizzato nella scheda Registri di tracciamento della consegna.

**Suggerimento**: Il tracciamento dei messaggi è abilitato per impostazione predefinita. Per configurare gli URL, selezionate l’opzione Visualizza URL nella sezione inferiore della procedura guidata di consegna. Per ciascun URL del messaggio, potete scegliere se attivare il tracciamento.

Per ulteriori informazioni, consulta la sezione [Configurazione del tracciamento](../../delivery/using/how-to-configure-tracked-links.md) e la descrizione degli indicatori [di](../../reporting/using/delivery-reports.md#tracking-indicators) tracciamento.

## Prestazioni di consegna {#delivery-performances}

Per misurare la velocità di invio dei messaggi, puoi controllare la velocità di consegna. I criteri corrispondono al numero di messaggi inviati ogni ora e alla dimensione dei messaggi (in bit al secondo). Per ulteriori informazioni, consulta [Distribuzione effettiva](../../reporting/using/global-reports.md#delivery-throughput).

**Suggerimenti**:

* Non mantenere le consegne in stato di errore nell&#39;istanza, in quanto questo mantiene le tabelle temporanee e influisce sulle prestazioni.

* Rimuovete dal database i recapiti non più necessari e i destinatari inattivi per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. Si prega di notare che possono essere necessari da 5 a 10 minuti per distribuire uniformemente il carico sul sistema.

## Risoluzione dei problemi di consegna {#delivery-troubleshooting}

È possibile eseguire azioni specifiche quando si verificano problemi con le consegne:

* [Problemi di realizzazione](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)

* [Problemi relativi alle prestazioni di distribuzione](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemi relativi](../../production/using/temporary-files.md) ai file temporanei - solo per i clienti *interni*
