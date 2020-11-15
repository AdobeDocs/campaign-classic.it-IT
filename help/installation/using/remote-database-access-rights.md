---
title: Autorizzazioni per l'accesso a un database esterno
description: Autorizzazioni di accesso al database esterno
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 1%

---


# Diritti di accesso al database remoto {#remote-database-access-rights}

In primo luogo, affinché l&#39;utente possa eseguire operazioni su un database esterno tramite FDA, quest&#39;ultimo deve avere un diritto specifico denominato in  Adobe Campaign.

1. Selezionate il **[!UICONTROL Administration > Access Management > Named Rights]** nodo in  Adobe Campaign Explorer.
1. Crea un nuovo diritto specificando l&#39;etichetta scelta.
1. Il **[!UICONTROL Name]** campo deve avere il seguente formato: **utente:base@server**, dove:

   * **l&#39;utente** corrisponde al nome dell&#39;utente nel database esterno.
   * **base** corrisponde al nome del database esterno.
   * **server** corrisponde al nome del server del database esterno.

      >[!NOTE]
      >
      >La parte **:base** è facoltativa in Oracle.

1. Salvate il nome a destra e collegatelo all&#39;utente scelto dal **[!UICONTROL Administration > Access Management > Operators]** nodo di Adobe Campaign Explorer .

Quindi, per elaborare i dati contenuti in un database esterno, l&#39;utente Adobe Campaign  deve disporre almeno dei diritti di scrittura sul database per poter creare tabelle di lavoro. Questi vengono eliminati automaticamente da  Adobe Campaign.

In generale, sono necessari i seguenti diritti:

* **CONNECT**: connessione al database remoto,
* **LEGGI dati**: accesso in sola lettura alle tabelle contenenti i dati dei clienti,
* **LEGGI &#39;MetaData&#39;**: accesso ai cataloghi di dati del server per ottenere la struttura della tabella,
* **CARICA**: carico di massa nelle tabelle di lavoro (richiesto quando si lavora su raccolte e join),
* **CREA/RILASCIA** per **TABELLA/INDICE/PROCEDURA/FUNZIONE** (solo per tabelle di lavoro generate da  Adobe Campaign),
* **EXPLAIN** (consigliato): per monitorare le prestazioni in caso di problemi,
* **SCRIVI dati** (a seconda dello scenario di integrazione).

L&#39;amministratore del database deve far corrispondere questi diritti ai diritti specifici di ciascun motore di database. Per ulteriori informazioni, consulta la sezione seguente.

## Diritti FDA {#fda-rights}

