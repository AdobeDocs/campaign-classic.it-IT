---
product: campaign
title: Autorizzazioni per l'accesso a un database esterno
description: Autorizzazioni di accesso al database esterno
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 1312f7c319c96851bc83ae21501164e2688d0dff
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 1%

---

# Diritti di accesso al database remoto {#remote-database-access-rights}

Innanzitutto, affinché l’utente possa eseguire operazioni su un database esterno tramite FDA, quest’ultimo deve disporre di un diritto specifico denominato in Adobe Campaign.

1. Seleziona il nodo **[!UICONTROL Administration > Access Management > Named Rights]** nell’explorer di Adobe Campaign.
1. Crea un nuovo diritto specificando l’etichetta selezionata.
1. Il campo **[!UICONTROL Name]** deve avere il formato seguente **utente:base@server**, dove :

   * **L’utente**  corrisponde al nome dell’utente nel database esterno.
   * **** corrisponde al nome del database esterno.
   * **** server corrisponde al nome del server di database esterno.

      >[!NOTE]
      >
      >La parte **:base** è facoltativa nell&#39;Oracle.

1. Salva il diritto denominato e collegalo all’utente scelto dal nodo **[!UICONTROL Administration > Access Management > Operators]** di Adobe Campaign Explorer.

Quindi, per elaborare i dati contenuti in un database esterno, l&#39;utente Adobe Campaign deve disporre almeno dei diritti di scrittura sul database per poter creare tabelle di lavoro. Vengono eliminate automaticamente da Adobe Campaign.

In generale, sono necessari i seguenti diritti:

