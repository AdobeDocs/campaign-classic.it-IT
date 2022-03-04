---
product: campaign
title: Guida introduttiva al tracciamento
description: Ulteriori informazioni sulle linee guida generali per il tracciamento in Adobe Campaign Classic
feature: Monitoring, Email
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 9%

---

# Guida introduttiva al tracciamento dei messaggi {#get-started-tracking}

![](../../assets/common.svg)

Grazie alle sue funzionalità di tracciamento, Adobe Campaign ti consente di monitorare i messaggi inviati e controllare il comportamento dei destinatari: apertura, clic sui collegamenti, annullamento dell’abbonamento, ecc.

Queste informazioni vengono recuperate nella **[!UICONTROL Tracking]** scheda del profilo di ciascun destinatario della consegna. Questa scheda presenta tutti i collegamenti URL tracciati e su cui il destinatario è stato selezionato dall’elenco. Si tratta dell’accumulo di tutti gli URL tracciati nelle consegne ancora presenti nella schermata di consegna. L’elenco può essere configurato e in genere contiene: l’URL su cui hai fatto clic, la data e l’ora del clic e il documento in cui è stato trovato l’URL. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/editing-a-profile.md#tracking-tab).

La **dashboard di consegna** è inoltre fondamentale per monitorare le consegne e gli eventuali problemi riscontrati durante l’invio dei messaggi. Per ulteriori informazioni, consulta [questa sezione](delivery-dashboard.md).

Il diagramma seguente mostra le fasi della finestra di dialogo tra l’utente e i vari server.

![](assets/tracking-diagram.png)

## Configurare il tracciamento {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Principio di funzionamento**

Prima di usare il tracciamento, devi prima configurarlo per la tua istanza. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#operating-principle)

**Server di tracciamento**

Per configurare il tracciamento, l’istanza deve essere dichiarata e registrata con i server di tracciamento. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#tracking-server)

**Salvataggio del tracciamento**

Una volta configurato il tracciamento e popolati gli URL, il server di tracciamento deve essere registrato. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#saving-tracking)

## Tracciamento dei messaggi {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Collegamenti tracciati**

Puoi tenere traccia della ricezione dei messaggi e dell’attivazione dei collegamenti inseriti nel contenuto del messaggio per comprendere meglio il comportamento dei destinatari. [Ulteriori informazioni](how-to-configure-tracked-links.md)

**Tracciamento URL**

Le opzioni di tracciamento possono essere configurate attivando o disattivando gli URL tracciati. [Ulteriori informazioni](personalizing-url-tracking.md)

**Personalizzazione dei collegamenti tracciati**

Le funzionalità di tracciamento di Campaign Classic ti consentono di aggiungere collegamenti nelle e-mail che possono essere personalizzati e che supportano il tracciamento. [Ulteriori informazioni](tracking-personalized-links.md)

**Registri di tracciamento**

Il flusso di lavoro tecnico di tracciamento recupera i dati di tracciamento dopo l’invio della consegna e l’attivazione del tracciamento. Questi dati si trovano nella scheda Tracking della consegna. [Ulteriori informazioni](accessing-the-tracking-logs.md)

**Test del tracking**

Prima di inviare i messaggi con il tracciamento, puoi testare il tracciamento sulla pagina speculare, i registri e i collegamenti e-mail. [Ulteriori informazioni](testing-tracking.md)

## Tracciamento delle applicazioni web {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Tracking di un’applicazione web**

È inoltre possibile tenere traccia e misurare le visite sulle pagine delle applicazioni Web con tag di tracciamento. Questa funzionalità può essere utilizzata per tutti i tipi di applicazioni Web, ad esempio i moduli e le pagine di destinazione. [Ulteriori informazioni](../../web/using/tracking-a-web-application.md)

**Rinuncia al tracking delle applicazioni web**

La rinuncia al tracciamento delle applicazioni web consente di interrompere il tracciamento dei comportamenti web degli utenti finali che rinunciano al tracciamento dei comportamenti. Puoi includere la possibilità di visualizzare un banner nelle applicazioni web o nelle pagine di destinazione per consentire agli utenti di rinunciare. [Ulteriori informazioni](../../web/using/web-application-tracking-opt-out.md)

## Tracking dei report {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Tracking delle statistiche**

Questo rapporto fornisce statistiche su aperture, clic e transazioni e consente di tenere traccia dell’impatto di marketing della consegna. [Ulteriori informazioni](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL e flussi di clic**

Questo rapporto mostra l’elenco delle pagine visitate dopo una consegna. [Ulteriori informazioni](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Persona/persone e destinatari**

Con questo esempio è meglio comprendere la differenza di tracciamento tra una persona/persone e un destinatario in Adobe Campaign. [Ulteriori informazioni](../../reporting/using/person-people-recipients.md)

**Indicatori di tracciamento**

Questo rapporto combina gli indicatori chiave per il tracciamento del comportamento dei destinatari alla ricezione della consegna, ad esempio tassi di click-through aperti e flussi di clic. [Ulteriori informazioni](../../reporting/using/delivery-reports.md#tracking-indicators)

**Calcolo indicatore**

Le diverse tabelle ti forniscono l’elenco degli indicatori utilizzati nei diversi rapporti e la relativa formula di calcolo a seconda del tipo di consegna. [Ulteriori informazioni](../../reporting/using/indicator-calculation.md)

## Risoluzione dei problemi di tracciamento {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

I seguenti suggerimenti per la risoluzione dei problemi consentono di risolvere i problemi più comuni che si verificano durante l’utilizzo del tracciamento in Adobe Campaign Classic. Per una risoluzione dei problemi più avanzata, consulta [questa sezione](tracking-troubleshooting.md).

* Verifica che il processo trackinglogd sia in esecuzione

   Questo processo legge dalla memoria condivisa IIS/Web Server e scrive i registri di reindirizzamento.

   Puoi accedervi dalla home page selezionando la scheda Monitoraggio nella tua istanza. Puoi anche eseguire il seguente comando sull&#39;istanza: `<user>@<instance>:~$ nlserver pdump`

   Se il processo trackinglogd non viene visualizzato nell&#39;elenco, avvialo con il seguente comando sull&#39;istanza: `<user>@<instance>:~$ nlserver start trackinglogd`

* Verifica che il flusso di lavoro tecnico di tracciamento sia stato eseguito di recente.

   Puoi trovare il flusso di lavoro tecnico Tracking nelle cartelle Administration > Production > Technical workflow .