|   | Snowflake  | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | UTILIZZO IN MAGAZZINO, UTILIZZO SUL DATABASE E UTILIZZO SUI privilegi DELLO SCHEMA | Creazione di un utente collegato all&#39;account AWS | CREA privilegio SESSION | Autorizzazione CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI |
| **Creazione di tabelle** | CREA IL privilegio TABELLA SU SCHEMA | CREA privilegio | CREATE TABLE, privilegio | CREA autorizzazione TABELLA | CREA privilegio | CREA privilegio |
| **Creazione di indici** | N/D | CREA privilegio | Privilegi INDEX o CREATE ANY INDEX | Autorizzazione ALTER | CREA privilegio | Privilegio INDEX |
| **Creazione di funzioni** | CREA FUNZIONE SUL privilegio SCHEMA | USAGE ON LANGUAGE plpythonu privilegio per poter chiamare script python esterni | CREA PROCEDURA o CREA QUALSIASI privilegio PROCEDURA | Autorizzazione CREATE FUNCTION | Privilegio USAGE | CREA privilegio ROUTINE |
| **Creazione di procedure** | N/D | USAGE ON LANGUAGE plpythonu privilegio per poter chiamare script python esterni | CREA PROCEDURA o CREA QUALSIASI privilegio PROCEDURA | AUTORIZZAZIONE CREA PROCEDURA | Privilegio USAGE (le procedure sono funzioni) | CREA privilegio ROUTINE |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Proprietario dell&#39;oggetto | Proprietario dell&#39;oggetto o superutente | DROP ANY &lt; oggetto >, privilegio | Autorizzazione ALTER | Tabella: proprietario dell&#39;indice della tabella: proprietario della funzione di indice: proprietario della funzione | Privilegio DROP |
| **Monitoraggio delle esecuzioni** | Privilegio MONITOR sull&#39;oggetto richiesto | Nessun privilegio richiesto per utilizzare il comando EXPLAIN | Privilegi INSERT e SELECT e privilegi necessari per eseguire l&#39;istruzione su cui si basa il PIANO EXPLAIN | Autorizzazione SHOWPLAN | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | SELECT, privilegio |
| **Scrittura dei dati** | Privilegi INSERT e/o UPDATE (a seconda dell&#39;operazione di scrittura) | Privilegi INSERT e UPDATE | INSERIRE, AGGIORNARE, INSERIRE E AGGIORNARE QUALSIASI privilegio TABELLA | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento di dati nelle tabelle** | CREA STAGE ON SCHEMA, SELEZIONA e INSERISCI sui privilegi della tabella di destinazione | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT | INSERIRE, AMMINISTRARE LE OPERAZIONI DI BULK E MODIFICARE LE AUTORIZZAZIONI TABELLA | Privilegi SELECT e INSERT | Privilegio FILE |
| **Accesso ai dati del client** | SELECT on (FUTURE) TABLE(S) o VIEW(S) Privilegi | SELECT, privilegio | SELEZIONARE O SELEZIONARE QUALSIASI privilegio TABELLA | SELECT, autorizzazione | SELECT, privilegio | SELECT, privilegio |
| **Accesso ai metadati** | Selezionare il privilegio INFORMATION_SCHEMA SCHEMA | SELECT, privilegio | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione DESCRIBE | VISUALIZZA autorizzazione DEFINIZIONE | Nessun privilegio richiesto per l&#39;utilizzo del comando &quot;\d table&quot; | SELECT, privilegio |

|   | DB2 UDB | TeraData | InfiniDB | IQ Sybase / Sybase ASE | Netezza | Greenplum | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Connessione al database remoto** | autorità CONNECT | privilegio CONNECT | Creazione di un utente associato a un host remoto con TUTTI I PRIVILEGI | Nessuna autorizzazione necessaria per utilizzare l&#39;istruzione CONNECT | Nessun privilegio richiesto | privilegio CONNECT | privilegio CONNECT |
| **Creazione di tabelle** | Autorità CREATETAB | CREA TABELLA o TABELLA, parola chiave | CREA privilegio | Autorità di RISORSA e autorizzazione CREATE | TABLE, privilegio | CREA privilegio | CREA privilegio |
| **Creazione di indici** | Privilegio INDEX | parola chiave CREATE INDEX o INDEX | Privilegio INDEX | Autorità di RISORSA e autorizzazione CREATE | Privilegio INDEX | CREA privilegio | CREA privilegio |
| **Creazione di funzioni** | Autorizzazione IMPLICIT_SCHEMA o privilegio CREATEIN | CREA FUNZIONE o FUNZIONE, parola chiave | CREA privilegio ROUTINE | Autorità di RISORSA o autorità DBA per le funzioni Java | Privilegio FUNCTION | Privilegio USAGE | CREA privilegio FUNCTION |
| **Creazione di procedure** | Autorizzazione IMPLICIT_SCHEMA o privilegio CREATEIN | CREA PROCEDURA o PROCEDURA, parola chiave | CREA privilegio ROUTINE | Autorità delle risorse | Privilegio di PROCEDURA | Privilegio USAGE | CREA privilegio FUNCTION |
| **Rimozione di oggetti (tabelle, indici, funzioni, procedure)** | Privilegio DROPIN o privilegio CONTROL o proprietario dell&#39;oggetto | DROP &lt; oggetto > o parola chiave correlata a un oggetto | Privilegio DROP | Proprietario dell&#39;oggetto o dell&#39;autorità DBA | Privilegio DROP | Proprietario dell&#39;oggetto | Proprietario dell&#39;oggetto |
| **Monitoraggio delle esecuzioni** | EXPLAIN, autorità | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | SELECT, privilegio | Solo un amministratore di sistema può eseguire sp_showplan | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN | Nessun privilegio richiesto per l&#39;utilizzo dell&#39;istruzione EXPLAIN |
| **Scrittura dei dati** | Privilegi INSERT e UPDATE o autorità ACCESS DATA | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE | Autorizzazioni INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE | Privilegi INSERT e UPDATE |
| **Caricamento di dati nelle tabelle** | AUTORIZZAZIONE DI CARICO | Privilegi SELECT e INSERISCI per utilizzare rispettivamente le istruzioni COPY TO e COPY FROM | Privilegio FILE | Proprietario della tabella o autorizzazione ALTER. A seconda dell&#39;opzione -gl, LOAD TABLE può essere eseguito solo se l&#39;utente ha l&#39;autorità DBA | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT | Privilegi SELECT e INSERT |
| **Accesso ai dati del client** | Privilegi INSERT/UPDATE o autorità DATAACCESS | SELECT, privilegio | SELECT, privilegio | SELECT, autorizzazione | SELECT, privilegio | SELECT, privilegio | SELECT, privilegio |
| **Accesso ai metadati** | Nessuna autorizzazione necessaria per utilizzare l&#39;istruzione DESCRIBE | SHOW, privilegio | SELECT, privilegio | Nessuna autorizzazione necessaria per utilizzare l&#39;istruzione DESCRIBE | Nessun privilegio richiesto per l&#39;utilizzo del comando &quot;\d table&quot; | Nessun privilegio richiesto per l&#39;utilizzo del comando &quot;\d table&quot; | Nessun privilegio richiesto per l&#39;utilizzo del comando SHOW |