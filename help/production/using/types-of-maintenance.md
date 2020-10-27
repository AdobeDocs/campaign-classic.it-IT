---
title: Tipi di manutenzione
seo-title: Tipi di manutenzione
description: Tipi di manutenzione
seo-description: null
page-status-flag: never-activated
uuid: 44faee3d-0549-4f63-8fdc-b24e6de47bc4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 4a436ccf-097c-43e6-9eda-492bada5512a
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---


# Tipi di manutenzione{#types-of-maintenance}

## Manutenzione dell&#39;applicazione {#application-maintenance}

 Adobe Campaign fornisce un flusso di lavoro integrato che consente di pianificare alcune attività di manutenzione del database: il flusso di lavoro **di pulizia del** database. Questo flusso di lavoro esegue le seguenti attività:

* soppressione dei documenti scaduti,
* eliminazione dei record orfani e reinizializzazione dello stato per gli oggetti scaduti,
* aggiornamento delle statistiche del database.

>[!IMPORTANT]
>
>L&#39;attività di pulizia si occupa principalmente della manutenzione del livello dell&#39;applicazione, non della manutenzione del livello RDBMS (ad eccezione dell&#39;aggiornamento statistico). Tuttavia, le operazioni di manutenzione saranno necessarie nel database. Anche se il flusso di lavoro di pulizia del database viene eseguito correttamente, ciò non significa che il database sia ottimamente sintonizzato.

## Manutenzione tecnica {#technical-maintenance}

Il flusso di lavoro di pulizia del database non include alcuno strumento di manutenzione del database: spetta a voi organizzare la manutenzione. A questo scopo, potete:

* collaborare con l&#39;amministratore del database per configurare la manutenzione del database con strumenti di terze parti,
* utilizzate il motore del flusso di lavoro Adobe Campaign  per pianificare e monitorare tali attività di manutenzione.

Tali procedure di manutenzione devono essere eseguite su base regolare e devono comprendere:

* reindicizzare tabelle aggiornate frequentemente,
* compatta/rigenera le tabelle per evitare la frammentazione.

### Programma di manutenzione {#maintenance-schedule}

È necessario trovare gli slot appropriati per eseguire queste attività di manutenzione. Possono influire notevolmente sulle prestazioni del database durante l&#39;esecuzione o persino il blocco dell&#39;applicazione (a causa del blocco).

Tali attività vengono in genere eseguite una volta alla settimana durante un periodo di attività bassa che non entra in conflitto con backup, ricaricamento dei dati o calcolo aggregato. Alcuni sistemi che sono molto richiesti richiedono una manutenzione più frequente.

Una volta al mese è possibile eseguire una manutenzione più approfondita, ad esempio una rigenerazione completa delle tabelle, preferibilmente con applicazioni completamente interrotte, poiché il sistema è comunque inutilizzabile.

### Ricreazione di una tabella {#rebuilding-a-table}

Sono disponibili diverse strategie:

<table> 
 <thead> 
  <tr> 
   <th> Operazioni </th> 
   <th> Descrizione </th> 
   <th> Vantaggi </th> 
   <th> Svantaggi </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Deframmentazione online<br /> </td> 
   <td> La maggior parte dei motori di database fornisce metodi di deframmentazione.<br /> </td> 
   <td> È sufficiente utilizzare il metodo di deframmentazione del database. Questi metodi in genere si occupano dei problemi di integrità bloccando i dati durante la deframmentazione.<br /> </td> 
   <td> A seconda del database, questi metodi di deframmentazione possono essere forniti come opzione RDBMS (Oracle) e non sono sempre il modo più efficiente per gestire tabelle più grandi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Discesa e ripristino<br /> </td> 
   <td> Eseguire il dump della tabella in un file, eliminare la tabella nel database e ripristinare dal dump.<br /> </td> 
   <td> Questo è il modo più semplice per deframmentare una tabella. Anche l'unica soluzione quando il database è quasi pieno.<br /> </td> 
   <td> Poiché la tabella viene eliminata e ricreata, l’applicazione non può essere lasciata in linea, anche in modalità di sola lettura (la tabella non è disponibile durante la fase di ripristino).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplica, rinomina e rilascia<br /> </td> 
   <td> Viene creata una copia di una tabella e dei relativi indici, quindi viene rilasciata quella esistente e rinominata la copia per sostituirla.<br /> </td> 
   <td> Questo metodo è più veloce del primo, in quanto genera meno IO (nessuna copia come file e lettura da questo file).<br /> </td> 
   <td> Richiede il doppio dello spazio.<br /> Tutti i processi attivi che scrivono alla tabella durante il processo devono essere interrotti. Tuttavia, i processi di lettura non saranno interessati, poiché la tabella viene scambiata all'ultimo momento dopo la ricostruzione. <br /> </td> 
  </tr> 
 </tbody> 
</table>

