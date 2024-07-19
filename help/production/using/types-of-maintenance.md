---
product: campaign
title: Tipi di manutenzione
description: Tipi di manutenzione
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 2%

---

# Tipi di manutenzione{#types-of-maintenance}



## Manutenzione dell’applicazione {#application-maintenance}

Adobe Campaign fornisce un flusso di lavoro integrato che consente di pianificare alcune attività di manutenzione del database: il **flusso di lavoro di pulizia del database**. Questo flusso di lavoro esegue le seguenti attività:

* la cancellazione dei dati scaduti,
* eliminazione dei record orfani e reinizializzazione dello stato per gli oggetti scaduti,
* aggiornamento delle statistiche del database.

>[!IMPORTANT]
>
>Si noti che l&#39;attività di pulizia riguarda principalmente la manutenzione a livello di applicazione, non la manutenzione a livello di RDBMS (ad eccezione dell&#39;aggiornamento delle statistiche). Tuttavia, le operazioni di manutenzione saranno richieste nel database. Anche se il flusso di lavoro di pulizia del database viene eseguito correttamente, ciò non significa che il database sia ottimizzato.

## Manutenzione tecnica {#technical-maintenance}

Il flusso di lavoro di pulizia del database non include alcuno strumento di manutenzione del database: è possibile organizzare la manutenzione. A questo scopo, puoi effettuare le seguenti operazioni:

* collaborare con l&#39;amministratore del database per impostare la manutenzione del database con strumenti di terze parti,
* utilizza il motore del flusso di lavoro di Adobe Campaign per pianificare e tenere traccia di queste attività di manutenzione.

Tali procedure di manutenzione devono essere eseguite regolarmente e devono comprendere quanto segue:

* reindicizzare le tabelle aggiornate di frequente,
* compatta/rigenera le tabelle per evitare la frammentazione.

### Pianificazione di manutenzione {#maintenance-schedule}

È necessario trovare gli slot appropriati per eseguire queste attività di manutenzione. Possono influire pesantemente sulle prestazioni del database durante l’esecuzione o addirittura bloccare l’applicazione (a causa del blocco).

Queste attività vengono in genere eseguite una volta alla settimana durante un periodo di bassa attività che non entra in conflitto con i backup, il ricaricamento dei dati o il calcolo dell’aggregazione. Alcuni sistemi molto richiesti richiedono una manutenzione più frequente.

Una manutenzione più approfondita, ad esempio la ricostruzione completa della tabella, può essere eseguita una volta al mese, preferibilmente con le applicazioni completamente arrestate in quanto il sistema è comunque inutilizzabile.

### Ricostruzione di una tabella {#rebuilding-a-table}

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
   <td> Deframmentazione in linea<br /> </td> 
   <td> La maggior parte dei motori di database fornisce metodi di deframmentazione.<br /> </td> 
   <td> È sufficiente utilizzare il metodo di deframmentazione del database. Questi metodi in genere gestiscono i problemi di integrità bloccando i dati durante la deframmentazione.<br /> </td> 
   <td> A seconda del database, questi metodi di deframmentazione possono essere forniti come opzione RDBMS (Oracle) e non rappresentano sempre il modo più efficiente per gestire le tabelle di grandi dimensioni.<br /> </td> 
  </tr> 
  <tr> 
   <td> Scarica e ripristina<br /> </td> 
   <td> Eseguire il dump della tabella in un file, eliminare la tabella nel database e ripristinare dal dump.<br /> </td> 
   <td> Questo è il modo più semplice per deframmentare una tabella. È anche l'unica soluzione quando il database è quasi pieno.<br /> </td> 
   <td> Poiché la tabella viene eliminata e ricreata, non è possibile lasciare l'applicazione online, nemmeno in modalità di sola lettura (la tabella non è disponibile durante la fase di ripristino).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplica, rinomina e rilascia<br /> </td> 
   <td> Verrà creata una copia di una tabella e dei relativi indici, quindi verrà eliminata quella esistente e la copia verrà rinominata per sostituirla.<br /> </td> 
   <td> Questo metodo è più veloce del primo approccio poiché genera meno I/O (nessuna copia come file e lettura da questo file).<br /> </td> 
   <td> Richiede il doppio dello spazio.<br /> Tutti i processi attivi che scrivono nella tabella durante il processo devono essere interrotti. Tuttavia, i processi di lettura non saranno interessati, poiché la tabella viene scambiata all’ultimo momento una volta ricreata. <br /> </td> 
  </tr> 
 </tbody> 
</table>
