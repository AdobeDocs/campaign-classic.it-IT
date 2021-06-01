---
product: campaign
title: Configurazione della piattaforma
description: Configurazione della piattaforma
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# Configurazione della piattaforma{#configuring-your-platform}

Alcune modifiche principali in Adobe Campaign v7 richiedono una configurazione per garantirne l’efficace funzionamento. Questi parametri possono essere necessari prima o dopo la migrazione. Le modifiche interessate e la relativa modalità di configurazione sono presentate in questa sezione.

Durante la migrazione, la tabella **NmsRecipient** viene ricreata dalla definizione degli schemi. Eventuali modifiche apportate alla struttura SQL di questa tabella al di fuori di Adobe Campaign andranno perse.

Elementi di esempio da controllare:

* Se hai aggiunto una colonna (o un indice) nella tabella **NmsRecipient** ma non lo hai specificato nello schema, questo non verrà salvato.
* L&#39;attributo **tablespace** recupera i valori per impostazione predefinita, ovvero quelli definiti nella procedura guidata di distribuzione.
* Se hai aggiunto una visualizzazione di riferimento alla tabella NmsRecipient, devi eliminarla prima di eseguire la migrazione.

Questo avviso riguarda anche gli utenti di Oracli: se hai aggiunto l&#39;opzione **usetimestamptz:1** durante un aggiornamento successivo (vedi [Fusi orari](../../migration/using/general-configurations.md#time-zones)), vengono ricreate tutte le tabelle contenenti almeno un campo **date+time**.

## Prima della migrazione {#before-the-migration}

Durante la migrazione ad Adobe Campaign v7, è necessario configurare i seguenti elementi. Questi elementi devono essere risolti prima di avviare **postupgrade**.

