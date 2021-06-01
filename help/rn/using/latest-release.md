---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic
feature: Panoramica
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 100%

---

# Ultima versione{#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign Classic Release Candidate**.

>[!NOTE]
>
>Le build di Campaign **General Availability (GA)** sono: [[!DNL Gold Standard] 11](../../rn/using/gold-standard.md#gs-11) e [Campaign 20.2.5](../../rn/using/release--20-2.md).

## ![](assets/do-not-localize/blue_2.png) Versione 21.1.2 - Build 9282 {#release-21-1-2-build-9282}

_15 aprile 2021_

* La gestione delle password è stata migliorata per potenziare la sicurezza.
* È stato risolto un problema che poteva causare arresti anomali dell’MTA.

## ![](assets/do-not-localize/red_2.png) Versione 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_22 febbraio 2021_

**Miglioramenti della sicurezza**

* Il meccanismo di autenticazione della console è stato migliorato per ottimizzare la sicurezza. (NEO-26944)
* È stato risolto un problema di sicurezza per rafforzare la protezione contro attacchi SSRF (Server Side Request Forgery). (NEO-28532)

**Aggiornamenti della compatibilità**

Campaign supporta ora i seguenti sistemi:

* L’utilizzo di un account Salesforce CRM esterno ora supporta la versione 49 delle API di Salesforce.

**Funzioni obsolete**

Il report **Technical Deliverability Monitoring** è ora obsoleto.

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md).

**Miglioramenti**

**Il servizio di feedback delle e-mail (EFS, Email Feedback Service)** è un servizio scalabile che acquisisce direttamente i commenti dall’MTA (Mail Transfer Agent) avanzato, migliorando così la precisione della generazione di rapporti. Questa funzionalità viene rilasciata come versione beta privata e sarà disponibile progressivamente per tutti i clienti nelle versioni future.

* Vengono ora acquisite tutte le categorie di feedback per la generazione di rapporti completi e precisi.
* Il calcolo dell’indicatore Delivered è ora basato sul feedback in tempo reale dall’MTA avanzato per una maggiore precisione e reattività.
* Il servizio EFS risolve il problema dei ritardi nella generazione sincrona di rapporti sui soft bounce.

