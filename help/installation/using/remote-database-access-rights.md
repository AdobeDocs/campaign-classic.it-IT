---
product: campaign
title: Autorizzazioni per accedere a un database esterno
description: Autorizzazioni di accesso al database esterno
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---

# Diritti di accesso al database remoto {#remote-database-access-rights}



In primo luogo, affinché l’utente possa eseguire operazioni su un database esterno tramite FDA, quest’ultimo deve disporre di un diritto denominato specifico in Adobe Campaign.

1. Seleziona la **[!UICONTROL Administration > Access Management > Named Rights]** in Adobe Campaign explorer.
1. Crea un nuovo diritto specificando l’etichetta scelta.
1. Il **[!UICONTROL Name]** il campo deve avere il seguente formato **utente:base@server**, dove :

   * **utente** corrisponde al nome dell&#39;utente nel database esterno.
   * **base** corrisponde al nome del database esterno.
   * **server** corrisponde al nome del server di database esterno.

     >[!NOTE]
     >
     >Il **:base** La parte è facoltativa in Oracle.

1. Salva l’autorizzazione denominata e collegala all’utente scelto da **[!UICONTROL Administration > Access Management > Operators]** nodo di Adobe Campaign explorer.

Quindi, per elaborare i dati contenuti in un database esterno, l’utente di Adobe Campaign deve disporre almeno dei diritti di scrittura sul database per poter creare tabelle di lavoro. Vengono eliminati automaticamente da Adobe Campaign.

In generale, sono necessari i seguenti diritti:

* **CONNECT**: connessione al database remoto,
* **LEGGI dati**: accesso in sola lettura alle tabelle contenenti i dati dei clienti,
* **LEGGI &quot;MetaData&quot;**: accesso ai cataloghi di dati sul server per ottenere la struttura della tabella,
* **CARICA**: caricamento di massa nelle tabelle di lavoro (richiesto quando si lavora su insiemi e join),
* **CREA/RILASCIA** per **TABELLA/INDICE/PROCEDURA/FUNZIONE** (solo per le tabelle di lavoro generate da Adobe Campaign),
* **SPIEGARE** (raccomandato): per monitorare le prestazioni in caso di problemi,
* **SCRIVI dati** (a seconda dello scenario di integrazione).

L&#39;amministratore del database deve fare in modo che tali diritti corrispondano a quelli specifici di ciascun motore di database. Per ulteriori informazioni, consulta la sezione seguente.

## Diritti FDA {#fda-rights}

