---
product: campaign
title: Errori di consegna e gestione della quarantena
description: Scopri come comprendere gli errori di consegna e gestire le quarantene in Campaign Classic v7
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 1%

---

# Errori di consegna e gestione della quarantena {#delivery-failures-quarantine}

>[!NOTE]
>
>Una guida completa sugli errori di consegna e sulla gestione della quarantena è documentata nella documentazione di Campaign v8. Questo contenuto si applica sia agli utenti di Campaign Classic v7 che a quelli di Campaign v8:
>
>* [Informazioni sugli errori di recapito](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} - Include i tipi di errore, i motivi dell&#39;errore, gli errori sincroni/asincroni, la gestione dei nuovi tentativi e la risoluzione dei problemi
>* [Gestione della quarantena](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}: riguarda la quarantena rispetto al inserisco nell&#39;elenco Bloccati di, le soglie di errore soft, i report di quarantena e la rimozione degli indirizzi
>
>In questa pagina è documentata la **configurazione specifica di Campaign Classic v7** per la gestione della posta non recapitata e della quarantena nelle distribuzioni ibride e on-premise.

## Informazioni sugli errori di consegna

Per informazioni sui concetti comuni relativi agli errori di consegna, sui tipi di errore e sulla risoluzione dei problemi, consulta la [Documentazione sugli errori di consegna in Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Configurazione e-mail non recapitate {#bounce-mail-config}

Le seguenti opzioni di configurazione sono disponibili per **distribuzioni ibride/on-premise di Campaign Classic v7** per gestire l&#39;elaborazione della posta non recapitata.

### Configurazione cassetta postale di mancato recapito {#bounce-mailbox-configuration}

Per le installazioni on-premise, la configurazione della cassetta postale di mancato recapito è descritta in [questa sezione](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

I messaggi di errore asincroni vengono raccolti dalla piattaforma Adobe Campaign tramite la cassetta postale di mancato recapito e qualificati dal processo inMail per arricchire l’elenco delle regole di gestione e-mail.

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, la configurazione della cassetta postale di mancato recapito viene eseguita e gestita da Adobe. Non è richiesta alcuna configurazione.

### Gestione delle qualifiche di mail non recapitate {#bounce-mail-qualification-management}

Per le installazioni on-premise e in hosting/ibride utilizzando l’MTA di Campaign legacy, quando la consegna di un’e-mail non riesce, il server di consegna Adobe Campaign riceve un messaggio di errore dal server di messaggistica o dal server DNS remoto. L&#39;elenco degli errori è costituito dalle stringhe contenute nel messaggio restituito dal server remoto. A ogni messaggio di errore vengono assegnati tipi e motivi di errore.

Questo elenco è disponibile tramite il nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**. Contiene tutte le regole utilizzate da Adobe Campaign per qualificare gli errori di consegna. Non è esaustivo, è regolarmente aggiornato da Adobe Campaign e può anche essere gestito dall’utente.

![](assets/tech_quarant_rules_qualif.png)

Il messaggio restituito dal server remoto alla prima occorrenza di questo tipo di errore viene visualizzato nella colonna **[!UICONTROL First text]** della tabella **[!UICONTROL Delivery log qualification]**. Se questa colonna non è visualizzata, fare clic sul pulsante **[!UICONTROL Configure list]** nella parte inferiore destra dell&#39;elenco per selezionarla.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtra questo messaggio per eliminare il contenuto della variabile (ad esempio ID, date, indirizzi e-mail, numeri di telefono e così via) e visualizza il risultato filtrato nella colonna **[!UICONTROL Text]**. Le variabili vengono sostituite con **`#xxx#`**, ad eccezione degli indirizzi sostituiti con **`*`**.

Questo processo consente di riunire tutti gli errori dello stesso tipo ed evitare più voci per errori simili nella tabella Qualificazione del registro di consegna.

>[!NOTE]
>
>Nel campo **[!UICONTROL Number of occurrences]** viene visualizzato il numero di occorrenze del messaggio nell&#39;elenco. Tale numero è limitato a 100 000. È possibile modificare il campo, ad esempio per reimpostarlo.

I messaggi non recapitati possono avere il seguente stato di qualifica:

* **[!UICONTROL To qualify]**: impossibile qualificare la posta non recapitata. È necessario assegnare la qualifica al team Deliverability per garantire un recapito della piattaforma efficiente. Se non è qualificata, la posta non recapitata non viene utilizzata per arricchire l’elenco delle regole di gestione e-mail.
* **[!UICONTROL Keep]**: la posta non recapitata è stata qualificata e verrà utilizzata dal flusso di lavoro **Aggiorna per il recapito messaggi** per essere confrontata con le regole di gestione e-mail esistenti e arricchire l&#39;elenco.
* **[!UICONTROL Ignore]**: la mail non recapitata viene ignorata dall&#39;MTA della campagna, il che significa che questa non recapitata non causerà mai la quarantena dell&#39;indirizzo del destinatario. Non verrà utilizzato dal flusso di lavoro **Aggiorna per il recapito messaggi** e non verrà inviato alle istanze client.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>In caso di interruzione di un ISP, le e-mail inviate tramite Campaign verranno contrassegnate erroneamente come messaggi non recapitati. Per risolvere questo problema, devi aggiornare la qualifica di mancato recapito. Per ulteriori informazioni, consulta [questa pagina](update-bounce-qualification.md).

### Configurazione delle regole di gestione e-mail {#email-management-rules}

Le regole di posta sono accessibili tramite il nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**. Le regole di gestione delle e-mail sono visualizzate nella parte inferiore della finestra.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>I parametri predefiniti della piattaforma sono configurati nella procedura guidata di distribuzione. Per ulteriori informazioni, consultare [questa sezione](../../installation/using/deploying-an-instance.md).

Le regole predefinite sono le seguenti:

>[!IMPORTANT]
>
>* Se i parametri sono stati modificati, il server di consegna (MTA) deve essere riavviato.
>* La modifica o la creazione di regole di gestione è riservata agli utenti esperti.

#### E-mail in entrata {#inbound-email}

Queste regole contengono le stringhe che possono essere restituite dai server remoti e che consentono di qualificare l&#39;errore (**Rigido**, **Morbido** o **Ignorato**).

Quando un messaggio e-mail non riesce, il server remoto restituisce un messaggio di mancato recapito all’indirizzo specificato nei parametri della piattaforma. Adobe Campaign confronta il contenuto di ogni messaggio non recapitato con le stringhe nell’elenco di regole, quindi assegna a tale messaggio uno dei tre tipi di errore.

>[!NOTE]
>
>L’utente può creare le proprie regole. Quando si importa un pacchetto e si aggiornano i dati tramite il flusso di lavoro **Aggiorna per il recapito messaggi**, le regole create dall&#39;utente vengono sovrascritte.

Per ulteriori informazioni sulla qualifica della posta non recapitata, consulta [questa sezione](#bounce-mail-qualification-management).

#### Gestione del dominio {#domain-management}

Per le installazioni on-premise, l&#39;MTA applica una singola regola di **gestione del dominio** a tutti i domini.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Puoi scegliere se attivare o meno alcuni standard di identificazione e chiavi di crittografia per controllare il nome di dominio, ad esempio **ID mittente**, **Chiavi di dominio**, **DKIM** e **S/MIME**.
* I parametri **Inoltro SMTP** consentono di configurare l&#39;indirizzo IP e la porta di un server di inoltro per un dominio specifico. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#smtp-relay).

Se i messaggi visualizzano **[!UICONTROL on behalf of]** nell&#39;indirizzo del mittente, assicurati di non firmare le e-mail con **ID mittente**, che è lo standard obsoleto di autenticazione delle e-mail proprietarie di Microsoft. Se l&#39;opzione **[!UICONTROL Sender ID]** è abilitata, deseleziona la casella corrispondente e contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Il recapito messaggi non sarà influenzato.

#### Gestione MX {#mx-management}

Per le installazioni on-premise, le regole di gestione MX vengono utilizzate per regolare il flusso delle e-mail in uscita per un dominio specifico.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

Queste regole sono disponibili nella procedura guidata di distribuzione e possono essere personalizzate:

* **[!UICONTROL MX Management]**: questa regola viene utilizzata per controllare il flusso delle e-mail in uscita per un dominio. Campiona i messaggi di mancato recapito e blocca l’invio dove appropriato.

* **[!UICONTROL Period]**: intervallo di tempo durante il quale i messaggi vengono limitati o bloccati.

* **[!UICONTROL Limit]**: numero massimo di messaggi consentiti per periodo di tempo.

* **[!UICONTROL Type]**: tipo di errore (rigido, morbido o ignorato) utilizzato per determinare il comportamento di invio. Per le definizioni dei tipi di errore, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

Per ulteriori informazioni sulla gestione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#about-mx-rules).

>[!NOTE]
>
>Per gli utenti di Campaign v8 Managed Cloud Services, le regole MX e la gestione del flusso di e-mail sono gestite da Adobe come parte dell’infrastruttura gestita. Contatta l’Assistenza clienti di Adobe se devi regolare le impostazioni MX per casi d’uso specifici.

## Gestione della quarantena {#quarantine-management}

Per informazioni complete sulla gestione della quarantena, consulta la [documentazione sulla gestione della quarantena di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Configurazione quarantena {#quarantine-config}

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

Per informazioni dettagliate sugli scenari di quarantena delle notifiche push (tipi di errore iOS e Android, comportamento dei nuovi tentativi, ecc.), consulta la [documentazione sugli errori di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} che include tabelle complete dei tipi di errore delle notifiche push.

### Specifiche di quarantena SMS {#sms-quarantine-specifics}

Per Campaign Classic v7, le quarantene di SMS seguono il meccanismo generale di quarantena con alcuni comportamenti specifici del canale relativi ai numeri di telefono anziché agli indirizzi e-mail.

Il meccanismo di quarantena SMS varia a seconda del connettore utilizzato:

* **Connettori SMPP standard**: le regole di qualificazione degli errori definite in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** si applicano alle consegne SMS.

* **Connettore SMPP generico esteso**: la gestione degli errori viene gestita in modo diverso utilizzando espressioni regolari (regex) per analizzare i messaggi del rapporto di stato (SR) restituiti dal provider SMSC.

Per informazioni dettagliate sugli scenari di quarantena SMS e sui tipi di errore, consulta la documentazione [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, che include tabelle complete sui tipi di errore SMS.

## Argomenti correlati

* [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8)
* [Gestione della quarantena](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentazione di Campaign v8)
* [Best practice per la consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentazione di Campaign v8)
* [Stati di consegna](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentazione di Campaign v8)
* [Flusso di lavoro di pulizia del database](../../production/using/database-cleanup-workflow.md) (v7 ibrido/on-premise)
* [Configura nuovi tentativi di consegna](communication-channels.md) (v7 ibrido/on-premise)
* [Aggiorna qualifica per mancato recapito](update-bounce-qualification.md) (v7 ibrido/on-premise)
* [Configurazione recapito messaggi e-mail](../../installation/using/email-deliverability.md) (v7 ibrido/on-premise)
* [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7 ibrido/on-premise)

