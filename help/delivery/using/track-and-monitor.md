---
product: campaign
title: Tracciare e monitorare i messaggi
description: Scopri come tracciare e monitorare i messaggi
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring, Reporting
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---

# Tracciare e monitorare {#track-and-monitor}



Hai fatto clic su **Invia** pulsante? Vediamo cosa succede. Una volta inviata la consegna, Adobe Campaign ti consente di tenere traccia dei messaggi inviati e scoprire come i destinatari reagiscono alla consegna. Questo ti aiuterà a migliorare l’invio futuro e a ottimizzare le campagne successive.

## Monitorare le consegne {#monitoring-deliveries}

Per controllare le campagne, devi assicurarti che il messaggio sia stato effettivamente recapitato ai destinatari.

Dal dashboard di consegna di Campaign, puoi controllare i messaggi elaborati e i registri di controllo della consegna.
Puoi anche controllare lo stato dei messaggi nei registri di consegna. [Ulteriori informazioni](about-delivery-monitoring.md).

Cosa succede se le consegne non vengono inviate e il loro stato rimane **In sospeso**?

* Il processo di esecuzione è in attesa della disponibilità di alcune risorse. L’MTA potrebbe non essere stato avviato.
Verifica che i moduli mta@instance siano avviati sui server MTA e, se necessario, avvia il modulo MTA. [Ulteriori informazioni](../../production/using/administration.md).

* La consegna potrebbe utilizzare un’affinità non configurata nell’istanza di invio.
Suggerimento: controlla la configurazione della gestione del traffico (affinità IP). Per ulteriori informazioni, consulta Controllare il traffico SMTP in uscita.

>[!NOTE]
>
>Questi passaggi possono essere eseguiti solo da un utente esperto.

## Tracciare il comportamento {#track-behaviour}

Per conoscere meglio il comportamento dei destinatari, puoi tenere traccia della loro reazione a una consegna: ricezione, apertura, clic su collegamenti, annullamenti di abbonamenti, ecc. In Campaign Classic, queste informazioni vengono visualizzate nella scheda Tracciamento dei destinatari interessati dalla consegna e nella scheda Tracciamento della consegna.

**Suggerimento**: il tracciamento dei messaggi è abilitato per impostazione predefinita. Per configurare gli URL, seleziona l’opzione Visualizza URL nella sezione inferiore della procedura guidata di consegna. Per ogni URL del messaggio, puoi scegliere se attivare il tracciamento.

Per ulteriori informazioni, consulta [Configurare il tracciamento](how-to-configure-tracked-links.md) sezione e [Indicatori di tracciamento](../../reporting/using/delivery-reports.md#tracking-indicators) descrizione.

## Prestazioni di consegna {#delivery-performances}

Per misurare la velocità alla quale vengono consegnati i messaggi, puoi controllare la velocità effettiva di consegna. I criteri sono il numero di messaggi inviati all’ora e le dimensioni dei messaggi (in bit al secondo). Per ulteriori informazioni, consulta [Velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput).

**Suggerimenti**:

* Non mantenere le consegne in stato di errore nell’istanza, in quanto questa operazione mantiene le tabelle temporanee e influisce sulle prestazioni.

* Rimuovi dal database le consegne che non sono più necessarie e i destinatari inattivi per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. Si prega di notare che possono essere necessari da 5 a 10 minuti per distribuire il carico uniformemente sul sistema.

## Risoluzione dei problemi nelle consegne {#delivery-troubleshooting}

Quando si verificano problemi con le consegne, è possibile eseguire azioni specifiche:

* [Problemi di recapito messaggi](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemi relativi alla visualizzazione delle immagini](../../production/using/image-display-issues.md)

* [Problemi di prestazioni della consegna](delivery-performances.md)

* [Problemi relativi ai file temporanei](../../production/using/temporary-files.md) - *solo clienti on-premise*
