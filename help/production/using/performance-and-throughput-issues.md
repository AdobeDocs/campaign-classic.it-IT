---
title: Problemi relativi a prestazioni e velocità effettiva
seo-title: Problemi relativi a prestazioni e velocità effettiva
description: Problemi relativi a prestazioni e velocità effettiva
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 4%

---


# Problemi relativi a prestazioni e velocità effettiva{#performance-and-throughput-issues}

>[!NOTE]
>
>Prima di tutto, verificate di disporre della build più recente installata. In questo modo avrete a disposizione le funzioni e le correzioni di bug più recenti. Per ulteriori informazioni sul contenuto di ciascuna versione, consulta [Note](../../rn/using/latest-release.md) sulla versione.

## Hardware e infrastruttura {#hardware-and-infrastructure}

Le linee guida generali per i requisiti hardware per i Campaign Classic locali sono descritte in dettaglio in questo [articolo](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

Il team di consulenza può fornire ai clienti ospitati uno strumento che consente di visualizzare facilmente lo spazio utilizzato da vari tipi di tabelle nel database e lo spazio utilizzato sul sito SFTP. Offre inoltre strumenti per la pulizia di dati non necessari. Contattate i team di consulenza o assistenza se avete bisogno di implementare questo strumento. Di seguito sono riportati alcuni elementi importanti da verificare utilizzando questo strumento:

* Se la dimensione dell&#39;indice è maggiore della dimensione della tabella, è necessario un vuoto.
* Controllare le tabelle con il numero massimo di caratteri jolly. Se queste tabelle vengono utilizzate frequentemente, devono essere svuotate.
* Il blocco del database può causare l&#39;interruzione dell&#39;invio delle e-mail.

 Adobe Campaign fornisce anche uno [strumento](../../production/using/monitoring-processes.md#manual-monitoring) per controllare l&#39;utilizzo di CPU e RAM. Utilizzate questo strumento e osservate indicatori specifici quali: **Memoria**, **Memoria** Swap, **Disco**, Processi **** Attivi. Se i valori sono troppo alti, puoi provare a ridurre il numero di flussi di lavoro o pianificare l&#39;avvio dei flussi di lavoro in momenti diversi.

## Prestazioni del database {#database-performances}

Nella maggior parte dei casi, i problemi di prestazioni sono collegati alla manutenzione del database. Gli elementi principali da verificare sono i seguenti:

* Configurazione: è consigliabile verificare la configurazione iniziale  piattaforma Adobe Campaign ed eseguire un controllo hardware completo.
* Installazione e configurazione della piattaforma Adobe Campaign : controlla la configurazione di rete e le opzioni di recapito della piattaforma.
* Manutenzione del database: accertatevi che l&#39;attività di pulizia del database sia operativa e che la manutenzione del database sia pianificata ed eseguita correttamente. Verificare il numero e la dimensione delle tabelle di lavoro.
* Diagnosi in tempo reale: controllate i file di registro di processo e piattaforma, quindi controllate l&#39;attività del database durante la ricreazione del problema.

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## Configurazione applicazione {#application-configuration}

Di seguito è riportato un elenco degli articoli relativi alle procedure ottimali per la configurazione dell&#39;applicazione:

* Processi e memoria MTA e MTAChild: il modulo **mta** distribuisce i messaggi ai suoi moduli figlio **principale** . Ogni **nodo secondario** prepara i messaggi prima di richiedere un&#39;autorizzazione al server delle statistiche e inviarli. Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* Configurazione TLS: l&#39;abilitazione di TLS a livello globale non è consigliata perché può ridurre il throughput. Al contrario, le impostazioni TLS per dominio, gestite dal team di recapito, dovrebbero essere regolate in base alle esigenze. Refer to this [page](../../installation/using/email-deliverability.md#mx-configuration) for more information.
* DKIM: per garantire il livello di protezione del DKIM, il formato 1024b è la dimensione consigliata per le best practice di cifratura. Le chiavi DKIM inferiori non saranno considerate valide dalla maggior parte dei provider di accesso. Fate riferimento a questa [pagina](../../delivery/using/technical-recommendations.md#dkim) e a questa [nota tecnica](https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html).

## Problemi di realizzazione {#deliverability-issues}

Di seguito è riportato un elenco delle best practice e degli articoli relativi alla recapito:

* reputazione IP: se la reputazione dell&#39;IP non è sufficiente, le prestazioni saranno influenzate. Il modulo **Deliverability Monitoring** offre diversi strumenti per monitorare le prestazioni della piattaforma. Refer to this [page](../../delivery/using/monitoring-deliverability.md).
* Riscaldamento IP: il riscaldamento dell&#39;IP viene eseguito dal team di recapito. Ciò comporta un aumento graduale del numero di e-mail attraverso nuovi IP in un periodo di poche settimane.
* Impostazione affinità IP: un&#39;impostazione errata dell&#39;affinità IP può arrestare completamente le e-mail (nome di operatore/affinità errato nella configurazione) o ridurre il throughput (numero limitato di IP nell&#39;affinità). Refer to this [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Dimensione e-mail: la dimensione dell&#39;e-mail svolge un ruolo importante nella trasmissione. La dimensione massima consigliata per l’e-mail è 60 KB. Refer to this [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Nel report [sulla velocità](../../reporting/using/global-reports.md#delivery-throughput) di consegna, controlla il numero di byte trasferiti per ora.
* Numero elevato di destinatari non validi: se è presente un numero elevato di destinatari non validi, può avere un impatto sul throughput. Il MTA continua a ripetere l&#39;invio di e-mail a destinatari non validi. Assicurarsi che il database sia ben mantenuto.
* Entità della personalizzazione: se una consegna rimane in &quot;Personalizzazione in corso&quot;, controlla il codice JavaScript utilizzato nei blocchi di personalizzazione.

>[!NOTE]
>
>Vedere anche [Sezione Punti](../../delivery/using/deliverability-key-points.md) chiave di recapito.

