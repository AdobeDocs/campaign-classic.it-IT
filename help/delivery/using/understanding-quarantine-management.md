---
product: campaign
title: Informazioni sulla gestione della quarantena
description: Informazioni sulla gestione della quarantena
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Informazioni sulla gestione della quarantena{#understanding-quarantine-management}

>[!NOTE]
>
>La pagina [Gestione quarantena di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines) contiene informazioni dettagliate sulla gestione della quarantena. Questo contenuto si applica sia agli utenti di Campaign Classic v7 che a Campaign v8 e riguarda:
>
>* Concetti di quarantena e di inserisco nell&#39;elenco Bloccati di
>* Perché gli indirizzi vengono messi in quarantena (errori rigidi/morbidi)
>* Gestione morbida degli errori e soglie dei contatori di errori
>* Come accedere e identificare gli indirizzi messi in quarantena
>* Come rimuovere gli indirizzi dalla quarantena (automatica, manuale, in blocco)
>* Report di gestione della quarantena
>
>In questa pagina è documentata la **configurazione specifica di Campaign Classic v7** per la gestione della quarantena nelle distribuzioni ibride e on-premise.

Per informazioni complete sulla gestione della quarantena, consulta la [documentazione sulla gestione della quarantena di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Configurazione quarantena {#v7-quarantine-config}

Per personalizzare il comportamento di quarantena, sono disponibili le seguenti opzioni di configurazione per **distribuzioni ibride/on-premise di Campaign Classic v7**.

### Configurazione soglia di errore morbida {#soft-error-threshold}

Per le installazioni on-premise che utilizzano l’MTA di Campaign legacy, puoi modificare il numero di errori e il periodo tra due errori prima che un indirizzo venga messo in quarantena.

Per configurare queste impostazioni:

1. Accedi alla procedura guidata di distribuzione da **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Passa a **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configura:
   * **Numero di errori**: il numero massimo di errori non permanenti prima della messa in quarantena di un indirizzo (impostazione predefinita: 5)
   * **Periodo tra due errori significativi**: intervallo di tempo (in secondi) per il conteggio degli errori (impostazione predefinita: 86.400 secondi = 1 giorno)

Quando il contatore di errori raggiunge la soglia, l’indirizzo viene messo in quarantena. Se l&#39;ultimo errore significativo si è verificato più di 10 giorni fa, il contatore degli errori viene reinizializzato.

Per ulteriori dettagli, consulta [questa pagina](communication-channels.md) in **Invio consegna** > **Configurazione nuovi tentativi**.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, le impostazioni dei nuovi tentativi e le soglie di errore sono gestite da Adobe in base alle prestazioni IP e alla reputazione del dominio. Non è richiesta alcuna configurazione.

### Flusso di lavoro di pulizia del database {#database-cleanup-workflow}

Per le installazioni on-premise, il flusso di lavoro tecnico **[!UICONTROL Database cleanup]** rimuove automaticamente gli indirizzi messi in quarantena che soddisfano condizioni specifiche.

Accedi a questo flusso di lavoro da **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

Il flusso di lavoro rimuove gli indirizzi dalla quarantena nei seguenti casi:

* Indirizzi nello stato **[!UICONTROL With errors]** dopo una consegna riuscita
* Indirizzi con stato **[!UICONTROL With errors]** se l&#39;ultimo messaggio non recapitato si è verificato più di 10 giorni fa
* Indirizzi nello stato **[!UICONTROL With errors]** con errore **[!UICONTROL Mailbox full]** dopo 30 giorni

Assicurati che questo flusso di lavoro venga eseguito regolarmente (consigliato: ogni giorno) per mantenere l’igiene degli elenchi di quarantena.

Per ulteriori informazioni sulla pulizia del database, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, il flusso di lavoro di pulizia del database è monitorato e gestito da Adobe.

### Specifiche di quarantena delle notifiche push {#push-quarantine-specifics}

Per Campaign Classic v7, le quarantene di notifiche push seguono il meccanismo di quarantena generale con alcuni comportamenti specifici del canale.

Per le notifiche push di **iOS** e **Android**, il meccanismo di quarantena utilizza token del dispositivo anziché indirizzi e-mail. Quando un’app mobile viene disinstallata o reinstallata, il token associato viene messo in quarantena.

Per informazioni dettagliate sugli scenari di quarantena delle notifiche push (tipi di errore iOS e Android, comportamento dei nuovi tentativi, ecc.), consulta la [documentazione sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} che include tabelle complete dei tipi di errore delle notifiche push.

### Specifiche di quarantena SMS {#sms-quarantine-specifics}

Per Campaign Classic v7, le quarantene di SMS seguono il meccanismo generale di quarantena con alcuni comportamenti specifici del canale relativi ai numeri di telefono anziché agli indirizzi e-mail.

Il meccanismo di quarantena SMS varia a seconda del connettore utilizzato:

* **Connettori SMPP standard**: le regole di qualificazione degli errori definite in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** si applicano alle consegne SMS.

* **Connettore SMPP generico esteso**: la gestione degli errori viene gestita in modo diverso utilizzando espressioni regolari (regex) per analizzare i messaggi del rapporto di stato (SR) restituiti dal provider SMSC.

Per informazioni dettagliate sugli scenari di quarantena SMS e sui tipi di errore, consulta la documentazione [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, che include tabelle complete sui tipi di errore SMS.

## Argomenti correlati

* [Gestione della quarantena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentazione di Campaign v8)
* [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8)
* [Best practice per la consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentazione di Campaign v8)
* [Flusso di lavoro di pulizia del database](../../production/using/database-cleanup-workflow.md) (v7 ibrido/on-premise)
* [Configura nuovi tentativi di consegna](communication-channels.md) (v7 ibrido/on-premise)
