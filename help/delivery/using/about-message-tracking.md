---
solution: Campaign Classic
product: campaign
title: Introduzione al tracciamento
description: Ulteriori informazioni sulle linee guida generali per il tracciamento in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 55cc09c0446e389029890e45b790bb5ec6ffdc27
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 8%

---


# Introduzione al tracciamento dei messaggi {#get-started-tracking}

Grazie alle sue funzionalità di tracciamento,  Adobe Campaign consente di monitorare i messaggi inviati e controllare il comportamento dei destinatari: apertura, clic sui collegamenti, annullamento della sottoscrizione ecc.

Queste informazioni vengono recuperate nella scheda **[!UICONTROL Tracking]** del profilo di ciascun destinatario della consegna. In questa scheda sono elencati tutti i collegamenti URL tracciati e su cui il destinatario è stato fatto clic. Si tratta dell’accumulo di tutti gli URL tracciati nelle distribuzioni ancora presenti nella schermata di consegna. L&#39;elenco può essere configurato e in genere contiene: l’URL su cui si è fatto clic, la data e l’ora del clic e il documento in cui è stato trovato l’URL. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/editing-a-profile.md#tracking-tab).

Il **dashboard di consegna** è inoltre fondamentale per monitorare le consegne e gli eventuali problemi riscontrati durante l&#39;invio dei messaggi. Per ulteriori informazioni, consultare [questa sezione](../../delivery/using/delivery-dashboard.md).

Il diagramma seguente mostra le fasi della finestra di dialogo tra l&#39;utente e i vari server.

![](assets/tracking-diagram.png)

## Configurare il tracciamento {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Principio di funzionamento**

Prima di usare il tracciamento, è necessario configurarlo per l’istanza. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#operating-principle)

**Server di tracciamento**

Per configurare il tracciamento, l’istanza deve essere dichiarata e registrata con i server di tracciamento. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#tracking-server)

**Salvataggio del tracciamento**

Una volta configurato il tracciamento e popolati gli URL, il server di tracciamento deve essere registrato. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#tracking-configuration#saving-tracking)

## Tracciamento dei messaggi {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Collegamenti tracciati**

Puoi tenere traccia della ricezione dei messaggi e dell’attivazione dei collegamenti inseriti nel contenuto del messaggio per comprendere meglio il comportamento dei destinatari. [Ulteriori informazioni](../../delivery/using/how-to-configure-tracked-links.md)

**Tracciamento URL**

Le opzioni di tracciamento possono essere configurate attivando o disattivando gli URL tracciati. [Ulteriori informazioni](../../delivery/using/personalizing-url-tracking.md)

**Personalizzazione dei collegamenti tracciati**

Le funzionalità di tracciamento dei Campaign Classic consentono di aggiungere collegamenti nelle e-mail che possono essere personalizzati e che supportano il tracciamento. [Ulteriori informazioni](https://helpx.adobe.com/campaign/kb/tracking-personnalized-links.html)

**Tracciamento dei registri**

Il flusso di lavoro tecnico di tracciamento recupera i dati di tracciamento una volta che la consegna è stata inviata e il tracciamento è attivato. Questi dati si trovano nella scheda Tracciamento della consegna. [Ulteriori informazioni](../../delivery/using/accessing-the-tracking-logs.md)

**Test del tracking**

Prima di inviare i messaggi con il tracciamento, potete verificare il tracciamento sulla pagina mirror, nei registri e nei collegamenti delle e-mail. [Ulteriori informazioni](../../delivery/using/testing-tracking.md)

## Tracciamento applicazione Web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Tracking di un’applicazione web**

È inoltre possibile monitorare e misurare le visite sulle pagine dell&#39;applicazione Web con tag di tracciamento. Questa funzionalità può essere utilizzata per tutti i tipi di applicazioni Web come moduli e sondaggi online. [Ulteriori informazioni](../../web/using/tracking-a-web-application.md)

**Rinuncia al tracking delle applicazioni web**

La rinuncia al tracciamento dell’applicazione Web consente di interrompere il tracciamento dei comportamenti Web degli utenti finali che rifiutano il tracciamento del comportamento. Potete includere la possibilità di visualizzare un banner nelle applicazioni Web o nelle pagine di destinazione per consentire agli utenti di rifiutare. [Ulteriori informazioni](../../web/using/web-application-tracking-opt-out.md)

## Tracciamento dei report {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Tracciamento delle statistiche**

Questo rapporto fornisce statistiche su aperture, clic e transazioni e consente di tenere traccia dell&#39;impatto marketing della consegna. [Ulteriori informazioni](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL e flussi di clic**

Questo rapporto mostra l&#39;elenco delle pagine visitate dopo la consegna. [Ulteriori informazioni](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Persona/persone e destinatari**

Comprendi meglio la differenza di tracciamento tra una persona/persone e un destinatario in  Adobe Campaign con questo esempio. [Ulteriori informazioni](../../reporting/using/person-people-recipients.md)

**Indicatori di tracciamento**

Questo rapporto combina gli indicatori chiave per tenere traccia del comportamento dei destinatari al momento della ricezione della consegna, come i tassi di click-through aperti e i flussi di clic. [Ulteriori informazioni](../../reporting/using/delivery-reports.md#tracking-indicators)

**Calcolo indicatore**

Le diverse tabelle forniscono l&#39;elenco degli indicatori utilizzati nei diversi rapporti e la relativa formula di calcolo a seconda del tipo di consegna. [Ulteriori informazioni](../../reporting/using/indicator-calculation.md)

## Tracciamento della risoluzione dei problemi {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

I seguenti suggerimenti per la risoluzione dei problemi aiuteranno a risolvere i problemi più comuni che si verificano quando si utilizza il tracciamento in Adobe Campaign Classic. Per una risoluzione dei problemi più avanzata, consultare [questa sezione](../../delivery/using/tracking-troubleshooting.md).

* Verificare che il processo trackinglogd sia in esecuzione

   Questo processo legge dalla memoria condivisa IIS/Web Server e scrive i registri di reindirizzamento.

   Per accedervi dalla home page, selezionate la scheda Monitoraggio nell’istanza. È inoltre possibile eseguire il comando seguente sull&#39;istanza: `<user>@<instance>:~$ nlserver pdump`

   Se il processo di monitoraggio non viene visualizzato nell&#39;elenco, avviatelo con il seguente comando nell&#39;istanza: `<user>@<instance>:~$ nlserver start trackinglogd`

* Verificare che il flusso di lavoro tecnico di tracciamento sia stato eseguito di recente.

   Potete individuare il flusso di lavoro tecnico di tracciamento nelle cartelle Amministrazione > Produzione > Flussi di lavoro tecnici.
