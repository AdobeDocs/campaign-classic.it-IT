---
solution: Campaign Classic
product: campaign
title: Problemi relativi a prestazioni e velocità effettiva
description: Problemi relativi a prestazioni e velocità effettiva
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 3%

---


# Problemi relativi a prestazioni e velocità effettiva{#performance-and-throughput-issues}

Prima di tutto, verificate di disporre della build più recente installata. In questo modo avrete a disposizione le funzioni e le correzioni di bug più recenti.

Per ulteriori informazioni sul contenuto di ciascuna versione, consultare le [Note sulla versione](../../rn/using/latest-release.md).

## Hardware e infrastruttura {#hardware-and-infrastructure}

Le linee guida generali per i requisiti hardware per i Campaign Classic locali sono descritte in dettaglio in questa [pagina](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

Il team di consulenza può fornire ai clienti ospitati uno strumento che consente di visualizzare facilmente lo spazio utilizzato da vari tipi di tabelle nel database e lo spazio utilizzato sul sito SFTP. Offre inoltre strumenti per la pulizia di dati non necessari. Contatta l&#39;Assistenza clienti [ Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) se hai bisogno di implementare questo strumento. Di seguito sono riportati alcuni elementi importanti da verificare utilizzando questo strumento:

* Se la dimensione dell&#39;indice è maggiore della dimensione della tabella, è necessario un vuoto.
* Controllare le tabelle con il numero massimo di caratteri jolly. Se queste tabelle vengono utilizzate frequentemente, devono essere svuotate.
* Il blocco del database può causare l&#39;interruzione dell&#39;invio delle e-mail.

 Adobe Campaign fornisce anche uno [strumento](../../production/using/monitoring-processes.md#manual-monitoring) per controllare l&#39;utilizzo di CPU e RAM. Utilizzate questo strumento e osservate indicatori specifici quali: **Memoria**, **Swap Memory**, **Disco**, **Processi attivi**. Se i valori sono troppo alti, puoi provare a ridurre il numero di flussi di lavoro o pianificare l&#39;avvio dei flussi di lavoro in momenti diversi.

## Controllo database {#database-performances}

Nella maggior parte dei casi, i problemi di prestazioni sono collegati alla manutenzione del database. Gli elementi principali da verificare sono i seguenti:

* Configurazione: è consigliabile verificare la configurazione iniziale  piattaforma Adobe Campaign ed eseguire un controllo hardware completo.
* Installazione e configurazione della piattaforma Adobe Campaign : controlla la configurazione di rete e le opzioni di recapito della piattaforma.
* Manutenzione del database: accertatevi che l&#39;attività di pulizia del database sia operativa e che la manutenzione del database sia pianificata ed eseguita correttamente. Verificare il numero e la dimensione delle tabelle di lavoro.
* Diagnosi in tempo reale: controllate i file di registro di processo e piattaforma, quindi controllate l&#39;attività del database durante la ricreazione del problema.

>[!NOTE]
>
>Per ulteriori informazioni, consulta questa sezione: [Prestazioni del database](../../production/using/database-performances.md).

## Configurazione applicazione {#application-configuration}

Di seguito è riportato un elenco degli articoli relativi alle procedure ottimali per la configurazione dell&#39;applicazione:

* Processi e memoria MTA e MTAChild: il modulo **mta** distribuisce i messaggi ai moduli figlio **master**. Ogni **nodo** prepara i messaggi prima di richiedere un&#39;autorizzazione al server delle statistiche e inviarli. Per ulteriori informazioni, fare riferimento a [page](../../installation/using/email-deliverability.md).
* Configurazione TLS: l&#39;abilitazione di TLS a livello globale non è consigliata perché può ridurre il throughput. Al contrario, le impostazioni TLS per dominio, gestite dal team di recapito, dovrebbero essere regolate in base alle esigenze. Per ulteriori informazioni, fare riferimento a [page](../../installation/using/email-deliverability.md#mx-configuration).
* DKIM: per garantire il livello di protezione del DKIM, il formato 1024b è la dimensione consigliata per le best practice di cifratura. Le chiavi DKIM inferiori non saranno considerate valide dalla maggior parte dei provider di accesso. Fare riferimento a questa [pagina](../../delivery/using/technical-recommendations.md#dkim) e a questa [nota tecnica](https://helpx.adobe.com/it/campaign/kb/domain-name-delegation.html).

## Problemi di recapito {#deliverability-issues}

Di seguito è riportato un elenco delle best practice e degli articoli relativi alla recapito:

* reputazione IP: se la reputazione dell&#39;IP non è sufficiente, le prestazioni saranno influenzate. Il modulo **Monitoraggio della realizzabilità** offre diversi strumenti per monitorare le prestazioni della piattaforma. Fare riferimento a questa [pagina](../../delivery/using/monitoring-deliverability.md).
* Riscaldamento IP: il riscaldamento dell&#39;IP viene eseguito dal team di recapito. Ciò comporta un aumento graduale del numero di e-mail attraverso nuovi IP in un periodo di poche settimane.
* Impostazione affinità IP: un&#39;impostazione errata dell&#39;affinità IP può arrestare completamente le e-mail (nome di operatore/affinità errato nella configurazione) o ridurre il throughput (numero limitato di IP nell&#39;affinità). Fare riferimento a questa [pagina](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Dimensione e-mail: la dimensione dell&#39;e-mail svolge un ruolo importante nella trasmissione. La dimensione massima consigliata per l’e-mail è 60 KB. Fare riferimento a questa [pagina](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Nel report [Trasmissione consegna](../../reporting/using/global-reports.md#delivery-throughput) controllare il numero di byte trasferiti per ora.
* Numero elevato di destinatari non validi: se è presente un numero elevato di destinatari non validi, può avere un impatto sul throughput. Il MTA continua a ripetere l&#39;invio di e-mail a destinatari non validi. Assicurarsi che il database sia ben mantenuto.
* Entità della personalizzazione: se una consegna rimane in &quot;Personalizzazione in corso&quot;, controlla il codice JavaScript utilizzato nei blocchi di personalizzazione.

>[!NOTE]
>
>Vedere anche sezione [Punti chiave di recapito](../../delivery/using/deliverability-key-points.md).
