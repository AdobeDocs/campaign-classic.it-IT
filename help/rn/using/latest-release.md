---
solution: Campaign Classic
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 5b5aae1b8c19e9fed5f3172d796b0f25022b6d58
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Ultima versione{#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni apportati con l’**ultima versione di Campaign Classic Release Candidate**.

Per la versione Campaign Classic Gold Standard (ultima build GA), [fare riferimento a questa pagina](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Versione 21.1.1 - Build 9277 {#release-21-1-1-build-9277}

_22 febbraio 2021_

**Miglioramenti della sicurezza**

* Il meccanismo di autenticazione della console è stato migliorato per ottimizzare la sicurezza. (NEO-26944)
* È stato risolto un problema di sicurezza per rafforzare la protezione contro gli attacchi SSRF (Server Side Request Forgery). (NEO-28532)

**Aggiornamenti della compatibilità**

Campaign supporta ora i seguenti sistemi:

* La versione 49 dell&#39;API Salesforce ora è supportata quando si utilizza l&#39;account esterno di Salesforce CRM.

**Funzioni obsolete**

Il report **Technical Deliverability Monitoring** è ora obsoleto.

Ulteriori informazioni sono disponibili nella pagina [Funzioni obsolete e rimosse](../../rn/using/deprecated-features.md).

**Miglioramenti**

**Il servizio EFS (Email Feedback Service)** è un servizio scalabile che acquisisce direttamente i commenti dall&#39;MTA avanzato, migliorando così la precisione dei rapporti. Questa funzionalità viene rilasciata come versione beta privata e sarà disponibile progressivamente per tutti i clienti nelle versioni future.

* Vengono ora acquisite tutte le categorie di feedback per la generazione di rapporti completi e precisi.
* Il calcolo dell’indicatore Delivered è ora basato sul feedback in tempo reale dall’MTA avanzato per una maggiore precisione e reattività.
* Il servizio EFS risolve il problema dei ritardi con la generazione sincrona di rapporti sui soft bounce.

Per ulteriori informazioni consulta la [documentazione dettagliata](../../delivery/using/sending-with-enhanced-mta.md#efs).
Se sei interessato a partecipare a questa versione beta privata, compila questo [modulo](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) e ti contatteremo di nuovo.

**Altre modifiche**

* La velocità di trasferimento è stata migliorata per i registri di tracciamento di grandi dimensioni utilizzando la compressione.
* Workflow Heatmap è stato migliorato per evitare timeout durante l&#39;esecuzione di flussi di lavoro con più attività. (NEO-27423).
* È stato risolto un problema che poteva consentire la presentazione di un&#39;offerta anche se la data di fine era stata superata. Il Campaign Classic ora prende in considerazione l&#39;intera marca temporale della data di fine, anziché solo la data. (NEO-27590)
* Il collegamento Google+ è stato rimosso dal blocco di personalizzazione **Social Network Links**.
* È stato risolto un problema dopo l’implementazione di una correzione di bug nell’ultima release. È stato aggiunto un controllo al nome host durante la connessione tramite SSL/TLS, che causava la mancata riuscita delle consegne di SMS. La verifica del nome host è stata disattivata per la maggior parte dei protocolli come POP3, SMS e HTTP con proxy e la verifica del certificato per l&#39;account esterno SMS è stata migliorata con tre valori (NEO-29581). [Ulteriori informazioni](../../delivery/using/sms-protocol.md#skip-tls)

**Patch**

* È stato risolto un problema che impediva il funzionamento delle scelte rapide da tastiera Tab, Invio ed Esc nella nuova schermata di accesso.
* È stato risolto un problema di aggiornamento a causa del quale il nome di un flusso di lavoro appena creato veniva sostituito con il valore predefinito dopo il salvataggio (NEO-26106).
* È stato risolto un problema che si verificava durante l&#39;esecuzione di flussi di lavoro in cui un nuovo campo veniva aggiunto come parte di un&#39;attività **Arricchimento** prima di un&#39;attività **Consegna** utilizzando un mapping di destinazione **File esterno**: i campi indesiderati sono stati aggiunti alla mappatura di destinazione **File esterno**. (NEO-27687)
* È stato risolto un problema che causava la modifica di alcuni caratteri nel codice sorgente alla riapertura di un&#39;applicazione Web precedentemente creata e salvata. (NEO-27597)
* È stato risolto un problema che poteva verificarsi durante l&#39;aggiornamento a una build, incluso il nuovo meccanismo di firma per i collegamenti di tracciamento (da Build 19.1.4 e Campaign 20.2): quando a un evento sono stati associati più modelli, l&#39;aggiornamento potrebbe causare la selezione del modello errato durante l&#39;invio del messaggio di transazione. (NEO-28326)
* È stato risolto un problema che causava la mancata risposta dell&#39;MTA e l&#39;impossibilità di elaborare le consegne a meno che non venisse riavviato. (NEO-27455)
* È stato risolto un problema nel database MSSQL relativo alla gestione delle marche temporali durante le operazioni di caricamento in massa per una colonna del tipo di data/ora.
* È stato corretto un problema di query del flusso di lavoro quando si utilizzavano le funzioni xtk Redshift. I SubDays, SubSeconds, SubMinutes e SubHours accettano ora entrambi i tipi di timestamp di spostamento (NEO-24962).
* È stato risolto un problema che causava la visualizzazione di un messaggio di errore script durante il tentativo di visualizzare in anteprima un report con accesso anonimo. (NEO-27081)
* È stato risolto un problema che poteva ridurre l&#39;utilizzo di memoria sul server durante l&#39;analisi della distribuzione.
* È stato risolto un problema che poteva impedire il funzionamento dell&#39;istanza durante il tentativo di esecuzione di query complesse specifiche.
* È stato risolto un problema che poteva impedire l&#39;esecuzione del flusso di lavoro tecnico **Sincronizzazione delle pagine Twitter**. (NEO-28634)
* È stato risolto un problema che poteva visualizzare un messaggio di errore relativo alla funzione decryptPassword quando si tentava di pubblicare su Twitter utilizzando il modello di consegna **Tweet (twitter)**. (NEO-28216)
* È stato risolto un problema che si verificava durante l&#39;utilizzo di un&#39;attività **Javascript** per effettuare una richiesta HTTP in un flusso di lavoro. Dopo aver definito il numero di porta nel nome host, la chiamata non riesce con il seguente errore (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* È stato risolto un problema che impediva l&#39;invio di nuove consegne con la personalizzazione dei dati di destinazione.
* È stato risolto un problema che causava diversi arresti anomali nell&#39;istanza di marketing causando file di base.
* È stato risolto un problema che causava un errore nel flusso di lavoro **Tracking** con il seguente errore (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* È stato risolto un problema che si verificava durante la creazione e il salvataggio di una consegna nella scheda **Targeting &amp; Workflow** di una campagna: l&#39;anteprima avrebbe esito negativo con il seguente errore (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* È stato corretto un errore che si verificava durante la configurazione di un account esterno tra un&#39;istanza di marketing e un&#39;istanza Adobe Campaign Standard  o un&#39;istanza mid-sourcing Campaign Classic e l&#39;utilizzo dell&#39;opzione &quot;DisableFOH2=1&quot;. Quando si utilizza l&#39;opzione &quot;DisableFOH2=1&quot; nell&#39;account esterno, le connessioni non venivano chiuse correttamente e si accumulava generando il seguente errore (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* È stato corretto un errore con SMS quando si verificavano problemi di connessione tra il server e il provider. La connessione viene quindi automaticamente disattivata dall&#39;elemento secondario MTA. Adobe Campaign Classic non tenterà di connettersi a questa connessione non funzionante finché non sarà stato avviato un nuovo figlio.
