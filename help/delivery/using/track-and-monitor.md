---
product: campaign
title: Tracciare e monitorare i messaggi
description: Scopri come tracciare e monitorare i messaggi
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# Tracciare e monitorare {#track-and-monitor}



Fai clic su **Invia** pulsante? Vediamo cosa succede. Una volta inviata la consegna, Adobe Campaign ti consente di tenere traccia dei messaggi inviati e scoprire come reagiscono i destinatari alla consegna. In questo modo potrai migliorare l’invio futuro e ottimizzare le campagne successive.

## Monitorare le consegne {#monitoring-deliveries}

Per controllare le campagne, assicurati che il messaggio sia stato effettivamente consegnato ai destinatari.

Dal dashboard di consegna Campaign, puoi controllare i messaggi elaborati e i registri di controllo della consegna.
Puoi anche controllare lo stato dei messaggi nei registri di consegna. [Ulteriori informazioni](about-delivery-monitoring.md).

Cosa succede se le consegne non vengono inviate e il loro stato rimane **In sospeso**?

* Il processo di esecuzione è in attesa della disponibilità di alcune risorse. L&#39;MTA potrebbe non essere stato avviato.
Verifica che i moduli mta@instance siano lanciati sui server MTA e avvia il modulo MTA se necessario. [Ulteriori informazioni](../../production/using/administration.md).

* La consegna può utilizzare un’affinità non configurata sull’istanza di invio.
Suggerimento: Controlla la configurazione della gestione del traffico (affinità IP). Per ulteriori informazioni, consulta Controllo del traffico SMTP in uscita.

>[!NOTE]
>
>Questi passaggi possono essere eseguiti solo da un utente esperto.

## Tracciamento del comportamento {#track-behaviour}

Per conoscere meglio il comportamento dei destinatari, puoi tenere traccia della loro reazione a una consegna: ricezione, apertura, clic su collegamenti, annullamenti di abbonamenti, ecc. In Campaign Classic, queste informazioni vengono visualizzate nella scheda Tracking dei destinatari target interessati dalla consegna e nella scheda Tracking della consegna.

**Suggerimento**: Il tracciamento dei messaggi è abilitato per impostazione predefinita. Per configurare gli URL, seleziona l’opzione Visualizza URL nella sezione inferiore della procedura guidata di consegna. Per ogni URL del messaggio, puoi scegliere se attivare il tracciamento.

Per ulteriori informazioni, consulta la sezione [Configurare il tracciamento](how-to-configure-tracked-links.md) la sezione [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators) descrizione.

## Prestazioni di consegna {#delivery-performances}

Per misurare la velocità di consegna dei messaggi, puoi controllare la velocità di consegna. I criteri corrispondono al numero di messaggi inviati all’ora e alle dimensioni dei messaggi (in bit al secondo). Per ulteriori informazioni, consulta [Velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput).

**Suggerimenti**:

* Non mantenere le consegne nello stato non riuscito sull’istanza, in quanto questo mantiene tabelle temporanee e influisce sulle prestazioni.

* Rimuovi dal database le consegne non più necessarie e inattive per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. Si prega di notare che possono essere necessari da 5 a 10 minuti per distribuire uniformemente il carico sul sistema.

## Risoluzione dei problemi nelle consegne {#delivery-troubleshooting}

È possibile eseguire azioni specifiche quando si verificano problemi con le consegne:

* [Problemi di recapito messaggi](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)

* [Problemi di prestazioni di consegna](delivery-performances.md)

* [Problemi relativi ai file temporanei](../../production/using/temporary-files.md) - *solo clienti on-premise*
