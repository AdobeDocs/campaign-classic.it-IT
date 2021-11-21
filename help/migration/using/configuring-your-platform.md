---
product: campaign
title: Configurazione della piattaforma
description: Configurazione della piattaforma
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# Configurazione della piattaforma{#configuring-your-platform}

![](../../assets/v7-only.svg)

Alcune modifiche importanti in Adobe Campaign v7 richiedono una configurazione per garantirne l’efficace funzionamento. Questi parametri possono essere necessari prima o dopo la migrazione. Le modifiche interessate e la relativa modalità di configurazione sono presentate in questa sezione.

Durante la migrazione, il **NmsRecipient** la tabella viene ricreata dalla definizione degli schemi. Eventuali modifiche apportate alla struttura SQL di questa tabella al di fuori di Adobe Campaign andranno perse.

Elementi di esempio da controllare:

* Se hai aggiunto una colonna (o un indice) nel **NmsRecipient** tabella ma non dettagliata nello schema, questa non verrà salvata.
* La **tablespace** l&#39;attributo recupera i valori per impostazione predefinita, ovvero quelli definiti nella procedura guidata di distribuzione.
* Se hai aggiunto una visualizzazione di riferimento alla tabella NmsRecipient, devi eliminarla prima di eseguire la migrazione.

Questo avviso riguarda anche gli utenti di Oracli: se hai aggiunto il **usetimestamptz:1** durante un aggiornamento successivo (vedi [Fusi orari](../../migration/using/general-configurations.md#time-zones)), tutte le tabelle contenenti almeno una **data e ora** i campi vengono ricostruiti.

## Prima della migrazione {#before-the-migration}

Durante la migrazione ad Adobe Campaign v7, è necessario configurare i seguenti elementi. Questi elementi devono essere affrontati prima di avviare il **postupgrade**.

* Timezoni

   Durante una migrazione da una piattaforma v5.11, devi specificare il fuso orario da utilizzare durante il post aggiornamento.

   Se desideri utilizzare la modalità &quot;multi-fuso orario&quot;, consulta la [Fusi orari](../../migration/using/general-configurations.md#time-zones) sezione .

   Se utilizzi Oracle come database, verifica che i file del fuso orario Oracle siano stati sincronizzati correttamente tra l&#39;application server e il database server. Per ulteriori informazioni, consulta la sezione [Oracle](../../migration/using/general-configurations.md#oracle) sezione .

* Zone di sicurezza

   Per motivi di sicurezza, la piattaforma Adobe Campaign non è più accessibile per impostazione predefinita: devi configurare le aree di protezione, che richiede la raccolta degli indirizzi IP dell’utente prima della migrazione.

   Per ulteriori informazioni, consulta la [Sicurezza](../../migration/using/general-configurations.md#security) sezione .

* Sintassi

   Alcune sintassi in JavaScript possono essere accettate nelle versioni 5.11 e 6.02 e non più nella versione v7, a causa dell&#39;uso di un nuovo interprete. Per ulteriori informazioni, consulta la [JavaScript](../../migration/using/general-configurations.md#javascript) sezione .

   Analogamente, in Adobe Campaign v7 viene introdotta una nuova sintassi per sostituire la sintassi basata su SQLData. Se utilizzi elementi di codice con questa sintassi, devi adattarli. Per ulteriori informazioni, consulta la [SQLData](../../migration/using/general-configurations.md#sqldata) sezione .

* Password

   È necessario configurare le **Amministratore** e **Interno** password. Per ulteriori informazioni, consulta la [Password utente](../../migration/using/before-starting-migration.md#user-passwords) sezione .

* Struttura ad albero

   Se esegui la migrazione da una piattaforma v5.11, devi riorganizzare le cartelle della struttura ad albero in base alle norme Adobe Campaign v6. Per ulteriori informazioni, consulta la [Struttura ad albero di Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) sezione .

* Interazione

   Se utilizzi **Interazione**, devi eliminare tutti i riferimenti di schema 6.02 che non esistono più in v7. Per ulteriori informazioni, consulta la [Interazione](../../migration/using/general-configurations.md#interaction) sezione .

## Dopo la migrazione {#after-the-migration}

Dopo l&#39;esecuzione **postupgrade**, devono essere presi in considerazione i seguenti elementi e devono essere eseguite le configurazioni corrispondenti.

* Pagine specchiate

   Il blocco di personalizzazione della pagina speculare è stato modificato con v6.x. Questa nuova versione migliora la sicurezza durante l’accesso a queste pagine.

   Se hai utilizzato il blocco di personalizzazione v5 nei messaggi, la visualizzazione della pagina speculare avrà esito negativo. Adobe consiglia vivamente di utilizzare il nuovo blocco di personalizzazione quando si inserisce una pagina speculare nei messaggi.

   Tuttavia, come soluzione temporanea (e dato che le pagine mirror sono ancora in tempo reale), puoi tornare al vecchio blocco di personalizzazione per evitare questo problema modificando l’opzione **[!UICONTROL XtkAcceptOldPasswords]** e impostarlo su **[!UICONTROL 1]**. Questo non influisce sull’utilizzo del nuovo blocco di personalizzazione v6.x.

* Sintassi

   Se si verificano errori relativi alla sintassi, durante il post aggiornamento devi attivare temporaneamente il **allowSQLInjection** in **serverConf.xml** file , poiché questo ti dà il tempo di riscrivere il codice. Una volta adattato il codice, assicurati di riattivare la sicurezza. Per ulteriori informazioni, consulta la sezione [SQLData](../../migration/using/general-configurations.md#sqldata) sezione .

* Conflitti

   La migrazione viene eseguita tramite un aggiornamento successivo e possono comparire conflitti in rapporti, moduli o applicazioni web. Questi conflitti possono essere risolti dalla console.

   Consulta la sezione [Conflitti](../../migration/using/general-configurations.md#conflicts) sezione .

* Tomcat

   Se hai personalizzato la cartella di installazione, accertati che sia stata aggiornata correttamente dopo la migrazione. Per ulteriori dettagli, consulta la [Tomcat](../../migration/using/general-configurations.md#tomcat) sezione .

* Rapporti

   Tutti i report predefiniti al momento utilizzano il motore di rendering v6.x. Se hai aggiunto il codice JavaScript ai rapporti, alcuni elementi possono essere modificati.

   Consulta la [Rapporti](../../migration/using/general-configurations.md#reports) sezione .

* Applicazioni Web

   Dopo l&#39;aggiornamento, se si verificano problemi di connessione alle applicazioni Web identificate, è necessario attivare la **allowUserPassword** e **sessionTokenOnly** nelle opzioni **serverConf.xml** file. Ricordare quindi di disattivare queste due opzioni. Per ulteriori informazioni, consulta la [Applicazioni web identificate](../../migration/using/general-configurations.md#identified-web-applications) sezione .

   A seconda del tipo di applicazioni Web e della relativa configurazione, è necessario eseguire ulteriori manipolazioni per garantirne il corretto funzionamento.

   Consulta la sezione [Applicazioni web](../../migration/using/general-configurations.md#web-applications) sezione .

   Se si esegue la migrazione da una piattaforma v5.11, è necessario eseguire configurazioni aggiuntive: per ulteriori informazioni, consulta [Applicazioni web](../../migration/using/specific-configurations-in-v5-11.md#web-applications) sezione .

* Zone di sicurezza.

   Prima di avviare il server, è necessario configurare le aree di protezione. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/security-zones.md) e [Sicurezza](../../migration/using/general-configurations.md#security) sezione .

* Schemi

   In Red Hat, potresti riscontrare errori durante la modifica di alcuni schemi. Per ulteriori informazioni, consulta la sezione [Cappello rosso](../../migration/using/general-configurations.md#red-hat) sezione .

* Flussi di lavoro

   Se esegui la migrazione da una piattaforma v5.11, devi controllare la directory di runtime dei flussi di lavoro. Per ulteriori informazioni, consulta la sezione [Flussi di lavoro](../../migration/using/specific-configurations-in-v5-11.md#workflows) sezione .

* Tracciamento

   Se esegui la migrazione da una piattaforma v5.11, devi configurare la modalità di tracciamento. Per ulteriori informazioni, consulta la sezione [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) sezione .

* Pagina Home

   Se esegui la migrazione da una piattaforma v6.02, puoi definire parametri aggiuntivi per mantenere la vecchia home page dalla v6.02. Per ulteriori informazioni, consulta la [Facilità di utilizzo: Home page e navigazione](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) sezione .

* Interazione

   Se utilizzi **Interazione**, è necessario regolare eventuali parametri dopo la migrazione. Per ulteriori informazioni, consulta la sezione [Interazione](../../migration/using/general-configurations.md#interaction) sezione .
