---
product: campaign
title: Tipi di manutenzione
description: Tipi di manutenzione
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Tipi di manutenzione{#types-of-maintenance}

![](../../assets/v7-only.svg)

## Manutenzione dell&#39;applicazione {#application-maintenance}

Adobe Campaign fornisce un flusso di lavoro integrato che consente di pianificare alcune attività di manutenzione del database: la **flusso di lavoro di pulizia del database**. Questo flusso di lavoro esegue le seguenti attività:

* eliminazione dei record scaduti,
* eliminazione dei record orfani e reinizializzazione dello stato per gli oggetti scaduti,
* aggiornamento delle statistiche del database.

>[!IMPORTANT]
>
>L&#39;attività di pulizia riguarda principalmente la manutenzione a livello di applicazione, non la manutenzione a livello di RDBMS (ad eccezione dell&#39;aggiornamento delle statistiche). Tuttavia, nel database saranno necessarie operazioni di manutenzione. Anche se il flusso di lavoro di pulizia del database viene eseguito correttamente, ciò non significa che il database sia ottimizzato.

## Manutenzione tecnica {#technical-maintenance}

Il flusso di lavoro di pulizia del database non include alcuno strumento di manutenzione del database: spetta a voi organizzare la manutenzione. A questo scopo, puoi effettuare le seguenti operazioni:

* collaborare con l&#39;amministratore del database per impostare la manutenzione del database con strumenti di terze parti,
* utilizza il motore del flusso di lavoro Adobe Campaign per pianificare e tenere traccia di queste attività di manutenzione.

Tali procedure di manutenzione devono essere eseguite su base regolare e devono comprendere quanto segue:

* reindicizzare tabelle aggiornate frequentemente,
* compattare/ricreare le tabelle per evitare la frammentazione.

### Programma di manutenzione {#maintenance-schedule}

È necessario trovare gli slot appropriati per l&#39;esecuzione di queste attività di manutenzione. Possono influire notevolmente sulle prestazioni del database durante l&#39;esecuzione o persino il blocco dell&#39;applicazione (a causa del blocco).

Queste attività vengono in genere eseguite una volta alla settimana durante un periodo di bassa attività che non è in conflitto con i backup, il ricaricamento dei dati o il calcolo aggregato. Alcuni sistemi molto richiesti richiedono una manutenzione più frequente.

Una volta al mese è possibile eseguire una manutenzione più approfondita, ad esempio la ricostruzione completa delle tabelle, preferibilmente con applicazioni completamente interrotte, poiché il sistema è comunque inutilizzabile.

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
   <td> Deframmentazione online<br /> </td> 
   <td> La maggior parte dei motori di database fornisce metodi di deframmentazione.<br /> </td> 
   <td> Utilizza semplicemente il metodo di deframmentazione del database. In genere, questi metodi si occupano dei problemi di integrità bloccando i dati durante la deframmentazione.<br /> </td> 
   <td> A seconda del database, questi metodi di deframmentazione possono essere forniti come opzione RDBMS (ad Oracle) e non sono sempre il modo più efficiente per gestire tabelle più grandi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Discesa e ripristino<br /> </td> 
   <td> Eseguire il dump della tabella in un file, eliminare la tabella nel database e ripristinarla dal dump.<br /> </td> 
   <td> Questo è il modo più semplice per deframmentare una tabella. Anche l'unica soluzione quando il database è quasi pieno.<br /> </td> 
   <td> Poiché la tabella viene eliminata e ricreata, l’applicazione non può essere lasciata online, anche in modalità di sola lettura (la tabella non è disponibile durante la fase di ripristino).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicare, rinominare e rilasciare<br /> </td> 
   <td> Crea una copia di una tabella e dei relativi indici, quindi rilascia quella esistente e rinomina la copia per sostituirla.<br /> </td> 
   <td> Questo metodo è più veloce del primo approccio in quanto genera meno IO (nessuna copia come file e lettura da questo file).<br /> </td> 
   <td> Richiede il doppio della quantità di spazio.<br /> È necessario arrestare tutti i processi attivi che scrivono alla tabella durante il processo. Tuttavia, i processi di lettura non saranno influenzati, poiché la tabella viene scambiata all’ultimo momento una volta ricostruita. <br /> </td> 
  </tr> 
 </tbody> 
</table>
