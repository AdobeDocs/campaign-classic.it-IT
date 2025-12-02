---
product: campaign
title: Autorizzazioni per accedere a un database esterno
description: Autorizzazioni di accesso al database esterno
feature: Installation, Instance Settings, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---

# Diritti di accesso al database remoto {#remote-database-access-rights}



In primo luogo, affinché l’utente possa eseguire operazioni su un database esterno tramite FDA, quest’ultimo deve disporre di un diritto denominato specifico in Adobe Campaign.

1. Selezionare il nodo **[!UICONTROL Administration > Access Management > Named Rights]** in Adobe Campaign Explorer.
1. Crea un nuovo diritto specificando l’etichetta scelta.
1. Il campo **[!UICONTROL Name]** deve avere il seguente formato: **utente:base@server**, dove:

   * **utente** corrisponde al nome dell&#39;utente nel database esterno.
   * **base** corrisponde al nome del database esterno.
   * **server** corrisponde al nome del server di database esterno.

     >[!NOTE]
     >
     >La parte **:base** è facoltativa in Oracle.

1. Salva l&#39;autorizzazione denominata e collegala all&#39;utente scelto dal nodo **[!UICONTROL Administration > Access Management > Operators]** di Adobe Campaign Explorer.

Quindi, per elaborare i dati contenuti in un database esterno, l’utente di Adobe Campaign deve disporre almeno dei diritti di scrittura sul database per poter creare tabelle di lavoro. Vengono eliminati automaticamente da Adobe Campaign.

In generale, sono necessari i seguenti diritti:

* **CONNECT**: connessione al database remoto,
* **LEGGI dati**: accesso in sola lettura alle tabelle contenenti i dati dei clienti,
* **LEGGI &#39;MetaData&#39;**: accesso ai cataloghi di dati del server per ottenere la struttura della tabella,
* **LOAD**: caricamento di massa nelle tabelle di lavoro (richiesto quando si lavora su insiemi e join),
* **CREATE/DROP** per **TABLE/INDEX/PROCEDURE/FUNCTION** (solo per le tabelle di lavoro generate da Adobe Campaign),
* **EXPLAIN** (consigliato): per monitorare le prestazioni in caso di problemi,
* **SCRIVI dati** (a seconda dello scenario di integrazione).

L&#39;amministratore del database deve fare in modo che tali diritti corrispondano a quelli specifici di ciascun motore di database. Per ulteriori informazioni, consulta la sezione seguente.

