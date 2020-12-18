---
solution: Campaign Classic
product: campaign
title: Configurazione della piattaforma
description: Configurazione della piattaforma
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---


# Configurazione della piattaforma{#configuring-your-platform}

Alcune modifiche principali  Adobe Campaign v7 richiedono una configurazione per garantirne l’effettivo funzionamento. Questi parametri possono essere necessari prima o dopo la migrazione. Le modifiche e la relativa modalità di configurazione sono presentate in questa sezione.

Durante la migrazione, la tabella **NmsRecipient** viene ricreata dalla definizione degli schemi. Qualsiasi modifica apportata alla struttura SQL di questa tabella all&#39;esterno di  Adobe Campaign andrà persa.

Elementi di esempio da verificare:

* Se nella tabella **NmsRecipient** è stata aggiunta una colonna (o un indice) ma non è stata specificata nello schema, la colonna non verrà salvata.
* L&#39;attributo **tablespace** recupera i valori predefiniti, in altre parole quelli definiti nella procedura guidata di distribuzione.
* Se hai aggiunto una visualizzazione di riferimento alla tabella NmsRecipient, devi eliminarla prima di eseguire la migrazione.

Questo avviso riguarda anche  utenti Oracle: se durante un post aggiornamento è stata aggiunta l&#39;opzione **usetimestamptz:1** (vedere [Fusi orari](../../migration/using/general-configurations.md#time-zones)), tutte le tabelle contenenti almeno un campo **data+ora** vengono ricreate.

## Prima della migrazione {#before-the-migration}

Durante la migrazione ad  Adobe Campaign v7, è necessario configurare i seguenti elementi. Questi elementi devono essere risolti prima di avviare **postupgrade**.

