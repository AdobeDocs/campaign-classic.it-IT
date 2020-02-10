---
title: Configurazione della piattaforma
seo-title: Configurazione della piattaforma
description: Configurazione della piattaforma
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Configurazione della piattaforma{#configuring-your-platform}

Alcune modifiche importanti in Adobe Campaign v7 richiedono una configurazione per garantirne l&#39;effettivo funzionamento. Questi parametri possono essere necessari prima o dopo la migrazione. Le modifiche e la relativa modalità di configurazione sono presentate in questa sezione.

Durante la migrazione, la tabella **NmsRecipient** viene ricreata dalla definizione degli schemi. Qualsiasi modifica apportata alla struttura SQL di questa tabella al di fuori di Adobe Campaign andrà persa.

Elementi di esempio da verificare:

* Se nella tabella **NmsRecipient** è stata aggiunta una colonna (o un indice) ma non è stata specificata nello schema, la colonna non verrà salvata.
* L&#39;attributo **tablespace** recupera i valori per impostazione predefinita, in altre parole quelli definiti nella procedura guidata di distribuzione.
* Se hai aggiunto una visualizzazione di riferimento alla tabella NmsRecipient, devi eliminarla prima di eseguire la migrazione.

Questo avviso riguarda anche gli utenti Oracle: se è stata aggiunta l&#39;opzione **usetimestamptz:1** durante un post aggiornamento (vedere Fusi [](../../migration/using/general-configurations.md#time-zones)orari), tutte le tabelle contenenti almeno un campo **data+ora** vengono ricreate.

## Prima della migrazione {#before-the-migration}

Durante la migrazione ad Adobe Campaign v7, devono essere configurati i seguenti elementi. Questi elementi devono essere risolti prima di avviare il **post aggiornamento**.

* Timezones

   Durante una migrazione da una piattaforma v5.11, dovete specificare il fuso orario da utilizzare durante l&#39;aggiornamento successivo.

   Se desiderate utilizzare la modalità &quot;multifuso&quot;, consultate la sezione Fusi [orari](../../migration/using/general-configurations.md#time-zones) .

   Se si utilizza Oracle come database, verificare che i file del fuso orario Oracle siano stati sincronizzati correttamente tra il server dell&#39;applicazione e il server del database. Per ulteriori informazioni, vedere la sezione [Oracle](../../migration/using/general-configurations.md#oracle) .

   Inoltre, durante una migrazione da una piattaforma v.5.11, in MySQL è necessario eseguire configurazioni aggiuntive. Per ulteriori informazioni, vedere la sezione [MySQL](../../migration/using/specific-configurations-in-v5-11.md#mysql) .

* Zone di protezione

   Per motivi di sicurezza, la piattaforma Adobe Campaign non è più accessibile per impostazione predefinita: è necessario configurare le aree di protezione, che richiedono la raccolta degli indirizzi IP dell&#39;utente prima della migrazione.

   Per ulteriori informazioni, consultare la sezione [Protezione](../../migration/using/general-configurations.md#security) .

* Sintassi

   Alcune sintassi in JavaScript possono essere accettate nelle versioni 5.11 e 6.02 e non più accettate nella versione v7, a causa dell&#39;utilizzo di un nuovo interprete. Per ulteriori informazioni, consultare la sezione [JavaScript](../../migration/using/general-configurations.md#javascript) .

   Analogamente, in Adobe Campaign v7 viene introdotta una nuova sintassi per sostituire la sintassi basata su SQLData. Se utilizzate elementi di codice con questa sintassi, dovete adattarli. Per ulteriori informazioni, vedere la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Password

   Devi configurare le password **Admin** e **Internal** . Per ulteriori informazioni, consulta la sezione [Password](../../migration/using/before-starting-migration.md#user-passwords) utente.

* Struttura ad albero

   Se effettui la migrazione da una piattaforma v5.11, devi riorganizzare le cartelle della struttura ad albero in base alle norme Adobe Campaign v6. Per ulteriori informazioni, consulta la sezione sulla struttura ad albero di [Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interazione

   Se utilizzate **Interazione**, dovete eliminare tutti i riferimenti allo schema 6.02 che non esistono più in v7. Per ulteriori informazioni, vedere la sezione [Interazione](../../migration/using/general-configurations.md#interaction) .

## Dopo la migrazione {#after-the-migration}

Dopo l&#39;esecuzione **del post-aggiornamento**, è necessario tenere conto dei seguenti elementi e delle relative configurazioni.

* Visualizzare le pagine

   Il blocco di personalizzazione delle pagine mirror è stato modificato con v6.x. Questa nuova versione migliora la protezione quando si accede a queste pagine.

   Se hai usato il blocco di personalizzazione v5 nei messaggi, la visualizzazione della pagina mirror non funzionerà. Adobe consiglia vivamente di utilizzare il nuovo blocco di personalizzazione quando si inserisce una pagina mirror nei messaggi.

   Tuttavia, come soluzione temporanea (e poiché le pagine mirror sono ancora live), potete tornare al vecchio blocco di personalizzazione per evitare questo problema modificando l&#39;opzione **[!UICONTROL XtkAcceptOldPasswords]** e impostandola su **[!UICONTROL 1]**. Ciò non influirà sull&#39;utilizzo del nuovo blocco di personalizzazione v6.x.

* Sintassi

   Se si verificano errori relativi alla sintassi, durante il post-aggiornamento è necessario attivare temporaneamente l’opzione **allowSQLInjection** nel file **serverConf.xml** , in quanto questo consente di riscrivere il codice. Una volta adattato il codice, assicurarsi di riattivare la sicurezza. Per ulteriori informazioni, consultate la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Conflitti

   La migrazione viene eseguita tramite un post-aggiornamento e possono verificarsi conflitti in rapporti, moduli o applicazioni Web. Questi conflitti possono essere risolti dalla console.

   Vedere la sezione [Conflitti](../../migration/using/general-configurations.md#conflicts) .

* Tomcat

   Se avete personalizzato la cartella di installazione, verificate che sia stata aggiornata correttamente dopo la migrazione. Per ulteriori dettagli, consultare la sezione [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Rapporti

   Tutti i report forniti attualmente utilizzano il motore di rendering v6.x. Se hai aggiunto codice JavaScript ai rapporti, alcuni elementi potrebbero essere modificati.

   Consultate la sezione [Rapporti](../../migration/using/general-configurations.md#reports) .

* Applicazioni Web

   Dopo l&#39;aggiornamento successivo, in caso di problemi di connessione alle applicazioni Web identificate, è necessario attivare le opzioni **allowUserPassword** e **sessionTokenOnly** nel file **serverConf.xml** . Ricordare di disattivare queste due opzioni. Per ulteriori informazioni, consultare la sezione Applicazioni [Web](../../migration/using/general-configurations.md#identified-web-applications) identificate.

   A seconda del tipo di applicazioni Web e della relativa configurazione, è necessario eseguire ulteriori manipolazioni per assicurarsi che funzionino correttamente.

   Vedere la sezione Applicazioni [](../../migration/using/general-configurations.md#web-applications) Web.

   Se si effettua la migrazione da una piattaforma v5.11, è necessario eseguire configurazioni aggiuntive: per ulteriori informazioni, vedere la sezione Applicazioni [](../../migration/using/specific-configurations-in-v5-11.md#web-applications) Web.

* Zone di sicurezza.

   Prima di avviare il server, è necessario configurare le aree di protezione. Per ulteriori informazioni, consultare [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones) e la sezione [Protezione](../../migration/using/general-configurations.md#security) .

* Schemi

   In Red Hat, è possibile che si verifichino errori durante la modifica di alcuni schemi. Per ulteriori informazioni, consultare la sezione [Red-Hat](../../migration/using/general-configurations.md#red-hat) .

* Flussi di lavoro

   Se esegui la migrazione da una piattaforma v5.11, devi controllare la directory di runtime dei flussi di lavoro. Per ulteriori informazioni, consultare la sezione [Flussi](../../migration/using/specific-configurations-in-v5-11.md#workflows) di lavoro.

* Tracciamento

   Se esegui la migrazione da una piattaforma v5.11, devi configurare la modalità di tracciamento. Per ulteriori informazioni, consulta la sezione [Tracciamento](../../migration/using/specific-configurations-in-v5-11.md#tracking) .

* Home page

   Se esegui la migrazione da una piattaforma v6.02, puoi definire parametri aggiuntivi per mantenere la vecchia pagina principale dalla v6.02. Per ulteriori informazioni, consulta la sezione [Facilità di utilizzo: Home page e sezione di navigazione](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) .

* Interazione

   Se si utilizza **Interazione**, è necessario regolare eventuali parametri dopo la migrazione. Per ulteriori informazioni, consulta la sezione [Interazione](../../migration/using/general-configurations.md#interaction) .

