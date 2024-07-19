---
product: campaign
title: Problemi relativi a prestazioni e velocità effettiva
description: Problemi relativi a prestazioni e velocità effettiva
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 6803b6628313db9108a191fd143dac68ee799149
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 2%

---

# Problemi relativi a prestazioni e velocità effettiva{#performance-and-throughput-issues}

Prima di tutto, devi verificare di aver installato la build più recente. In questo modo potrai disporre delle funzioni e delle correzioni di bug più recenti.

Per ulteriori informazioni sul contenuto di ciascuna versione, consulta le [Note sulla versione](../../rn/using/latest-release.md).

## Hardware e infrastruttura {#hardware-and-infrastructure}

Le linee guida generali sui requisiti hardware per on-premise Campaign Classic sono descritte in dettaglio in questa [pagina](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

Il team di consulenza può fornire ai clienti in hosting uno strumento che consente di visualizzare facilmente la quantità di spazio utilizzato dai vari tipi di tabelle nel database e lo spazio utilizzato sul sito SFTP. Fornisce inoltre strumenti che consentono di eliminare i dati non necessari. Se hai bisogno che questo strumento sia implementato, contatta [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Di seguito sono riportati alcuni aspetti importanti da verificare con questo strumento:

* Se la dimensione dell&#39;indice è maggiore della dimensione della tabella, è necessario un vuoto.
* Controlla le tabelle che hanno il gonfiore massimo. Se queste tabelle vengono utilizzate frequentemente, è necessario aspirarle.
* Il blocco del database può causare l’interruzione dell’invio delle e-mail.

Adobe Campaign fornisce anche uno [strumento](../../production/using/monitoring-processes.md#manual-monitoring) per verificare l&#39;utilizzo della CPU e della RAM. Utilizzare questo strumento e controllare indicatori specifici quali: **Memoria**, **Scambia memoria**, **Disco**, **Processi attivi**. Se i valori sono troppo elevati, puoi provare a ridurre il numero di flussi di lavoro o pianificare i flussi di lavoro in modo che inizino in momenti diversi.

## Controllo del database {#database-performances}

Nella maggior parte dei casi, i problemi di prestazioni sono collegati alla manutenzione del database. Di seguito sono riportati gli elementi principali da verificare:

* Configurazione: è consigliabile verificare la configurazione iniziale della piattaforma Adobe Campaign ed eseguire una verifica hardware completa.
* Installazione e configurazione della piattaforma Adobe Campaign: controlla la configurazione di rete e le opzioni di recapito della piattaforma.
* Manutenzione del database: verificare che l&#39;attività di pulizia del database sia operativa e che la manutenzione del database sia stata pianificata ed eseguita correttamente. Controllare il numero e le dimensioni delle tabelle di lavoro.
* Diagnosi in tempo reale: controlla i file di registro del processo e della piattaforma, quindi monitora l’attività del database durante la ricreazione del problema.

>[!NOTE]
>
>Per ulteriori informazioni, vedere questa sezione: [Prestazioni del database](../../production/using/database-performances.md).

## Configurazione dell’applicazione {#application-configuration}

Di seguito è riportato un elenco di articoli relativi alle best practice per la configurazione delle applicazioni:

* MTA e MTAChild elaborano e memorizzano: il modulo **mta** distribuisce messaggi ai relativi **mtachild** moduli secondari. Ogni **mtachild** prepara i messaggi prima di richiedere un&#39;autorizzazione al server delle statistiche e inviarli. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/email-deliverability.md).
* Configurazione TLS: si sconsiglia di abilitare TLS a livello globale perché può ridurre la velocità effettiva. È invece necessario ottimizzare le impostazioni TLS per dominio, gestite dal team di recapito messaggi, in base alle esigenze. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/email-deliverability.md#mx-configuration).

  >[!NOTE]
  >
  >Il team di recapito messaggi si basa sul contratto e i clienti devono contattare il proprio rappresentante di Adobe per informazioni relative al progetto di recapito messaggi.

* DKIM: per garantire il livello di sicurezza di DKIM, 1024b è la dimensione di crittografia consigliata come best practice. Le chiavi DKIM inferiori non saranno considerate valide dalla maggior parte dei fornitori di accesso. Consulta [questa pagina](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

## Problemi di recapito messaggi {#deliverability-issues}

Di seguito è riportato un elenco di best practice e articoli relativi al recapito messaggi:

* Reputazione IP: se la reputazione IP non è sufficientemente buona, si verifica un impatto sulle prestazioni. Il modulo **Monitoraggio del recapito messaggi** offre diversi strumenti per monitorare le prestazioni del recapito messaggi della piattaforma. Fai riferimento a questa [pagina](../../delivery/using/monitoring-deliverability.md).
* Riscaldamento IP: il riscaldamento IP viene eseguito dal team di recapito messaggi. Ciò comporta un graduale aumento del numero di e-mail tramite nuovi IP nell’arco di alcune settimane.

  >[!NOTE]
  >
  >Il team di recapito messaggi si basa sul contratto e i clienti devono contattare il proprio rappresentante di Adobe per informazioni relative al progetto di recapito messaggi.

* Impostazione affinità IP: una configurazione di affinità IP errata può interrompere completamente le e-mail (nome di operatore/affinità non corretto nella configurazione) o ridurre la velocità effettiva (numero ridotto di IP nell’affinità). Fai riferimento a questa [pagina](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* Dimensione dell’e-mail: la dimensione dell’e-mail svolge un ruolo importante nella velocità effettiva. La dimensione massima consigliata per l’e-mail è 60 KB. Fai riferimento a questa [pagina](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Nel report [Velocità effettiva di consegna](../../reporting/using/global-reports.md#delivery-throughput), controllare il numero di byte trasferiti per ora.
* Numero elevato di destinatari non validi: quando il numero di destinatari non validi è elevato, può influire sulla velocità effettiva. L’MTA continua a tentare di inviare e-mail a destinatari non validi. Assicurarsi che il database sia in buono stato di manutenzione.
* Quantità di personalizzazione: se una consegna rimane in &quot;Personalization in progress&quot;, controlla il JavaScript utilizzato nei blocchi di personalizzazione.

>[!NOTE]
>
>Consulta anche la sezione [Recapito messaggi](../../delivery/using/about-deliverability.md). Per informazioni più approfondite sul recapito messaggi, consulta l&#39;[Adobe di guida alle best practice per il recapito messaggi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).