* **CONNECT**: connessione al database remoto,
* **LEGGI I Dati**: accesso in sola lettura alle tabelle contenenti i dati dei clienti,
* **LEGGI &#39;MetaData&#39;**: accesso ai cataloghi di dati del server per ottenere la struttura della tabella,
* **CARICA**: carico di massa nelle tabelle di lavoro (richiesto quando si lavora su collezioni e giunti),
* **CREARE/** RILASCIARE PER  **TABLE/INDEX/PROCEDURE/FUNCTION**  (solo per tabelle di lavoro generate da Adobe Campaign),
* **EXPLAIN**  (consigliato): per il monitoraggio delle prestazioni in caso di problemi,
* **SCRIVI dati**  (a seconda dello scenario di integrazione).

L’amministratore del database deve far corrispondere questi diritti con i diritti specifici di ciascun motore di database. Per ulteriori informazioni, consulta la sezione seguente.

## Diritti FDA {#fda-rights}

|   | Snowflake | Redshift |  Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | UTILIZZO SU WAREHOUSE, UTILIZZO SU DATABASE E UTILIZZO SU privilegi SCHEMA | Creazione di un utente collegato all’account AWS | CREA privilegio SESSION | Autorizzazione CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI |
| **Creazione di tabelle** | CREA IL privilegio TABELLA SU SCHEMA | Privilegio CREATE | CREA privilegio TABELLA | Autorizzazione CREA TABELLA | Privilegio CREATE | Privilegio CREATE |
| **Creazione degli indici** | N/D | Privilegio CREATE | Privilegio INDEX o CREATE ANY INDEX | Autorizzazione ALTER | Privilegio CREATE | Privilegio INDEX |
| **Creazione di funzioni** | CREA FUNZIONE SUL privilegio SCHEMA | UTILIZZARE IL privilegio plpythonu LINGUAGE per poter chiamare script python esterni | CREA PROCEDURA o CREA UN privilegio DI PROCEDURA | Autorizzazione CREA FUNCTION | Privilegio di utilizzo | CREA privilegio ROUTINE |
| **Creazione di procedure** | N/D | UTILIZZARE IL privilegio plpythonu LINGUAGE per poter chiamare script python esterni | CREA PROCEDURA o CREA UN privilegio DI PROCEDURA | Autorizzazione CREA PROCEDURA | Privilegio di utilizzo (le procedure sono funzioni) | CREA privilegio ROUTINE |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Proprietario dell&#39;oggetto | Proprietario dell&#39;oggetto o utente avanzato | DROP ANY &lt; oggetto > privilegio | Autorizzazione ALTER | Tabella: Titolare dell&#39;indice della tabella: Titolare della funzione di indice: proprietario della funzione | Privilegio DROP |
| **Monitoraggio delle esecuzioni** | Privilegio MONITOR sull&#39;oggetto richiesto | Nessun privilegio richiesto per l&#39;utilizzo del comando EXPLAIN | Privilegio INSERT e SELECT e privilegio necessario per eseguire l&#39;istruzione su cui si basa il piano EXPLAIN | Autorizzazione SHOWPLAN | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | Privilegio SELECT |
| **Scrittura dei dati** | Privilegi INSERT e/o UPDATE (a seconda dell&#39;operazione di scrittura) | Privilegi INSERT e UPDATE | INSERIRE e AGGIORNARE o INSERIRE e AGGIORNARE I privilegi DI TABELLA | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento dei dati nelle tabelle** | CREA FASE SU SCHEMA, SELEZIONA e INSERISCI sui privilegi della tabella di destinazione | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT | INSERIRE, AMMINISTRARE LE OPERAZIONI IN BLOCCO E MODIFICARE LE AUTORIZZAZIONI DI TABELLA | Privilegi SELECT e INSERT | Privilegio FILE |
| **Accesso ai dati client** | SELEZIONARE (FUTURO) TABELLA(I) o privilegio(i) VISUALIZZAZIONE(I) | Privilegio SELECT | Privilegi SELECT o SELECT ANY TABLE | Autorizzazione SELECT | Privilegio SELECT | Privilegio SELECT |
| **Accesso ai metadati** | SELEZIONARE il privilegio SCHEMA INFORMATION_SCHEMA | Privilegio SELECT | Nessun privilegio necessario per utilizzare l&#39;istruzione DESCRIBE | Autorizzazione VIEW DEFINITION | Nessun privilegio richiesto per utilizzare il comando &quot;\d tabella&quot; | Privilegio SELECT |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ / SFONDO | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | autorità CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI | Non è richiesta alcuna autorizzazione per utilizzare l’istruzione CONNECT | Nessun privilegio richiesto | privilegio CONNECT |
| **Creazione di tabelle** | AUTORIZZAZIONE CREATETAB | CREA TABELLA o TABELLA parola chiave | Privilegio CREATE | AUTORIZZAZIONE RISORSA e autorizzazione CREATE | Privilegio TABLE | Privilegio CREATE |
| **Creazione degli indici** | Privilegio INDEX | CREARE una parola chiave INDEX o INDEX | Privilegio INDEX | AUTORIZZAZIONE RISORSA e autorizzazione CREATE | Privilegio INDEX | Privilegio CREATE |
| **Creazione di funzioni** | Autorizzazione IMPLICIT_SCHEMA o privilegio CREATEIN | CREA FUNZIONE o FUNZIONE, parola chiave | CREA privilegio ROUTINE | Autorità RISORSA o autorità DBA per le funzioni Java | Privilegio FUNCTION | CREA privilegio FUNCTION |
| **Creazione di procedure** | Autorizzazione IMPLICIT_SCHEMA o privilegio CREATEIN | CREA PROCEDURA o parola chiave PROCEDURA | CREA privilegio ROUTINE | RESPONSABILE DELLE RISORSE | privilegio PROCEDURA | CREA privilegio FUNCTION |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Privilegio DROPIN o privilegio CONTROL o proprietario dell&#39;oggetto | DROP &lt; oggetto > o parola chiave correlata all&#39;oggetto | Privilegio DROP | Proprietario dell’oggetto o dell’autorità DBA | Privilegio DROP | Proprietario dell&#39;oggetto |
| **Monitoraggio delle esecuzioni** | AUTORIZZAZIONE SPIEGATA | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | Privilegio SELECT | Solo l&#39;amministratore di sistema può eseguire sp_showplan | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN |
| **Scrittura dei dati** | Privilegi di INSERT e UPDATE o autorità DATAACCESS | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento dei dati nelle tabelle** | AUTORIZZAZIONE DI CARICO | Privilegi SELECT e INSERT per utilizzare rispettivamente le istruzioni COPY TO e COPY FROM | Privilegio FILE | Proprietario della tabella o autorizzazione ALTER. A seconda dell’opzione -gl, LOAD TABLE può essere eseguito solo se l’utente dispone dell’autorità DBA | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT |
| **Accesso ai dati client** | Privilegi INSERT/UPDATE o autorità DATAACCESS | Privilegio SELECT | Privilegio SELECT | Autorizzazione SELECT | Privilegio SELECT | Privilegio SELECT |
| **Accesso ai metadati** | Nessuna autorizzazione necessaria per utilizzare l&#39;istruzione DESCRIBE | privilegio SHOW | Privilegio SELECT | Nessuna autorizzazione necessaria per utilizzare l&#39;istruzione DESCRIBE | Nessun privilegio richiesto per utilizzare il comando &quot;\d tabella&quot; | Nessun privilegio richiesto per l&#39;utilizzo del comando SHOW |
