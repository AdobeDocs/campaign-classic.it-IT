---
product: campaign
title: Configurazione della rete
description: Scopri le linee guida per la comunicazione di sistema
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 1%

---

# Configurazione della rete{#network-configuration}



## Comunicazione tra processi {#communication-between-processes}

Alcuni processi dell&#39;applicazione devono comunicare con altri o accedere alla LAN e a Internet. Ciò significa che alcune porte TCP devono essere aperte per questi processi.

Utilizza la porta Apache Tomcat incorporata come priorità (8080 per impostazione predefinita) per le comunicazioni interne tra i vari server applicazioni di una piattaforma Adobe Campaign.

### Server di consegna {#delivery-server}

Per il server di consegna (**nlserver mta**), è necessario aprire le porte seguenti:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Ovunque<br /> </td> 
   <td> Traffico SMTP per trasmissione e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (dominio)<br /> </td> 
   <td> Server DNS<br /> </td> 
   <td> Query DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta predefinita)<br /> </td> 
   <td> Gateway SMS<br /> </td> 
   <td> Utilizzato per inviare traffico SMS al router SMS NetSize [opzione].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Server statistiche<br /> </td> 
   <td> Accesso al server delle statistiche.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Posta in entrata {#inbound-mail}

Per il processo di ripristino della posta in entrata (**nlserver inMail**), è necessario aprire le porte seguenti:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Server di posta interna<br /> </td> 
   <td> Traffico POP3 per raccogliere i messaggi non recapitati.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Server di posta interna<br /> </td> 
   <td> Traffico SMTP per inviare i messaggi non recapitati rimanenti che non vengono elaborati automaticamente dalle regole predefinite.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Server dell’applicazione {#application-server}

Per il server applicazioni (**nlserver web**), è necessario aprire le porte seguenti:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Ovunque<br /> </td> 
   <td> Traffico HTTP o HTTPS (incluso per l'offerta di recapito messaggi).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Quando diversi server applicazioni di una piattaforma Adobe Campaign devono comunicare tra loro, si consiglia di utilizzare la porta del server Apache Tomcat (per impostazione predefinita: 8080) anziché quella della porta HTTP del server web con cui è stata eseguita l’integrazione del modulo di reindirizzamento. Ciò significa che la porta deve essere aperta tra questi server.

### Stato della consegna SMS {#sms-delivery-status}

Per tenere traccia delle consegne SMS (**nlserver sms**), è necessario aprire la porta seguente:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta predefinita)<br /> </td> 
   <td> Gateway SMS<br /> </td> 
   <td> Esegue una query sullo stato della coda di recapito gestito dal gateway SMS NetSize [opzione].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Client avanzato {#rich-client}

Per il client avanzato Adobe Campaign (**nlclient**), è necessario aprire le porte seguenti:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Server applicazioni<br /> </td> 
   <td> Traffico SOAP (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Accesso al database {#database-access}

Tutti i componenti che utilizzano il database devono essere in grado di connettersi ad esso. Questo è il caso della maggior parte dei componenti, ad eccezione del server di reindirizzamento, che può funzionare da solo, e del thin client Win32, che utilizza HTTP (o HTTPS) solo per comunicare con il server applicazioni.

Le porte predefinite sono le seguenti:

<table> 
 <tbody> 
  <tr> 
   <td> Tipo di database<br /> </td> 
   <td> Porta (predefinita)<br /> </td> 
   <td> Destinazione<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Server database<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Accesso esterno {#external-access}

Inoltre, alcuni componenti devono essere accessibili da Internet per consentire la visualizzazione delle campagne e-mail eseguite direttamente da Adobe Campaign. Ciò significa che alcune porte devono essere aperte per i componenti.

### Server di reindirizzamento {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Posizione<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Ovunque. Ogni clic su un collegamento tracciato genera una richiesta HTTP sul server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Server web esterno {#external-web-server}

Questo server ospita moduli web, pagine mirror e così via. Le seguenti porte devono essere aperte:

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Posizione<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Ovunque. Necessario quando i moduli Web vengono gestiti direttamente dalla piattaforma Adobe Campaign o quando vengono utilizzate pagine mirror.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Server applicazioni interno (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Posizione<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Tutti i computer che eseguono thin client o rich client.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integrazione con Adobe Experience Manager {#integration-with-adobe-experience-manager}

L’integrazione tra Adobe Campaign e Adobe Experience Manager richiede l’apertura di più porte se l’installazione è &quot;on-premise&quot;. Per ulteriori informazioni sulla configurazione di questa integrazione, consulta la [documentazione dettagliata](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Descrizione<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Connessione AEM ad Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Connessione Adobe Campaign alle istanze "authoring" e "pubblicazione" dell’AEM. Le porte da aprire potrebbero essere diverse dalle porte predefinite, a seconda della configurazione AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Larghezza di banda {#bandwidth}

Un altro parametro chiave della configurazione di rete da considerare. È quasi sempre in uscita e molto richiesto durante le trasmissioni e-mail. Di seguito sono riportati alcuni esempi di configurazioni basate sulla nostra esperienza:

* 1 Mb/s per 10.000 e-mail all&#39;ora (dimensione media di 30 Kb)
* Da 8 a 10 Mb/s per 100.000 e-mail all&#39;ora (dimensione media di 30 Kb)

Se disponi di vincoli in termini di larghezza di banda, puoi pianificare l’esecuzione delle campagne durante la notte quando la domanda è più bassa.