Per ulteriori informazioni consulta la [documentazione dettagliata](../../delivery/using/sending-with-enhanced-mta.md#efs).
Per partecipare alla versione beta privata, compila questo [modulo](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e ti contatteremo.

**Altre modifiche**

* Utilizzando la compressione è stata migliorata la velocità di trasferimento per i registri di tracciamento di grandi dimensioni.
* La funzione Workflow Heatmap è stata migliorata per evitare timeout durante l’esecuzione di flussi di lavoro con più attività. (NEO-27423).
* È stato risolto un problema a causa del quale un’offerta poteva essere presentata anche dopo la data di fine. Campaign Classic ora prende in considerazione l’intera marca temporale della data di fine, anziché solo la data. (NEO-27590)
* Il collegamento Google+ è stato rimosso dal blocco di personalizzazione dei **collegamenti per condivisione social network**.
* È stato risolto un problema in seguito all’implementazione di una correzione di bug nell’ultima release. È stato aggiunto un controllo al nome host durante la connessione tramite SSL/TLS, che causava la mancata riuscita delle consegne di SMS. La verifica del nome host è stata disattivata per la maggior parte dei protocolli come POP3, SMS e HTTP con proxy e la verifica del certificato per l’account SMS esterno è stata migliorata con tre valori (NEO-29581). [Ulteriori informazioni](../../delivery/using/sms-protocol.md#skip-tls)

**Patch**

* È stato risolto un problema che impediva il funzionamento delle scelte rapide da tastiera Tab, Invio ed Esc nella nuova schermata di accesso.
* È stato risolto un problema di aggiornamento a causa del quale il nome di un flusso di lavoro appena creato veniva sostituito con il valore predefinito dopo il salvataggio (NEO-26106).
* È stato risolto un problema che si verificava durante l’esecuzione di flussi di lavoro in cui un nuovo campo veniva aggiunto come parte di un’attività **Enrichment** (Arricchimento) prima di un’attività **Delivery** (Consegna) utilizzando una mappatura di destinazione tramite **file esterno**: dei campi indesiderati venivano aggiunti alla mappatura di destinazione tramite **file esterno**. (NEO-27687)
* È stato risolto un problema che causava la modifica di alcuni caratteri nel codice sorgente alla riapertura di un’applicazione web creata e salvata in precedenza. (NEO-27597)
* È stato risolto un problema che poteva verificarsi durante l’aggiornamento a una build contenente il nuovo meccanismo di firma per il tracciamento dei collegamenti (da Build 19.1.4 e Campaign 20.2): se a un evento erano associati più modelli, l’aggiornamento poteva causare la selezione del modello errato durante l’invio del messaggio transazionale. (NEO-28326)
* È stato risolto un problema che causava la mancata risposta dell’MTA e l’impossibilità di elaborare le consegne, a meno che non venisse riavviato. (NEO-27455)
* È stato risolto un problema nel database MSSQL relativo alla gestione della marca temporale durante le operazioni di caricamento in massa per una colonna del tipo datetime.
* È stato corretto un problema di query del flusso di lavoro che si verificava con l’utilizzo delle funzioni xtk Redshift. SubDays, SubSeconds, SubMinutes e SubHours accettano ora entrambi i tipi di marca temporale Redshift (NEO-24962).
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore script durante il tentativo di visualizzare in anteprima un rapporto con accesso anonimo. (NEO-27081)
* È stato risolto un problema che poteva ridurre l’utilizzo di memoria sul server durante l’analisi della consegna.
* È stato risolto un problema che poteva impedire il funzionamento dell’istanza durante il tentativo di eseguire specifiche query complesse.
* È stato risolto un problema che poteva impedire l’esecuzione del flusso di lavoro tecnico per la **sincronizzazione delle pagine Twitter**. (NEO-28634)
* È stato risolto un problema che poteva mostrare un messaggio di errore relativo alla funzione decryptPassword quando si tentava di pubblicare su Twitter utilizzando il modello di consegna **Tweet (twitter)**. (NEO-28216)
* È stato risolto un problema che si verificava durante l’utilizzo di un’attività **JavaScript** per effettuare una richiesta HTTP in un flusso di lavoro. Dopo aver definito il numero di porta nel nome host, la chiamata non riusciva e veniva visualizzato il seguente errore (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* È stato risolto un problema che impediva l’invio di nuove consegne con la personalizzazione dei dati di targeting (NEO-30323).
* È stato risolto un problema che causava diversi arresti anomali nell’istanza di marketing causando core file.
* È stato risolto un problema a causa del quale il flusso di lavoro di **tracciamento** non riusciva e veniva visualizzato il seguente errore (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* È stato risolto un problema che si verificava durante la creazione e il salvataggio di una consegna nella scheda **Targeting &amp; Workflow** di una campagna: l’anteprima non riusciva e veniva visualizzato il seguente errore (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* È stato corretto un errore che si verificava durante la configurazione di un account esterno tra un’istanza di marketing e un’istanza Adobe Campaign Standard o un’istanza midsourcing Campaign Classic e l’utilizzo dell’opzione “DisableFOH2=1”. Con l’utilizzo dell’opzione “DisableFOH2=1” nell’account esterno, le connessioni non venivano chiuse correttamente e si accumulavano, generando il seguente errore (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* È stato corretto un errore relativo alla funzione SMS che si verificava in caso di problemi di connessione tra il server e il provider. La connessione veniva quindi automaticamente disattivata dall’elemento secondario MTA. Adobe Campaign Classic non tentava il collegamento a questa connessione non funzionante finché non fosse stato avviato un nuovo elemento secondario.