* Timezones

   Durante una migrazione da una piattaforma v5.11, dovete specificare il fuso orario da utilizzare durante l&#39;aggiornamento successivo.

   Se si desidera utilizzare la modalità &quot;multi timezone&quot;, fare riferimento alla sezione [Fusi orari](../../migration/using/general-configurations.md#time-zones).

   Se utilizzate  Oracle come database, verificate che i file  fuso orario Oracle siano stati sincronizzati correttamente tra il server dell&#39;applicazione e il server del database. Per ulteriori informazioni, consultare la sezione [ Oracle](../../migration/using/general-configurations.md#oracle).

* Zone di protezione

   Per motivi di sicurezza, la piattaforma Adobe Campaign  non è più accessibile per impostazione predefinita: è necessario configurare le aree di protezione, che richiedono la raccolta degli indirizzi IP dell&#39;utente prima della migrazione.

   Per ulteriori informazioni, consultare la sezione [Sicurezza](../../migration/using/general-configurations.md#security).

* Sintassi

   Alcune sintassi in JavaScript possono essere accettate nelle versioni 5.11 e 6.02 e non più accettate nella versione v7, a causa dell&#39;utilizzo di un nuovo interprete. Per ulteriori informazioni, consultare la sezione [JavaScript](../../migration/using/general-configurations.md#javascript).

   Analogamente, in  Adobe Campaign v7 viene introdotta una nuova sintassi per sostituire la sintassi basata su SQLData. Se utilizzate elementi di codice con questa sintassi, dovete adattarli. Per ulteriori informazioni, consultare la sezione [SQLData](../../migration/using/general-configurations.md#sqldata).

* Password

   È necessario configurare le password **Admin** e **Internal**. Per ulteriori informazioni, consultare la sezione [Password utente](../../migration/using/before-starting-migration.md#user-passwords).

* Struttura ad albero

   Se esegui la migrazione da una piattaforma v5.11, devi riorganizzare le cartelle della struttura ad albero in base  norme Adobe Campaign v6. Per ulteriori informazioni, consultate la sezione [ struttura ad albero di Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure).

* Interazione

   Se utilizzate **Interaction**, dovete eliminare tutti i riferimenti allo schema 6.02 che non esistono più in v7. Per ulteriori informazioni, consultare la sezione [Interazione](../../migration/using/general-configurations.md#interaction).

## Dopo la migrazione {#after-the-migration}

Dopo l&#39;esecuzione di **postupgrade**, è necessario tenere conto dei seguenti elementi ed eseguire le configurazioni corrispondenti.

* Visualizzare le pagine

   Il blocco di personalizzazione delle pagine mirror è stato modificato con v6.x. Questa nuova versione migliora la protezione quando si accede a queste pagine.

   Se hai usato il blocco di personalizzazione v5 nei messaggi, la visualizzazione della pagina mirror non funzionerà.  Adobe consiglia vivamente di utilizzare il nuovo blocco di personalizzazione quando si inserisce una pagina mirror nei messaggi.

   Tuttavia, come soluzione temporanea (e poiché le pagine mirror sono ancora live), potete tornare al vecchio blocco di personalizzazione per evitare questo problema modificando l&#39;opzione **[!UICONTROL XtkAcceptOldPasswords]** e impostarla su **[!UICONTROL 1]**. Ciò non influirà sull&#39;utilizzo del nuovo blocco di personalizzazione v6.x.

* Sintassi

   Se si verificano errori relativi alla sintassi, durante il post aggiornamento è necessario attivare temporaneamente l&#39;opzione **allowSQLInjection** nel file **serverConf.xml**, in quanto questo consente di riscrivere il codice. Una volta adattato il codice, assicurarsi di riattivare la sicurezza. Per ulteriori informazioni, consultare la sezione [SQLData](../../migration/using/general-configurations.md#sqldata).

* Conflitti

   La migrazione viene eseguita tramite un post-aggiornamento e possono verificarsi conflitti in rapporti, moduli o applicazioni Web. Questi conflitti possono essere risolti dalla console.

   Vedere la sezione [Conflitti](../../migration/using/general-configurations.md#conflicts).

* Tomcat

   Se avete personalizzato la cartella di installazione, verificate che sia stata aggiornata correttamente dopo la migrazione. Per ulteriori dettagli, fare riferimento alla sezione [Tomcat](../../migration/using/general-configurations.md#tomcat).

* Rapporti

   Tutti i report forniti al momento utilizzano il motore di rendering v6.x. Se hai aggiunto codice JavaScript ai rapporti, alcuni elementi potrebbero essere modificati.

   Consultare la sezione [Report](../../migration/using/general-configurations.md#reports).

* Applicazioni Web

   Dopo l&#39;aggiornamento successivo, in caso di problemi di connessione alle applicazioni Web identificate, è necessario attivare le opzioni **allowUserPassword** e **sessionTokenOnly** nel file **serverConf.xml**. Ricordare di disattivare queste due opzioni. Per ulteriori informazioni, consultare la sezione [Applicazioni Web identificate](../../migration/using/general-configurations.md#identified-web-applications).

   A seconda del tipo di applicazioni Web e della relativa configurazione, è necessario eseguire ulteriori manipolazioni per assicurarsi che funzionino correttamente.

   Vedere la sezione [Applicazioni Web](../../migration/using/general-configurations.md#web-applications).

   Se si effettua la migrazione da una piattaforma v5.11, è necessario eseguire configurazioni aggiuntive: per ulteriori informazioni, consultare la sezione [Applicazioni Web](../../migration/using/specific-configurations-in-v5-11.md#web-applications).

* Zone di sicurezza.

   Prima di avviare il server, è necessario configurare le aree di protezione. Per ulteriori informazioni, consultare [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones) e la sezione [Security](../../migration/using/general-configurations.md#security).

* Schemi

   In Red Hat, è possibile che si verifichino errori durante la modifica di alcuni schemi. Per ulteriori informazioni, consultare la sezione [Red-Hat](../../migration/using/general-configurations.md#red-hat).

* Flussi di lavoro

   Se esegui la migrazione da una piattaforma v5.11, devi controllare la directory di runtime dei flussi di lavoro. Per ulteriori informazioni, consultare la sezione [Flussi di lavoro](../../migration/using/specific-configurations-in-v5-11.md#workflows).

* Tracking

   Se esegui la migrazione da una piattaforma v5.11, devi configurare la modalità di tracciamento. Per ulteriori informazioni, consultare la sezione [Tracciamento](../../migration/using/specific-configurations-in-v5-11.md#tracking).

* Pagina Home

   Se esegui la migrazione da una piattaforma v6.02, puoi definire parametri aggiuntivi per mantenere la vecchia pagina principale dalla v6.02. Per ulteriori informazioni, fare riferimento alla [Facilità di utilizzo: Home page e sezione di navigazione](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interazione

   Se si utilizza **Interaction**, è necessario regolare eventuali parametri dopo la migrazione. Per ulteriori informazioni, consultare la sezione [Interazione](../../migration/using/general-configurations.md#interaction).