## Diritti FDA {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | UTILIZZO NEL MAGAZZINO, UTILIZZO NEL DATABASE e UTILIZZO NEI privilegi DELLO SCHEMA | Creazione di un utente collegato all’account AWS | Privilegio CREATE SESSION | Autorizzazione CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI |
| **Creazione di tabelle** | Privilegio CREATE TABLE ON SCHEMA | CREA privilegio | Privilegio CREATE TABLE | Autorizzazione CREA TABELLA | CREA privilegio | CREA privilegio |
| **Creazione degli indici** | N/D | CREA privilegio | Privilegio INDEX o CREATE ANY INDEX | Modifica autorizzazione | CREA privilegio | Privilegio INDEX |
| **Creazione di funzioni** | Privilegio CREATE FUNCTION ON SCHEMA | UTILIZZO ON Privilegio di linguaggio plpythonu per poter richiamare script python esterni | Privilegio CREATE PROCEDURE o CREATE ANY PROCEDURE | Autorizzazione CREATE FUNCTION | Privilegio di utilizzo | CREA privilegio DI ROUTINE |
| **Creazione delle procedure** | N/D | UTILIZZO ON Privilegio di linguaggio plpythonu per poter richiamare script python esterni | Privilegio CREATE PROCEDURE o CREATE ANY PROCEDURE | autorizzazione CREA PROCEDURA | Privilegio d&#39;uso (le procedure sono funzioni) | CREA privilegio DI ROUTINE |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Proprietà dell&#39;oggetto | Possesso dell&#39;oggetto o utente avanzato | DROP ANY &lt; oggetto > privilegio | Modifica autorizzazione | Tabella: proprietà della tabella Indice: proprietà dell&#39;indice Funzione: proprietà della funzione | Privilegio DROP |
| **Esecuzioni di monitoraggio** | Privilegio MONITOR sull&#39;oggetto richiesto | Nessun privilegio richiesto per utilizzare il comando EXPLAIN | privilegi INSERT e SELECT e privilegi necessari per eseguire l&#39;istruzione su cui si basa EXPLAIN PLAN | autorizzazione SHOWPLAN | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN | SELECT privilegio |
| **Scrittura dei dati** | privilegi INSERT e/o UPDATE (a seconda dell&#39;operazione di scrittura) | Privilegi INSERT e UPDATE | privilegi INSERT e UPDATE o INSERT e UPDATE ANY TABLE | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento dei dati nelle tabelle** | CREATE STAGE ON SCHEMA, SELECT e INSERT sui privilegi della tabella di destinazione | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT | INSERIRE, AMMINISTRARE OPERAZIONI IN BLOCCO E MODIFICARE LE AUTORIZZAZIONI TABELLA | Privilegi SELECT e INSERT | Privilegio FILE |
| **Accesso ai dati client** | SELEZIONARE i privilegi di TABELLE o VISTE FUTURE | SELECT privilegio | Privilegio SELECT o SELECT ANY TABLE | SELECT permission | SELECT privilegio | SELECT privilegio |
| **Accesso ai metadati** | SELEZIONARE il privilegio SCHEMA INFORMATION_SCHEMA | SELECT privilegio | Nessun privilegio richiesto per utilizzare l&#39;istruzione DESCRIBE | autorizzazione VIEW DEFINITION | Nessun privilegio richiesto per utilizzare il comando &quot;\d tabella&quot; | SELECT privilegio |

|   | Teradata | InfiniDB | Sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI | Non è richiesta alcuna autorizzazione per utilizzare l’istruzione CONNECT | Nessun privilegio richiesto | privilegio CONNECT |
| **Creazione di tabelle** | parola chiave CREATE TABLE o TABLE | CREA privilegio | Autorità RISORSA e autorizzazione CREATE | Privilegio TABLE | CREA privilegio |
| **Creazione degli indici** | PAROLA CHIAVE CREATE INDEX o INDEX | Privilegio INDEX | Autorità RISORSA e autorizzazione CREATE | Privilegio INDEX | CREA privilegio |
| **Creazione di funzioni** | parola chiave CREATE FUNCTION o FUNCTION | CREA privilegio DI ROUTINE | Autorità RESOURCE o autorità DBA per le funzioni Java | privilegio FUNCTION | Privilegio CREATE FUNCTION |
| **Creazione delle procedure** | parola chiave CREATE PROCEDURE o PROCEDURE | CREA privilegio DI ROUTINE | AUTORITÀ RISORSA | Privilegio PROCEDURE | Privilegio CREATE FUNCTION |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | DROP &lt; oggetto > o parola chiave correlata all&#39;oggetto | Privilegio DROP | Proprietario dell&#39;oggetto o dell&#39;autorità DBA | Privilegio DROP | Proprietà dell&#39;oggetto |
| **Esecuzioni di monitoraggio** | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN | SELECT privilegio | Solo un amministratore di sistema può eseguire sp_showplan | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN |
| **Scrittura dei dati** | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento dei dati nelle tabelle** | Privilegi SELECT e INSERT per utilizzare rispettivamente le istruzioni COPY TO e COPY FROM | Privilegio FILE | Essere il proprietario della tabella o dell&#39;autorizzazione ALTER. A seconda dell&#39;opzione -gl, LOAD TABLE può essere eseguito solo se l&#39;utente dispone dell&#39;autorità DBA | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT |
| **Accesso ai dati client** | SELECT privilegio | SELECT permission | SELECT privilegio | SELECT privilegio |  |
| **Accesso ai metadati** | MOSTRA privilegio | SELECT privilegio | Non è richiesta alcuna autorizzazione per utilizzare l’istruzione DESCRIBE | Nessun privilegio richiesto per utilizzare il comando &quot;\d tabella&quot; | Nessun privilegio richiesto per utilizzare il comando SHOW |
