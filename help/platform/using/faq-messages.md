---
product: campaign
title: Domande frequenti su test e invio
description: Domande frequenti su Campaign Classic
feature: Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 83%

---

# Convalidare, inviare e tracciare messaggi {#validate-send-track}



## Test e convalida {#test-and-validate-before-sending}

Scopri come eseguire i passaggi di test e convalida prima di inviare messaggi all’interno di Adobe Campaign.

### Cos’è l’analisi della consegna? {#what-is-the-delivery-analysis-}

L’analisi della consegna è la fase in cui viene calcolata la popolazione target e viene preparato il contenuto della consegna. Una volta completata, la consegna è pronta all’invio. Consulta i log per verificare che tutto sia corretto.

[Fai clic qui per ulteriori informazioni](../../delivery/using/steps-validating-the-delivery.md).

### Perché dovrei creare delle prove? {#why-should-i-create-proofs-}

Adobe consiglia vivamente di creare messaggi di prova per testare la consegna su un gruppo di approvazione prima di inviarla al target principale. Puoi quindi convalidare contenuto dei messaggi, personalizzazione e parametri di consegna.

[Fai clic qui per ulteriori informazioni](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Come si utilizzano gli indirizzi di seed in Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Gli indirizzi di seed vengono utilizzati per eseguire il targeting di destinatari che non corrispondono ai criteri di target definiti. Questi destinatari vengono aggiunti al target: possono essere importati o creati direttamente nella consegna o nella campagna. Per le consegne di direct mail, essi vengono aggiunti durante l’estrazione e mescolati nel documento di output.

Ciò offre i seguenti vantaggi:

* Sostituzione casuale di campi con dati provenienti dai profili dei destinatari: ciò ti consente di inserire solo l’indirizzo e-mail, ad esempio nella sezione dell’indirizzo di seed.
* Quando si utilizza un flusso di lavoro con funzionalità di gestione dei dati, i dati aggiuntivi elaborati nelle consegne possono essere inseriti a livello di indirizzo di seed per imporre dei valori: in questo modo si evita la sostituzione casuale dei valori.

[Fai clic qui per ulteriori informazioni sugli indirizzi di seed](../../delivery/using/about-seed-addresses.md).

### Come posso impostare un processo di approvazione prima di inviare messaggi? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

Per rilevare eventuali errori nella configurazione dei messaggi, Adobe consiglia vivamente di impostare un ciclo di convalida della consegna. Accertati che il contenuto sia approvato con la frequenza necessaria inviando delle prove a destinatari di test. Per approvare il contenuto, deve essere inviata una prova ogni volta che viene apportata una modifica.

[Fai clic qui per ulteriori informazioni](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Cos’è una regola di tipologia? {#what-is-a-typology-rule-}

Per evitare conflitti tra campagne, Adobe Campaign può sottoporre a test diverse combinazioni applicando regole di vincolo specifiche. Ciò garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali.

[Fai clic qui per ulteriori informazioni](../../campaign-opt/using/about-campaign-typologies.md).

## Inviare i messaggi {#send-your-messages}

Scopri come inviare messaggi in diversi canali con Adobe Campaign.

### Come posso inviare le e-mail in modo graduale? {#how-can-i-send-emails-in-waves-}

Prima di inviare una consegna a una popolazione numerosa, puoi [configurare delle ondate](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) per suddividere i messaggi in più batch e bilanciare il carico.

### Quali sono i passaggi chiave per creare un’e-mail in Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

Una volta creata e convalidata la consegna dell’e-mail, puoi inviarla. Puoi decidere di inviare l’e-mail al target principale immediatamente o pianificare una consegna per una data successiva. Se necessario, prima di questo passaggio, puoi anche effettuare una stima della popolazione target.

[Fai clic qui per ulteriori informazioni](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Come si pianifica una consegna? {#how-to-schedule-a-delivery-}

Puoi posticipare la consegna dei messaggi per pianificare la consegna o per gestire la pressione di vendita ed evitare di sollecitare eccessivamente una popolazione.

[Fai clic qui per ulteriori informazioni](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Posso aggiungere un allegato alle e-mail? {#can-i-add-an-attachment-to-emails-}

Con Campaign Classic, puoi aggiungere allegati personalizzati alle e-mail.

[Fai clic qui per ulteriori informazioni sugli allegati e-mail](../../delivery/using/attaching-files.md).

## Tracciare i messaggi e misurarne l’impatto {#track-your-messages-and-measure-their-impact}

Dopo aver inviato i messaggi, scopri come tracciarne e misurarne l’impatto con Adobe Campaign.

### Come posso configurare collegamenti tracciati in una consegna e-mail? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

Per ogni consegna, puoi tracciare la ricezione dei messaggi e l’attivazione dei collegamenti inseriti nel contenuto del messaggio. In questo modo puoi tracciare il comportamento dei destinatari in seguito alle azioni di consegna per le quali sono stati oggetto di targeting.

Per ogni URL del messaggio, puoi scegliere se attivare o meno il tracking, cambiare l’etichetta del collegamento, raggruppare i collegamenti per categorie, ad esempio a scopo di reporting.

[Fai clic qui per ulteriori informazioni](../../delivery/using/about-message-tracking.md) su come tracciare i messaggi in Campaign Classic.

### Dove posso accedere ai registri di consegna e di tracciamento? {#where-can-i-access-delivery-and-tracking-logs-}

Scopri come tenere traccia delle consegne e comprendere il comportamento dei destinatari [da questa pagina](../../delivery/using/delivery-dashboard.md).

### Dove posso ottenere i report di consegna? {#where-can-i-get-delivery-reports-}

 Adobe Campaign dispone di una serie di report per monitorare le consegne e tracciare i messaggi.

[Fai clic qui per ulteriori informazioni sui report integrati](../../reporting/using/delivery-reports.md).

### In che modo Adobe Campaign definisce e gestisce gli indirizzi in quarantena? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

 Adobe Campaign gestisce un elenco di indirizzi in quarantena. I destinatari il cui indirizzo è stato messo in quarantena sono esclusi per impostazione predefinita durante l’analisi della consegna e non saranno oggetto di targeting. Un indirizzo e-mail può essere posto in quarantena, ad esempio, quando la casella di posta è piena o se l’indirizzo non esiste.

[Fai clic qui per ulteriori informazioni sulla gestione della quarantena](../../delivery/using/understanding-quarantine-management.md).
