---
product: campaign
title: Problemi relativi a prestazioni e velocità effettiva
description: Problemi relativi a prestazioni e velocità effettiva
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 4%

---

# Problemi relativi a prestazioni e velocità effettiva{#performance-and-throughput-issues}

![](../../assets/v7-only.svg)

Prima di tutto, verifica di avere installato la build più recente. In questo modo potrai disporre delle funzioni e delle correzioni di bug più recenti.

Per ulteriori informazioni sul contenuto di ciascuna versione, consulta le [Note sulla versione](../../rn/using/latest-release.md) .

## Hardware e infrastruttura {#hardware-and-infrastructure}

Le linee guida generali sui requisiti hardware per Campaign Classic on-premise sono descritte in dettaglio in questa sezione [pagina](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

Il team di consulenza può fornire ai clienti in hosting uno strumento che consente di visualizzare facilmente lo spazio utilizzato da vari tipi di tabelle nel database e lo spazio utilizzato sul sito SFTP. Fornisce inoltre strumenti per consentire la pulizia di dati non necessari. Contatta l’ [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) se hai bisogno che questo strumento sia implementato. Di seguito sono riportati alcuni aspetti importanti da verificare utilizzando questo strumento:

* Se la dimensione dell&#39;indice è superiore alla dimensione della tabella, è necessario un vuoto.
* Controlla le tabelle che hanno il numero massimo di gonfiamenti. Se queste tabelle vengono utilizzate frequentemente, devono essere svuotate.
* Il blocco del database può causare l’interruzione dell’invio delle e-mail.

Adobe Campaign fornisce anche uno [strumento](../../production/using/monitoring-processes.md#manual-monitoring) per controllare l&#39;utilizzo della CPU e della RAM. Utilizza questo strumento e osserva indicatori specifici quali: **Memoria**, **Scambia memoria**, **Disco**, **Processi attivi**. Se i valori sono troppo elevati, puoi provare a ridurre il numero di flussi di lavoro o pianificare l’avvio dei flussi di lavoro in momenti diversi.

## Controllo del database {#database-performances}

Nella maggior parte dei casi, i problemi di prestazioni sono collegati alla manutenzione del database. Di seguito sono riportati i principali elementi da verificare:

* Configurazione: è consigliabile controllare la configurazione iniziale della piattaforma Adobe Campaign ed eseguire un controllo completo dell’hardware.
* Installazione e configurazione della piattaforma Adobe Campaign: controlla la configurazione di rete e le opzioni di recapito della piattaforma.
* Manutenzione del database: assicurarsi che l&#39;attività di pulizia del database sia operativa e che la manutenzione del database sia pianificata ed eseguita correttamente. Controllare il numero e la dimensione delle tabelle di lavoro.
* Diagnosi in tempo reale: controlla i file di log del processo e della piattaforma, quindi monitora l&#39;attività del database durante la ricreazione del problema.

>[!NOTE]
>
>Per ulteriori informazioni, consulta questa sezione: [Prestazioni del database](../../production/using/database-performances.md).

## Configurazione dell&#39;applicazione {#application-configuration}

Elenco degli articoli relativi alle best practice per la configurazione dell’applicazione:

* MTA e MTAChild processi e memoria: il modulo **mta** distribuisce i messaggi ai relativi moduli figlio **mtachild**. Ogni **elemento secondario** prepara i messaggi prima di richiedere un&#39;autorizzazione dal server di statistiche e di inviarli. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/email-deliverability.md) .
* Configurazione di TLS: l’abilitazione di TLS a livello globale non è consigliata perché può ridurre il throughput. Invece, le impostazioni TLS per dominio, gestite dal team di recapito messaggi, devono essere regolate in base alle esigenze. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/email-deliverability.md#mx-configuration) .
* DKIM: per garantire il livello di sicurezza del DKIM, la dimensione di crittografia 1024b è la best practice consigliata. Le chiavi DKIM inferiori non saranno considerate valide dalla maggior parte dei provider di accesso. Consulta [questa pagina](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

## Problemi di recapito messaggi {#deliverability-issues}

Elenco delle best practice e degli articoli relativi al recapito messaggi:

* reputazione IP: se la reputazione dell&#39;IP non è sufficientemente buona, le prestazioni risulteranno compromesse. Il modulo **Monitoraggio recapito messaggi** offre vari strumenti per tenere traccia delle prestazioni di recapito messaggi della piattaforma. Fai riferimento a questa [pagina](../../delivery/using/monitoring-deliverability.md).
* Riscaldamento IP: il team di recapito esegue il riscaldamento dell’IP. Ciò comporta un graduale aumento del numero di e-mail attraverso nuovi IP in un periodo di alcune settimane.
* Impostazione dell’affinità IP: una configurazione errata dell’affinità IP può arrestare completamente le e-mail (nome di operatore/affinità errato nella configurazione) o ridurre il throughput (numero limitato di IP nell’affinità). Fai riferimento a questa [pagina](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Dimensione e-mail: la dimensione dell’e-mail svolge un ruolo importante nella velocità effettiva. La dimensione massima consigliata dell’e-mail è 60 KB. Fai riferimento a questa [pagina](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Nel rapporto [Velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput) controlla il numero di byte trasferiti per ora.
* Numero elevato di destinatari non validi: se è presente un numero elevato di destinatari non validi, può influire sul throughput. L’MTA continua a ripetere l’invio di e-mail a destinatari non validi. Assicurati che il database sia ben mantenuto.
* Quantità di personalizzazione: se una consegna rimane in &quot;Personalizzazione in corso&quot;, controlla il JavaScript utilizzato nei blocchi di personalizzazione.

>[!NOTE]
>
>Vedi anche la sezione [Recapito messaggi](../../delivery/using/about-deliverability.md) . Per informazioni più approfondite sul recapito messaggi, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).