* Timezoni

   Durante una migrazione da una piattaforma v5.11, devi specificare il fuso orario da utilizzare durante il post aggiornamento.

   Se desideri utilizzare la modalità &quot;multifuso orario&quot;, consulta la sezione [Fusi orari](../../migration/using/general-configurations.md#time-zones) .

   Se utilizzi Oracle come database, verifica che i file del fuso orario Oracle siano stati sincronizzati correttamente tra l&#39;application server e il database server. Per ulteriori informazioni, consulta la sezione [Oracle](../../migration/using/general-configurations.md#oracle) .

* Zone di sicurezza

   Per motivi di sicurezza, la piattaforma Adobe Campaign non è più accessibile per impostazione predefinita: devi configurare le aree di protezione, che richiede la raccolta degli indirizzi IP dell’utente prima della migrazione.

   Per ulteriori informazioni, consulta la sezione [Sicurezza](../../migration/using/general-configurations.md#security) .

* Sintassi

   Alcune sintassi in JavaScript possono essere accettate nelle versioni 5.11 e 6.02 e non più nella versione v7, a causa dell&#39;uso di un nuovo interprete. Per ulteriori informazioni, consulta la sezione [JavaScript](../../migration/using/general-configurations.md#javascript) .

   Analogamente, in Adobe Campaign v7 viene introdotta una nuova sintassi per sostituire la sintassi basata su SQLData. Se utilizzi elementi di codice con questa sintassi, devi adattarli. Per ulteriori informazioni, consulta la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Password

   Devi configurare le password **Admin** e **Internal** . Per ulteriori informazioni, consulta la sezione [Password utente](../../migration/using/before-starting-migration.md#user-passwords) .

* Struttura ad albero

   Se esegui la migrazione da una piattaforma v5.11, devi riorganizzare le cartelle della struttura ad albero in base alle norme Adobe Campaign v6. Per ulteriori informazioni, consulta la sezione [Struttura ad albero Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interazione

   Se utilizzi **Interazione**, devi eliminare tutti i riferimenti allo schema 6.02 che non esistono più in v7. Per ulteriori informazioni, consulta la sezione [Interazione](../../migration/using/general-configurations.md#interaction) .

## Dopo la migrazione {#after-the-migration}

Dopo aver eseguito **postupgrade**, è necessario tenere conto dei seguenti elementi ed eseguire le configurazioni corrispondenti.

* Pagine specchiate

   Il blocco di personalizzazione della pagina speculare è stato modificato con v6.x. Questa nuova versione migliora la sicurezza durante l’accesso a queste pagine.

   Se hai utilizzato il blocco di personalizzazione v5 nei messaggi, la visualizzazione della pagina speculare avrà esito negativo. Adobe consiglia vivamente di utilizzare il nuovo blocco di personalizzazione quando si inserisce una pagina speculare nei messaggi.

   Tuttavia, come soluzione temporanea (e dato che le pagine mirror sono ancora in tempo reale), puoi tornare al vecchio blocco di personalizzazione per evitare questo problema cambiando l’opzione **[!UICONTROL XtkAcceptOldPasswords]** e impostarla su **[!UICONTROL 1]**. Questo non influisce sull’utilizzo del nuovo blocco di personalizzazione v6.x.

* Sintassi

   Se si verificano errori relativi alla sintassi, durante il post aggiornamento è necessario attivare temporaneamente l&#39;opzione **allowSQLInjection** nel file **serverConf.xml**, in quanto questo ti dà il tempo di riscrivere il codice. Una volta adattato il codice, assicurati di riattivare la sicurezza. Per ulteriori informazioni, consulta la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Conflitti

   La migrazione viene eseguita tramite un aggiornamento successivo e possono comparire conflitti in rapporti, moduli o applicazioni web. Questi conflitti possono essere risolti dalla console.

   Consulta la sezione [Conflitti](../../migration/using/general-configurations.md#conflicts) .

* Tomcat

   Se hai personalizzato la cartella di installazione, accertati che sia stata aggiornata correttamente dopo la migrazione. Per ulteriori dettagli, consulta la sezione [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Rapporti

   Tutti i report predefiniti al momento utilizzano il motore di rendering v6.x. Se hai aggiunto il codice JavaScript ai rapporti, alcuni elementi possono essere modificati.

   Consulta la sezione [Rapporti](../../migration/using/general-configurations.md#reports) .

* Applicazioni Web

   Dopo l&#39;aggiornamento, se si verificano problemi di connessione alle applicazioni Web identificate, è necessario attivare le opzioni **allowUserPassword** e **sessionTokenOnly** nel file **serverConf.xml**. Ricordare quindi di disattivare queste due opzioni. Per ulteriori informazioni, consulta la sezione [Applicazioni web identificate](../../migration/using/general-configurations.md#identified-web-applications) .

   A seconda del tipo di applicazioni Web e della relativa configurazione, è necessario eseguire ulteriori manipolazioni per garantirne il corretto funzionamento.

   Vedere la sezione [Applicazioni web](../../migration/using/general-configurations.md#web-applications) .

   Se si esegue la migrazione da una piattaforma v5.11, è necessario eseguire configurazioni aggiuntive: per ulteriori informazioni, consulta la sezione [Applicazioni web](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Zone di sicurezza.

   Prima di avviare il server, è necessario configurare le aree di protezione. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/security-zones.md) e la sezione [Sicurezza](../../migration/using/general-configurations.md#security) .

* Schemi

   In Red Hat, potresti riscontrare errori durante la modifica di alcuni schemi. Per ulteriori informazioni, consulta la sezione [Red-Hat](../../migration/using/general-configurations.md#red-hat) .

* Flussi di lavoro

   Se esegui la migrazione da una piattaforma v5.11, devi controllare la directory di runtime dei flussi di lavoro. Per ulteriori informazioni, consulta la sezione [Flussi di lavoro](../../migration/using/specific-configurations-in-v5-11.md#workflows) .

* Tracciamento

   Se esegui la migrazione da una piattaforma v5.11, devi configurare la modalità di tracciamento. Per ulteriori informazioni, consulta la sezione [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) .

* Pagina Home

   Se esegui la migrazione da una piattaforma v6.02, puoi definire parametri aggiuntivi per mantenere la vecchia home page dalla v6.02. Per ulteriori informazioni, consulta la sezione [Facilità di utilizzo: Home page e sezione navigazione](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interazione

   Se utilizzi **Interazione**, devi regolare eventuali parametri dopo la migrazione. Per ulteriori informazioni, consulta la sezione [Interazione](../../migration/using/general-configurations.md#interaction) .
