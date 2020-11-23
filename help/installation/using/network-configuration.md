---
solution: Campaign Classic
product: campaign
title: Configurazione di rete
description: Informazioni sulle linee guida per la comunicazione del sistema
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---


# Configurazione di rete{#network-configuration}

## Comunicazione tra i processi {#communication-between-processes}

Alcuni processi dell&#39;applicazione devono comunicare con altri o accedere alla LAN e a Internet. Ciò significa che alcune porte TCP devono essere aperte per questi processi.

Utilizzate la porta Apache Tomcat incorporata come priorità (per impostazione predefinita 8080) per le comunicazioni interne tra i vari server applicazioni di una piattaforma Adobe Campaign .

### Server di consegna {#delivery-server}

Per il server di consegna (**nlserver mta**), devono essere aperte le seguenti porte:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> Traffico SMTP per la trasmissione di posta elettronica.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (dominio)<br /> </td> 
   <td> Server DNS<br /> </td> 
   <td> Query DNS.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta predefinita)<br /> </td> 
   <td> gateway SMS<br /> </td> 
   <td> Utilizzato per inviare il traffico SMS al router NetSize SMS [opzione].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Server di statistiche<br /> </td> 
   <td> Accesso al server di statistiche.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Posta in arrivo {#inbound-mail}

Per il processo di recupero della posta in entrata (**nlserver inMail**), devono essere aperte le seguenti porte:

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
   <td> Traffico POP3 per recuperare i messaggi di rimbalzo.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Server di posta interna<br /> </td> 
   <td> Traffico SMTP per inviare i messaggi di rimbalzo rimanenti che non vengono elaborati automaticamente dalle regole predefinite.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Server dell’applicazione {#application-server}

Per il server applicazione (**nlserver Web**), devono essere aperte le seguenti porte:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> Traffico HTTP o HTTPS (incluso per l'offerta di recapito).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Quando diversi server applicazioni di una piattaforma Adobe Campaign  devono comunicare tra loro, si consiglia di utilizzare la porta del server Apache Tomcat (per impostazione predefinita: 8080) invece di quella della porta HTTP del server Web con cui è stata eseguita l&#39;integrazione del modulo di reindirizzamento. Ciò significa che la porta deve essere aperta tra questi server.

### Stato consegna SMS {#sms-delivery-status}

Per tenere traccia delle consegne SMS (**nlserver sms**), è necessario aprire la seguente porta:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (porta predefinita)<br /> </td> 
   <td> gateway SMS<br /> </td> 
   <td> Interroga lo stato della coda di consegna gestita dal gateway NetSize SMS [opzione].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Client avanzato {#rich-client}

Per il client Adobe Campaign avanzato  (**nlclient**), devono essere aperte le seguenti porte:

<table> 
 <tbody> 
  <tr> 
   <td> Porte<br /> </td> 
   <td> Destinazione<br /> </td> 
   <td> Commenti<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Server dell’applicazione<br /> </td> 
   <td> Traffico SOAP (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Accesso al database {#database-access}

Tutti i componenti che utilizzano il database devono essere in grado di connettersi ad esso. Questo è il caso della maggior parte dei componenti, ad eccezione del server di reindirizzamento, che può funzionare da solo, e del client Win32 sottile, che utilizza HTTP (o HTTPS) solo per comunicare con il server dell&#39;applicazione.

Le porte predefinite sono le seguenti:

<table> 
 <tbody> 
  <tr> 
   <td> Tipo di database<br /> </td> 
   <td> Porta (predefinito)<br /> </td> 
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
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Accesso esterno {#external-access}

Inoltre, alcuni componenti devono essere accessibili da Internet pubblico in modo da poter visualizzare le campagne e-mail eseguite direttamente da  Adobe Campaign. Ciò significa che alcune porte devono essere aperte per i componenti.

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

### Server Web esterno {#external-web-server}

Questo server ospita moduli Web, pagine mirror, ecc. Devono essere aperte le seguenti porte:

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Posizione<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Ovunque. Necessario quando i moduli Web vengono gestiti direttamente dalla piattaforma Adobe Campaign  o quando vengono utilizzate pagine mirror.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Server applicazione interno (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Posizione<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Tutti i computer che eseguono il client sottile o il client avanzato.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integrazione con Adobe Experience Manager {#integration-with-adobe-experience-manager}

L&#39;integrazione tra  Adobe Campaign e Adobe Experience Manager richiede l&#39;apertura di diverse porte se l&#39;installazione è &quot;in sede&quot;. Per ulteriori informazioni sulla configurazione di questa integrazione, consulta la documentazione [](../../integrations/using/about-adobe-experience-manager.md)dettagliata.

<table> 
 <tbody> 
  <tr> 
   <td> Porta di ascolto<br /> </td> 
   <td> Descrizione<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Connessione AEM a  Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td>  connessione Adobe Campaign a AEM istanze "authoring" e "pubblicazione". Le porte da aprire possono essere diverse dalle porte predefinite, a seconda della configurazione AEM.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Larghezza di banda {#bandwidth}

Un altro parametro chiave della configurazione di rete da tenere in considerazione. È quasi sempre in uscita e molto richiesto durante le trasmissioni di posta elettronica. Di seguito sono riportati alcuni esempi di configurazioni basate sulla nostra esperienza:

* 1 Mb/s per 10.000 e-mail all&#39;ora (dimensione media di 30 Kb)
* Da 8 a 10 Mb/s per 100.000 e-mail all&#39;ora (dimensione media di 30 Kb)

In presenza di vincoli in termini di larghezza di banda, è possibile pianificare l&#39;esecuzione delle campagne durante la notte quando la domanda è inferiore.