|   | Snowflake | Redshift |  Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | UTILIZZO NEL MAGAZZINO, UTILIZZO NEL DATABASE e UTILIZZO NEI privilegi DELLO SCHEMA | Creazione di un utente collegato all’account AWS | Privilegio CREATE SESSION | autorizzazione CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI |
| **Creazione di tabelle** | Privilegio CREATE TABLE ON SCHEMA | CREA privilegio | Privilegio CREATE TABLE | Autorizzazione CREA TABELLA | CREA privilegio | CREA privilegio |
| **Creazione di indici** | N/D | CREA privilegio | Privilegio INDEX o CREATE ANY INDEX | Modifica autorizzazione | CREA privilegio | Privilegio INDEX |
| **Creazione di funzioni** | Privilegio CREATE FUNCTION ON SCHEMA | UTILIZZO ON Privilegio di linguaggio plpythonu per poter richiamare script python esterni | Privilegio CREATE PROCEDURE o CREATE ANY PROCEDURE | Autorizzazione CREATE FUNCTION | Privilegio di utilizzo | CREA privilegio DI ROUTINE |
| **Creazione di procedure** | N/D | UTILIZZO ON Privilegio di linguaggio plpythonu per poter richiamare script python esterni | Privilegio CREATE PROCEDURE o CREATE ANY PROCEDURE | autorizzazione CREA PROCEDURA | Privilegio d&#39;uso (le procedure sono funzioni) | CREA privilegio DI ROUTINE |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Proprietà dell&#39;oggetto | Possesso dell&#39;oggetto o utente avanzato | DROP ANY &lt; oggetto > privilegio | Modifica autorizzazione | Tabella: proprietà della tabella Indice: proprietà dell&#39;indice Funzione: proprietà della funzione | Privilegio DROP |
| **Monitoraggio delle esecuzioni** | Privilegio MONITOR sull&#39;oggetto richiesto | Nessun privilegio richiesto per utilizzare il comando EXPLAIN | privilegi INSERT e SELECT e privilegi necessari per eseguire l&#39;istruzione su cui si basa EXPLAIN PLAN | autorizzazione SHOWPLAN | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN | SELECT privilegio |
| **Scrittura di dati** | privilegi INSERT e/o UPDATE (a seconda dell&#39;operazione di scrittura) | Privilegi INSERT e UPDATE | privilegi INSERT e UPDATE o INSERT e UPDATE ANY TABLE | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento dei dati nelle tabelle** | CREATE STAGE ON SCHEMA, SELECT e INSERT sui privilegi della tabella di destinazione | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT | INSERIRE, AMMINISTRARE OPERAZIONI IN BLOCCO E MODIFICARE LE AUTORIZZAZIONI TABELLA | Privilegi SELECT e INSERT | Privilegio FILE |
| **Accesso ai dati client** | SELEZIONARE i privilegi di TABELLE o VISTE FUTURE | SELECT privilegio | Privilegio SELECT o SELECT ANY TABLE | SELECT permission | SELECT privilegio | SELECT privilegio |
| **Accesso ai metadati** | SELEZIONARE il privilegio SCHEMA INFORMATION_SCHEMA | SELECT privilegio | Nessun privilegio richiesto per utilizzare l&#39;istruzione DESCRIBE | autorizzazione VIEW DEFINITION | Nessun privilegio richiesto per utilizzare il comando &quot;\d tabella&quot; | SELECT privilegio |

|   | DB2 UDB | Teradata | InfiniDB | Sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | autorità CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI | Non è richiesta alcuna autorizzazione per utilizzare l’istruzione CONNECT | Nessun privilegio richiesto | privilegio CONNECT |
| **Creazione di tabelle** | Autorità CREATETAB | parola chiave CREATE TABLE o TABLE | CREA privilegio | Autorità RISORSA e autorizzazione CREATE | Privilegio TABLE | CREA privilegio |
| **Creazione di indici** | Privilegio INDEX | PAROLA CHIAVE CREATE INDEX o INDEX | Privilegio INDEX | Autorità RISORSA e autorizzazione CREATE | Privilegio INDEX | CREA privilegio |
| **Creazione di funzioni** | Autorizzazione IMPLICIT_SCHEMA o privilegio CREATE | parola chiave CREATE FUNCTION o FUNCTION | CREA privilegio DI ROUTINE | Autorità RESOURCE o autorità DBA per le funzioni Java | privilegio FUNCTION | Privilegio CREATE FUNCTION |
| **Creazione di procedure** | Autorizzazione IMPLICIT_SCHEMA o privilegio CREATE | parola chiave CREATE PROCEDURE o PROCEDURE | CREA privilegio DI ROUTINE | AUTORITÀ RISORSA | Privilegio PROCEDURE | Privilegio CREATE FUNCTION |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Privilegio DROPIN o privilegio CONTROL o proprietario dell&#39;oggetto | DROP &lt; oggetto > o parola chiave correlata all&#39;oggetto | Privilegio DROP | Proprietario dell&#39;oggetto o dell&#39;autorità DBA | Privilegio DROP | Proprietà dell&#39;oggetto |
| **Monitoraggio delle esecuzioni** | ESPLICITA autorità | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN | SELECT privilegio | Solo un amministratore di sistema può eseguire sp_showplan | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN | Nessun privilegio richiesto per utilizzare l&#39;istruzione EXPLAIN |
| **Scrittura di dati** | Privilegi INSERT e UPDATE o autorità DI ACCESSO AI DATI | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento dei dati nelle tabelle** | AUTORITÀ DI CARICAMENTO | Privilegi SELECT e INSERT per utilizzare rispettivamente le istruzioni COPY TO e COPY FROM | Privilegio FILE | Essere il proprietario della tabella o dell&#39;autorizzazione ALTER. A seconda dell&#39;opzione -gl, LOAD TABLE può essere eseguito solo se l&#39;utente dispone dell&#39;autorità DBA | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT |
| **Accesso ai dati client** | Privilegi INSERT/UPDATE o autorità DI ACCESSO AI DATI | SELECT privilegio | SELECT privilegio | SELECT permission | SELECT privilegio | SELECT privilegio |
| **Accesso ai metadati** | Nessuna autorizzazione necessaria per utilizzare l&#39;istruzione DESCRIBE | MOSTRA privilegio | SELECT privilegio | Non è richiesta alcuna autorizzazione per utilizzare l’istruzione DESCRIBE | Nessun privilegio richiesto per utilizzare il comando &quot;\d tabella&quot; | Nessun privilegio richiesto per utilizzare il comando SHOW |
